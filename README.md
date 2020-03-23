# Python
Just notes for Python, getting started and running the PizzaPi code example
  www.python.org
  
    download version 3.8.2 for windows.  
    which version for Mac?
    
    Install with all options
    
    Running
      Python - 
              Opens a command line window.
              type print("hello")  and enter.
              Not so useful, yet.
      Python Manuals - 
              Opens a library of information
              Includes tutorials.
              All very useful information!
      Python Module Docs - 
              Opens a web browser linked to an "index of modules"
              All the listed things can be added to a Python program; makes Python more powerful and easier
                  Built in modules - python code someone else already set up
                  DLL - dynamic linked libraries, not python coded but can be linked in and used
                  Lib
                  Packages                  
              Click "math" under "modules"
                  All the math functions that can be used are listed with some information on how to use.
                  py.math needs to be included in the code to allow access!
              Browse the list of modules available. Lots of power.
      Python IDLE
              This is where a Python codeded program can be set up and run.
              It starts off in "SHELL" mode.
              Click the "File" menu then choose "New File"
              A blank new file is created.
              Copy and paste the PizzaPi text into the new file then click the "Run" menu and choose "Run Module"
              
#Run Python Code at
#https://repl.it/languages/python3
#
#This program is a special Pizza Pi Day program...
#
#All the lines with # aren't hashtagged... these are remarks. The Python editor shows them in Grey.  They aren't needed to run the code.

#Python statements are all lower case! They show up in blue. IF something isn't working look for upper case or spelling mistakes.

#Some things need to be indented exactly the right amount.  Just put the cursor at the beginning of a line and tap the [shift] key once for each indent.  Python will show you lines along the indented areas so its easy to see if it's indented correctly.

#So, Python sometimes needs extra things imported. Like math functions,constants and things. The constant Pi is one of the math items needed, so we have to import math...
import math

#This next area is the calculation area of the program code. This is where the number of cups of cheese is calculated based on the pie's diameter and how thick the cheese will be.
#This first line is a def statement that defines a 'function' for calculating the amount of cheese needed in cups, using PieDiameter and CheeseThickness in inches.
def CalculateCupsOfCheeseNeeded(PieDiameter, CheeseThickness):
  #Google says the volume of a cup of stuff is 14.43 cubic inches.  That simply means the length, width and height of the volume of the stuff are all described in inches.

  #We asked the chef how many inches it is across the pizza. That's the diameter of the pizza.

  #We need the radius for the calculation Pi R Squared! The radius is, of course, the diameter divided by two.
  PieRadius = PieDiameter/2

  #The area of the top surface of the pizza is Pi times Radius times Radius;  (note - use math.pi !)
  SurfaceArea = math.pi * PieRadius * PieRadius
  #Don't forget this value is in units of inches.
 
  #The volume of cheese needed is the area of the top of the surface of the pizza times the thickness of the cheese. This is also in inches.  Eventually we want cups!
  VolumeOfCheeseInCubicInches = SurfaceArea * CheeseThickness

  #The number of cups needed is simply a conversion from cubic inches to cups (that's why the google info up there relating cubic inches and cups).

  #The conversion ratio is 14.43 cubic inches per cup...  or one cup per 14.43 cubic inches; they are equal ratios just written one way or the other:

  # 14.43 cubic inches / 1 cup
  # 1 cup / 14.43 cubic inches
 
  #Pick the one with the cubic inches value in the denominator for our calculation.  This lets cubic inches cancel out and leaves a value in cups. The code is easier to write if you cancel units yourself and just put the (1/14.43) conversion ratio in the statement.
  TheCheeseWeNeed=(1/14.43) *VolumeOfCheeseInCubicInches
  return TheCheeseWeNeed

#-----------------------------------------------------  
#Here we go...

#Introductions
print("HI...  I'm your Pizza Pie Assistant")
ChefName = input ("What's your name?  > ")
print("") 
print ("Hello, " + ChefName + ".")
print () 
print ("I'm here to help.")

#The "While" statement that controls the main loop below requires the pie diameter pie diameter to be greater than zero, so initialize the pie diameter with a value greater than zero.
PieDiameter = 1

#Below is the main "While" loop that runs if a test expression in the While statement is true.

#The test expression below is "PieDiamter > 0".

#If the test expression is true the indented statements that follow it get executed and then, after the indented statements are executed, the program loops back to the While statement. However, if the expression is not true... if it's false, the program skips the indented part and does not loop back.
while PieDiameter > 0:
  #Now let's ask the Chef how big the Pie really is.
  #Python ugliness... you need to convert the Chef's reply, which is seen as text by python, into a number. 'int' is used for integers, like 6 or 8.  But for a 12.5 inch pizza you need a floating decimal number. So we use 'float'
  ChefInput = input (ChefName + ", how many inches across is your pizza?  > ")
  #This part is hokey but I couldn't find a better way to see if the Chef entered a letter instead of a number. There's probably an easy way.  It's 3:38a.m by the way.  Still early?
  if ChefInput >="a":
    PieDiameter = -1
  else:
    PieDiameter = float(ChefInput)
  print()

  #The next statement, an If statement, also checks an expression.  If the expression is true, it executes the following indented statements. If not, the program bypasses these indented statements and goes down to the 'else' statement.
  if PieDiameter > 0: 
    #If we're here in the running code, the Chef entered a pie diameter value greater than zero. Calculate how many cups of cheese are needed.
    #Wait. We also need to know how thick the cheese will be on the pizza!
    #This program could get complicated if we also ask the Chef  how thick he wants the cheese.  Let's keep it simple and say the cheese will be a quarter inch thick.
    CheeseThickness = 0.25

    #The statement with 'CupsOfCheeseNeeded' is a function that we create separately.  It's the brain of the program, actually.

#Ok I spent a long time on this section and it annoyed me because it's not like old BASIC. Ugh. It's supposed to make the result print something like You need 1.20 cups of cheese ... blah blah instead of You need 1.204234469 cups of cheese.
#This was VERY confusing for me.  Research print format.  Ack.
    print ("You need {0:4.2f} cups of cheese to make a pizza {1:4.2f} inches across with cheese {2:4.2f} thick!".format(CalculateCupsOfCheeseNeeded(PieDiameter, CheeseThickness), PieDiameter, CheeseThickness))

#this is the printing thats simpler but it's messy.
    #print ("You need "+ str(CalculateCupsOfCheeseNeeded(PieDiameter, CheeseThickness))+ " cups of cheese to make a pizza "+ str(PieDiameter)+ " inches across with cheese "+ str(CheeseThickness)+ "inches thick!")

    print()
    
    #Because the PieDiameter was greater than zero, the program only does the indented part under the "If" statement... it skips the 'else' section and the program will loop back to the 'While' statement and ask the chef all over again... until a non positive number reply is given.
else:
    #The chef entered a pie diameter value of zero or less so it's quitting time. The program goes back to the While statement now but will bypass the indented statements because the test condition will now be false, and will exit the loop.

    print ()
    print ("See you later, ", ChefName, "!")


                  
                  
    
