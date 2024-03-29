LuaJIT is a just-in-time compiler for Lua, which implements the language as it was in the reference Lua 5.1 implementation (referred to as PUC Lua to distinguish it) albeit with some additions and differences see ([[LuaJIT Differences]]).

More often than not, unless you have compiled Minetest from source without LuaJIT, Minetest will use LuaJIT as its Lua runtime. The official Windows, Android and most packaged Linux builds should be compiled with LuaJIT enabled. To confirm what Lua runtime Minetest is built with you can open a terminal and run `./minetest --version`.

If you are using LuaJIT the result would look something like this:

```
$ ./minetest --version                                                                                                                                        
[...]
Using LuaJIT 2.1.1702233742
```

If you are using PUC Lua the result would look something like this:

```
$ ./minetest --version                                                                                                                                        
[...]
Using Lua 5.1.5
```

When building from source, Minetest will always use LuaJIT if it is found on the system. This usually means having the development package for it installed. If LuaJIT is not found or if `-DENABLE_LUAJIT=FALSE` is explicitly passed then Minetest will fall back to the vendored PUC Lua 5.1.

## "Do I have LuaJIT?" Flowchart
If you are still unsure, you can consult this (tongue-in-cheek) flowchart on whether you have LuaJIT:

![](/images/luajit.webp)
