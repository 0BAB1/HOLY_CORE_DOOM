# Doom classic port to the HOLY CORE

Based on smunaut's Version : [https://github.com/smunaut/doom_riscv](link).
Pulled from this knazarov's repo : [https://git.knazarov.com/knazarov](link).

## Prerequisites

- risv gnu toolchain
- some holy core librairy or equivalaent
- make sure the SoC addresses definitions are right in the holy core library and `i_video.c`.
- `i_video.c` output the image to an SPI based TFT 2.8" screen (ili9341 controller) and uses a Xilinx's AXI to SPI IP to actually generate the SPI signals via hardware, making this setups quite specific, make sure you adapt `i_video.c` if needed.

## Build

- `cd` into `src/holy_core`.
- run `make`, it build multple output formats (bin, elf), includiinh an hexdump ready for HDL simulation.