# Supporting Files for the Pi-puck

The Pi-puck is a [Raspberry Pi](https://www.raspberrypi.org) extension board for the [e-puck](https://www.gctronic.com/doc/index.php?title=E-Puck) and [e-puck2](https://www.gctronic.com/doc/index.php?title=e-puck2) robot platforms, designed and built as a collaboration between the [York Robotics Laboratory (YRL)](https://www.york.ac.uk/robot-lab/) at the [University of York](https://www.cs.york.ac.uk), and [GCtronic](https://www.gctronic.com).

For more information about the Pi-puck, see:
- YRL Pi-puck documentation - https://pi-puck.readthedocs.io
- GCtronic wiki page - https://www.gctronic.com/doc/index.php?title=Pi-puck
- Pi-puck on the YRL website - https://www.york.ac.uk/robot-lab/pi-puck/
- IROS 2017 paper - https://eprints.whiterose.ac.uk/120310/

Additional software sources can be found in the following repositories:
- GCtronic Pi-puck repository - https://github.com/gctronic/Pi-puck
- Pi-puck Debian packages - https://github.com/yorkrobotlab/pi-puck-packages
- Pi-puck Raspbian distribution - https://github.com/yorkrobotlab/pi-gen


## Device Tree Overlay, etc.

**[device-tree/](device-tree/)**

Device tree overlay and associated `config.txt` for booting the Pi-puck.

The device tree overlay enables all the hardware on the board within Linux, with some configurable parameters. The `config.txt` options enable this device tree overlay and set up certain GPIO pins with required default values.


## Software Utilities

**[utilities/](utilities/)**

Linux utilities for configuring the Pi-puck hardware.


## Configuration Files

**[config/](config/)**

Various Linux configuration files for Pi-puck hardware.


## Software Examples

**[examples/](examples/)**

Linux examples for using the Pi-puck.


## Python Library

**[python-library/](python-library/)**

Python library (and example code) for controlling the Pi-puck and e-puck hardware.


## e-puck1 Code

**[e-puck1/](e-puck1/)**

PIC firmware, bootloader and programming script for the e-puck1.


## FT903 Code

**[ft903/](ft903/)**

Firmware and DFU programming script for the FT903 chip.


## Documentation

**[docs/](docs/)**

Documentation sources for Read The Docs site (https://pi-puck.readthedocs.io).

These can also be built in several different formats using [Sphinx](https://www.sphinx-doc.org).


## Licence

Hardware designs are licensed under a [Creative Commons Attribution-ShareAlike 4.0 International Licence][cc-by-sa].

Unless otherwise specified, software is licensed under an [MIT Licence][mit].


[cc-by-sa]: http://creativecommons.org/licenses/by-sa/4.0/
[mit]: /LICENSE-MIT
