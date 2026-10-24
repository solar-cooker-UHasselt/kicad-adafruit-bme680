# kicad-adafruit-bme680

[![ERC/DRC](https://img.shields.io/github/actions/workflow/status/solar-cooker-UHasselt/kicad-adafruit-bme680/kibot.yml?branch=main&event=push&label=ERC%2FDRC)](https://github.com/solar-cooker-UHasselt/kicad-adafruit-bme680/actions/workflows/kibot.yml)
[![KiCad 10](https://img.shields.io/badge/KiCad-10-314CB0)](https://www.kicad.org/download/)

A breakout board for the Bosch BME680, an environmental sensor that measures
temperature, humidity, barometric pressure and VOC gas, with a 3.3 V regulator and
level shifting so it works with 3.3 V and 5 V boards. It is a KiCad 10 port of
[Adafruit's BME680 breakout](https://github.com/adafruit/Adafruit-BME680-PCB),
originally drawn in Eagle.

In the [solar cooker](https://github.com/solar-cooker-UHasselt) testing station, the
firmware ([arduino-code](https://github.com/solar-cooker-UHasselt/arduino-code)) reads
the ambient temperature, humidity and pressure from it over SPI.

[![3D render of the board, top side](https://solar-cooker-uhasselt.github.io/kicad-adafruit-bme680/BME680-render-top.png)](https://solar-cooker-uhasselt.github.io/kicad-adafruit-bme680/)

- [Board page](https://solar-cooker-uhasselt.github.io/kicad-adafruit-bme680/): 3D
  renders, drawings, schematic and board PDF, interactive BOM and the BOM CSV for
  Eurocircuits, rebuilt by CI on every push to `main`
- [PCB source](https://github.com/adafruit/Adafruit-BME680-PCB): Adafruit's Eagle files
- [Adafruit guide](https://learn.adafruit.com/adafruit-bme680-humidity-temperature-barometic-pressure-voc-gas):
  pinout, wiring and Arduino examples

## Installation

### Requirements

- [KiCad 10](https://www.kicad.org/download/), to open and edit the board
- [git](https://git-scm.com), to clone the repo with its library
- Optional, for the checks: [just](https://just.systems)

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

## Usage

Open `BME680.kicad_pro` in KiCad 10. The schematic and board open from there.

Before committing, run ERC and DRC, reports in `tmp/`:

```bash
just check
```

`just --list` shows the other recipes: PDFs, and the CI workflow run locally.

## Contributing

- Work on a branch and open a pull request to `main`. It merges once CI passes and a code
  owner (listed in [.github/CODEOWNERS](.github/CODEOWNERS)) approves it. `main`
  accepts no force pushes.
- CI runs ERC and DRC on every pull request, through the shared workflows in
  [kicad-ci](https://github.com/solar-cooker-UHasselt/kicad-ci). `just check` runs the
  same check locally. A push to `main` that changes more than Markdown also rebuilds
  the board page.
- Commits follow Conventional Commits, with one change per commit. Types, scopes and the
  ERC/DRC check are in
  [.agents/commit_conventions.md](.agents/commit_conventions.md).
- Changes to the board setup, CI or docs are made and tested in
  [kicad-adafruit-ds3231](https://github.com/solar-cooker-UHasselt/kicad-adafruit-ds3231)
  first, then copied here.

## Authors and acknowledgment

The board is Adafruit's design, by Limor Fried/Ladyada for Adafruit Industries
([PCB source](https://github.com/adafruit/Adafruit-BME680-PCB)). The KiCad 10 port is by
Lowie Van Vyve for the UHasselt solar cooker project.

Adafruit invests time and resources providing this open source design. Please support
Adafruit and open-source hardware by purchasing products from
[Adafruit](https://www.adafruit.com).

<details>
<summary>Adafruit's original README, included as its license asks</summary>

> **Adafruit BME680 PCB**
>
> [Click here to purchase one from the Adafruit shop](http://www.adafruit.com/products/3660)
>
> PCB files for the Adafruit BME680 Breakout. Format is EagleCAD schematic and board
> layout
>
> For more details, check out the product page at
>
> - https://www.adafruit.com/product/3660
>
> **Description**
>
> The long awaited BME680 from Bosch gives you all the environmental sensing you want in
> one small package. This little sensor contains temperature, humidity, barometric
> pressure, and VOC gas sensing capabilities. All over SPI or I2C at a great price!
>
> Like the BME280 & BMP280, this precision sensor from Bosch can measure humidity with
> ±3% accuracy, barometric pressure with ±1 hPa absolute accuracy, and temperature with
> ±1.0°C accuracy. Because pressure changes with altitude, and the pressure measurements
> are so good, you can also use it as an altimeter with ±1 meter or better accuracy!
>
> The BME680 takes those sensors to the next step in that it contains a small MOX
> sensor. The heated metal oxide changes resistance based on the volatile organic
> compounds (VOC) in the air, so it can be used to detect gasses & alcohols such as
> Ethanol, Alcohol and Carbon Monoxide, and perform air quality measurements. Note it
> will give you one resistance value, with overall VOC content, but it cannot
> differentiate gasses or alcohols.
>
> Please note this sensor, like all VOC/gas sensors, has variability and to get precise
> measurements you will want to calibrate it against known sources! That said, for
> general environmental sensors, it will give you a good idea of trends and comparisons.
> We recommend that you run this sensor for 48 hours when you first receive it to "burn
> it in", and then 30 minutes in the desired mode every time the sensor is in use. This
> is because the sensitivity levels of the sensor will change during early use, and the
> resistance will slowly rise over time as the MOX warms up to its baseline reading.
>
> For your convenience we've pick-and-placed the sensor on a PCB with a 3.3V regulator
> and some level shifting, so it can be easily used with your favorite 3.3V or 5V
> microcontroller.
>
> **License**
>
> Adafruit invests time and resources providing this open source design, please support
> Adafruit and open-source hardware by purchasing products from
> [Adafruit](https://www.adafruit.com)!
>
> Designed by Limor Fried/Ladyada for Adafruit Industries.
>
> Creative Commons Attribution/Share-Alike, all text above must be included in any
> redistribution. See license.txt for additional details.

</details>

## License

[CC BY-SA 4.0](LICENSE). Adafruit's original design is licensed CC BY-SA 3.0, which
allows adaptations like this port under a later version with the same terms.
