# Star Fox EX Overclocked

Star Fox EX source code adapted for overclocked SuperFX cartridge development.

> **NR-RetroWorks fork notice:** This repository is an overclocking-focused fork of the original [Star Fox EX project](https://github.com/Sunlitspace542/star-fox-ex), maintained by NachtRaveVL for use with the **33MHz+ SuperFX overclocking PCB** sold through [NR-RetroWorks on Etsy](https://www.etsy.com/shop/NachtRaveRetroWerks). The upstream repository remains the general-purpose source project.
>
> **The hardware overclock is external:** a replacement clock source drives the SuperFX hardware. Source-level configuration and timing work are separate from the physical clock change.

Go [here](#building) to jump straight to the build instructions.

## Credits (A-Z)

- **Argonaut Software and Nintendo** — Original Star Fox development.
- **Kandowontu** — Star Fox EX programming and rumble support.
- **Nachtrave** - Optimizations, overclocking/elapsed time fixes, FASTROM support
- **Randal Linden (Randy)** — Rumble and Super FX 3 work, as credited in-game.
- **Random** — Music contributions and the MSU-1 soundtrack arrangements described by upstream.
- **Sunlit** — Original Star Fox EX project maintainer and programmer.

## Features

### Cartridge Hardware Support and ROM Configuration

- Intended for real **GSU-2 SuperFX hardware overclocked to approximately 33MHz+** using the NR-RetroWorks overclocking adapter PCB
- Super FX clock divider disabled via `fast equ 1`
- Super FX MS1 high-speed multiply enabled
- FastROM support
- MSU-1 support

### Accessory and Feature Support

- Existing rumble support and the corresponding in-game credits remain in the codebase.
- Existing MSU-1-related source, soundtrack cues, and release infrastructure remain available, subject to the relevant permissions and build settings.
- The current EX source contains the 1.11.03 upstream work, including its later sound, code, and credits updates.

### Miscellaneous

- **Kando and Randy were involved so you know it's good**

## Building

### Building on Windows

**Requirements:** Microsoft Windows, the included DOS-based assembly/toolchain files, and the DOSBox-X environment configured for the project.

Download or clone the repository:

```bash
git clone https://github.com/NachtRaveVL/star-fox-ex-oc.git
```

The root provides `1build.cmd`, `BUILD.BAT`, `BLDSG.BAT`, and other build scripts. Use the supplied DOSBox-X workflow and inspect configuration such as `SFES/VARS.INC` and command-line build flags before selecting a hardware or emulator build.

**Do not assume that the upstream release scripts are already configured for a finished 26 MHz OC release.** Validate the generated ROM and the intended cartridge configuration before distribution or hardware use.

### Uploading to SNES with SD2SNES / FXPAK Pro

The repository includes USB upload command scripts such as `send2snes.cmd`. Use the required [QUsb2Snes](https://github.com/Skarsnik/QUsb2snes/releases) setup and a compatible device, and verify the build first.

## Upstream History and Music Attribution

Sunlit archived the original Star Fox EX repository on **November 8, 2026**, following the **1.11.03** update. That archival decision applies to the upstream project, not to this independently maintained OC fork.

The upstream README identifies **Random** as composer of the new MSU-1 soundtrack arrangements and states that reuse requires Random's permission. Continuing this fork does not change that requirement; soundtrack arrangements should not be redistributed or reused without the relevant permission.

## Contributing

Pull requests and corrections are welcome. Submit changes against this fork's [`main`](https://github.com/NachtRaveVL/star-fox-ex-oc/tree/main) branch. Preserve existing credits, birthday messages, and third-party attribution.

## Helpful Links/Tools

[NR-RetroWorks](https://nr-retroworks.com/)  
[NR-RetroWorks on Etsy](https://www.etsy.com/shop/NachtRaveRetroWerks)  
[NR-RetroWorks on Patreon](https://www.patreon.com/nachtrave)  
[Original Star Fox EX Repository](https://github.com/Sunlitspace542/star-fox-ex)  
[Star Fox EX Archive](https://archive.org/details/Starfox-EX-Archive)  
[ArgSfx/SASM Assembler Manual](https://github.com/Sunlitspace542/ArgSfx-SASM-Docs/tree/main)  
[Super FX (MARIO) Chip ASM Reference](https://en.m.wikibooks.org/wiki/Super_NES_Programming/Super_FX_tutorial)

## Project Structure

```text

star-fox-ex-oc
├── SFES: Main Star Fox EX source code directory
│   ├── *.ASM: Main game code (65816)
│   ├── *.MC: Super FX (MARIO) assembly code
│   ├── *.INC: Assembly includes and configuration
│   ├── *.EXT: External symbol declarations
│   ├── DATA: Graphics and other game data
│   ├── FACE: Character portrait assets
│   ├── MAPS: Level scripts
│   ├── MSPRITES: Super FX textures
│   ├── MSU1: MSU-1 driver, macros, and track definitions
│   ├── SND: Sound and music data
│   ├── docs: Technical documentation and bank information
│   └── tex: Texture graphics
├── SOUND_SRC: Reconstructed sound source files
│   ├── Track directories: Individual music and sound sources
│   ├── Makefile: Sound build automation
│   └── README.md: Sound source documentation
├── BIN: Assemblers, linkers, and build utilities
├── baseroms: Base ROM setup and documentation
├── manual_source: Manual, box art, and label source files
├── msu1-map1-srcdata: MSU-1 Map 1 audio sources
├── msu1-map2-srcdata: MSU-1 Map 2 audio sources
├── release-data: Release support assets
│   ├── Cover, Box Art, Labels, and Branding
│   ├── Star Fox EX Changelog.txt
│   ├── Star Fox EX Manual.pdf
│   └── Additional release documentation
├── releases: Output directory for release packages
├── BUILD.BAT: ROM build script
├── BLDSG.BAT: Alternative ROM build script
├── 1build.cmd: DOSBox-X build launcher
├── 2buildrelease.cmd: Release patch and package generation
├── bankreport.py: ROM bank usage reporting
├── build and send to snes.cmd: Build and upload to SNES
├── build palette.cmd: Palette build launcher
├── clean.cmd: Build cleanup launcher
├── dosbox-x.conf: DOSBox-X configuration
├── version.cmd: Release version configuration
└── README.MD: Project overview and build documentation
```
