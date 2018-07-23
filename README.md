## Getting Started With The mbed-os Example for the SPI Flash Block Device

This is the mbed-os example for the SPIFBlockDevice driver.
See the [spi-driver](https://github.com/GreenWaves-Technologies/spif-driver) repository for more information.

This guide outlines the steps to get a SPI NOR flash part working on an mbed OS platform.

Please install [mbed CLI](https://github.com/ARMmbed/mbed-cli#installing-mbed-cli).

## Hardware Requirements

This example can be used on an mbedos platform with a SPI NOR part connected to the SPI pins (on the Arduino header, for example).

This document uses the GAP8 as an example. Simply change the relevant options (e.g. -m GAP8) to be appropriate for your target.

## Create the Example Application

From the command-line, import the example:

```
mbed import https://github.com/GreenWaves-Technologies/mbed-os-example-spiflash-driver
```

You should see:


	[mbed] Adding library "spif-driver" from "https://github.com/GreenWaves-Technologies/spif-driver" at rev #decf10be9b7d
	[mbed] Adding library "mbed-os" from "https://github.com/GreenWaves-Technologies/mbed-os" at rev #b0f31ea774ac

Move into the newly created directory:

```
cd mbed-os-example-spiflash-driver
```

If the mbed-os library was not automatically added (see trace above), do the following to import mbed-os:

```
mbed new .
```


## Build the Example

Invoke `mbed compile`, and specify the name of your platform and your favorite toolchain (`GCC_RISCV`, `GCC_ARM`, `ARM`, `IAR`). For example, for the GCC_RISCV toolchain:

```
mbed compile -m GAP8 -t GCC_RISCV
```

Your PC may take a few minutes to compile your code. At the end, you see the following result:

```
Elf2Bin: mbed-os-example-spiflash-driver
+-----------------+-------+-------+------+
| Module          | .text | .data | .bss |
+-----------------+-------+-------+------+
| BUILD/GAP8      | 22178 |   380 | 1311 |
| [fill]          |     2 |     4 |   13 |
| [lib]/c.a       |  9576 |  2096 |   60 |
| [lib]/gcc.a     |  1798 |     0 |    0 |
| mbed-os/targets |   288 |     4 |   28 |
| Subtotals       | 33842 |  2484 | 1412 |
+-----------------+-------+-------+------+
Total Static RAM memory (data + bss): 3896 bytes
Total Flash memory (text + data): 36326 bytes
```


## <a name="run-the-example-binary-on-the-GAP8"></a> Run the Example Binary on the GAP8

1. Connect your device (with sensor board) to the computer over USB.
1. Execute the script (make sure you have already install the [gap_sdk](https://github.com/GreenWaves-Technologies/gap_sdk)) :

```
source ./USER_PATH/gap_sdk/sourceme.sh
run_mbed ./BUILD/GAP8/GCC_RISCV/mbed-os-example-spiflash-driver.elf
```

After connecting a serial console and resetting the target, the following trace should be seen:

	spif test
	spif size: 8388608
	spif read size: 1
	spif program size: 1
	spif erase size: 4096
	Hello World!


# Troubleshooting

1. Make sure `mbed-cli` is working correctly and its version is newer than `1.0.0`.

 ```
 mbed --version
 ```

 If not, update it:

 ```
 pip install mbed-cli --upgrade
 ```
