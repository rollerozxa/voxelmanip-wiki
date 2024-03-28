This page contains a list of tools that are useful for developing games and mods for Minetest.

## General Lua Tools
- [luacheck](https://github.com/lunarmodules/luacheck): Lua linter and static code analyser (see also [the chapter in rubenwardy's modding book](https://rubenwardy.com/minetest_modding_book/en/quality/luacheck.html))
- [busted](https://olivinelabs.com/busted/): Lua unit testing framework (see also [the chapter in rubenwardy's modding book](https://rubenwardy.com/minetest_modding_book/en/quality/unit_testing.html))
- [Lua pattern viewer](https://gitspartv.github.io/lua-patterns/): A site like Regexr but for visualising and working with Lua patterns.

## Debugging/profiling
- [debug](https://content.minetest.net/packages/LMD/dbg/): Minetest mod library that offers more debugging capabilities.
- [LuaJIT Profiler](https://content.minetest.net/packages/jwmhjwmh/jitprofiler/): Minetest mod that allows you to profile mods using LuaJIT's built-in profiler and Flamegraph.

## Schematics
- [Schematic Editor](https://content.minetest.net/packages/Wuzzy/schemedit/): Minetest mod that allows you to import, edit and export schematics straight within Minetest.
- [MTS Editor](https://forum.minetest.net/viewtopic.php?f=14&t=23724): Standalone program to view and edit Minetest schematics, but it supports other file formats (e.g. Minecraft schematics) as well.
- [Lua2Mts](https://content.minetest.net/packages/Neuromancer/lua2mts/): Minetest mod to convert .lua schematics to .mts schematics.

## Perlin Noise
- [Perlin Explorer](https://content.minetest.net/packages/Wuzzy/perlin_explorer/): Minetest mod that allows you to experiment with all sorts of perlin noise.

## 3D models
- Blender: Essential for making animated models in Minetest, see [Using Blender](https://wiki.minetest.land/Using_Blender).
- [Blockbench](https://www.blockbench.net/): Useful for making static voxel models for Minetest.
- [NodeBoxEditor](https://forum.minetest.net/viewtopic.php?f=14&t=2840): External program to make nodebox models for Minetest.

## Formspecs
- [formspec_editor](https://content.minetest.net/packages/Just_Visiting/formspec_editor/): Minetest game that allows you to write formspecs and preview them instantly within Minetest.
- [Minetest Formspec Editor](https://luk3yx.gitlab.io/minetest-formspec-editor/): WYSIWYG online formspec editor

## Translation
- [mod_translation_updater](https://github.com/minetest/minetest/blob/master/util/mod_translation_updater.py): Python script to create and update mod translation files (\*.tr)
- [minetest_translation_tools](https://codeberg.org/Wuzzy/minetest_translation_tools): Additional Python scripts for maintaining Minetest mod translations
