<div align=center>

<img src="extras/banner.png" alt="Banner" width="40%">

</div>
<h1 align=center>Sonic Triple Trouble 16-bit Android Port</h1>

This is a wrapper/port of the Android version of *Sonic Triple Trouble 16-Bit* (`com.noahncopeland.game`, v1.2.8). It loads the original game binaries and runs them: we natively run the original Android ARM64 `.so` file inside a minimal emulated Android environment on the Nintendo Switch.

### How to Install

To play this game, you will need the **`.apk`** file for **version 1.2.8** (Android arm64-v8a build). You can get it for free from the official page:

👉 **[https://gamejolt.com/games/sonictripletrouble16bit/322794](https://gamejolt.com/games/sonictripletrouble16bit/322794)**

> Download → select the **Android (arm64-v8a)** build.

From it, you need:
* **`lib/arm64-v8a/libyoyo.so`** — the GameMaker Studio 2 game engine.
* **`lib/arm64-v8a/libc++_shared.so`** — the C++ runtime.
* The **entire `assets/` folder** from your `.apk` (containing `game.droid`, `audiogroup*.dat`, and all other game data).
* The **`.apk` file itself**, renamed to **`game.apk`**.

#### Setup Instructions:

1. Create a folder called `stt16bit_nx` inside the `switch` folder on your SD card (i.e. `sdmc:/switch/stt16bit_nx/`).
2. Extract **`lib/arm64-v8a/libyoyo.so`** from your `.apk` and copy it to `sdmc:/switch/stt16bit_nx/libyoyo.so`.
3. Extract **`lib/arm64-v8a/libc++_shared.so`** from your `.apk` and copy it to `sdmc:/switch/stt16bit_nx/libc++_shared.so`.
4. Copy the **entire `assets/` folder** from your `.apk` into `sdmc:/switch/stt16bit_nx/assets/`.
5. Copy the **`.apk` file itself** to `sdmc:/switch/stt16bit_nx/` and rename it to **`game.apk`** (so its path is `sdmc:/switch/stt16bit_nx/game.apk`).
6. Copy **`stt16bit_nx.nro`** into `sdmc:/switch/stt16bit_nx/`.

Your final layout should look like this:

```
sdmc:/switch/stt16bit_nx/
├── stt16bit_nx.nro
├── libyoyo.so
├── libc++_shared.so
├── game.apk
└── assets/
    ├── game.droid
    ├── audiogroup0.dat
    ├── audiogroup1.dat
    └── ... (all other asset files)
```

### Notes

* This port **will not work** in applet mode (Album). Please launch the Homebrew Menu using a game override (hold the **R** button while launching any installed game) to give it full memory access and the required syscalls.
* Save data (`save.sav`) and `config.txt` are kept in `sdmc:/switch/stt16bit_nx/`.

### Configuration

`config.txt` is created on first run and supports the following options:
* `screen_width` / `screen_height` — render resolution; invalid values automatically pick 1280×720 in handheld mode and 1920×1080 in docked mode.
* `language` — game language code (e.g. `en`, `de`, `fr`, `es`, `it`, `pt`, `ru`, `ja`).

### How to Build

You will need the `devkitA64` toolchain and the following `devkitPro` packages:
* `switch-dev`
* `switch-sdl2`
* `switch-mesa`
* `switch-libdrm_nouveau`
* `switch-freetype`
* `switch-libpng`
* `switch-ffmpeg`

Run `make` to compile.

### Credits

* [fgsfdsfgs](https://github.com/fgsfdsfgs) for [ct_nx](https://github.com/fgsfdsfgs/ct_nx) and [max_nx](https://github.com/fgsfdsfgs/max_nx), which this loader is heavily based on.
* [TheOfficialFloW](https://github.com/TheOfficialFloW) for the original Vita ports that pioneered the Android `.so` loading technique.
* [Noah Copeland](https://gamejolt.com/games/sonictripletrouble16bit/322794) for *Sonic Triple Trouble 16-Bit*.

### Legal

This project has no direct affiliation with SEGA or YoYo Games. "Sonic the Hedgehog" is a trademark of SEGA. "GameMaker Studio" is a trademark of YoYo Games Ltd. All Rights Reserved.

No assets or program code from the original game are included in this repository. We do not condone piracy and encourage users to legally obtain the original game from the official source linked above.

Unless specified otherwise, the source code provided in this repository is licensed under the MIT License. Please see the accompanying LICENSE file.
