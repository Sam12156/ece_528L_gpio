#Overview

Project enables displaying an array of LED light patterns depending on inputs of two buttons nd four switches.

###LED pattern 1 

###LED pattern 2

			for (int led_count = 0; led_count <= 0xFF; led_count++)
			{
				PMOD_8LD_Output(led_count);
				Clock_Delay1ms(100);
				uint8_t switch_status = Get_PMOD_SWT_Status();
				if (switch_status != 0x01)
				{
					break;
				}
			}


###LED pattern 3

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

###LED pattern 4

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

###LED pattern 5

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

###LED pattern 6 Jonson counter

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
#Components Used:

* TI MSP432 LaunchPad
* PMOD SWT (4 Slide Switches) - [Product Link](https://digilent.com/reference/pmod/pmodswt/start)
* PMOD 8LD (8 LEDs) - [Product Link](https://digilent.com/shop/pmod-8ld-eight-high-brightness-leds/)

#Known Issues or Limitations:

#Author Contribution:

#References:#Overview

Project enables displaying an array of LED light patterns depending on inputs of two buttons nd four switches.

###LED pattern 1 

###LED pattern 2
			for (int led_count = 0; led_count <= 0xFF; led_count++)
			{
				PMOD_8LD_Output(led_count);
				Clock_Delay1ms(100);
				uint8_t switch_status = Get_PMOD_SWT_Status();
				if (switch_status != 0x01)
				{
					break;
				}
			}


###LED pattern 3

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

###LED pattern 4
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

###LED pattern 5

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

###LED pattern 6 Jonson counter

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
#Components Used:

* TI MSP432 LaunchPad
* PMOD SWT (4 Slide Switches) - [Product Link](https://digilent.com/reference/pmod/pmodswt/start)
* PMOD 8LD (8 LEDs) - [Product Link](https://digilent.com/shop/pmod-8ld-eight-high-brightness-leds/)

#Known Issues or Limitations:

#Author Contribution:

#References:
