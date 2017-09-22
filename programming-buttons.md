# Programming the Buttons

## Setup

First update the import at the top of your file to include `Button`.

```py
from gpiozero import Button, LED
```

Near the top of your file, after you setup the LED, setup your buttons with the pin numbers that you connected them to when building your circuit.

```py
player_one_button = Button(-1) # Change the pin number to match your circuit
player_two_button = # Setup based on your circuit
```

## Running Code when the Buttons are Pressed

In order to run code when the buttons are pressed, copy the incomplete `button_pressed` function below where you setup the buttons.

```py
def button_pressed(button):
    # Code to respond to buttons being pressed goes here
```

The `button_pressed` function requires a single argument named `button` and will not return anything. To run this function whenever the buttons are pressed, configure the GPIO library to call it. Below the `button_pressed` function, add the following code **for each button**. For example, to configure player one's button, use the following code.

```py
player_one_button.when_pressed = button_pressed
```

It is important to **reference the function, but not call it** when configuring the GPIO library. You refer to the function by using it's name alone, without any parentheses or arguments. If you call the function, the GPIO library will be configured to run the _return value_ of the function when the button is pressed. This might cause an error when this line of your program runs, or your program may work without any errors, but it will not behave how you expect it to.

When correctly configured, the GPIO library will call the `button_pressed` function with the button that was pressed as the argument whenever a button is pressed. For example, if player one's button was pressed, `button_pressed` would run, and the value of it's argument would be equal to `player_one_button`.

## Responding to Button Presses

Add a variable named `game_over` before the `button_pressed` function and after you setup the LED and buttons. Initialize `game_over` to the value `False`. The `game_over` variable will be used so the program waits until a button is pressed before exiting.

Implement the `button_pressed` function so that when a button is pressed, it

1. Checks if `game_over` is `True`. If it is not `True`
   1. Set `game_over` to `True`
   2. Print "Player one wins." or "Player two wins.", depending on which button was pressed

To change the value of `game_over` in the `button_pressed` function, you will need to add the following line in `button_pressed` before you try changing the value of `game_over`. This line tells the Python interpreter that you want to change the value of `game_over` instead of making a new variable named `game_over` that exists only in the `button_pressed` function.

```py
global game_over
```

At the end of your file, add the following loop to wait until `game_over` is `True` to exit the program.

```py
while not game_over:
    sleep(0.01)
```

This code waits a small amount of time as long as the game is not over, meaning a button has not been pressed.

If you're wondering how the above code works, recall that the `button_pressed` function is called by the GPIO library whenever a button is pressed, and you can imagine it as running at the same time as the loop above. The loop periodically checks if the `button_pressed` function has changed the value of `game_over` to indicate that the program should end. The small sleep time allows other code, such as the `button_pressed` function or other programs on the Raspberry Pi, to run while your code waits for `game_over` to change.

## Testing

Before going further, make sure that your button code is working. Run your program and push each button when the LED turns off. Make sure that the correct player is printed when you push the button.

If the buttons don't do what you expect them to, there may be a problem in your circuit or code. Identify and fix any problems, then run your program again to check if the problem has been fixed.