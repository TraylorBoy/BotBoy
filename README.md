# BotBoy
Multithreading &amp; processing worker that executes functions and prints the
result

**Version 2 Release**

## Installation
```
pip install botboy
```

## Usage
### Create a new BotBoy object with a pre-defined function object and a name.
Optional silent property to display log messages **(default is True)**

```
from botboy import BotBoy

bot = BotBoy('Adder', lambda x, y: x + y, silent=False)

# Or
# Getter and setter
bot = BotBoy()
bot.name = 'Adder'
bot.task = lambda x, y: x + y
```

### Display the information

```
bot.info()

> Name: Adder
> Task: <function <lambda> at 0x109a860e0>
> Result: None
> Process: None
> Thread: None
```

### Execute function object on separate thread

```
bot.execute(1, 2)

> Adder is executing task: <function <lambda> at 0x10e6e8040>
> Retrieved result from Adder: 3
```

### Wait for result
```
bot.execute(10, 20, wait=True)

> Waiting for <function <lambda> at 0x109a860e0> to finish
> Adder is executing task: <function <lambda> at 0x109a860e0>
> Retrieved result from Adder: 30
```

### Execute function object on separate process

```
# Cannot wait on process
bot.execute(30, 40, process=True)

> Running <function <lambda> at 0x109a860e0> on separate process: <Process name='Adder' parent=47604 initial>
> Adder is executing task: <function <lambda> at 0x109a860e0>
> Retrieved result from Adder: 70
```

### Can retrieve result after execution
```
# Returns the result retrieved from function
print(bot.result)

> 70
```

### Store result in a file or provide a path

```
# Store result in a file at current directory
bot.save('test.txt')

> Storing result at test.txt

import os
# Store result at path
bot.save(os.getcwd() + '/test2.txt')

> Storing result at /Users/traylorboy/Desktop/TraylorTheBoy/TraylorDev/python_apps/BotBoy/test2.txt
```

## Test

Runs the tests on the BotBoy module

```
make test
```

or

```
python3 test
```
