# Writing Ping Pong Game in python with turtle library:
In this code, I used turtle library to create a screen, rockets, a ball, and a board to show the result of the play.

#Introduction of Turtle library:
Turtle is a Python library to create pictures and shapes.
<!-- The onscreen pen that you use for drawing is called the turtle, this is what gives the library its name.-->
In this library, the turtle is like a pen with attributes such as a location, an orientation, color, width, and on/off state.
The turtle moves around with commands and creates shapes.
<!--In computer graphics, turtle graphics are vector graphics using a relative cursor upon a Cartesian plane. Turtle graphics is a feature of the Logo programming language. -->
The order of functions to make a ping pong game:
<br />
1. Asking the user to enter the speed and maximum score for winning tha game.
* speed=float(input("enter the speed of Ball(between 3-10): " ))
* num=int(input("enter the Maxium score for winning:"))<br />
2. Generating a green screen for the game with the size 1200 X 700 mm2 with the name "pong play".
* screen=turtle.Screen()
* screen.setup(1200,700)
* screen.title("pong play")
* screen.bgcolor("green")<br />
3. Generating a center line to divide the screen into two equal parts for each player.
* center_line=turtle.Turtle()
* center_line.penup()
* center_line.goto(0,350)
* center_line.pendown()
* center_line.goto(0,-350)
Note: penup() means no drawing when moving the turtle and pendown() means drawing when the turtle moves, and with goto(x,y) you can indicate the cartesian place of the turtle. <br />
4. Making rackets on both sides of the screen.
4.1 Left rocket properties: the square shape in black color with the shape size(7,1) in the position (x,y)=(-500, 0)
* Racket_Left = turtle.Turtle(shape="square")
* Racket_Left.color("black")
* Racket_Left.shapesize(7, 1)
* Racket_Left.penup()
* Racket_Left.goto(-500, 0)
4.2 Right racket properties: the square shape in black color with the shape size(7,1) in the position (x,y)=(500, 0)
* Racket_Right = turtle.Turtle(shape="square")
* Racket_Right.color("black")
* Racket_Right.shapesize(7, 1)
* Racket_Right.penup()
* Racket_Right.goto(500, 0)<br />
5. Making the ball in a white color with 20 mm diameter and its speed in two directions x and y.
* Ball= turtle.Turtle(shape='circle')
* Ball.color("white")
* Ball.dx=speed
* Ball.dy=-speed
6. Producing a board for showing the score of each player with yellow color in the position (0,310), also indicating the score 0 for each player at the start of the game.
* Score = turtle.Turtle()
* Score.color("yellow")
* Score.penup()
* Score.goto(0, 310)
* Score.write("Player 1: 0   Player 2: 0", align="center", font=("Arial", 20 ))
* score1=0
* score2=0 <br />
7. Creating a board to show the winner at the end of the game in a white color and the position (0,150).
* winner=turtle.Turtle()
* winner.color("white")
* winner.penup()
* winner.goto(0,150)
8. Defining functions for the rackets' movements to up and down in order to catch the ball
8.1 Racket_Left movment to up and down by the step 40 mm
* def Racketup_L():
    y = Racket_Left.ycor()
    y = y+40
    Racket_Left.sety(y)
* def RocketDown_L():
    y=Racket_Left.ycor()
    y=y-40
    Racket_Left.sety(y)
8.2 Racket_Right movment to up and down by the step 40 mm
* def Racketup_R():
    y = Racket_Right.ycor()
    y = y+40
    Racket_Right.sety(y)
* def RacketDown_R():
    y= Racket_Right.ycor()
    y=y-40
    Racket_Right.sety(y)
9. Associating keyboard letters to the rackets' movement functions that are defined in step 8:
* screen.listen()
* screen.onkeypress(Racketup_L,"s")
* screen.onkeypress(RacketDown_L,"d")
* screen.onkeypress(Racketup_R,"k")
* screen.onkeypress(RacketDown_R,"l")
* Ball.penup()
Note: The function listen() listens to the keyboard-events. Dummy arguments are provided in order to be able to pass listen() to the onclick method.
Note: turtle.onkeyrelease(fun, key) connects a function to a key, so we presse the associated key, then the function is applied.
Note: Ball.penup() is used to deactivate the drawing of a turtle ball.
10. The main program that controls the movement of the ball:
* while True:<br />

    # First part
    * In the first part, the screen is updated and the starting position and movement of the ball are defined.
    screen.update()<br />
    Ball.setx(Ball.xcor()+Ball.dx)<br />
    Ball.sety(Ball.ycor()+Ball.dy)<br />

    # Second part
    * In the second part, when the score of one player reaches the num (Max score for winning), the game ends and the winner is announced on the scoring board.
    if (score1==num or score2==num):<br />
        if score1==num:<br />
            winner.write("Player 1 win the game", align="center",font=("Arial", 20 ))<br />
         elif score2==num:<br />
            winner.write("Player 2 win the game", align="center", font=("Arial", 20 ))<br />
        break<br />
    
    # Third part
    * In the third part when the ball touches the top or down line of the screen,  the ball comes back to the screen by changing its direction (multiplying its speed in the y-direction by -1)
    if Ball.ycor()>335:<br />
        Ball.sety(335)<br />
        Ball.dy=Ball.dy*(-1)<br />
    if Ball.ycor()<-335:<br />
        Ball.sety(-335)<br />
        Ball.dy=Ball.dy*(-1)<br />
        
    # Fourth part
    * In the fourth part, when the ball touches the left or right line of the screen, this means that the player missed the ball and the racket did not touch the ball so the following steps happen:
   a- Ball goes back to the position (0,0)<br />
   b- The score of the player on the opposit side increases by one.<br />
   c- Changing the y-direction of the ball by multiplying its speed with -1 <br />
   d- The scoring board is updated by the new value.<br /><br />
    if Ball.xcor()>600:<br />
        Ball.home()<br />
        score1=score1+1<br />
        Ball.dy=Ball.dy*(-1)<br />
        Score.clear()<br />
        Score.write("Player 1: {}   Player 2: {}".format(score1,score2), align="center", font=("Arial", 20 ))<br />
    if Ball.xcor()<-600:<br />
        Ball.home()<br />
        score2=score2+1<br />
        Ball.dy=Ball.dy*(-1)<br />
        Score.clear()<br />
        Score.write("Player 1: {}   Player 2: {}".format(score1,score2), align="center", font=("Arial", 20 ))<br />
    # Fifth part
    * In the fifth part, when the ball hits the surface of the racket, then the ball's direction changes, where its x-direction becomes the opposite side by multiplying by -1.<br />
    if (Ball.xcor()>=475) and (Ball.xcor()<500) and (Ball.ycor()<Racket_Right.ycor()+45) and (Ball.ycor()>Racket_Right.ycor()-45):<br />
        Ball.dx=Ball.dx*(-1)<br />          
    if (Ball.xcor()<=-475) and (Ball.xcor()>-500) and (Ball.ycor()<Racket_Left.ycor()+45) and (Ball.ycor()>Racket_Left.ycor()-45):<br />
        Ball.dx=Ball.dx*-1<br />
    
   
  
