- Search "Anaconda"

After opening Anaconda Prompt or the terminal, choose any of the following methods to verify: Enter 

$ conda list

. If Anaconda is installed and working, this will display a list of installed packages and their versions.
Enter the command python. This command runs the Python shell. If Anaconda is installed and working, the version information it displays when it starts up will include “Anaconda”. To exit the Python shell, enter the command quit().
Open Anaconda Navigator with the command 

$ anaconda-navigator

If Anaconda is installed properly, Anaconda Navigator will open.

Once a module has been imported, we can call its elements using the following syntax:
```
import numpy
numpy.zeros(2) #We call function zeros() of module numpy
```

- BOOT.PY AND MAIN.PY
boot.py and main.py are two Python scripts that are executed on boot. You may open and study them, but our advice is not to modify them, as they have been written to ease your developments.

boot.py is configured to stop the SDS011 fan on boot (in case it would be spinning). It will also turn-off the WiFi access-point when not in programming mode, as a way to save battery.

main.py handles the automatic call of iiot_full_sensor.py script when the sensor is not in programming mode. It also handles reboot upon catching an unexpected exception.


- TEST CODE: [microconda](http://micropython.org/unicorn/)

## THE REPL

The "Read-Eval-Print-Loop" is an interactive terminal that lets you interact with your LoPy in Python in real-time. It is very convenient to test pieces of code that may ultimately got to a Python file.

The REPL is characterized by its ">>>" prompt.

>>>

