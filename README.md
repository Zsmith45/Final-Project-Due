# Final-Project-Due
#Zahir Smith
#4/15/22
#ROCK, PAPER, SCISSORS, SHOOT!!!







import pygame
import random
if __name__ == '__main__':

    # define a list with the name of the images
    images = ['rock.jpeg', 'paper.jpeg', 'scissors.jpeg']

    pygame.init()
    screen = pygame.display.set_mode([800, 500])

    # Get size of screen
    width = screen.get_width()
    height = screen.get_height()

     # buttons position and size
    buttonSize = [140, 40]
    buttonPos1 = [(1/2)*width-300, (3/4)*height]
    buttonPos2 = [(1/2)*width-buttonSize[0]/2, (3/4)*height]
    buttonPos3 = [(1/2)*width+150, (3/4)*height]


    # color for letters
    color_light = (0,255,255) 
    
    # color for button background
    color_dark = (0,0,125)

    # white color
    color = (255,0,0)

    # defining a font
    smallfont = pygame.font.SysFont('Calibri',35)
    
    # font for text
    text1 = smallfont.render('Rock' , True , color)
    text2 = smallfont.render('Paper' , True , color)
    text3 = smallfont.render('Scissors' , True , color)

    playerTitle = smallfont.render('Player' , True , color_dark)
    cpuTitle = smallfont.render('CPU' , True , color_dark)

    # Fill the background with white
    screen.fill((0, 255, 0))

    # start game
    running = True
    while running:
        
        # get mouse
        mouse = pygame.mouse.get_pos()
        # Check if user clicked close button
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                running = False

            # Check if user clicked mouse
            if event.type == pygame.MOUSEBUTTONDOWN:
                # user clicked "Rock" button
                if buttonPos1[0] <= mouse[0] <= buttonPos1[0]+buttonSize[0] and buttonPos1[1] <= mouse[1] <= buttonPos1[1]+buttonSize[1]:
                    # Display images
                    playerImage = pygame.image.load('rock.jpeg')
                    cpuImage = pygame.image.load(images[random.randint(0, 2)])
                    screen.blit(playerImage, (100,100))
                    screen.blit(cpuImage, (500,100))

                # user clicked Paper" button
                if buttonPos2[0] <= mouse[0] <= buttonPos2[0]+buttonSize[0] and buttonPos2[1] <= mouse[1] <= buttonPos2[1]+buttonSize[1]:
                    # Display images
                    playerImage = pygame.image.load('paper.jpeg')
                    cpuImage = pygame.image.load(images[random.randint(0, 2)])
                    screen.blit(playerImage, (100,100))
                    screen.blit(cpuImage, (500,100))

                # user clicked "Scissors" button
                if buttonPos3[0] <= mouse[0] <= buttonPos3[0]+buttonSize[0] and buttonPos3[1] <= mouse[1] <= buttonPos3[1]+buttonSize[1]:
                    # Display images
                    playerImage = pygame.image.load('scissors.jpeg')
                    cpuImage = pygame.image.load(images[random.randint(0, 2)])
                    screen.blit(playerImage, (100,100))
                    screen.blit(cpuImage, (500,100))
        
        # If the mouse hovers the button, change background color to light
        if buttonPos1[0] <= mouse[0] <= buttonPos1[0]+buttonSize[0] and buttonPos1[1] <= mouse[1] <= buttonPos1[1]+buttonSize[1]:
            pygame.draw.rect(screen,color_light,buttonPos1+buttonSize)
        else:
            pygame.draw.rect(screen,color_dark,buttonPos1+buttonSize)

        # If the mouse hovers the button, change background color to light
        if buttonPos2[0] <= mouse[0] <= buttonPos2[0]+buttonSize[0] and buttonPos2[1] <= mouse[1] <= buttonPos2[1]+buttonSize[1]:
            pygame.draw.rect(screen,color_light,buttonPos2+buttonSize)
        else:
            pygame.draw.rect(screen,color_dark,buttonPos2+buttonSize)


        # If the mouse hovers the button, change background color to light
        if buttonPos3[0] <= mouse[0] <= buttonPos3[0]+buttonSize[0] and buttonPos3[1] <= mouse[1] <= buttonPos3[1]+buttonSize[1]:
            pygame.draw.rect(screen,color_light,buttonPos3+buttonSize)
        else:
            pygame.draw.rect(screen,color_dark,buttonPos3+buttonSize)

        # Place etxt in buttons
        screen.blit(text1 , [buttonPos1[0]+buttonSize[0]/4, buttonPos1[1]])
        screen.blit(text2 , [buttonPos2[0]+buttonSize[0]/4, buttonPos2[1]])
        screen.blit(text3 , [buttonPos3[0]+buttonSize[0]/4-20, buttonPos3[1]])

        # Add titles
        screen.blit(playerTitle, (120,50))
        screen.blit(cpuTitle, (600,50))

        # updates the frames of the game
        pygame.display.flip()
        pygame.display.update()

    pygame.quit()

