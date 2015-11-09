#include <iostream>
#include <iomanip>
#include <cstdlib>
#include <ctime>
#include <cmath>
#include <string>

using namespace std;

string userName();
void menu(); //this calls the menu of the game.
char userMovement(); //this function will ask the user for their desired move.
void takeDrink (int& eggnog, int& thirsty);
void fullSpeed (int& advancement, int& miles, int& thirsty, int& tiredness, int& elvesAdvance, int& elvesMiles); //this function will let the user move at full speed.
void modSpeed (int& advancement, int& miles, int& thirsty, int& tiredness, int& elvesAdvance, int& elvesMiles);
void rest(int& tiredness, int& elvesAdvance); //this function will allow the user to let himself and the reindeer rest.
void oasis (int& eggnog, int& thirsty, int& tiredness);
void statusCheck (int& miles, int& eggnog, int& elvesMiles);
void checkThirst (int& thirsty, bool& end);
void checkStamina(int tiredness, bool& end); //tiredness is a pass-by-value because you're not changing the tiredness level, you're just copying it in the function to check if the reindeer is tired.
void checkDistance(int advancement, int elvesMiles, bool& end); //advancement and elvesMiles are pass-by-values because you're checking the distance between the elves and reindeer; NOT, trying to change either of them.
void win(int advancement, bool& end);
void surpriseWin(bool& end);
void krampusToTheRescuePsych(bool& end);
void error(string user);

int main() 
{
    srand(time(0));
    
    char choice;
    string playerName;
    bool done = false;
    int milesTrav = 20;
    int reindeerTiredness = 0;
    int milesElvesTrav = 0;
    int eggnogInCanteen = 3;
    int thirst = 0;
    int elvesCreepingForward, advance, getTired;
    
    // Intro
    cout << "\nWelcome to..." << endl;
    cout << "                                                           \\           / " << endl;
    cout << "                                                          __\\/       \\/__" << endl;
    cout << "       ____       _           __                  __       __\\/     \\/__" << endl;
    cout << "      / __ \\___  (_)___  ____/ /__  ___  _____   / /          \\-'''-/ " << endl;
    cout << "     / /_/ / _ \\/ / __ \\/ __  / _ \\/ _ \\/ ___/  / /         (_,     ,_)  " << endl;
    cout << "    / _, _/  __/ / / / / /_/ /  __/  __/ /     /_/            |6   6| " << endl;
    cout << "   /_/ |_|\\___/_/_/ /_/\\__,_/\\___/\\___/_/     (_)             |     |     " << endl;
    cout << "                                                              |     |         " << endl;
    cout << "                                                              | \\_/ |  " << endl;
    cout << "                                                              '._|_.'      " << endl << endl;
    cout << "You have stolen a reindeer to make your way across the great North Pole." << endl;
    cout << "Santa wants his reindeer back, so now the elves are chasing you down! Survive your" << endl;
    cout << "icy trek and out run the elves." << endl;
    
    playerName = userName();
    cout << "\nOkay " << playerName << ", the following are moves you can choose. ✧٩(^ᴗ^)۶✧ \n";
    
    while (done == false)
    {
        //void menu function below:
        
        menu();
        choice = userMovement();
        switch(choice)
        {
            case 'A':
                takeDrink (eggnogInCanteen, thirst);
                break;
            case 'B':
                modSpeed (advance, milesTrav, thirst, reindeerTiredness, elvesCreepingForward, milesElvesTrav);
                break;
            case 'C':
                fullSpeed(advance, milesTrav, thirst, reindeerTiredness, elvesCreepingForward, milesElvesTrav);
                break;
            case 'D':
                rest(reindeerTiredness, milesElvesTrav);
                break;
            case 'E': 
                statusCheck (milesTrav, eggnogInCanteen, milesElvesTrav);
                break;
            case 'Q':
                done = true;
                break;
            default:
                error(playerName);
                break;
        }
        checkThirst (thirst , done);//check thirst function
        
        krampusToTheRescuePsych (done);// you autmatically lose, 1 in 200 chance
        
        checkStamina(reindeerTiredness, done);//check reindeer tiredness function
        
        checkDistance(milesTrav, milesElvesTrav, done);//if the elves have caught up, print that they caught the player and end the game.
        
                    win(milesTrav, done);//You win
        
        surpriseWin(done);
        
        oasis(eggnogInCanteen, thirst, reindeerTiredness);
    }    

    return 0;
}//END MAIN
//**************************************************************************************************************************************************

