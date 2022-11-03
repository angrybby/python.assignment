import random

def compare_number(number, user_guess):
    cowbull = [0, 0, 0, 0]
    for i in range(len(number)):
        if number[i] == user_guess[i]:
           cowbull[i] += 1
    return cowbull


if __name__ == "__main__":
    playing = True
    number = str(random.randint(1000, 10000))
    guesses = 0

    print("Let's Play A Game Of Cows And Bulls!")
    print("I Will Generate A 4 Digit Number, And You Have To Guess The Numbers One Digit At A Time.")
    print("For Every Number I The Wrong Place, You Get A Bull. For Every Number In The Right Place, You Get A Cow.")
    print("The Game Will End When You Get 4 Bulls.")
    print("Type Exit At Any Prompt To Exit!")

while playing:
    user_guess = input("Give Me The Best You Got!: ")
    if user_guess.lower() == "exit":
        break
    cowbull_count = compare_number(number, user_guess)
    guesses += 1
    correct = sum(cowbull_count)
    wrong = len(number) - correct
    print(f"You Have {correct} Cows, And {wrong} Bulls.")

    if correct == 4:
        playing = False
        print(f"You Win The Game After {guesses} Guess(es)!. The Number Was {number}.")
        break
    else:
        print(f"Your Guess Isn't Quite Right, Try Again!.")
        if correct >= 1:
            print(str([user_guess[i] for i, x in enumerate(cowbull_count) if x == 1]) + " was correct!")
