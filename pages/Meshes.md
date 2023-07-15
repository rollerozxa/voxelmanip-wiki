Nodes and entities are able to use a custom mesh in order to create more detailed things than simple cubes or sprites.

## Static meshes
If you do not need any kind of animation, then you would want to use the `.obj` model format. It is very ubiquitous, and most 3D modelling software supports it, including software designed for voxel-esque models such as [Blockbench](https://www.blockbench.net/).

## Animated meshes
Using animated meshes are a bit more complicated, as Minetest does not support any modern model format that includes animation. The formats Minetest supports are the Blitz3D model format (`.b3d`) and the DirectX model format (`.x`). Out of these, `.b3d` is the least obsolete and broken one.

Usually Blender is used, as it is among the only software that has a reasonably functional exporter for these obsolete model formats. See [Using Blender](https://wiki.minetest.land/Using_Blender) for more information. You could use another software, but if it doesn't export to an appropriate format you will need to import it from your favourite software into Blender and export it there.