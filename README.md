# 2812PyFx
Easy WS2812 effects on most boards that supports spi-dev, using the Hardware SPI MOSI.

## Wiring
Connect the SPI MOSI pin on the Data pin of the led (single or string).

## Requirements
- Python 3
- Numpy
- spi-dev enabled
- py-spidev

### Installing py-spidev

```
pip3 install spidev
```

### Testing this ws2812.py module
This module can be tested using:
    python ws2812.py



## Problems

### Flickering and first led is always green
/usr/local/lib/python3.7/dist-packages/ws2812.py

modify write2812_numpy4(spi,data)-function:
```
    tx = numpy.insert(tx, 0, 0x00) # fix first green led
    spi.max_speed_hz = int(4/1.05e-6) # fix flickering
    spi.writebytes(tx.tolist()) # fix flickering
```
or use https://github.com/mcgurk/ws2812-spi/blob/master/ws2812.py

