env_meta.txt is a world file that is used to store various environmental data about a world, such as the time and LBM data. It is also prone to corruption, especially on Windows. (See [#9425](https://github.com/minetest/minetest/issues/9425))

## Corruption (and fix)
If env_meta.txt for a world is corrupted, trying to start the world will throw this error:

```
A fatal error occurred: attempted to query on non fully set up LBMManager
```

To fix, you should go into the last backup you have for the world and transplant the `env_meta.txt` found there. If you do not have a backup, then simply delete the file and the world will work again.

While resetting `env_meta.txt` will lead to the in-game time resetting and LBMs being re-run, it should not cause any damage to the map of the world itself.