# kicad-adafruit-bme680

- [Board page](https://solar-cooker-uhasselt.github.io/kicad-adafruit-bme680/): 3D
  renders, drawings, schematic and board PDF, interactive BOM and the BOM CSV for
  Eurocircuits, rebuilt by CI on every push to `main`
- [PCB source](https://github.com/adafruit/Adafruit-BME680-PCB)
- [Wiki](https://learn.adafruit.com/adafruit-bme680-humidity-temperature-barometic-pressure-voc-gas)

## Installation

### Clone

Own footprints come from
[kicad-common](https://github.com/solar-cooker-UHasselt/kicad-common), a git submodule
at `kicad-common/`. Clone with it:

```bash
git clone --recurse-submodules https://github.com/solar-cooker-UHasselt/kicad-adafruit-bme680.git
```

Or, in a clone made without it:

```bash
git submodule update --init
```
