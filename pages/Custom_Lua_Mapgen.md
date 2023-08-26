The Minetest engine provides several built-in mapgens implemented in C++, where biomes and decorations can be registered by mods. In addition to this you can also write your own mapgen in Lua. Usually this is done by hooking into the `singlenode` mapgen (by default consisting only of void) and generating your own terrain in the `on_generated` callback using VoxelManip.

## Performance
While it is possible to write very performant Lua mapgens, it will always generally be slower compared to C++ mapgens that run in their own thread and don't block the Lua thread. (This will be fixed once [#13092](https://github.com/minetest/minetest/pull/13092) is merged)

For a list of optimisation techniques you can use to write performant mapgens, see [[Mapgen Optimisations]].

## Examples
A good initial example of how to write a custom Lua mapgen is [lvm_example](https://content.minetest.net/packages/ROllerozxa/lvm_example/). It incorporates most optimisations techniques to create a performant mapgen and uses Perlin noise to generate random looking terrain.

For more examples of custom Lua mapgens, see the [Custom mapgen](https://content.minetest.net/packages/?type=mod&page=1&tag=custom_mapgen) tag on ContentDB.

## Libraries
- [Luamap](https://content.minetest.net/packages/MisterE/luamap/) is a library that seeks to take out some of the pain of making custom mapgens by abstracting it away.

- [Biomegen](https://content.minetest.net/packages/Gael%20de%20Sailly/biomegen/) reimplements the biome system used in built-in C++ mapgens for use with custom Lua mapgens.