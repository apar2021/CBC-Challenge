# Task 2 - Extract the Firmware - (Hardware analysis, Datasheets)Points: 100
Thanks to your efforts the USCG discovered the unknown object by trilaterating the geo and timestamp entries of their record with the correlating entries you provided from the NSA databases.
Upon discovery, the device appears to be a device with some kind of collection array used for transmitting and receiving. 
Further visual inspection shows the brains of this device to be reminiscent of a popular hobbyist computer. 
Common data and visual ports non-responsive; the only exception is a boot prompt output when connecting over HDMI. 
Most interestingly there is a 40pin GPIO header with an additional 20pin header.
Many of these physical pins show low-voltage activity which indicate data may be enabled. 
There may be a way to still interact with the device firmware...
Find the correct processor datasheet, and then use it and the resources provided to enter which physical pins enable data to and from this device
Hints:

Note: For the pinout.svg, turn off your application's dark mode if you're unable to see the physical pin labels (eg: 'P1', 'P60')
The pinout.svg has two voltage types. The gold/tan is 3.3v, the red is 5v.
The only additional resource you will need is the datasheet, or at least the relevant information from it

Downloads:

Rendering of debug ports on embedded computer (pinout.svg)
image of device CPU (cpu.jpg)
copy of display output when attempting to read from HDMI (boot_prompt.log)
Prompts:

Provide the correct physical pin number to power the GPIO header
Provide a correct physical pin number to ground the board:
Provide the correct physical pin number for a UART transmit function:
Provide the correct physical pin number for a UART receive function:

# Problem Solving Approach
In order to solve this task, we can first find the device from the pinout diagram or a basic semblance of the device in this case. 
While in this case, we can do a process of elimination for the pins for grounding the board. By determining the device, we can find a pinout diagram that corresponds to 
grounding the board. I however didn't fully understand that there was device responses for getting some of the pins right. It took me some time to find the answer in this case. 
for the 
