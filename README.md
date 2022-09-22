# MacOS Input Fixes

## What it does

Fixes [MC-121772](https://bugs.mojang.com/browse/MC-121772)

Fixes [MC-255800](https://bugs.mojang.com/browse/MC-255800)

Specific fixes:
- Correctly detects left click while control is pressed
- Make trackpad scrolling not scroll a rediculous number of items at once
- It also fixes momentum scrolling (which changes the number of scroll events based on how quickly you did it, even by like x5-10, meaning you couldn't easily scroll to the correct item)
- On the trackpad it also only considers scrolling while fingers are on the trackpad (and the same for any fancy mice that support the relevant api e.g. probably apple's fancy mice/trackpad thing)
- It also fixes (almost perfectly) scrolling being broken when shift is down, this issue only affects mice that use older input APIs and doesn't change anything on the trackpad. It converts scrolling with shift down which shows as horizontal scrolling to the correct vertical scroll, the only issue when you actually scroll horizontally and hold shift, this will show as vertical scrolling (which is imo acceptable since very few people would be scrolling Minecraft items with horizantal scrolling on a non-apple input device compared to people scrolling vertical on any mice; and they could, if they need, use vertical scrolling instead which would be completely consistent - and this also isn't an issue if the Minecraft item scroll direction for + vertical scrolling is treated the same as + horizontal scrolling). TL;DR - this project will work properly for both vertical and horizontal scrolling including when pressing shift.
- Fix scroll direction on macOS.

On platforms other than macOS, the mod does nothing, so it can be safely included in any modpack.

## Running

This mod requires Fabric, Fabric loader >= 0.14.9, and Minecraft 1.14+. I've only really tested it properly on 1.14 and 1.19.1, so ymmv, but it should work on all of the in-between versions.

## Setup

For setup instructions please see the [fabric wiki page](https://fabricmc.net/wiki/tutorial:setup) that relates to the IDE that you are using.

## Building

To build this, you also need to build the native file before building the mod itself any time you modify it. This can only be done on macOS and requires Apple's XCode (or command line-tools) to be installed on the machine. To build the native library, simply run `make clean && make` in the `src/main/native` directory. This should work on both intel and arm machines, but I've only tested in on an intel machine. The resulting binary supports both x64 and arm64, so no need to worry about the architecture of the native.

## License

This project is available under the BSD-3-Clause license.

Some files and/or folders may be under different license(s), please check any relevant files and folders to see if they are under a different license.

If you are Mojang, feel free to contact about licensing to possibly license the project under a different license if BSD-3-Clause doesn't work for you.
