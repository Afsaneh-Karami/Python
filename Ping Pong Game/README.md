# Writing Ping Pong Game in python with turtle library:
In this code I used turtle library to creat screen, rockets, ball, and a board to show the result of play.

### introduction of Turtle library:
turtle is a Python library that enables users to create pictures and shapes by providing them with a virtual canvas. The onscreen pen that you use for drawing is called the turtle and this is what gives the library its name. In computer graphics, turtle graphics are vector graphics using a relative cursor upon a Cartesian plane. Turtle graphics is a key feature of the Logo programming language. 
The order of functions to make a ping pong game:<br /
1. asking th euser to enter the speed of ball and maximum score for winning tha game
* speed=float(input("enter the speed of Ball(between 3-10): " ))
* num=int(input("enter the Maxium score for winning:"))<br />
2. producing a green screen for playing with the size 1200X700 mm2 with the name 'pong play"
* screen=turtle.Screen()
* screen.setup(1200,700)
* screen.title("pong play")
* screen.bgcolor("green")<br />
3. producing a center line to divide the screen to two eqaul parts, each parts is for one player
* center_line=turtle.Turtle()
* center_line.penup()
* center_line.goto(0,350)
* center_line.pendown()
* center_line.goto(0,-350)
Note: penup() means no drawing when moving the turtle and pendown() means drawing when the turtle moves, and with goto(x,y) you can indicate the place of turtle <br />
4. making rackets in both side of screen
4.1 left rocket properties; the square shape in black color with the shape size(7,1) in the position (x,y)=(-500, 0)
* Racket_Left = turtle.Turtle(shape="square")
* Racket_Left.color("black")
* Racket_Left.shapesize(7, 1)
* Racket_Left.penup()
* Racket_Left.goto(-500, 0)
4.2 right rocket properties; the square shape in black color with the shape size(7,1) in the position (x,y)=(500, 0)
* Racket_Right = turtle.Turtle(shape="square")
* Racket_Right.color("black")
* Racket_Right.shapesize(7, 1)
* Racket_Right.penup()
* Racket_Right.goto(500, 0)<br />
5. making the ball in white color and diameter 20 mm and speed show its speed in two direction x and y
* Ball= turtle.Turtle(shape='circle')
* Ball.color("white")
* Ball.dx=speed
* Ball.dy=-speed
6. producing a board for score of each player with yellow color in the position (0,310), also indicating the score 0 for each player at the start of game
* Score = turtle.Turtle()
* Score.color("yellow")
* Score.penup()
* Score.goto(0, 310)
* Score.write("Player 1: 0   Player 2: 0", align="center", font=("Arial", 20 ))
* score1=0
* score2=0 <br />
7. producing a board to show the winner at the end of game in white color and position (0,150)
* winner=turtle.Turtle()
* winner.color("white")
* winner.penup()
* winner.goto(0,150)
8. define the fuction for rockets movment to up and down in order to catch the ball
8.1 Racket_Left movment to up and down by the step 40 mm
* def Racketup_L():
    y = Racket_Left.ycor()
    y = y+40
    Racket_Left.sety(y)
* def RocketDown_L():
    y=Racket_Left.ycor()
    y=y-40
    Racket_Left.sety(y)
8.2 Racket_Left movment to up and down by the step 40 mm
* def Racketup_R():
    y = Racket_Right.ycor()
    y = y+40
    Racket_Right.sety(y)
* def RocketDown_R():
    y= Racket_Right.ycor()
    y=y-40
    Racket_Right.sety(y)
9. key connection that related to the fuctions difine in step 8
* screen.listen()
* screen.onkeypress(Racketup_L,"s")
* screen.onkeypress(RocketDown_L,"d")
* screen.onkeypress(Racketup_R,"k")
* screen.onkeypress(RocketDown_R,"l")
* Ball.penup()
Note: with listen() set focus on TurtleScreen in order to collect key-events. Dummy arguments are provided in order to be able to pass listen() to the onclick method.
Note: turtle.onkeyrelease(fun, key) related a function to a key, so when you press that key related function apply.
Note:Ball.penup() use to inactive drawing of turtle ball
10. main program that control the movement of ball 
* while True:<br />

    # first part
    * in first part screen updates and start movement of ball defines.
    screen.update()<br />
    Ball.setx(Ball.xcor()+Ball.dx)<br />
    Ball.sety(Ball.ycor()+Ball.dy)<br />

    # second part
    * in second part when the score of one player reach to the num (Max score for winning) the game end and the winner is define in score board.
    if (score1==num or score2==num):<br />
        if score1==num:<br />
            winner.write("Player 1 win the game", align="center",font=("Arial", 20 ))<br />
         elif score2==num:<br />
            winner.write("Player 2 win the game", align="center", font=("Arial", 20 ))<br />
        break<br />
    
    # third part
    * in third part if the ball touch the top or down line of the screen this code comes back the ball by changing its direction (multiplying its speed in y direction by -1)
    if Ball.ycor()>335:<br />
        Ball.sety(335)<br />
        Ball.dy=Ball.dy*(-1)<br />
    if Ball.ycor()<-335:<br />
        Ball.sety(-335)<br />
        Ball.dy=Ball.dy*(-1)<br />
        
    # fourth part
    * in fourth part if ball touch left or right line of the screen, means that the rockets can not touch the ball so following steps happen:
   a- ball go back to the position (0,0)<br />
   b- the score of the player in the opposit side increase by one.<br />
   c- changing the y direction of teh ball by mutiplying its speed with -1 <br />
   d- the board of score update by new value<br /><br />
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
    # fifth part
    * In the fifth part the position of impaction of ball on the rockets surface is defined, when ball touch the face of rocket then should change its x direction to oppositr side by multiplying by -1.<br />
    if (Ball.xcor()>=475) and (Ball.xcor()<500) and (Ball.ycor()<Racket_Right.ycor()+45) and (Ball.ycor()>Racket_Right.ycor()-45):<br />
        Ball.dx=Ball.dx*(-1)<br />          
    if (Ball.xcor()<=-475) and (Ball.xcor()>-500) and (Ball.ycor()<Racket_Left.ycor()+45) and (Ball.ycor()>Racket_Left.ycor()-45):<br />
        Ball.dx=Ball.dx*-1<br />
    
   
  
