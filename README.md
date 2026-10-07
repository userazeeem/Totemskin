<div align="center">

# TOTEM SKIN

**A small Fabric mod that gives the Totem of Undying a new face.**

![Minecraft](https://img.shields.io/badge/Minecraft-26.2-1f1f1f?style=flat-square)
![Loader](https://img.shields.io/badge/Loader-Fabric-1f1f1f?style=flat-square)
![Java](https://img.shields.io/badge/Java-25+-1f1f1f?style=flat-square)
![Side](https://img.shields.io/badge/Side-Client-1f1f1f?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-1f1f1f?style=flat-square)

</div>

---

## Overview

Totem Skin replaces the look of the Totem of Undying with a custom animated character. The totem sways and hops wherever you see it, in your hands, in your inventory, on the ground and in item frames.

It changes only how the item looks. Nothing about how the totem works is touched, so it is safe to use on any server.

---

## Features

- Custom texture for the Totem of Undying in the main hand and the off hand
- Works in both first person and third person (F5)
- Shows in the inventory, chests and every other item slot
- Shows on the ground when the totem is dropped
- Shows in item frames
- Animated dance made of 24 frames, with sway, hop and squash and stretch
- Client-side only, with no gameplay changes
- Pixel art kept sharp, with no blurring between frames

---

## Requirements

| Requirement | Version |
| --- | --- |
| Minecraft | 26.2 |
| Fabric Loader | 0.19.5 or newer |
| Fabric API | Any compatible version |
| Java | 25 or newer |

---

## Installation

1. Install Fabric Loader for Minecraft 26.2.
2. Download Fabric API and place it in your `mods` folder.
3. Download `totemskin-1.0.0.jar` and place it in the same `mods` folder.
4. Launch the game using the Fabric profile.

The `mods` folder on Windows is found at `%appdata%\.minecraft\mods`.

---

## How It Works

Totem Skin is built on item model definitions and an animated texture. No code is needed to change the look.

```
assets/
  minecraft/
    items/
      totem_of_undying.json        chooses the custom model
  totemskin/
    models/item/
      totem_offhand.json           size and position for each view
    textures/item/
      totem_offhand.png            animation frames, stacked vertically
      totem_offhand.png.mcmeta     animation speed
```

The item definition selects the custom model for each display context: both hands in first and third person, the inventory, the ground and item frames. The model file sets the scale and position for each view. The texture is a tall strip of 128 by 128 frames, and the `.mcmeta` file tells the game to play them in order.

---

## Customising

### Change the animation speed

Edit `totem_offhand.png.mcmeta`:

```json
{
  "animation": {
    "frametime": 2,
    "interpolate": false
  }
}
```

A lower `frametime` plays faster, and a higher one plays slower.

### Change the size or position

Edit the `display` block in `totem_offhand.json`. For each view, `translation` moves the item as left and right, up and down, forward and back. `scale` changes its size.

### Use your own image

Replace `totem_offhand.png` with your own transparent PNG. For a still image, use a single square frame and delete the `.mcmeta` file. For an animation, stack square frames from top to bottom.

---

## Building From Source

Clone the repository and run the build from the project folder.

```
git clone https://github.com/YOUR_USERNAME/totemskin.git
cd totemskin
.\gradlew build
```

On Linux or macOS, use `./gradlew build` instead.

The finished jar is written to `build/libs/`. Use the file without `-sources` in its name.

To test in a development client:

```
.\gradlew runClient
```

---

## Compatibility

Totem Skin overrides the item definition for `minecraft:totem_of_undying`. If another mod or resource pack changes the same item, only one of the two will be shown, depending on load order.

---

## Credits

Created by **Mohammed Azeem**.

---

## License

Released under the MIT License.