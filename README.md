# Guessing-Game-Python-unfair-
#The unfair version uses a binary search based concept for better odds of the computer winning.

#You think of a number and the computer tries to guess it.
#You instruct the computer to go higher or lower or tell if the guess is correct.
#The number of guesses the computer uses are counted.

#Then the computer thinks of a number and you try to guess it.
#The computer instructs you to go higher or lower or tell if the guess is correct.
#The number of guesses you use are counted.

#The one who requires minimum number of guesses wins.

import random

def player_num():
    '''
    Here, the player thinks of a number and the
    computer tries to guess it.
    '''

    #initializations
    min = 1        #initial guessed random num's range beginning
    max = 51      #initial guessed random num's range end
    no_of_guesses = 0

    #start the game
    start = int(input("Think of a number between 1 to 50. \nPress 1 when ready."))
    while(start == 1):
        
        #comp guesses a num
        while(max>=min):
            guessed_num = min+((max-min)//2)

            #comp asks for a clue
            num_range = input("Is the number " + str(guessed_num) + "? (higher/lower/equal):")

            #if player's num is higher, guess next num in a range higher than the currently guessed num
            #when while loop executes again, it will use this newly assigned value of min to guess new number
            if(num_range == 'higher'):
                no_of_guesses += 1  #num of guesses inc by 1
                min = guessed_num

            #if player's num is lower, guess next num in a range lower than the currently guessed num
            #when while loop executes again, it will use this newly assigned value of max to guess new number
            elif(num_range == 'lower'):
                no_of_guesses += 1  #num of guesses inc by 1
                max = guessed_num

            #if payer's num is equal, display guessed num & num of guesses used by comp
            #return num of guesses
            elif(num_range == 'equal'):
                no_of_guesses += 1   #num of guesses inc by 1
                print("The computer has successfully guessed the number!")
                print("The number is " + str(guessed_num) + "!")
                print("The computer has required " + str(no_of_guesses) + " number of guesses.")
                return no_of_guesses


def comp_num():
    '''
    Here, the comp thinks of a number and the
    player tries to guess it.
    '''

    #initializations
    min = 0
    max = 51
    no_of_guesses = 0
    
    #Comp thinks of a num
    comp_num = random.randrange(0,51)

    #start
    print("The computer has thought of a number between 1 and 50")
    start = int(input("Press 1 when you're ready to play: "))
    while(start == 1):

        #take number from player
        guessed_num = int(input("Enter your guess (you have to guess between " + str(min) + " and " + str(max) + "): "))

        #player's guess is low
        if(guessed_num < comp_num):
            no_of_guesses += 1  #num of guesses inc by 1

            #When the while loop executes again and the player inputs another guess, the player is prompted to guess a num higher than that currently guessed.
            #This prevents repetition of numbers.
            min = guessed_num

            #Gives the player a clue
            print("Go higher!")

        #player's guess is high
        elif(guessed_num > comp_num):
            no_of_guesses += 1  #num of guesses inc by 1

            #When the while loop executes again and the player inputs another guess, the player is prompted to guess a num higher than that currently guessed.
            #This prevents repetition of numbers.
            max = guessed_num

            #gives the player a clue
            print("Go lower!")

        #if payer's num is equal, display guessed num & num of guesses used by comp
        #return num of guesses
        elif(guessed_num == comp_num):
            no_of_guesses += 1  #num of guesses inc by 1
            print("You have successfully guessed the number!")
            print("The number is " + str(guessed_num) + "!")
            print("You have required " + str(no_of_guesses) + " number of guesses.")
            return no_of_guesses




def main():
    no_of_guesses_comp = player_num()
    no_of_guesses_player = comp_num()
    if(no_of_guesses_comp == no_of_guesses_player):
        print("IT'S A TIE!")

    if(no_of_guesses_comp > no_of_guesses_player):
        print("PLAYER WINS!")

    if(no_of_guesses_comp < no_of_guesses_player):
        print("COMPUTER WINS!")


if __name__ == '__main__':
    main()
