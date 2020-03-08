Title: 34C04 EEPROM Driver
Date: 2020-03-08 11:38
Category: Software
Author: Wayne du Preez
icon: language

# Description

So after geting some PCB's made I decided to try my hand at writing drivers for the 34C04 EEPROM
I2C chips that I use to identify each PCB plugged into the backplane board.

I decided to write this in rust as my C language foo is not so great, also rust looks cool and I need to learn some of it.

My setup is as follows:
1. IDE = VScode.
2. OS = Ubuntu - I run ubuntu at home and virtualize Windows where needed.
3. Target = STM32 - Blue Pill

Some example code:
```rust
let address = eeprom34c04::SlaveAddr::A2A1A0(false, true, true);

let mut eeprom = eeprom34c04::Eeprom34c04::new_34c04(i2c_setup, address);

let memory_address = 0x0F;

let data = 0xF0;

eeprom.write_byte(memory_address, data).unwrap();

delay.delay_ms(5u16);

let read_data = eeprom.read_byte(memory_address).unwrap();

```

[Link to Github 34C04 repo](https://github.com/waynedupreez1/eeprom34c04-rs)

### __And Thats it until the next one.__
