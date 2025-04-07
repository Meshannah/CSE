import pygame
import random

pygame.init()

#screen display width, height
screen = pygame.display.set_mode((800, 600))

#title and icon
pygame.display.set_caption("Space Invader")
icon = pygame.image.load('ufo.png')
pygame.display.set_icon(icon)


#player
playerImg = pygame.image.load('space-invaders.png')
playerX = 370
playerY = 480
playerX_change = 0

#enemy
enemyImg = pygame.image.load('enemy.png')
enemyX = random.randint(0, 800)
enemyY = random.randint(50, 150)
enemyX_change = 0


def player(x,y):
    screen.blit(playerImg, (x, y))

def enemy(x,y):
    screen.blit(enemyImg, (x, y))

#game loop
running = True
while running:

#RBG red blue green(color)
    screen.fill((0, 0, 0))
#movement
    # playerX -= 0.1

#happening inside game window
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

#if keystroke pressed is left or right
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_LEFT:
                playerX_change = -0.4
            if event.key == pygame.K_RIGHT:
                playerX_change = 0.4
        if event.type == pygame.KEYUP:
            if event.key == pygame.K_LEFT or event.key == pygame.K_RIGHT:
                playerX_change = 0


    playerX += playerX_change
    if playerX <= 0:
        playerX = 0
    elif playerX >= 736:
        playerX = 736


    player(playerX, playerY)
    enemy(enemyX, enemyY)
    pygame.display.update()
