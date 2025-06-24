[[INTERESTING]]

**Method to cut shapes from pictures**

- Import png or jpeg in Cura by drag and drop
- Set height to your actual layer height and "darker is higher", and base layer height to 0
- extruder/bed temp 0 degree
- Download Z-offset plugin from Cura marketplace, and setup it according to your pen attachment (z distance between nozzle and blade tip)
- Wall line count 0
- top and bottom layer count both 0 to remove infill
- printing speed 60mm/s
The blade will go in the center of the sliced lines instead of the picture edge, set line width to 0.01 mm (or you can change "horizontal expansion" to adjust the line positions but this is less precise)

If you want the pen to go up after printing add end Gcode:
```
G91 ; relative coords in order to lift extruder from this position
G1 Z40 F10000 ; raise hotend 40 mm
G90 ; go back to absolute coords
```

*for writing/cutting text:*
use font with constant line width or some part of the letter will be ignored by the slicer
for example Reem Kufi or MedusaGothic

**Method for complex shapes/paths**

For example I made a svg file with [https://github.com/aaronse/hz-scratch-hologram](https://github.com/aaronse/hz-scratch-hologram) to make a [scratch hologram](https://www.youtube.com/watch?v=sv-38lwV6vc)

Next instructions mainly sourced from [this video](https://www.youtube.com/watch?v=6b_XMrfLMc0)

Open Inkscape,
- `File>>Document Properties`, then in custom size fill your buildplate dimensions
- Import your svg and adjust its size
- `Gcode tools>>Tools library`, select cylindrical cutter, a layer will appear, with text tools set 
	- diameter 0.01
	- feed 3600 (=print speed, units are mm/minute so 60mms is 3600)
	- penetration angle 90
	- penetration feed 600 (=z hop speed)
	- depth step 1
- `Gcode tools>>Orientation points`
	- 2-points mode
	- Z surface is the z coordinate of the surface of your material, but you want it to be **over** the surface, no carving it yet, so it will  =*Z depth + some safe offset to not touch the surface*
	- Z depth is the deepest the blade will enter in the material, **it is not an offset but a coordinate too**
	- I have a 3.6 tool offset (z distance with nozzle) and want to cut into 1.65mm acrylic so I put Z depth=5.25 and Z surface=6
	- 2 arrows with coordinates will appear, don't touch them
- `Gcode tools>>Path To Gcode`
	- In preference put the file name ending by `.gcode`
	- "Z safe height for G00 move over blank" is the height it should be to not touch cutting surface when moving, it **MUST BE GREATER OR EQUAL TO Z SURFACE**
	- click apply to generate the Gcode file (you need to be on "path to Gcode" tab or it won't work)

In the generated file you need to add the `G28` command somewhere so your 3d printer will search for the home (0,0,0 coordinates) before executing Gcode instead of just doing it relative to the current position and aggressively try to ram you printhead/bed over their limits.

Here is a python script that does it automatically to all Gcode files in the directory :

```python
import os

for filename in os.listdir('.'):
    if filename.endswith(".gcode"):
        filepath = os.path.join('.', filename)
        print(f"Processing file: {filepath}")
        with open(filepath, 'r') as f:
            content = f.read()

            if "G28" not in content:
                print("G28 not found, inserting it")
                modified_content = content.replace("G21 (All units in mm)", "G21 (All units in mm)"+"\nG28")
                with open(filepath, 'w') as f:
                    f.write(modified_content)
                    print(f"Successfully modified {filename}")
            else:
             print(f"G28 already found. No changes needed for {filename}")
    print("______________________")
```

Then run the Gcode on your machine