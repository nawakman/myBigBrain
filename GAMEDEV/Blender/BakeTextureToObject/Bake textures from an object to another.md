[[Blender]]
context: I use photogrammetry to make a 3d file of a figurine, the texture it generated was just horrible, didn't seem like UV unwrapping, more like photos slapped together (left). Plus, I wanted a lowpoly version of it because the scanned version had way too much polygons, so I needed to reproject the texture too. So I wanted a cleaner, reprojected version. At the end I got this (right)
![[awfulTexture.jpg|300]] ![[bakedGrogu.png|300]] 
Even if it does not look any better (because I used smart uv project), the physically near areas are now represented next to each other on the picture. Physically, baking do not change anything if used on the same model, however if you make a lowpoly version of a model it can be useful to avoid texture artifacts.
![[groguVersions.png|700]]

In order to do this:

- On the object that will receive the texture, setup a material with an empty texture
- In hierarchy select first the object from which you want to take the texture, then ctrl+select the one to which it will be applied
- switch to cycles, in bake settings, tick "selected to active","bake type": diffuse, in "Influence" only keep "Color" else it will bake light too
- if there are artifacts tick "cage", let empty "cage object" and set Cage extrusion around 0.01m
- the two objects must be at the exact same position in space
- selecting in 3d view is not the same order as in the hierarchy
- "margin" is the amount of texture rendered outside UVmap to avoid artifacts
- Click "Bake"
- now the (previously) empty texture is filled