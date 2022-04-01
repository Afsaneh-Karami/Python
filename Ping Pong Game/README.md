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
Note: penup() means no drawing when moving the turtle, and with goto(x,y) you can indicate the place of turtle <br />
4. 
