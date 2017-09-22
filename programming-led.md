# Programming the Lights

## Setup

First create a new Python script named `reaction_time.py`.

At the top of the file, import `LED` from the GPIO module. Setup your LED with the pin number that you connected it to when building your circuit.

```py
from gpiozero import LED

led = LED(0) # Change the pin number to match your circuit
```

At the end of the file, write code which turns the LED on, waits five seconds, and then turns the LED off.

In order to wait, recall the `sleep` function from the `time` module. To use it, add the following import to the top of your file.

```py
from time import sleep
```

Run your program and check that the LED turns on, and turns off five seconds later. If the LED doesn't do what you expect it to, there may be a problem in your circuit or code. Identify and fix any problems, then run your program again to check if the problem has been fixed.

## Randomizing the Time the LED is On

In order to make the LED turn off randomly, so players can't be prepared to push their buttons, use the random module. At the top of your file, add the following import.

```py
from random import uniform
```

The `uniform` function can be used to generate a random floating point number. The random module's documentation provides the following description of `uniform`.

> `random.uniform(a, b)`
>
> Return a random floating point number `N` such that `a <= N <= b` for `a <= b` and `b <= N <= a` for `b < a`.
>
> The end-point value `b` may or may not be included in the range depending on floating-point rounding in the equation `a + (b-a) * random().`

Replace the five second time you added above with a random time by using the return value of the `uniform` function. You will need to choose values of `a` and `b` to set the maximum and minimum delay for your game.

## Testing

Before going further, make sure that your LED code is working. Run your program several times and check that the LED turns on and then off after a random amount of time. The time it takes the LED to turn off should be different each time your program runs \(although you might not be able to see a different time depending on the minimum and maximum delay you chose\).

If the LED doesn't do what you expect it to, there may be a problem in your circuit or code. Identify and fix any problems, then run your program again to check if the problem has been fixed.

