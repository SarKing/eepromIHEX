# eepromIHEX

Takes data from a CSV file and formats it to IHEX. This file is then ready to be uploaded into an avr eeprom using avrdude.

- [Installation](#installation)
    - [Uninstall](#uninstall)
- [Usage](#usage)
    - [Arguments](#arguments)
    - [Examples](#examples)
- [Uploading](#uploading)

## Installation

For installing, clone this repository to your computer, enter in the folder
eeproeepromIHEX and type "make", then "make install" as root.

```bash
$ git clone https://github.com/SarKing/eepromIHEX
$ cd eepromIHEX
$ make
$ sudo make install
```

By default it's installed in /opt/eepromIHEX

#### Unistall

If you want to uninstall the application enter with your terminal in the folder
that you downloaded and type:

```bash
$ sudo make uninstall
```

## Usage

The basic use of this application just requires from you the CSV data file.

```bash
$ eepromIHEX data_file
```
And it will generate a file called "a.eep" that contains your data formatted t
o IHEX.

But you have more customization the form of arguments.

#### Arguments

    -output             -o      The name of the output file. DEFAULT: a.eep
    --datalenght        -d      Maximum number of bytes per IHEX entry. DEFAULT:
    16
    --address           -a      The first address you want to write to. DEFAULT:
    0
    --verbose           -v      Prints verbose information
    --help              -h      Prints help page
    --version                   Displays the version message

#### Examples

Get data from data.csv, output IHEX formatted data to eeprom.eep
```bash
$ eepromIHEX -o eeprom.eep data.csv
```

Format IHEX with 8 byte data length instead of the default 16
```bash
$ eepromIHEX -d 8 data.csv
```

Start writing to eeprom address 0xFF instead of the default 0
```bash
$ eepromIHEX -a 255 data.csv
```

## Uploading

Once you have the .eep file, for uploading it to a AVR microcontroller using
avrdude you have to use this command.
```bash
$ avrdudde eeprom:w:filename:i
```