string userName()
{
    string name;
    cout << setw(40) << "\n ―――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――" << endl; 
    cout << setw(60) << "(ﾉ^ヮ^)ﾉ*:・ﾟ✧ 【Hello!】" << endl;
    cout << setw(45) << "What's your name?\n";
    cout << setw(35) << "Adventurer ";
    getline (cin, name);
    cout << setw(40) << "\n ―――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――" << endl;
    return name;
}
//**************************************************************************************************************************************************

void menu()
{
    cout << "\n\tPick and enter a letter below: \n";
    cout << "\n\t\t(A) Drink eggnog from your canteen" << endl;
    cout << "\t\t(B) Ahead moderate speed." << endl;
    cout << "\t\t(C) Hear the bells jingle, ahead full speed!" << endl;
    cout << "\t\t(D) Take a break, stop for the night." << endl;
    cout << "\t\t(E) Status check." << endl;
    cout << "\t\t(Q) Quit." << endl;
}
//**************************************************************************************************************************************************

char userMovement()
{
    char move;
    cout << "Your choice? ";
    cin >> move;
    move = toupper(move);
    while(!(move>64 && move<70 || move==81))
    {
        cout << "\n【 I'm sorry, you must pick the letter corresponding to your desired move. 】\n";
        menu();
        cout << "Your choice? ";
        cin >> move;
        move = toupper(move);
    }
    return move;
}
//**************************************************************************************************************************************************

void takeDrink (int& eggnog, int& thirsty)
{
    if(eggnog != 0)
    {
        cout << "\n ―――――――――――――――――――――――――――――――――――――――――――――――――――\n";
        cout << "\t\t  Drinking eggnogg...\n\n";
        cout << "\t\t            ) " << endl;
        cout << "\t\t       .-'(' '-. " << endl;
        cout << "\t\t     .-|`'---'`| " << endl;
        cout << "\t\t     | |       | " << endl;
        cout << "\t\t      \\|       |  " << endl;
        cout << "\t\t      `\\       /  " << endl;
        cout << "\t\t        `'---'` " << endl;
        cout << "\n ―――――――――――――――――――――――――――――――――――――――――――――――――――\n";
                    
        eggnog -= 1;
        thirsty = 0;
    }
    else
    {
        cout << "\nOops, there's no more EGGnog." << endl;
    }
}
//**************************************************************************************************************************************************

void fullSpeed (int& advancement, int& miles, int& thirsty, int& tiredness, int& elvesAdvance, int& elvesMiles)
{
    advancement = rand() % 20 + 10;
    int additionalTiredness = rand() % 3 + 1;
    miles += advancement;
    thirsty += 1;
    tiredness += additionalTiredness;
    elvesAdvance = rand() % 7 + 7;
    elvesMiles -= elvesAdvance;
    cout << "\nʚ✧⃛ɞ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ʚ✧⃛ɞ\n";
    cout << "\n\n\tε=ε=ε=ε=ε=ε=ε=ε=(⊃≧□≦)⊃ !!\n"; 
    cout << "\t\tGoing full speed...\n\n";
    cout << "\tYou have traveled " << advancement << " miles." << endl;
    cout << "\tThe elves are now " << elvesAdvance << " miles closer." << endl;
    cout << "ʚ✧⃛ɞ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ʚ✧⃛ɞ\n";
}
//**************************************************************************************************************************************************

void modSpeed (int& advancement, int& miles, int& thirsty, int& tiredness, int& elvesAdvance, int& elvesMiles)
{
    advancement = rand() % 7 + 5;
    miles += advancement;
    thirsty+= 1;
    tiredness += 1;
    elvesAdvance = rand() % 7 + 7;
    elvesMiles -= elvesAdvance;
    cout << "\nʚ☆ɞ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ʚ☆ɞ\n";
    cout << "\n\tε=ε=ε=ε=ε=┌(；　・＿・)┘｡ﾟ\n";
    cout << "\t\tGoing moderate speed..." << endl;
    cout << "\n\tYou have traveled " << advancement << " miles." << endl;
    cout << "\tThe elves are now " << elvesAdvance << " miles closer." << endl;
    cout << "\nʚ☆ɞ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ʚ☆ɞ\n";

}
//**************************************************************************************************************************************************

