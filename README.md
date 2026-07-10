 import random

# List of predefined words
words = ["python", "computer", "science", "program", "hangman"]

# Randomly choose a word
word = random.choice(words)

guessed_letters = []
wrong_guesses = 0
max_wrong = 6

print("🎮 Welcome to Hangman Game!")
print("Guess the word one letter at a time.")
print(f"You have {max_wrong} incorrect guesses.\n")

while wrong_guesses < max_wrong:

    # Display the current word
    display_word = ""
    for letter in word:
        if letter in guessed_letters:
            display_word += letter + " "
        else:
            display_word += "_ "

    print("\nWord:", display_word)

    # Check if word is completed
    if "_" not in display_word:
        print("\n🎉 Congratulations! You guessed the word:", word)
        break

    # Take user input
    guess = input("Enter a letter: ").lower()

    # Validate input
    if len(guess) != 1 or not guess.isalpha():
        print("❌ Please enter only one alphabet.")
        continue

    # Check duplicate guess
    if guess in guessed_letters:
        print("⚠️ You already guessed that letter.")
        continue

    guessed_letters.append(guess)

    # Check if guess is correct
    if guess in word:
        print("✅ Correct!")
    else:
        wrong_guesses += 1
        print("❌ Wrong guess!")
        print("Remaining chances:", max_wrong - wrong_guesses)

# If player loses
if wrong_guesses == max_wrong:
    print("\n💀 Game Over!")
    print("The correct word was:", word)
