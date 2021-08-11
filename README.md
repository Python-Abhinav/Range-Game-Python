# Range-Game-Python
This is a range game where you'll have to guess the computer's number by two hints - high or low!

    def range_game():

	    from random import randint
        print("Welcome to Range Game!\nRules:\nYou have to get the correct number taken by the computer randomly.\nIt gives you hints to get closer\n")
        try:
            game_chances = int(input("How many number of chances do you want?: "))
            total_chances = game_chances
            range_taken = int(input("What range do you want? [Including your number]: "))
            computer_num = randint(0,range_taken)
        except:
            print("Invalid!")
            range_game()
        while game_chances != 0:
            try:
                user_num = int(input("Select a number: "))
            except:
                print("Invalid!")
                range_game()
            if user_num < 0:
                print(f"Your number {user_num} exceeds the lowest possible number!")
            elif user_num > range_taken:
                print(f"Your number {user_num} exceeds the highest possible number!")
            elif user_num > computer_num:
                print(f"Your number {user_num} is too high!")
                game_chances -= 1
            elif user_num < computer_num:
                print(f"Your number {user_num} is too low!")
                game_chances -= 1
            elif user_num == computer_num:
                print(f"Correct! Your answer ({user_num}) matched with computer answer ({computer_num})")
                print(f"You did it in {total_chances-game_chances} chances !")
                break
            print(f"Chances left:- {game_chances}\n")
        if game_chances == 0:
            print(f"You lost! Chances Left: {game_chances}")
            print(f"Computer number: {computer_num}")
        restart = input("Would you try again? (Yes/No): ").lower().strip()
        range_game() if restart == 'yes' else exit()
    range_game()
