# Gamble-game
import random

def lucky_number_game():
    balance = 100
    print("Welcome to Lucky Number!")
    print("Guess a number between 1 and 10. If you guess right, you win 10x your bet. Otherwise, you lose your bet.")
    print("You start with $100. Good luck!\n")

    while balance > 0:
        print(f"Your current balance: ${balance}")
        try:
            bet = int(input("Enter your bet amount (or 0 to quit): "))
            if bet == 0:
                print("Thanks for playing!")
                break
            if bet < 0 or bet > balance:
                print("Invalid bet amount. Try again.")
                continue
            guess = int(input("Guess a number between 1 and 10: "))
            if guess < 1 or guess > 10:
                print("Invalid number. Try again.")
                continue
        except ValueError:
            print("Please enter valid numbers.")
            continue

        winning_number = random.randint(1, 10)
        if guess == winning_number:
            winnings = bet * 10
            balance += winnings
            print(f"Congratulations! The winning number was {winning_number}. You win ${winnings}!")
        else:
            balance -= bet
            print(f"Sorry, the winning number was {winning_number}. You lose your bet.")

    if balance <= 0:
        print("You're out of money! Game over.")

if __name__ == "__main__":
    lucky_number_game()