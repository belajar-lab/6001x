## Introduction

In this problem set, you'll implement *two* versions of a wordgame!

Don't be intimidated by the length of this problem set. There is a lot of reading, but it can be done with a reasonable amount of thinking and coding. It'll be helpful if you start this problem set a few days before it is due!

Let's begin by describing the 6.00 wordgame: This game is a lot like Scrabble or Words With Friends, if you've played those. Letters are dealt to players, who then construct one or more words out of their letters. Each **valid** word receives a score, based on the length of the word and the letters in that word.

The rules of the game are as follows:

### Dealing

- A player is dealt a hand of $n$ letters chosen at random (assume $n=7$ for now).
- The player arranges the hand into as many words as they want out of the letters, using each letter at most once.
- Some letters may remain unused (these won't be scored).

### Scoring

- The score for the hand is the sum of the scores for each word formed.
- The score for a word is the sum of the points for letters in the word, multiplied by the length of the word, plus 50 points if all $n$ letters are used on the first word created.
- Letters are scored as in Scrabble; A is worth 1, B is worth 3, C is worth 3, D is worth 2, E is worth 1, and so on. We have defined the dictionary `SCRABBLE_LETTER_VALUES` that maps each lowercase letter to its Scrabble letter value.
- For example, 'weed' would be worth 32 points ((4+1+1+2) for the four letters, then multiply by `len('weed')` to get (4+1+1+2)*4 = 32). Be sure to check that the hand actually has 1 'w', 2 'e's, and 1 'd' before scoring the word!
- As another example, if $n=7$ and you make the word 'waybill' on the first try, it would be worth 155 points (the base score for 'waybill' is (4+1+4+3+1+1+1)*7=105, plus an additional 50 point bonus for using all $n$ letters).

### Sample Output
<details>
    <summary>Here is how the game output will look!</summary>
    Loading word list from file...
       83667 words loaded.
    Enter n to deal a new hand, r to replay the last hand, or e to end game: n
    Current Hand: p z u t t t o
    Enter word, or a "." to indicate that you are finished: tot
    "tot" earned 9 points. Total: 9 points
    Current Hand: p z u t
    Enter word, or a "." to indicate that you are finished: .
    Total score: 9 points.
    
    Enter n to deal a new hand, r to replay the last hand, or e to end game: r
    Current Hand: p z u t t t o
    Enter word, or a "." to indicate that you are finished: top
    "top" earned 15 points. Total: 15 points
    Current Hand: z u t t
    Enter word, or a "." to indicate that you are finished: tu
    Invalid word, please try again.
    Current Hand: z u t t
    Enter word, or a "." to indicate that you are finished: .
    Total score: 15 points.
    
    Enter n to deal a new hand, r to replay the last hand, or e to end game: n
    Current Hand: a q w f f i p
    Enter word, or a "." to indicate that you are finished: paw
    "paw" earned 24 points. Total: 24 points
    Current Hand: q f f i
    Enter word, or a "." to indicate that you are finished: qi
    "qi" earned 22 points. Total: 46 points
    Current Hand: f f
    Enter word, or a "." to indicate that you are finished: .
    Total score: 46 points.
    
    Enter n to deal a new hand, r to replay the last hand, or e to end game: n
    Current Hand: a r e t i i n
    Enter word, or a "." to indicate that you are finished: inertia
    "inertia" earned 99 points. Total: 99 points
    Run out of letters. Total score: 99 points.
    
    Enter n to deal a new hand, r to replay the last hand, or e to end game: e
</details>


## Getting Started

The file *ps4a.py* has a number of already implemented functions. You can ignore the code between the following comments, though you should read and understand how to use each helper function by reading the docstrings:
    
    # -----------------------------------
    # Helper code
    # You don't need to understand this helper code,
    # but you will have to know how to use the functions
    # (so be sure to read the docstrings!)
        .
        .
        .
    # (end of helper code)
    # ----------------------------------- 
    
This problem set is structured so that you will write a number of modular functions and then glue them together to form the complete word playing game. Instead of waiting until the entire game is **ready**, you should test each function you write, individually, before moving on. This approach is known as **unit testing**, and it will help you debug your code.

We have provided several test functions to get you started. After you've written each new function, unit test by running the file *test_ps4a.py* to check your work.

If your code passes the unit tests you will see a `SUCCESS` message; otherwise you will see a `FAILURE` message. These tests aren't exhaustive. You will want to test your code in other ways too.

Try running *test_ps4a.py* now (before you modify the *ps4a.py* skeleton). You should see that all the tests fail, because nothing has been implemented yet.

These are the provided test functions:

- `test_getWordScore()`
Test the `getWordScore()` implementation.
- `test_updateHand()`
Test the `updateHand()` implementation.
- `test_isValidWord()`
Test the `isValidWord()` implementation.