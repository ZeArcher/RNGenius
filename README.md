#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <math.h>
#include <ctype.h>
#include <windows.h>


void main()
{
	//uses time to seed the random number generators
	srand(time(NULL));

	//setting all my variables beforehand
	int play = 1, validOption = 0, endGame, gameChoice;
	int coinFlip, coinChoice, topWinStreakCoin = 0, winStreakCoin = 0, winsCoin = 0, lossCoin = 0;
	int diceRoll, diceChoice, topWinStreakDice = 0, winStreakDice = 0, winsDice = 0, lossDice = 0;
	int suitDraw, cardDraw, suitChoice, cardChoice, topWinStreakCard = 0, winStreakCard = 0, winsCard = 0, lossCard = 0;
	int winsTotal, lossTotal;
	float winrateCoin, winrateDice, winrateCard, winrateTotal, gamesTotal, gamesCoin, gamesDice, gamesCard;
	char again;

	printf("Welcome to our game!\n\n");

	//loop made to have an exit
	while (play == 1)
	{

		//Menu for games
		printf("Pick a game below:\n");
		printf("1. Coin flip (Easy: 1/2)\n");
		printf("2. Dice Roll (Medium: 1/6)\n");
		printf("3. Card Guess (Hard: 1/52)\n");
		printf("4. Score Output\n");
		printf("5. Exit Program\n");
		printf("Choice: ");
		scanf("%d", &gameChoice);

		//switch case for games
		switch (gameChoice)
		{
		case 1:

			printf("Welcome to coin flip!\n\n");

			printf("Pick a side you want it to flip to, coin will flip until it ends (1/2). High score is tracked\n");

			//looping the game to replay
			do
			{
				//resetting values
				endGame = 0;
				validOption = 0;

				//menu for the game
				printf("Current score: %d\n", winStreakCoin);
				printf("Current High score: %d\n", topWinStreakCoin);
				printf("Pick a side:\n");
				printf("1. heads\n");
				printf("2. talis\n");
				scanf("%d", &coinChoice);

				//this randomises the output
				coinFlip = (rand() % 2) + 1;

				//This delays the flip for authenticity
				Sleep(200);
				printf("Flipping...");
				Sleep(400);

				//check to see if user guess correctly, incorrently, or to validate a choice not given
				if (coinChoice == coinFlip)
				{
					printf("Correct Guess!\n\n");
					winsCoin = winsCoin + 1;
					winStreakCoin = winStreakCoin + 1;
				}
				else if (coinChoice < 1 || coinChoice > 2)
				{
					printf("Pick a valid choice!\n\n");
				}
				else
				{
					//if incorrect, reset winstreak, add a loss, and ask if they want to play again
					winStreakCoin = 0;
					lossCoin = lossCoin + 1;
					printf("You lost!\n");
					while (validOption == 0)
					{
						printf("Play again? (y/n)\n");
						scanf(" %c", &again);
						again = tolower(again);
						if (again == 'n')
						{
							endGame = 1;
							validOption = 1;
						}
						else if (again == 'y')
						{
							validOption = 1;
						}
						else
						{
							printf("Please enter a valid option\n\n");
						}
					} 
				}
				
				//sets the highest winstreak
				if (topWinStreakCoin < winStreakCoin)
				{
					topWinStreakCoin = winStreakCoin;
				}

			} while (endGame == 0);
			break;

		case 2:

			//looping the game to replay
			do
			{
				//resetting values
				endGame = 0;
				validOption = 0;

				//menu for the game
				printf("Lets roll a dice! Pick a number between 1 and 6: ");
				scanf("%d", &diceChoice);

				//this randomises the output
				diceRoll = (rand() % 6) + 1;

				//check to see if user guess correctly, incorrently, or to validate a choice not given
				if (diceRoll == diceChoice)
				{
					printf("You win! Your guess was %d and the dice roll was %d\n", diceChoice, diceRoll);
					winsDice = winsDice + 1;
					winStreakDice = winStreakDice + 1;
				}
				else if (diceChoice > 6 || diceChoice < 1)
				{
					printf("Enter a number between 1 and 6 please\n");
				}
				else
				{
					//if incorrect, reset winstreak, add a loss, and ask if they want to play again
					printf("You lost! Your guess was %d and the dice roll was %d\n", diceChoice, diceRoll);
					if (winStreakDice > topWinStreakDice)
					{
						topWinStreakDice = winStreakDice;

					}
					winStreakDice = 0;
					lossDice = lossDice + 1;
					while (validOption == 0)
					{
						printf("Play again? (y/n)\n");
						scanf(" %c", &again);
						again = tolower(again);
						if (again == 'n')
						{
							endGame = 1;
							validOption = 1;
						}
						else if (again == 'y')
						{
							validOption = 1;
						}
						else
						{
							printf("Please enter a valid option\n\n");
						}
					}
				}
			} while (endGame == 0);

			//sets the highest winstreak
			if (winStreakDice > topWinStreakDice)
			{
				topWinStreakDice = winStreakDice;
			}
			break;

		case 3:
			
			printf("Welcome to card guess!\n\n");

			printf("Guess the card, card will randomly be drawn until you are incorrect (1/52). High score is tracked\n");

			//looping the game to replay
			do
			{
				//resetting values
				endGame = 0;
				validOption = 0;

				//menu for the game
				printf("Current score: %d\n", winStreakCard);
				printf("Current High score: %d\n", topWinStreakCard);
				printf("Pick a suit on the card:\n");
				printf("1. Spades\n");
				printf("2. Clubs\n");
				printf("3. Diamonds\n");
				printf("4. Hearts\n");
				printf("Choice: ");
				scanf("%d", &suitChoice);
				printf("Pick a face on the card:\n");
				printf("1. Ace\n");
				printf("2. 2\n");
				printf("3. 3\n");
				printf("4. 4\n");
				printf("5. 5\n");
				printf("6. 6\n");
				printf("7. 7\n");
				printf("8. 8\n");
				printf("9. 9\n");
				printf("10. 10\n");
				printf("11. Jack\n");
				printf("12. Queen\n");
				printf("13. King\n");
				printf("Choice: ");
				scanf("%d", &cardChoice);
				printf("\n");

				//this randomises the output
				suitDraw = (rand() % 4) + 1;
				cardDraw = (rand() % 13) + 1;

				if ((cardChoice > 0 && cardChoice < 14) || (suitChoice > 0 && suitChoice < 5))
				{

					//This delays the flip for authenticity
					Sleep(200);
					printf("Drawing...\n\n");
					Sleep(400);

					//Outputs the card results that were generated
					switch (suitDraw)
					{
					case 1:
						if (cardDraw == 1)
						{
							printf("The card drawn is: Ace of Spades\n\n");
						}
						else if (cardDraw == 11)
						{
							printf("The card drawn is: Jack of Spades\n\n");
						}
						else if (cardDraw == 12)
						{
							printf("The card drawn is: Queen of Spades\n\n");
						}
						else if (cardDraw == 13)
						{
							printf("The card drawn is: King of Spades\n\n");
						}
						else
						{
							printf("The card drawn is: %d of Spades\n\n", cardDraw);
						}
						break;

					case 2:
						if (cardDraw == 1)
						{
							printf("The card drawn is: Ace of Clubs\n\n");
						}
						else if (cardDraw == 11)
						{
							printf("The card drawn is: Jack of Clubs\n\n");
						}
						else if (cardDraw == 12)
						{
							printf("The card drawn is: Queen of Clubs\n\n");
						}
						else if (cardDraw == 13)
						{
							printf("The card drawn is: King of Clubs\n\n");
						}
						else
						{
							printf("The card drawn is: %d of Clubs\n\n", cardDraw);
						}
						break;

					case 3:
						if (cardDraw == 1)
						{
							printf("The card drawn is: Ace of Diamonds\n\n");
						}
						else if (cardDraw == 11)
						{
							printf("The card drawn is: Jack of Diamonds\n\n");
						}
						else if (cardDraw == 12)
						{
							printf("The card drawn is: Queen of Diamonds\n\n");
						}
						else if (cardDraw == 13)
						{
							printf("The card drawn is: King of Diamonds\n\n");
						}
						else
						{
							printf("The card drawn is: %d of Diamonds\n\n", cardDraw);
						}
						break;

					case 4:
						if (cardDraw == 1)
						{
							printf("The card drawn is: Ace of Hearts\n\n");
						}
						else if (cardDraw == 11)
						{
							printf("The card drawn is: Jack of Hearts\n\n");
						}
						else if (cardDraw == 12)
						{
							printf("The card drawn is: Queen of Hearts\n\n");
						}
						else if (cardDraw == 13)
						{
							printf("The card drawn is: King of Hearts\n\n");
						}
						else
						{
							printf("The card drawn is: %d of Hearts\n\n", cardDraw);
						}
						break;

					}
				}


				//check to see if user guess correctly, incorrently, or to validate a choice not given
				if (cardChoice == cardDraw && suitChoice == suitDraw)
				{
					printf("Correct Guess!\n\n");
					winsCard = winsCard + 1;
					winStreakCard = winStreakCard + 1;
				}
				else if ((cardChoice < 1 || cardChoice > 13) || (suitChoice < 1 || suitChoice > 4))
				{
					printf("Pick a valid choice!\n\n");
				}
				else
				{
					//if incorrect, reset winstreak, add a loss, and ask if they want to play again
					winStreakCard = 0;
					lossCard = lossCard + 1;
					printf("You lost!\n");
					while (validOption == 0)
					{
						printf("Play again? (y/n)\n");
						scanf(" %c", &again);
						again = tolower(again);
						if (again == 'n')
						{
							endGame = 1;
							validOption = 1;
						}
						else if (again == 'y')
						{
							validOption = 1;
						}
						else
						{
							printf("Please enter a valid option\n\n");
						}
					}
				}
			} while (endGame == 0);

			//sets the highest winstreak
			if (topWinStreakCard < winStreakCard)
			{
				topWinStreakCard = winStreakCard;
			}
			break;

		case 4:

			//This does all the calculations for outputs
			winsTotal = winsCoin + winsDice + winsCard;
			lossTotal = lossCoin + lossDice + lossCard;
			gamesTotal = (float)winsTotal + lossTotal;
			gamesCoin = (float)winsCoin + lossCoin;
			gamesDice = (float)winsDice + lossDice;
			gamesCard = (float)winsCard + lossCard;
			winrateTotal = (float)(winsTotal / gamesTotal) * 100;
			winrateCoin = (float)(winsCoin / gamesCoin) * 100;
			winrateDice = (float)(winsDice / gamesDice) * 100;
			winrateCard = (float)(winsCard / gamesCard) * 100;

			//menu for scores
			printf("SCORES\n\n");

			printf("---------------\n\n");

			printf("Overall\n\n");

			printf("Total Wins: %d\n", winsTotal);
			printf("Total Losses: %d\n", lossTotal);
			printf("Overall Winrate: %.2f\n\n", winrateTotal);

			printf("---------------\n\n");

			printf("Coin Flip\n\n");

			printf("Highest Winstreak: %d\n\n", topWinStreakCoin);
			printf("Total Wins: %d\n", winsCoin);
			printf("Total Losses: %d\n", lossCoin);
			printf("Winrate: %.2f\n\n", winrateCoin);

			printf("---------------\n\n");

			printf("Dice Roll\n\n");

			printf("Highest Winstreak: %d\n\n", topWinStreakDice);
			printf("Total Wins: %d\n", winsDice);
			printf("Total Losses: %d\n", lossDice);
			printf("Winrate: %.2f\n\n", winrateDice);

			printf("---------------\n\n");

			printf("Card Draw\n\n");

			printf("Highest Winstreak: %d\n\n", topWinStreakCard);
			printf("Total Wins: %d\n", winsCard);
			printf("Total Losses: %d\n", lossCard);
			printf("Winrate: %.2f\n\n", winrateCard);
			
			break;

		case 5:

			//Exits program
			printf("Thank you for playing our game!");
			play = 0;
			break;

		default:
			//valid check
			printf("Please select a valid option\n\n");
			break;
		}
	}
}
