# SD_CARD_via_GPIO
External SD CARD I/O Library for RaspberryPi/OrangePi.   
You can access external SD CARD using this.   

I ported from here.   
http://blogsmayan.blogspot.jp/p/interfacing-sd-card.html   


---

# Wirering for External SD CARD module

|SD CARD|Rpi/OPI|
|:-:|:-:|:-:|
|GND|--|GND|
|VCC|--|5V|
|MISO|--|Pin#21(SPI MISO)|
|MOSI|--|Pin#19(SPI MOSI)|
|SCK|--|Pin#23(SPI SCLK)|
|CS|--|Pin#24(SPI CE0)(**)|
|CS|--|Pin#26(SPI CE1)(**)|

Note:   
Rpi have 2 SPI.   
CE0 and Pin#24.   
CE1 and Pin#26.   

Opi have only 1 SPI.   
OPi-PC have CE0 and Pin#24.   
OPi ZERO have CE1 and Pin#24.   

You must to chack mmcbb_gpio.c   

```
//use CE0
#define         CE              10
//use CE1
//#define       CE              11
```

---

# How to use

Using bcm2835 Library(RPi Only)   
cc -o RpiSDCard main.c ff.c mmcbb.c -lbcm2835   

Using wiringPi Library(RPi/OPi)   
cc -o RpiSDCard_gpio main.c ff.c mmcbb_gpio.c -lwiringPi

