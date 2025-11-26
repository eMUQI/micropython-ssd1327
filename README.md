# MicroPython SSD1327

A MicroPython library for SSD1327 128x128 4-bit greyscale OLED displays, over I2C or SPI.

## Example

Copy the file to your device, using ampy, webrepl or compiling and deploying. eg.

```bash
$ ampy put ssd1327.py
```

### I2C Example

```python
from machine import Pin, I2C
import ssd1327

# ESP32 S3 ZERO
i2c = I2C(0, scl=Pin(2), sda=Pin(1), freq=400000)

# Raspberry Pi Pico
# i2c = I2C(0, scl=Pin(1), sda=Pin(0), freq=400000)

# Initialize Display (Address usually 0x3C or 0x3D)
display = ssd1327.SSD1327_I2C(128, 128, i2c, addr=0x3D) # WaveShare 1.5inch OLED Module

display.fill(0)  # Clear screen
display.text('Hello World', 0, 0, 15) # Draw text in full brightness (15)
display.show()
```

### SPI Example

```python
from machine import Pin, SPI
import ssd1327

# ESP32 S3 ZERO
spi = SPI(1, baudrate=10000000, polarity=0, phase=0, sck=Pin(13), mosi=Pin(11))
display = ssd1327.SSD1327_SPI(128, 128, spi, dc=Pin(8), res=Pin(9), cs=Pin(10))

display.fill(0)
display.text('SPI Display', 0, 0, 15)
display.show()
```

See [/examples](/examples) for more.

## Parts

* [WaveShare ESP32-S3 Zero](https://www.waveshare.com/esp32-s3-zero.htm)
* [Raspberry Pi Pico](https://core-electronics.com.au/raspberry-pi-pico.html)
* [WaveShare 1.5inch OLED Module, SPI/I2C interface](https://www.waveshare.com/1.5inch-oled-module.htm)

## Links

* [micropython.org](http://micropython.org)
* [micropython docs](http://docs.micropython.org/en/latest/)
* [Adafruit Ampy](https://learn.adafruit.com/micropython-basics-load-files-and-run-code/install-ampy)

## License

Licensed under the [MIT License](http://opensource.org/licenses/MIT).
