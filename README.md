# Scripts and device tree overlays for the Pi-puck

## Device tree overlays

The Device Tree Source (DTS) file for the target board revision must first be compiled into Device Tree Blob (DTB) overlays as follows:

```
dtc -@ -I dts -O dtb -o pi-puck-v2_0.dtbo overlays/pi-puck-v2_0.dts
```

The resulting `.dtbo` file should then be copied to `/boot/overlays/` on the Raspberry Pi. To enable the overlay, add the following line to `/boot/config.txt`, using the correct board revision number, and replacing the parameters as detailed below:

```
dtoverlay=rpi-puck-v2_0:parameters1,parameter2
```

The device tree overlays enable the following hardware:

- System LEDs
- Control switch keys (optional)
- Control switch power key
- UART enable (disables Bluetooth)
- Audio output (v2.0+)
- I2C devices (v2.0+)
  - I2C switch
  - User GPIO expander
    - User LEDs
  - Navigation GPIO expander
    - Navigation panel LED
  - ADC
    - Battery level inputs
    - External ADC channels (optional)
  - e-puck (I2C switch channel only)
  - Distance sensors (I2C switch channel only)

### Overlay parameters

The device tree overlays allow certain features to be enabled/disabled/customised through parameters specified in `config.txt`.

- `control_keys` enables the system DIP switches to trigger Linux keyboard events (keys 256, 257, 258 and 259 for SW1, SW2, SW3 and SW4 respectively).
- `power_key` sets up SW1 of the system DIP switches as a Linux power key, causing an immediate shutdown to occur when switched on. This overrides the assignment to key 256 if `control_keys` is also enabled.
- `uart` disables the Bluetooth and instead enables the hardware UART output on Pi 3 and Pi Zero W. This is the same as using `dtoverlay=pi3-disable-bt`.
- `ain2`/`ain3` (v2.0+) enables the external AIN2/AIN3 inputs to the ADC.
- `ain2_gain`/`ain3_gain` (v2.0+) sets the gain for the AIN2/AIN3 channels of the ADC (see [ads1015 documentation](https://github.com/raspberrypi/linux/blob/master/Documentation/devicetree/bindings/hwmon/ads1015.txt) for values).
- `ain2_datarate`/`ain3_datarate` (v2.0+) sets the data rate for the AIN2/AIN3 channels of the ADC (see [ads1015 documentation](https://github.com/raspberrypi/linux/blob/master/Documentation/devicetree/bindings/hwmon/ads1015.txt) for values).


## Python scripts

First, install `supervisord` by running `sudo apt-get install supervisor`. Then, copy the Python scripts to `/usr/local/bin/`, and use `chmod +x` to make them executable. Finally, copy the `.conf` files to `/etc/supervisor/conf.d/`, and reboot the Raspberry Pi.

Note that the `control_keys` and `power_key` parameters must be disabled (default) for `gpio_shutdown.py` to function, and `control_keys` parameter disabled (default) for `gpio_getty.py` to function.
