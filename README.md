# Doom Classic Port for HOLY CORE

A port of the classic Doom game to the [HOLY CORE](https://github.com/0BAB1/HOLY_CORE_COURSE) RISC-V platform.

## Credits

This port is based on:
- [smunaut's RISC-V Doom port](https://github.com/smunaut/doom_riscv)
- Pulled from [knazarov's repository](https://git.knazarov.com/knazarov)

## Overview

This implementation outputs video to a 2.8" SPI TFT display with an ILI9341 controller. The SPI communication is handled in hardware using Xilinx's AXI-to-SPI IP core, making this a hardware-accelerated setup.

**Note:** The display configuration in `i_video.c` is specific to this hardware setup. You'll need to adapt it for different display controllers or communication interfaces.

## Prerequisites

### Required Tools
- RISC-V GNU toolchain
- HOLY CORE library (or equivalent SoC library)
- Make

### Hardware Requirements
- HOLY CORE RISC-V SoC
- 2.8" SPI TFT display (ILI9341 controller)
- Xilinx AXI-to-SPI IP core (or adapt `i_video.c` for your hardware)

### Configuration

Before building, verify the following:

1. **SoC Address Definitions**: Ensure memory-mapped peripheral addresses in the HOLY CORE library match your hardware configuration
2. **Video Output Settings**: Check `i_video.c` to confirm SPI and display controller addresses are correct for your setup

## Building

```bash
cd src/holy_core
make
```

The build process generates multiple output formats:
- Binary (`.bin`)
- ELF executable (`.elf`)
- Hexdump format (for HDL simulation)

## Adaptation Notes

If you're using different hardware:
- Modify `i_video.c` to match your display interface (parallel, different SPI controller, etc.)
- Update peripheral base addresses in both the HOLY CORE library and `i_video.c`
- Adjust the display initialization sequence if using a different LCD controller

## "Run it" guidelines

Franckly, you need to have the exact same setup as me to run this.

**Therefore, there is no "how to run tutorial"** to be found here. Seriously, you need the same screen (TFT 2.8"), same screen controller (ILI9341), same fpga board (arty S7-50), same SoC memory map, same SPI controller in the SoC (Xilinx AXI-QSPI), same CPU (HOLY CORE), same base I/O librairy ([holy core lib](https://github.com/0BAB1/HOLY_CORE_COURSE/tree/master/3_perf_edition/hc_lib)).

Maybe I'll make a tutorial / quickestart guide in the future but might as well teach you how to make your own DOOM port at this point, like there is too much moving parts.