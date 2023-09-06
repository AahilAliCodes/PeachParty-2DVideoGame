﻿1. Control Flow of PlayerAvatar and BankSquare
First, a pointer to a PlayerAvatar is generated by calling a getOverlappingPlayer(Actor* a) in StudentWorld, which uses an iterator to loop through an STL vector of actors in the game and returns a pointer to a PlayerAvatar that is overlapping the Bank Square. The Actor class has a pointer to StudentWorld called getWorld. Then, if the player pointer is not nullptr, we can call the getter function of the Bank Class, getBankBalance, and use the player function setCoins to getBankBalance. The function calls playsound after.  Else if the Player has moved on the square but not landed on it, the function deducts 5 points from player and adds 5 to the bank balance using setBankBalance. Play sound. 


Known Bugs:
* getOverlapingPlayer() logic is flawed such that it returns a player pointer for each square the player is walking on yet excludes the square that the player lands on (Player is at a Waiting State). This causes all the baddies and squares to run their functionality of overlapping players when the player crosses them rather than lands on them.
* Bowser moves at the same location giving the animation that they are walking in place. He also doesn't convert any squares into DroppingSquares proving that the addDroppingSquare method does not work as intended. 
* My PlayerAvatars, Peach and Yoshi, also have a bug when they are at a turning point in the bottom left corner that causes them to turn out of bounds a few pixels above the coin square. 
* Sometimes a player does not go the direction of square points.
* Vortex doSomething not implemented ; Action Fire does not fire a vortex
* Fork function is implemented but does not work correctly; checks if there are > 2 directions and gets an action from the user but the sprite does not ever stop at at fork. 
* BankSquare doSomething does not work as intended when checking if player landed if (player != nullptr && player->getState() == PlayerAvatar::WAITING) because getOverlapingPlayer() only counts overlap for n-1 die rolls and when the player is walking. 
* Bowser and Boo will sometimes get stuck at the bottom left or top left of the grid and not move.
* Dropping square is not dropped because doing so deletes by Bowser.
* Bowser will sometimes get a BAD_ACCESS Memory Leak error if it tries to put down more than 1 dropping square. 


Overall: Code implementing the functionality for each square is present; however, since the getOverlapingPlayer() in StudentWorld is flawed, the squares are activated when a player moves on them rather than when a player lands on them. Boo and Bowser move and will interact with the player if a player moves on them or they move on the player, but the browser cannot drop a dropping square. Vortex doSomething is not implemented. 


Assumptions made:
* Bowser only changes blue coin squares to dropping squares (FAQ later clarified)
* Used Dynamic_cast when not checking for types, EX) In the std::ostringstream for the  setGameStatText(s); function I used | P2 Roll: "   << dynamic_cast<PlayerAvatar*>(yoshi)->getDieRoll() to indicate the changing values.