void rest(int& tiredness, int& elvesAdvance)
{
    tiredness = 0;
    int elvesCreepingForward = rand() % 7 + 7;
    elvesAdvance -= elvesCreepingForward;
    cout << "\n☆━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━☆\n";
    cout << "\n\t【☆sweet dream☆】(―― ω ――).zZZ\n";
    cout << "\n\t\tStopping for the night..." << endl << endl;
    cout << "\t           || " << endl;
    cout << "\t           ||                   || " << endl; //OMG, this is the cutest thing ever.
    cout << "\t        ||/||___                ||" << endl;
    cout << "\t        || /`   )____________||_/|" << endl;
    cout << "\t        ||/___ //_/_/_/_/_/_/||/ |" << endl;
    cout << "\t        ||(___)/_/_/_/_/_/_/_||  |" << endl;
    cout << "\t        ||     |_|_|_|_|_|_|_|| /|" << endl;
    cout << "\t        ||     | | | | | | | ||/||" << endl;
    cout << "\t        ||~~~~~~~~~~~~~~~~~~~||" << endl;
    cout << "\t        ||                   ||" << endl << endl;
    
    cout << "The reindeer is feeling jolly & rested with milk and cookies!" << endl;
    cout << "\t\tThe elves are now " << elvesCreepingForward << " miles closer." << endl;
    cout << "\n☆━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━☆\n";
}
//**************************************************************************************************************************************************

void statusCheck (int& miles, int& eggnog, int& elvesMiles)
{
    cout << "\n___________________________________________________________\n";
    cout << "\n༼∩ •́ ヮ •̀ ༽⊃━☆ﾟ. * ･ ｡ﾟ\n";
    cout << "\t\tChecking status... \n\n";
    cout << "\tMiles traveled: " << miles << endl;
    cout << "\tDrinks in canteen: " << eggnog<< endl; 
    cout << "\tThe elves are "<< miles - fabs(elvesMiles) << " miles behind you.";
    cout << "\n___________________________________________________________\n";
}
//**************************************************************************************************************************************************

void win(int advancement, bool& end)
{
    if (advancement > 200)
    {
        cout << "\nYou have outrun Santa's elves. You won!" << endl;
        cout << "Make the best with that reindeer, son!" << endl;
        end = true;
    }
}
//**************************************************************************************************************************************************

void surpriseWin (bool& end)
{
    int randNum = rand() % 200 + 1;
    if (randNum == 1)
    {
        cout << "You have found a wormhole and outrun Santa's elves!" << endl;
        cout << "Keep the reindeer, conquer this world!" << endl;
        end = true;
    }
}
//**************************************************************************************************************************************************

void oasis (int& eggnog, int& thirsty, int& tiredness)
{
    int num = rand() % 20 + 1;
    if (num == 1)
    {   
        eggnog = 3;
        thirsty = 0;
        tiredness = 0;
        
        cout << "\nCongratulations, you found an eggnog oasis!" << endl;
        cout << "You have refilled your canteen, quenched your thirst, and rested your reindeer." << endl;
    }
}
//**************************************************************************************************************************************************void checkThirst (int& thirsty, bool& end)
void checkThirst (int& thirsty, bool& end)
{
    if ((thirsty >= 3) && (thirsty < 5))
    {
        cout << "\nYou are thirsty! Ho,ho,ho~" << endl; //What? it's what Santa says.
    }
    if (thirsty >= 5) 
    {
        cout << "\nHo,ho,ho~ You died of thirst... " << endl;
        cout << "Merry Christmas!" << endl;
        end = true;
    }
}
//**************************************************************************************************************************************************

void checkStamina(int tiredness, bool& end)
{
    if (tiredness >= 6) //warns the user
    {
        cout << "\nYour reindeer is getting tired." << endl;
    }
    else if (tiredness >= 8 && tiredness > 6)
    {
        cout << "\nYour reindeer is dead..." << endl << endl;
        end = true;
    }
}
//**************************************************************************************************************************************************

