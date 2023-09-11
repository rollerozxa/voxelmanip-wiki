MSYS2 is a collection of tools and libraries providing you with an easy-to-use environment for building, installing and running native Windows software. This page lists how to compile Minetest on Windows using MSYS2.

[toc]

## Installation
Please download and install the latest version of MSYS2 here: https://www.msys2.org/

After installation, a terminal opens. Run the following command to update the environment:

```bash
pacman -Syu
```

The terminal will then ask you to close it when done. Proceed with doing so, and then go to the start menu and run MSYS MINGW64 (the one with a blue background). Run the commands below to install the necessary dependencies.

## Compiling
First install all the necessary dependencies:

```bash
pacman -S git base-devel mingw-w64-x86_64-{toolchain,cmake,ninja,curl,libpng,libjpeg-turbo,freetype,libogg,libvorbis,sqlite3,openal,zstd,gettext}
```

Navigate to some folder where you want to clone the Minetest repository. To get out of MSYS' home folder and into your regular users folder, you would want to enter something like this:

```bash
cd /c/Users/<username>/Documents
```

Clone Minetest and IrrlichtMt:

```bash
git clone --depth 1 https://github.com/minetest/minetest.git
cd minetest
git clone --depth 1 https://github.com/minetest/irrlicht.git lib/irrlichtmt
```

And start the building process:

```bash
mkdir build; cd build
cmake .. -G Ninja
ninja
```

Once it's finished compiling, there should be a minetest.exe executable inside of `bin/` inside your Minetest folder. You can run it inside of the MINGW64 terminal by doing `../bin/minetest.exe`, but it will not work if you try to open the executable from Windows explorer, as the necessary DLLs aren't next to the executable.

## Bundling DLLs
For bundling DLLs, [mingw-bundledlls](https://github.com/mpreisler/mingw-bundledlls) will be used which is a Python script that will copy over any libraries the executable is linked against and put it next to the executable.

If you're lazy, run the following commands from the build directory to install Python and download the script:

```bash
pacman -S mingw-w64-x86_64-python
curl https://raw.githubusercontent.com/mpreisler/mingw-bundledlls/master/mingw-bundledlls > ../mingw-bundledlls
chmod +x ../mingw-bundledlls
```

When you have downloaded the script, usage is as such:

```bash
../mingw-bundledlls --copy ../bin/minetest.exe
```

It will print out a list of libraries it has copied to the binary folder once finished. Now it should be possible to run the Minetest executable outside of the MINGW64 terminal.

## Notes

### Something about packages being untrusted or corrupted?
If you have an existing MSYS2 install that has been dormant for a while without updates, you might run into issues trying to install or update packages as the keyring is outdated. See [this section](https://www.msys2.org/docs/updating/#potential-issues) on the MSYS2 website on how to solve this.

### Building 32-bit
The instructions above assume you want to build a 64-bit version of Minetest using MINGW64. If you want to build a 32-bit version of Minetest you would want to use the MINGW32 terminal (grey background).

When installing dependencies, replace `x86-64` with `i686` to get their 32-bit counterpart.

### Graphics is broken in a VM
If you're doing this inside of a VM and you want to test the executable but get graphics issues due to a lack of hardware acceleration, you can try downloading the Mesa software renderer as a DLL. [Download the 64-bit version of the DLL here](https://fdossena.com/?p=mesa/index.frag) and put it next to the executable in `bin/`. It will be slow but should be usable for testing.