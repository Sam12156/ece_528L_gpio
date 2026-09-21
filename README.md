# Overview

Project enables displaying an array of LED light patterns depending on inputs of two buttons and four switches.

### LED pattern 1 (one of four cases hown here)

			int led1_i = 0x01;
			int led2_i = 0x02;
			PMOD_8LD_Output(PMOD_8LD_ALL_OFF);
			while(Get_Buttons_Status() == 0x00)
			{

				LED1_Output(led1_i);
				LED2_Output(led2_i);
				led1_i ^= 0x01;
				led2_i ^= 0x02;
				Clock_Delay1ms(1000);

			}
			break;


### LED pattern 3 Binary Down Counter

			for (int led_count = 0xFF; led_count >= 0x00; led_count--)
			{
				PMOD_8LD_Output(led_count);
				Clock_Delay1ms(100);
				uint8_t switch_status = Get_PMOD_SWT_Status();
				if (switch_status != 0x02)
				{
					break;
				}
			}

### LED pattern 4 Ring Counter Left

			for (int led_count = 0x01; led_count <= 0x80; led_count <<= 1)
			{
				PMOD_8LD_Output(led_count);
				Clock_Delay1ms(200);
				uint8_t switch_status = Get_PMOD_SWT_Status();
				if (switch_status != 0x04)
				{
					break;
				}
			}

### LED pattern 5 Ring Counter Right

			for (int led_count = 0x80; led_count >= 0x01; led_count >>= 1)
			{
				PMOD_8LD_Output(led_count);
				Clock_Delay1ms(200);
				uint8_t switch_status = Get_PMOD_SWT_Status();
				if (switch_status != 0x08)
				{
					break;
				}
			}

### LED pattern 6 Johnson counter

			for (int i = 0x00; i <= 0x0F; i++)
			{
				if (i < 0x08)
					led_count = (led_count << 1) | 0x01;
				else
					led_count = (led_count << 1) & 0xFF;


				PMOD_8LD_Output(led_count);
				Clock_Delay1ms(200);
				uint8_t switch_status = Get_PMOD_SWT_Status();
				if (switch_status != 0x03)
				{
					break;
				}
			}	
# Components Used:

* TI MSP432 LaunchPad
* PMOD SWT (4 Slide Switches) - [Product Link](https://digilent.com/reference/pmod/pmodswt/start)
* PMOD 8LD (8 LEDs) - [Product Link](https://digilent.com/shop/pmod-8ld-eight-high-brightness-leds/)

# Known Issues or Limitations:
Originally for the pattern one snippet we used "while(button_status == 0x00)" but that caused the main while loop to never advance and never update button_status
so we used the read function directly "while(Get_Buttons_Status() == 0x00)".

# Author Contribution:
| Sam  | Omer |
| ------------- | ------------- |
| led pattern 1  | led pattern 3  |
| led pattern 6 | led pattern 4  |
|  | led pattern 5  |
# References:

1. [MSP432P401R SimpleLink Microcontroller LaunchPad Development Kit User's Guide](https://docs.rs-online.com/3934/A700000006811369.pdf)
2. [MSP432P401R Datasheet](https://www.ti.com/lit/ds/slas826e/slas826e.pdf)
3. [Robot Systems Learning Kit (TI-RSLK) User Guide](https://www.ti.com/lit/pdf/sekp166)
4. [MSP432P4xx SimpleLink Microcontrollers Technical Reference Manual](https://web.archive.org/web/20200402132841/http:/www.ti.com/lit/ug/slau356i/slau356i.pdf)
5. [PMOD SWT Reference Manual](https://digilent.com/reference/pmod/pmodswt/reference-manual)
6. [PMOD LED Reference Manual](https://reference.digilentinc.com/reference/pmod/pmodled/reference-manual)
7. [PMOD 8LD Reference Manual](https://digilent.com/reference/pmod/pmod8ld/reference-manual)
