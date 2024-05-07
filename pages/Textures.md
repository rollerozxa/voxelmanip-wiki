This page lists the image formats that Minetest supports for textures, along with information on optimising them or working with them programmatically.

[toc]

## PNG (`.png`)
PNG is an all-round good image format, with lossless compression.

### Optimising
PNG files can be losslessly optimised using the [`optipng`](https://optipng.sourceforge.net/) tool, which is useful for trimming the filesize of all textures without losing any important information.

When run with no arguments `optipng` optimizes completely losslessly (no color, metadata or transparency is lost). However there are arguments in addition that can be added in order to further reduce the size or to preserve specific data you might want to keep. A more exhaustive list of arguments and what they do can be found in optipng's manual or in the help text available with `optipng -h`.

* **`-strip all`**: Strips all image metadata your image editor has embedded into the image.
* **`-o7 -zm1-9`**: Sets both optipng and zlib's optimization/compression levels to the highest available. Will take significantly longer to optimise but can further reduce the file size.
* **`-nc`**: Disables color type reduction. **This is necessary if you have color data you want to preserve in transparent pixels, such as ones in leaf textures.**

A general-purpose script for optimizing images as aggressively as possible without losing color information can be found in Minetest Game: [optimize_textures.sh](https://github.com/minetest/minetest_game/blob/master/utils/optimize_textures.sh)

For lossy optimisation of PNG files, there is `pngquant`. It will throw away (hopefully unnoticeable) colour data and replace it with dithering. This is useful for larger images (e.g. game backgrounds) where the loss of colour data isn't noticeable, but the filesize is substantially smaller.

### Encoding and Decoding
Since 5.5.0 Minetest has a built-in function to encode PNG files, `minetest.encode_png`. However it is known to generate large, unoptimised images and does not support writing indexed images.

[`modlib`](https://github.com/appgurueu/modlib) contains both an encoder and decoder for PNG images.

## JPEG (`.jpg` / `.jpeg`)
JPEG is a lossy image format. It is useful for large photorealistic textures such as skyboxes or high-resolution textures.

### Optimising
JPEG images can be optimised using `guetzli`, which reencodes a JPEG image as optimal as possible for the lowest filesize while not reducing the quality.

## TGA (`.tga`)
TGA is a simple format, that either is an uncompressed stream of pixel data or with RLE encoding, depending on the format type of the file.

Due to its simplicity, it is easy and quick to programmatically generate TGA images on the fly.

Minetest only supports Type 1-3 and 10 TGA images, if you try to load an unsupported type it will give an `Unsupported TGA file type` error.

### Encoding
[`tga_encoder`](https://content.minetest.net/packages/erlehmann/tga_encoder/) can be used to encode TGA images. It supports both compressed and uncompressed TGA format types.

## BMP (`.bmp`)
Another simple format like TGA. It is kept due to IrrlichtMt depending on it for built in fonts, but might be dropped in the future and isn't recommended to be used.

## Older versions
Prior to 5.5.0, Minetest used to be able to load PCX, PPM, PSD, PVR, DDS, WAL, LMP and RGB as part of Irrlicht's image loading capabilities. These are no longer supported and should be converted to a format that is still supported.
