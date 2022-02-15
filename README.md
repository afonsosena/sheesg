# sheesg
import turtle
import random
import time
import tkinter as tkinter
import os

win = turtle.Screen()
win.title("Simple Car Game")
win.setup(840,650)
win.bgpic("background-1_0.png")
win.tracer(0)
win.listen()
win.register_shape("carro7.gif")
win.register_shape("carro4.gif")
win.register_shape("1carro.gif")
win.register_shape("2carro.gif")
win.register_shape("3carro.gif")
win.register_shape("4carro.gif")
win.register_shape("5carro.gif")
win.register_shape("6carro.gif")
win.register_shape("7carro.gif")
win.register_shape("8carro.gif")
win.register_shape("9carro.gif")
win.register_shape("10carro.gif")
win.register_shape("11carro.gif")
win.register_shape("12carro.gif")
win.register_shape("13carro.gif")
win.register_shape("14carro.gif")
win.register_shape("15carro.gif")
win.register_shape("16carro.gif")
win.register_shape("17carro.gif")
win.register_shape("18carro.gif")

car = turtle.Turtle()
car.shape("carro7.gif")
car.shapesize(2,2)
car.up()
car.goto(0,-250)




carros =  ["15carro.gif", "11carro.gif", "3carro.gif", "4carro.gif", "4carro.gif", "5carro.gif"]



enemy_list = []


for i in range(8):
    enemy = turtle.Turtle()
    enemy.shape(random.choice(carros))
    enemy.up()
    enemy.speed = random.randint(2,8)
    enemy.goto(random.randint(-250, 250), 550)
    enemy_list.append(enemy)
    
        
   

def move_enemy(): 
    for i in enemy_list:
        i.goto(i.xcor(), i.ycor()-i.speed)

        if i.ycor() < -400:
            i.goto(random.randint(-250,250), 500)
            i.speed = random.randint(2,8)



def move_left():
    if car.xcor()>=-200:
        car.goto(car.xcor()-20, car.ycor())

def move_right():
    if car.xcor()<= 200:
        car.goto(car.xcor()+20, car.ycor())




win.onkey(move_left, "Left")
win.onkey(move_right, "Right")


game_over = False


while not game_over:
    time.sleep(0.0001)
    move_enemy()
    
    for i in enemy_list:
        if i.distance(car) <= 45:
            game_over = True;
            os.system('python E:\carros2\gameover.py')
            
        win.update()
