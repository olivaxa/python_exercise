# python_exercise
#It's the roulette game : player bets money on a number between 0 and 49. If the result of the roulette is this number, the player wins 3 times the amount he bet.
#If he finds the win color (if he bet on a odd number (respectivly even number) and the result is an odd number (respectivly even number)), he win 0.5 time the
#amount he bet. Otherwise, he loses. He can play as long as he has money.

import random
print("How much money do you have ?")
money=input()
while money<=0:
    print("The number must be positive")
    money=input()
restart=True

while restart:
    print("On which number between 0 and 49 do you bet ?")
    num=input()
    while num<0 or num>49:
        print("Your number must be between 0 and 49")
        num=input()
    print("How much money do you bet ?")
    bet=input()
    while bet<=0 or bet>money:
        print("The bet amount must be strictly positive and cannot be greater than the money you have")
        bet=input()
    result=random.randint(0,49)
    print("The win number is ",result," !")
    if result==num:
        money=money+3*bet
        print("Congratulations, you found the win number and win ",3*bet" dollars")
    else:
        if result%2==num%2:
            money=money+0.5*bet
            print("You found the win color and win ",0.5*bet," dollars")
        else:
            money=money-bet
            print("Sorry, you have lost")
    if money==0:
        print("You don't have money anymore, game is over")
        restart=False
    else:
        print("You have now ",money," dollars")
        game=input("Do you want to replay (y/n) ?")
        if game=="y":
            restart=True
        else:
            restart=False
