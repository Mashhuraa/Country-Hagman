Country Hangman Game
--------------------------------------

Overwiev
----------------------------------
This repository contains a Python implementation of a `Hangman game` focused on guessing country names. The game selects a random country from a predefined list and allows the player to guess the name letter by letter within a limited number of chances.

Features:
-------------------------------------
* Randomly selects a country name from a predefined list.

* Displays the current state of the word with underscores for unguessed letters.

* Provides feedback on whether a guessed letter is in the word.

* Tracks the number of remaining chances.
  
* Defines winning and losing conditions.
  
Usage
------------------------------
Clone the repository:
git clone https://github.com/yourusername/country-hangman-game.git
cd country-hangman-game

Run the game:
---------------------------------
python hangman.py

Game Mechanics
------------------------------------------

Set Up Your Word List

The game uses a list of countries as potential secret words:

countries =` ["Canada", "Brazil", "India", "Germany", "Australia"]`

Random Selection
--------------------------------
A random country is selected from the list:

import random

secret_word = random.choice(countries).lower()

Display Current State
---------------------------
A function to display the current state of the word with underscores for unguessed letters:

def display_current_state(secret_word, guessed_letters):
    return " ".join([letter if letter in guessed_letters else "_" for letter in secret_word])\
    
Guessing Chances
--------------------------------
The player gets a number of chances equal to the length of the country name plus 2:

chances = len(secret_word) + 2

Process Letter Guess
----------------------------------
A function to process the player's guess and update the state of the game:

def process_guess(secret_word, guessed_letters, guess):
    if guess in secret_word:
        guessed_letters.add(guess)
        return True
    return False
    
Winning Condition
--------------------------------
A function to check if the player has won:

def check_winning(secret_word, guessed_letters):
    return all(letter in guessed_letters for letter in secret_word)
    
Main Game Loop
----------------------------------------------
The main game loop that interacts with the player:

def play_game():
    guessed_letters = set()
    secret_word = random.choice(countries).lower()
    chances = len(secret_word) + 2
    print("Welcome to Country Hangman!")
    while chances > 0:
        print("\nCurrent state:", display_current_state(secret_word, guessed_letters))
        print("Chances remaining:", chances)
         guess = input("Enter a letter: ").lower()
         if process_guess(secret_word, guessed_letters, guess):
            print("Correct guess!")
        else:
            print("Incorrect guess!")
            chances -= 1
       if check_winning(secret_word, guessed_letters):
            print("\nCongratulations! You guessed the word:", secret_word)
            return
         print("\nGame over! The word was:", secret_word)

if __name__ == "__main__":
    play_game()

GitHub Repository
----------------------------
Upload the following files to your GitHub repository:

`README.md` (this file)
`hangman.py` (the main game script)
