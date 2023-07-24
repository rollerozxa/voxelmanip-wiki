Nodes (also called blocks by players) are what make up the voxel terrain in Minetest. They are generally cubic in shape, with a full node being considered one cubic meter in volume, and make up the voxel world. Only one node can exist in a particular position in the voxel grid, but can extend into other cells and take wildly different shapes. In most games, the player is able to break and place nodes to shape the terrain into what they see fit, or can be interacted with to provide different gameplay functions. 

Usually games and mods register their own nodes, but the engine also registers some technical nodes.

## Built-in nodes

### Air
Air (itemstring `air`, `CONTENT_AIR` in C++) is a technical node that exists in every generated area that no other node exists in. It is a fully transparent node, using the airlike drawtype and being unpointable.

### Ignore
Ignore (itemstring `ignore`, `CONTENT_IGNORE` in C++) is an airlike technical node that exists in place of ungenerated and unloaded mapblocks. If `minetest.get_node` is called on an unloaded mapblock, it will return Ignore.

### Unknown Node
An unknown node takes the place of any node that exists in the world that is no longer being registered, whether it be due to a mod being removed of updates to a game changing itemstrings. Unknown Node is not a node in itself, but can be any node with an unregistered itemstring.