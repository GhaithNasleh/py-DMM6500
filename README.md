# py-DMM6500

Library to communicate easily with a Keithley DMM6500 multimeter via pyvisa

**Note1: Be sure to set the multimeter in SCPI communication mode**

Example usage:
````
import pyvisa as visa
from DMM6500 import DMM6500
from DMM6500_SCPI import Function

mm = DMM6500(visa.ResourceManager().open_resource('USB::0x05e6::0x6500::*******::INSTR'))
mm.reset()
mm.function = Function.DC_VOLTAGE
print(mm.measure())
````

For more examples, see the examples folder.

## Requirements
If you want to just generate the SCPI commands in textual form this library has no requirements.

If you want to communicate with your DMM6500 trough pyvisa this library requires:
* pyvisa

If you have no native visa driver installed, you can use these libraries to handle the communication in user space in linux:
* pyvisa-py 
* pyusb

For windows, install the [ni-visa](http://www.ni.com/download/ni-visa-17.5/7220/en/) from National Instruments. See 

## Documentation
All native SCPI commands are generated by `DMM6500_SCPI.py`.
Please refer to this file for a list of all possible commands.

Commands with the prefix `set_` are special in the sense that you can command to set them as if you are setting a property on the multimeter object. For example `mm.set_range('auto')` does the same as `mm.range ='auto'`

It is possible to set a bunch of settings at the same time from a dictionary. See `example2.py`

It could be usefull to refer to the Keithley DMM6500 Reference Manual. 

## Development
### TODO
* Handle overflow nicely
* Add more settings
* Test on Windows
* Generate documentation
