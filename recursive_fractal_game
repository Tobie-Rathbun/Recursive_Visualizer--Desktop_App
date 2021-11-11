#created by Tobie Rathbun

#import libraries
import pygame
import random
import screen
import itertools 

#define screen properties
width = 1920
height = 1080
fps = 60
widthVar = width
heightVar = height
midHorizon = widthVar / 2
midVertical = heightVar / 2
centerX = midHorizon
centerY = midVertical
centerXacc = 0
centerYacc = 0


#define colors
white = (255,255,255)
black = (0,0,0)
red = (255,0,0)
orange = (225,128,0)
yellow = (255,255,0)
green = (0,255,0)
blue = (0,255,255)
indigo = (0,0,255)
violet = (127,0,255)
def colSel():
	randCol = ((random.randint(0,255)),(random.randint(0,255)),(random.randint(0,255)))	
	return randCol



#define units
unit = 50
unitAcc = 0

#initialize pygame and create window
pygame.init()
pygame.mixer.init()
screen = pygame.display.set_mode((width, height))
pygame.display.set_caption("My Game")
clock = pygame.time.Clock()




def drawSquare(midUnit):
	#colorSel = random.choice(colorVar)
	nextColor = next(colorCycle)
	midUnit -= 10
	pygame.draw.circle(screen, nextColor, (centerX, centerY), midUnit)
	if midUnit > 2:
		drawSquare(midUnit)


#game loop
running = True
	#set running to false to end game
while running:
	#keep loop running at right speed
	clock.tick(fps)
	#process input
	for event in pygame.event.get():
		#check for closing window
		if event.type == pygame.QUIT:
			running = False
		pressed = pygame.key.get_pressed()
		if pressed[pygame.K_w]:
			fps += 1
		if pressed[pygame.K_s]:
			fps -= 1
		if pressed[pygame.K_a]:
			unitAcc -= 1
		if pressed[pygame.K_d]:
			unitAcc += 1
		if pressed[pygame.K_UP]:
			centerYacc -= 2
		if pressed[pygame.K_DOWN]:
			centerYacc += 2
		if pressed[pygame.K_LEFT]:
			centerXacc -= 2
		if pressed[pygame.K_RIGHT]:
			centerXacc += 2
		if pressed[pygame.K_ESCAPE]:
			running = False
		moused = pygame.mouse.get_pressed()
		mouseLoc = pygame.mouse.get_pos()
		if moused == (1,0,0):
			centerX = mouseLoc[0]
			centerY = mouseLoc[1]
		if moused == (0,1,0):	
			centerXacc += 100
			centerYacc += 100
		if moused == (0,0,1):
			centerXacc = 0
			centerYacc = 0
		
		if event.type == pygame.MOUSEWHEEL:
			if event.y == -1:
				centerXacc = centerXacc/2
				centerYacc = centerYacc/2
			if event.y == 1:
				centerXacc = centerXacc*2
				centerYacc = centerYacc*2
	#update
	unit += unitAcc
	if unit < 30 or unit > 300:
		unitAcc = -unitAcc
	centerY += centerYacc
	centerX += centerXacc
	if centerX > width * .90 or centerX < width * .10:
		centerXacc = -centerXacc
	if centerY > height * .90 or centerY < height * .10:
		centerYacc = -centerYacc
	#colorSel = random.choice(colorVar)
	#color cycles
	col1 = colSel()
	col2 = colSel()
	col3 = colSel()
	col4 = colSel()
	colorVar = [black, col1, white, col2, black, col3, white, col4]
	colorCycle = itertools.cycle(colorVar)
	#drawing
	screen.fill(black)
	drawSquare(unit)
	#after drawing, flips the display
	pygame.display.flip()


pygame.quit()