void checkDistance(int advancement, int elvesMiles, bool& end)
{
    if ((elvesMiles < 15) && (elvesMiles > 1)) //warns the user
    {
        cout << "\nThe elves are getting close!" << endl;
    }
    if (elvesMiles > advancement)
    {
        cout << "\nTough luck, the elves have caught up and reclaimed the reindeer!" << endl;
        cout << "You are now on Santa's naughty list." << endl;
        cout << "Thank you for playing!" << endl;
        end = true;
    }
}
//**************************************************************************************************************************************************

void krampusToTheRescuePsych(bool& end)
{
    int randNum = rand() % 150 + 1;
    if (randNum == 1)
    {
        cout << endl;
        cout << "                 ┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼" << endl;
        cout << "                 ┼┼┼┼┼┼┼┼██┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼██┼┼┼┼┼┼┼┼┼" << endl;
        cout << "                 ┼┼┼┼┼┼████▄┼┼┼▄▄▄▄▄▄▄┼┼┼▄████┼┼┼┼┼┼┼" << endl;
        cout << "                 ┼┼┼┼┼┼┼┼┼▀▀█▄█████████▄█▀▀┼┼┼┼┼┼┼┼┼┼" << endl;
        cout << "                 ┼┼┼┼┼┼┼┼┼┼┼█████████████┼┼┼┼┼┼┼┼┼┼┼┼" << endl;
        cout << "                 ┼┼┼┼┼┼┼┼┼┼┼██▀▀▀███▀▀▀██┼┼┼┼┼┼┼┼┼┼┼┼" << endl;
        cout << "                 ┼┼┼┼┼┼┼┼┼┼┼██┼┼┼███┼┼┼██┼┼┼┼┼┼┼┼┼┼┼┼" << endl;
        cout << "                 ┼┼┼┼┼┼┼┼┼┼┼█████▀▄▀█████┼┼┼┼┼┼┼┼┼┼┼┼" << endl;
        cout << "                 ┼┼┼┼┼┼┼┼┼┼┼┼███████████┼┼┼┼┼┼┼┼┼┼┼┼┼" << endl;
        cout << "                 ┼┼┼┼┼┼┼┼▄▄▄██┼┼█▀█▀█┼┼██▄▄▄┼┼┼┼┼┼┼┼┼" << endl;
        cout << "                 ┼┼┼┼┼┼┼┼▀▀██┼┼┼┼┼┼┼┼┼┼┼██▀▀┼┼┼┼┼┼┼┼┼" << endl;
        cout << "                 ┼┼┼┼┼┼┼┼┼┼▀▀┼┼┼┼┼┼┼┼┼┼┼▀▀┼┼┼┼┼┼┼┼┼┼┼" << endl;
        cout << "                 ┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼┼" << endl << endl;
        cout << "Krampus has found you..." << endl;
        cout << "Krampus punishes children during the Christmas season who have misbehaved." << endl;
        cout << "He has eaten you with a strawberry milkshake and a side of curly fries, you are now dead." << endl;
        end = true;
    }
}
//**************************************************************************************************************************************************

void error(string user)
{
    cout << "\n___________________________________________________________________________________________________________________\n";
    cout << "\n\n\t\t·͙⁺˚*•̩̩͙✩•̩̩͙*˚⁺‧͙⁺˚*•̩̩͙✩•̩̩͙*˚⁺‧͙⁺˚*•̩̩͙✩•̩̩͙*˚⁺‧͙   ERROR   ·͙⁺˚*•̩̩͙✩•̩̩͙*˚⁺‧͙⁺˚*•̩̩͙✩•̩̩͙*˚⁺‧͙⁺˚*•̩̩͙✩•̩̩͙*˚⁺‧͙\n\n";
    cout << user << ", this error message either means you're doing something wrong or we just can't comprehend what you're doing.\n";
    cout << "\tAsk a friend or Google to see how this actually game works before you get back on the sleigh!\n";
    cout << "\n___________________________________________________________________________________________________________________\n";
}
//**************************************************************************************************************************************************

