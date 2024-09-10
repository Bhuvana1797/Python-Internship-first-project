### Introduction to "Guess the Number" Project

The *"Guess the Number"* project is a simple Python game where players guess a randomly generated number within a limited number of attempts. The game provides feedback, indicating if the guess is too high or too low, and allows the player to choose a difficulty level. It demonstrates basic programming concepts such as loops, conditionals, and input validation.



import random

def guess_the_number():
    print("Welcome to Guess the Number!")
    
    # Select difficulty level
    while True:
        difficulty = input("Select difficulty level (easy, medium, hard): ").lower()
        if difficulty == "easy":
            max_number = 50
            attempts = 15
            break
        elif difficulty == "medium":
            max_number = 100
            attempts = 10
            break
        elif difficulty == "hard":
            max_number = 200
            attempts = 5
            break
        else:
            print("Invalid choice, please select either 'easy', 'medium', or 'hard'.")
            # The loop will continue until valid input is given

    # Generate a random number
    random_number = random.randint(1, max_number)
    score = 0
    
    print(f"Try to guess the number (between 1 and {max_number}). You have {attempts} attempts.")

    # Game loop
    while attempts > 0:
        # Get player input
        try:
            guess = int(input("Enter your guess: "))
        except ValueError:
            print("Please enter a valid number.")
            continue

        # Check if the guess is correct
        if guess == random_number:
            print(f"Congratulations! You guessed the number {random_number} correctly.")
            score += attempts * 10  # Score based on remaining attempts
            break
        elif guess < random_number:
            print("Your guess is too low.")
        else:
            print("Your guess is too high.")
        
        # Reduce attempts and display remaining attempts
        attempts -= 1
        print(f"Remaining attempts: {attempts}")
        print(f"Score so far: {score}")

        # End game if out of attempts
        if attempts == 0:
            print(f"Sorry! You've run out of attempts. The correct number was {random_number}.")
            break

    # Option to play again
    play_again = input("Do you want to play again? (yes/no): ").lower()
    if play_again == "yes":
        guess_the_number()
    else:
        print(f"Thanks for playing! Your final score was: {score}")

# Start the enhanced console-based game
guess_the_number()
