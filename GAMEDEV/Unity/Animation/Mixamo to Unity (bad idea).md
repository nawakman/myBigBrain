[[Animation]]
[[Mixamo to Blender]]

You don't want to import directly from Mixamo to Unity because mixamo animations use root motion, which mean in unity it moves the game objects it is attached to regardless of its name.

Plus, you can't use mixamo animations with unity animation layers, beacause of the absence of root bone name in the animation, I tried everything to get it working but you really can't with this setup.

Passing by blender gives a name to the animation root bone so unity now know what bone to move first, and how to apply avatar mask on these animations. 