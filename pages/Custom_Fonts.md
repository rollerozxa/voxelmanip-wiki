Currently the Minetest engine does not officially support custom fonts sent as media by a game or mod (See issue [#10416](https://github.com/minetest/minetest/issues/10416)). However if you are making a singleplayer game there is a workaround that requires changing the engine's font settings from a mod.

As you will be making changes that set global settings, please be mindful of the player's previous settings! You should reset back to the original settings' values on shutdown, and take extra precautions in the case of an unclean shutdown. See [Caution](#Caution) for more on that.

[toc]

## Example
Say for example you have some fonts in a folder at the root of your game's directory, and a mod in your game that will set the font settings. This would be the file structure:

```
cool_game/
  fonts/
    Archivo-Bold.ttf
    Archivo-BoldItalic.ttf
    Archivo-Italic.ttf
    Archivo-LICENSE.txt
    Archivo-Regular.ttf
  mods/
    cool_game_mod/
      init.lua
```

The font path settings require an absolute path, so you need to construct an absolute path to the font files inside of your game. This code takes the mod's path, goes up to the game's root and then into the fonts folder:

```lua
-- cool_game/mods/cool_game_mod/init.lua

local modpath = minetest.get_modpath(minetest.get_current_modname())
local modname = minetest.get_current_modname()

local fontpath = modpath:gsub("/mods/"..modname, "") .. "/fonts/"
```

The variable `fontpath` could for example become `/home/rollerozxa/.minetest/games/cool_game/fonts/`, which is where the fonts provided would be located. Now you can set the font settings you want to change to load your game's provided fonts:

```lua
for key, value in pairs{
	font_path = fontpath.."Archivo-Regular.ttf",
	font_path_bold = fontpath.."Archivo-Bold.ttf",
	font_path_italic = fontpath.."Archivo-Italic.ttf",
	font_path_bold_italic = fontpath.."Archivo-Bold-Italic.ttf",
	font_size = 18,
	font_shadow_alpha = 255,
} do
	minetest.settings:set(key, value)
end
```

## Caution
It is very important to note that setting the font path like this **WILL take effect outside of your game,** as settings set from a mod will be saved to the player's global settings file.

You should save the previous values of the font settings you change in a persistent storage (e.g. [[ModStorage]]), both such that it can be reset on shutdown, and to recover previous settings if the game crashed. For example, if the game detects previous settings existing in storage it can assume an unclean shutdown and opt to reset the settings to what the user had set previously during the next clean shutdown. (TODO: example of such a system)
