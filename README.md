*Note:* this example is based on mbed OS 3.0 and now superseeded by the [Blinky example based on mbed OS 5](https://github.com/ARMmbed/mbed-os-example-blinky)

# example-mbedos-blinky

Blinky is a simple example program that blinks an LED on an mbed-enabled board with mbed OS.

## What Blinky does

This is a short review of the Blinky code. More information is available on the user guide, where we explain [how to write mbed OS applications](https://docs.mbed.com/docs/getting-started-mbed-os/en/latest/Full_Guide/app_on_mbed_os/) and how to [work with yotta](https://docs.mbed.com/docs/getting-started-mbed-os/en/latest/Full_Guide/app_on_yotta/).

1. The code begins with ``include``. The included header is ``mbed.h``, from the ``mbed-drivers`` library. It is a key library for mbed OS, and includes most of the functionality standard applications need. yotta, our build system, includes ``mbed-drivers`` during compilation because that library is listed as a dependency in Blinky's ``module.json`` file.

1. mbed OS applications start with ``app_start``, replacing ``main``.

1. MINAR is the mbed OS scheduler; we use it here to create a callback that will run every 500 milliseconds. The function we're running is ``blinky``.

1. ``blinky`` creates a DigitalOut using the LED1 on our board. It then turns the LED on and off and prints its status to the terminal using ``printf`` over the serial port (115200 baud, 8 data bits, no parity bit, 1 stop bit (8N1)).


**Tip:** To learn more about writing applications for mbed OS, see the [mbed OS user guide's review of Blinky](https://docs.mbed.com/docs/getting-started-mbed-os/en/latest/Full_Guide/app_on_mbed_os/).


## Building the example

### If you're using yotta as a command-line tool

**Tip:** If you need help setting up yotta or building a project, see our [quick guide](https://docs.mbed.com/docs/getting-started-mbed-os/en/latest/FirstProjectmbedOS/), which uses the same example.

To build Blinky with yotta as a command-line tool:

1. Clone the repository from GitHub:

	```
	$ git clone https://github.com/ARMmbed/example-mbedos-blinky.git
	$ cd example-mbedos-blinky
	```

2. Select a target platform:

	```
	$ yotta target frdm-k64f-gcc
	```

3. Build it:

	```
	$ yotta build
	... bunch of build messages ...
	[135/135] Linking CXX executable source/example-mbedos-blinky
	```

yotta will put the compiled binary in the project's `/build` folder. Copy the binary  `/build/frdm-k64f-gcc/source/example-mbedos-blinky.bin` to your mbed board over USB.

### If you're on the online IDE

**Tip:** If you need help getting started with the IDE, see our [quick guide](https://docs.mbed.com/docs/getting-started-mbed-os/en/latest/FirstProjectmbedOS/), which uses the same example.

To build Blinky in your IDE workspace:

1. The IDE needs to know which target to build for. Click *Target*:
 
 1. The list displays your recently used targets. If the target you need is listed, click it.
 
 1. If your target isn't in the drop-down list, click *Search in Registry*. A list of targets opens. Select your target and click *Set*.

1. Click *Build Project*.

The IDE will build the project as a binary file and ask you to download it. When the download finishes, copy the file to your mbed board over USB.
