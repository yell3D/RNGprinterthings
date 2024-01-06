# Mini 12864 on Creality 4.2.2 MCU

All credits to [u/Schnabulation](https://www.reddit.com/r/klippers/comments/sw9mej/12864_mini_display_working_with_stock_creality/)

Need to disable SWD at boot for the encoder to work.
Do this in `make menuconfig` 
![image](https://user-images.githubusercontent.com/45492899/201928390-f8b1308a-f4a2-4cc4-8a64-75578c037eb7.png)

### Printer.cfg

```ini
[board_pins]
aliases:
    # EXP1 header
    EXP1_1=<5V>, EXP1_3=PB15, EXP1_5=PB13, EXP1_7=PB11, EXP1_9=PB2,
    EXP1_2=<GND>, EXP1_4=PB12, EXP1_6=PB14, EXP1_8=PB10, EXP1_10=PC6

[display]
lcd_type: uc1701
cs_pin: EXP1_3
a0_pin: EXP1_4
rst_pin: EXP1_5
contrast: 63
encoder_pins: ^PA13, ^PA14
click_pin: ^!EXP1_9

spi_software_miso_pin: EXP1_8
spi_software_mosi_pin: EXP1_7
spi_software_sclk_pin: EXP1_6

[neopixel mini12864]
pin: EXP1_10
chain_count: 3
color_order: RGB
initial_RED: 0
initial_GREEN: 0
initial_BLUE: 1
```



## wiring

![main_wiring](main_wiring.jpeg?raw=true)

![additional_wiring](additional_wiring.jpeg?raw=true)
