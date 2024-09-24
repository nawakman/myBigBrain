[[Animation]]

In order to import one or multiple animations from Blender to Unity first open your Blender project, go into animation tab, then in the bottom open both a dope sheet and a non linear animation tab.

In the dope sheet go to action editor mode, then do the following for each animation:
	-select the animation in action editor
	-then in the NLA, in the hierachy near the animation name there will be a button (push down action), click it, yout current animation will appear in a new track (or in the same)

Then, in NLA, put every animation one after annother IN THE SAME TRACK and LEAVE ONE EMPTY FRAME between each(if you don't let frames between animations, in unity the frist frame off the animation will be broken with wrong scale and T-pose).

Once done, export animation to unity.

In unity, import separately the mesh only and the mesh with all anims, this way you can duplicate the animations from the mesh with all anims in order to sort it in another folder, and then delete the mesh with all anims. This way animations and mesh will be separated and workflow will be easier