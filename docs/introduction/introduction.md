## Mbed OS 5

Arm Mbed OS lets you write applications that run on embedded devices, by providing the layer that interprets your application's code in a way the hardware can understand.

Your application code is written in C and C++. It uses the *application programming interfaces* (APIs) that Mbed OS provides. These APIs allow your code to work on different microcontrollers in a uniform way. This reduces the challenges of getting started with Arm-based microcontrollers and integrating large software projects.

#### Where to start

<span class="tips">If you're working on Windows, you might need to [install a serial driver](/docs/development/tutorials/windows-serial-driver.html).

The easiest way to work with Mbed OS is using one of our development tools. We've set up an example, [Blinky](/docs/development/tutorials/your-first-program.html), that you can try on each of the tools. Blinky teaches you to build and run an application on your board.

Once you know how to build an existing application, it's time to learn [how to write your own applications](/docs/development/reference/index.html).

##### Development tools

- Our offline development tool is [Arm Mbed CLI](/docs/development/tools/arm-mbed-cli.html), a command-line tool. This requires having a toolchain installed on your computer.
- The [Arm Mbed Online Compiler](/docs/development/tools/arm-online-compiler.html) lets you write and build applications using a web browser.
- If you're working with third party tools, look at [exporting instructions for the most popular ones](/docs/development/tools/exporting.html).

##### Communicating with and monitoring your board

You can [monitor and control an Mbed board](/docs/development/tutorials/serial-comm.html) to help you debug and test your applications.

<span class="tips">**Tip:** Learn more about debugging in the [debugging applications section](/docs/development/tutorials/debugging-applications.html).</span>

#### How to continue

When you've started writing applications using your selected development tool:

- Learn about [collaborative work and version control](/docs/development/tools/collab-online-comp.html).
- Try one of the [tutorials](/docs/development/tutorials/index.html), which cover concepts such as debugging and memory tracing.
- Ask questions and give advice on the [forum](https://os.mbed.com/forum/).

#### Contributing to Mbed OS

If you want to contribute to the `mbed-os` codebase, please see [the contribution section](/docs/development/reference/contributing.html).

You can find past releases and the current release on [GitHub](https://github.com/ARMmbed/mbed-os/releases/).

#### Porting to Mbed OS

Our full contributing guide is still being written. For now, we have:

- A guide to [contributing targets](/docs/development/reference/contributing-target.html).
- Information about the [tools you need to contribute targets](/docs/development/reference/contributing-tools.html).
- APIs about [storage](/docs/development/reference/contributing-storage.html) and [connectivity](/docs/development/reference/contributing-connectivity.html) in relation to porting.

## How Mbed works

The Arm Mbed hardware architecture is designed to make sure you have all the tools and utilities to be productive. Most boards have an integrated debug circuit that assists development by programming the device, logging program execution and giving access to the debug access port. Here is how it works.

#### Architecture diagram

This is the basic architecture of an Mbed board:

<span class="images">![](https://s3-us-west-2.amazonaws.com/mbed-os-docs-images/MbedOS@2x.png)<span>A sketch of a typical Mbed board's hardware architecture</span></span>

#### How programming works

There are two options:

1. When you plug an Mbed Enabled board to your PC using USB, it appears as a USB flash disk. The Mbed interface presents this small disk. It allows you to save Arm microcontroller binaries you want to run directly on to the board, without drivers.
2. The same USB connection exposes a debug protocol such as CMSIS-DAP. This enables lots of IDEs to program and debug the device.

##### How USB serial works

The Arm Mbed interface also presents a USB serial/com interface. This is basically a UART-USB bridge, and it connects to the interface's UART. So if you send characters out of the target board's UART, the Arm Mbed interface will read them and transfer them over the USB link. When you `printf()`, it is just sending characters to UART. This means that if you make your own PCB, these characters will still appear on UART.

##### Notes

The `.bin` files the Mbed microcontroller accepts are standard raw binaries. Use any compiler you like to generate them. As the separate interface manages programming over JTAG or SWD, you have unlimited control of the target microcontroller. You really are just loading on a raw binary; this means you can build your own PCB using the same target microcontroller, and the same program binary will run on that.

#### The Arm Mbed interface

You can find more information about the Mbed interface and the circuits on which it runs in the [HDK reference manual](/docs/development/reference/contributing-tools.html#arm-mbed-hdk) or on the [DAPLink page](/docs/development/tools/daplink.html). The HDK includes reference circuits you can use to create your own boards, and DAPLink is the firmware that runs on these circuits.

#### Connectivity

The best representation of the connectivity of the Mbed interface is the same diagram we showed above.

The Mbed interface:

- Provides a USB connection to the host computer, which exposes a Mass Storage (flash disk) and a USB serial port.
- Has an SWD or JTAG connection to the target, so it can program the target flash. You can also use this for debugging.
- A physical UART connection exists between the target and the interface, which is relayed over the interface's USB serial port.
