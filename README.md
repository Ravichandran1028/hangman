import random

word_list = ["apple", "tiger", "chair", "brick", "plane"]


secret_word = random.choice(word_list)


guessed_letters = []


max_attempts = 6
wrong_attempts = 0


print("🎮 Welcome to Hangman!")
print("_ " * len(secret_word))  # Initial hidden word


while wrong_attempts < max_attempts:
    guess = input("Guess a letter: ").lower()

  
    if not guess.isalpha() or len(guess) != 1:
        print("Please enter a single letter.")
        continue

    if guess in guessed_letters:
        print("You already guessed that letter.")
        continue

  
    guessed_letters.append(guess)

    
    if guess in secret_word:
        print("✅ Correct!")
    else:
        print("❌ Incorrect!")
        wrong_attempts += 1

    
    display_word = ""
    for letter in secret_word:
        if letter in guessed_letters:
            display_word += letter + " "
        else:
            display_word += "_ "

    print("Word: ", display_word.strip())
    print(f"Wrong guesses: {wrong_attempts}/{max_attempts}")

    
    if all(letter in guessed_letters for letter in secret_word):
        print("🎉 Congratulations! You guessed the word!")
        break
else:
    print(f"💀 Game Over! The word was: {secret_word}")
