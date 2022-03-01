from itertools import count
from math import *
from random import *
from time import *

from database import adminusername
from database import adminpassword
from database import countriescapitals

gameRunning = True
gameRunning2 = True
chosenValue = 848917238917389

# Current know issues:
# Repeated values buggish, somewhat fixed
# 

valuesAlreadyInSystem = {" "}
currentScore = 0
currentTries = 0
overallTotal = 0
overallCorrect = 0

print("Welcome!")
print("Within this game, you must guess the capitals to these countries!")
while True:
    print("Menu:")
    print("1. Play Game")
    print("2. Help")
    print("3. Clear Data")
    print("4. Quit")
    try:
        chosenValue = int(input("Please chose an argument!"))
    except:
        print("Error occured! Have you chosen the argument carfully?")
    if chosenValue not in {1, 2, 3, 4,}:
        continue
    elif chosenValue == 1:
        while gameRunning == True:
            try:
                amountOfGoes = int(input("Please input the amount of attempts you would like to do."))
            except:
                print("Error occured! Have you chosen the argument carfully?")
            if amountOfGoes > 5:
                print("This value is over the scales of the amount of data!")
                print("Currently, the max amount of goes is 4 as there isn't as much values currently.")
            else:
                while gameRunning2 == True:
                    chosenQuestion = choice(list(countriescapitals.items()))
                    if chosenQuestion in valuesAlreadyInSystem:
                        continue
                    elif chosenQuestion not in valuesAlreadyInSystem:
                        while True:
                            print("What is the Capital City of", chosenQuestion[0] + "?")
                            questionGuess = input("What is your guess?")
                            if questionGuess.lower() == chosenQuestion[1].lower():
                                currentScore += 1
                                print("Correct! The Capital City of", chosenQuestion[0], "was", chosenQuestion[1] + "!")
                            else:
                                print("Incorrect! The Capital City of", chosenQuestion[0], "was", chosenQuestion[1] + "!")
                            valuesAlreadyInSystem.add(chosenQuestion[0])
                            currentTries += 1
                            break
                        if currentTries == amountOfGoes:
                            print("Game over!")
                            overallCorrect += currentScore
                            overallTotal += currentTries
                            print("You have guessed", str(currentScore), "correctly, out of", str(currentTries) + "!")
                            print("Your overall accuracy was", str(floor((overallCorrect/overallTotal)*100)) + "%.")
                            currentTries = 0
                            currentScore = 0
                            valuesAlreadyInSystem.clear()
                            gameRunning2 = False
                            gameRunning = False
                            break              
    elif chosenValue == 2:
        print("You must attempt to guess the capital city of the country")
        print("For example, if the question asked about the Capital City of the Russia, the answer would be Moscow.")
    elif chosenValue == 3:
        currentScore = 0
        overallCorrect = 0
        overallTotal = 0
    elif chosenValue == 4:
        print("Thank you for playing")
        break
    elif chosenValue == adminusername: #testing admin  (not secure)
        password = input("Please enter the password!")
        if password == adminpassword:
            evalCommand = input("Input command!")
            eval(evalCommand) # Wanting to edit the script, while client is running
        else:
            print("Really? You aren't meant to find this!")
            break
