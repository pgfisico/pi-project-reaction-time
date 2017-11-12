# Disqualifying Players

Try running your program again, but this time push a button before the LED turns off.

You should find that your program prints that the player whose button you pushed has won, and that it has calculated a reaction time that doesn't seem right. Why is this happening?

This happens because you initialize `start_time` to zero, and if you push the button while the LED is still on, `start_time` is not set correctly and remains zero when the `button_pressed` function is running. This causes the calculated reaction time to be incorrect.

In order to workaround this issue, the game will disqualify players who push their button before the LED has been turned off.

## Tracking When Button Presses are Allowed

To track when button presses are allowed, and will not disqualify a player, add a variable named `button_press_allowed` above `start_time` and set it to `False`.

Before turning the LED off, but after updating `start_time`, set `button_press_allowed` to `True`. The order should be as follows:

1. Set `start_time`
2. Set `button_press_allowed`
3. Turn the LED off

This order ensures that `start_time` is correctly set before button presses are allowed. The order also prevents there from being a very small amount of time just after the LED turns off that we disqualify players even though the LED is off at that point.

Update the `button_pressed` function to check if button presses are allowed. If they are not, print either "Player one pushed their button before the LED turned off and is disqualified. Player two wins." or "Player two pushed their button before the LED turned off and is disqualified. Player one wins." depending on which button was pressed. If button presses are allowed, the function should continue to print which player won and their reaction time. In both cases, the function should continue to set `game_over` to `True`.

## Playing the Game

Run your program and try pressing the buttons before the LED turns off. Make sure that the appropriate player is disqualified depending on which button was pressed. Also make sure it continues to work if you press a button after the LED turns off. If your program doesn't do what you thought it would, identify and fix any problems, then run your program again to check if the problem has been fixed.

Once it's working, try challenging someone to a competition!

