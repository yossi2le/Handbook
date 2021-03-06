<h2 id="mesh-api">Mesh</h2>

The Arm Mbed mesh API allows the application to use the IPv6 mesh network topologies through the [nanostack](/docs/development/reference/technology.html#nanostack) networking stack.

**Tips:**
- The mesh API supports 6LoWPAN-ND (neighbor discovery) and Thread bootstrap modes.
- The applications do not use this module directly. The applications use `LoWPANNDInterface`, `ThreadInterface` or `NanostackEthernetInterface` directly.
- When using an Ethernet interface, there are no configuration options available. It is using the dynamic mode to learn the IPv6 prefix from the network.

### Mesh class reference

[![View code](https://www.mbed.com/embed/?type=library)](http://os-doc-builder.test.mbed.com/docs/development/mbed-os-api-doxy/class_mesh_interface.html)

### Usage

1. Create a network interface and driver objects.
1. Initialize the interface with given PHY driver.
1. Connect to network.

### Mesh example

The application below demonstrates a simple light control application, where devices can control the LED status of all devices in the network. You can build the application for the unsecure 6LoWPAN-ND or Thread network.

[![View code](https://www.mbed.com/embed/?url=https://github.com/ARMmbed/mbed-os-example-mesh-minimal/)](https://github.com/ARMmbed/mbed-os-example-mesh-minimal/blob/master/main.cpp)

### Related content

- [Nanostack](/docs/development/reference/technology.html#nanostack) technology reference material.
