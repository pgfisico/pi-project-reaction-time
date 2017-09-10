# Measuring Reaction Time

## Setup

In order to measure reaction time, use the `perf_counter` function from the time module. This function requires no arguments and returns a floating point number of seconds. The number of seconds returned has no specific reference point, however the difference between the number of seconds returned by two different calls to `perf_counter` can be used to find the number of seconds that has passed between the two calls.

To use `perf_counter`, update the import at the top of your file to include `perf_counter`.

```py
from time import perf_counter, sleep
```

## Storing the Start Time

Above the `button_pressed` function and below where you setup the LED and buttons, add a variable named `start_time` and set it's value to zero.

Immediately before turning off the LED, store the return value of the `perf_counter` function in `start_time`.

## Calculating Reaction Time

At the beginning of the `button_pressed` function, add a variable named `end_time` and assign it the return value of the `perf_counter` function. This should be the first line in the `button_pressed` function so that you stop timing as soon as possible, and are not including the time your code takes to run in the reaction time.

Update the `button_pressed` function to calculate the reaction time of the winning player using `start_time` and `end_time`, and print out the calculated reaction time for the winning player.

## Testing

Before going further, make sure that your reaction time code is working. Run your program and push each button when the LED turns off. Make sure that the correct player and a reasonably accurate reaction time is printed when you push the button.

If the buttons don't do what you expect them to, there may be a problem in your circuit or code. Identify and fix any problems, then run your program again to check if the problem has been fixed.