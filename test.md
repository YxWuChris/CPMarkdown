# Online TicTacToe
Chris Wu
### Doucmentation
This is an online Internet program that involves two users in the same tic-tac-toe game or allows a single user to play with an automated remote user. In a two-user interactive play, each user starts the game locally and operates on a local 3-by-3 tic-tac-toe through the Internet, so that the two users can view the same ongoing progress in their game. And it allow user to use "Auto play" function to play with computer. Since I used jsch in the program, so the compile cammnd code is:  `javac -cp jsch-0.1.54.jar *.java`

Here is command to start the program for players run on different servers:
for 1st player on cssmpi1h server:  `java OnlineTicTacToe cssmpi2h 12345`
for 2st player on cssmpi2h server: `java OnlineTicTacToe cssmpi1h 12345`
The code for this function is simliar to lab 2, each program read the target server address and trying to connect to other as the server or the client.  Once the connection is establish, It will decide which side is "O" and which side is "X". Both program with start counterpart thread to keep listening from each other. while it listening, the main thread will wait until the other player make his move.


here is the command to let two user play this game on one localhost:
for both players on cssmpi1h server `java OnlineTicTacToe cssmpi2h 12345`
This part of function is very simliar to the function above. But the previous code will cause a excpetion that the address already be used by the first program as the server address. So try to avoid this problem, we need set the porgam as client in the exception catch part and skip the part we used to establish connect as two server. 



here is the command to let one user play this game with computer:
for one player on cssmpi1h server `java -cp /jsch-0.1.54.jar: OnlineTicTacToe cssmpi1h 12345 auto`
it use the jsch to establish the connection with other sverver, as same as what we do in lab3. Once a connection has been established through JSCH, this real user may assume that s/he will play first with the mark “O” and the automated player will play second with the mark “X”. I set a arraylist in the server program, it store all buttons from 0-9, as soon as the play choose one, it will delete that from the arraylist and choose a random one from the list, and send the number of button to the player program.
