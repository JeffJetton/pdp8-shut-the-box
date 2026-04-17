# PDP-8 SHUT THE BOX: HOW TO PLAY
  


## Setting Up the Game

In the "real world" version of Shut the Box, there are nine hinged wooden doors or flaps that cover up the numbers one through nine. At the beginning of a game, you open them up so that all the numbers are visible. The goal is to shut the doors based on the results of dice rolls.

For this PDP-8 version, the Switch Register switches are our doors that start out "open" (flipped down to their set/on position), and the goal is to "shut" them (flip them back up) according to virtual dice that are rolled in the Accumulator indicator lights.

* Start the program running (from address 0200). The Accumulator indicator lights will reflect the current Switch Register.
* Open **nine** "doors" in a row by flipping any nine consecutive Switch Register switches to the down (set) position, causing their corresponding Accumulator light to turn on.
* The remaining switches should remain "shut" (flipped up/unset).
* The game will kick off as soon as nine--and only nine--switches are set in a row.
    * NOTE: If the switches are already correcly set before the program starts, you'll still need to toggle one of them off and on to signal to the computer that you're ready to play.

These doors/switches are assigned the values **one** through **nine**, in order from left to right.


On a PDP-8 without numbers printed over the switches, it's easiest to keep track if you set them either flush left or flush right, so the doors are color-coded in three groups of three:

```
  *** *** *** ---
  123 456 789
  
        or     
  
  --- *** *** ***
      123 456 789

```
On models such as the PDP-8/E, where bit numbers are printed over the switches, you'll probably want to set bits 1-9, so the numbers match the door values:

```
               11
  012 345 678 901
  -** *** *** *--
```



## Playing

* Once the switches are set correctly, two virtual  dice will be automatically "rolled" for you in the Accumulator lights. The number of lit-up lights for each die tells you the result of the roll.
* Choose one or more open doors to "shut" by flipping them back up. **The total value of those doors must match the total shown on the dice**
* Once you're satisfied with your choices, press **Start** or **Continue** to submit your turn. (Be careful not to press Load Address, Deposit, or Examine by accident!)
* The dice will roll again, and the process repeats. If the total value of remaining open doors becomes **six or less**, only a single die will be rolled.

## Ending the Game

If the rolled dice total is impossible to match with any combination of still-open doors, the **the dice will flash slowly** at the end of the roll to let you know that **the game is over**.
  
* Your **score** is the total value of remaining open doors--the lower, the better.
* If your PDP-8 has an MQ register, this score will also display there (one light per point, up to a maximum of 12).
   
If you manage to shut all the doors (flip up every switch), congratulations! You've **Shut the Box** and earned the best possible score of zero. This is not an easy feat!

To play again, just reset the switches so that you have any nine open doors (flipped down switches) in a row again. A new game will automatically start.


  
 
## Example

Let's say you start a new game and get this result for your first roll of the dice:

```
   --**---****--
```

That's a two and four, for a total of six. Your options would be any of the following combinations that add up to that same total:

* Shut door **6**
* Shut doors **1** and **5**
* Shut doors **2** and **4**
* Shut doors **1**, **2**, and **3**

Perhaps you door **6** first, but change your mind and re-open it (flip it back down). That's okay--your turn doesn't count until you press Start/Continue.

You finally decide to shut doors **2** and **4**.

On your next roll, you get two sixes, for a total of twelve (all AC lights lit):

```
   ************
```

You again have several options, such as **9** and **3**, or **1**, **3**, and **8**. But you can't choose a combination like **4** and **8**, since you already shut door **4** in a prior turn. (Once a door is shut in a previous turn, it stays shut.)

After a few more turns, you wind up with every switch flipped up except for the one corresponding to door **4**. Since the remaining doors total less than five, only one die is rolled:

```
   -------****-
```

How lucky! You got a four!

You flip up the last switch and... *nothing*. Remember, you still have to **submit** your turn by pressing Start or Continue, even if it's the game-winning flip.

## Making Mistakes

If you submit your turn by pressing Start/Continue and get one or more **quickly-flashing lights** in the Accumulator, that means your selection was invalid due to:

* The doors you just shut do not add up to dice roll total, and/or...
* One or more doors that were shut in a previous turn have been reopened

Toggle the switches that correspond to the blinking lights to "undo" your entire move. Once everything is back the way it was before, the previous dice results will redisplay, and you can try again.

## Multiple Players

Compete with your friends by letting everyone play a full game and seeing who can get the best (lowest) score.

You can also play the **golf** variation:

* Decide in advance how many "holes" to play, such as nine or a full 18.
* For each hole, all players play a full game in turn and write down their scores. This is the number of "strokes" they took for the hole.
* The player with the lowest total score over all holes is the winner.
* Mercy rule: Any game score over twelve counts as twelve strokes. That is, you can only score a maximum of twelve on any one hole, no matter how poorly you do on it.
* Shut Rule: Anyone who "Shuts the Box" scores zero for that hole, and all other players have to *add* twelve strokes to their own score.
