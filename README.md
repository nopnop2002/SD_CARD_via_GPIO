# SD_CARD_via_GPIO
External SD CARD I/O Library for RaspberryPi/OrangePi.   
You can access external SD CARD using this.   

I ported from here.   
http://blogsmayan.blogspot.jp/p/interfacing-sd-card.html   


---

# Wirering for External SD CARD module   

|SD CARD||Rpi/OPI|
|:-:|:-:|:-:|
|GND|--|GND|
|VCC|--|5V|
|MISO|--|Pin#21(SPI MISO)|
|MOSI|--|Pin#19(SPI MOSI)|
|SCK|--|Pin#23(SPI SCLK)|
|CS|--|Pin#24(SPI CE0)(*)|
|CS|--|Pin#26(SPI CE1)(*)|

\*Note:   
Rpi have 2 SPI.   
CE0 and GPIO10.   
CE1 and GPIO11.   

Opi-PC have only 1 SPI.   
CE0 and GPIO10.   

Opi-ZERO have only 1 SPI.   
CE1 and GPIO10.   

You must to chack mmcbb_gpio.c   

```
//GPIO10 as CE
#define 	CE		10
//GPIO11 as CE
//#define 	CE		11
```

---

# How to use   

_Using bcm2835 Library(RPi Only)_   
This is original Library.  
Thank you for Rajiv.   

cc -o RpiSDCard main.c ff.c mmcbb.c -lbcm2835   
sudo ./RpiSDCard   



_Using wiringPi Library(RPi/OPi)_   

cc -o RpiSDCard_gpio main.c ff.c mmcbb_gpio.c -lwiringPi   
sudo ./RpiSDCard_gpio   

