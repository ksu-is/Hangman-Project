# Hangman-Project
This project aims to create a word game to guess a word before the player runs out of attempts. The game should be challenging and rewarding for players of all skill levels and ages. 



#Base code





import random

def choose_word():
    words = ["apple", "banana", "orange", "grape", "pineapple"]
    return random.choice(words)

def display_word(secret_word, guessed_letters):
    display = ""
    for letter in secret_word:
        if letter in guessed_letters:
            display += letter + " "
        else:
            display += "_ "
    return display.strip()

def hangman():
    secret_word = choose_word()
    guessed_letters = []
    attempts_left = 7
    
    print("Welcome to Hangman!")
    
    while attempts_left > 0:
        print("\nWord:", display_word(secret_word, guessed_letters))
        print("Attempts left:", attempts_left)
        
        guess = input("Guess a letter: ").lower()
        
        if len(guess) != 1 or not guess.isalpha():
            print("Please enter a single letter.")
            continue
        
        if guess in guessed_letters:
            print("You've already guessed that letter.")
            continue
        
        guessed_letters.append(guess)
        
        if guess not in secret_word:
            print("Incorrect guess!")
            attempts_left -= 1
        else:
            print("Correct guess!")
        
        if all(letter in guessed_letters for letter in secret_word):
            print("\nCongratulations! You've guessed the word:", secret_word)
            break
    
    if attempts_left == 0:
        print("\nSorry, you've run out of attempts. The word was:", secret_word)

hangman()
