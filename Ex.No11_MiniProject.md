# Ex.No: 11  Mini Project 
### DATE:25-10-2024                                                         
### REGISTER NUMBER : 212222230171
### AIM: 
To write a python program to simulate the game using pygame
### Algorithm:
Initialize Game World:Set up the game environment (background, platforms, and obstacles).
Player Input:Detect user input for movement (left, right, jump).
Gravity Simulation:Continuously apply gravity to Mario, making him fall if not on a platform.
Collision Detection:Check for collisions between Mario and platforms, walls, enemies, and items.
Platform Movement:If the game includes moving platforms, update their positions.
Enemy Behavior:Define enemy movement patterns (e.g., walking back and forth).
Item Collection:Define collectible items (coins, power-ups).
Score Management:Track the score based on items collected, enemies defeated, or other events.
Level Progression:Define the end of each level (e.g., reaching a flag or goal).
Game Over/Win:Display a game-over screen when Mario runs out of lives.

### Program:
``` python
import pygame
from classes.Dashboard import Dashboard
from classes.Level import Level
from classes.Menu import Menu
from classes.Sound import Sound
from entities.Mario import Mario


windowSize = 640, 480


def main():
    pygame.mixer.pre_init(44100, -16, 2, 4096)
    pygame.init()
    screen = pygame.display.set_mode(windowSize)
    max_frame_rate = 60
    dashboard = Dashboard("./img/font.png", 8, screen)
    sound = Sound()
    level = Level(screen, sound, dashboard)
    menu = Menu(screen, dashboard, level, sound)

    while not menu.start:
        menu.update()

    mario = Mario(0, 0, level, screen, dashboard, sound)
    clock = pygame.time.Clock()

    while not mario.restart:
        pygame.display.set_caption("Super Mario running with {:d} FPS".format(int(clock.get_fps())))
        if mario.pause:
            mario.pauseObj.update()
        else:
            level.drawLevel(mario.camera)
            dashboard.update()
            mario.update()
        pygame.display.update()
        clock.tick(max_frame_rate)
    return 'restart'


if __name__ == "__main__":
    exitmessage = 'restart'
    while exitmessage == 'restart':
        exitmessage = main()
```
### Output:
![image](https://github.com/user-attachments/assets/aa0338ea-8ea1-4970-b7ea-73ba945e3543)


### Result:
Thus the simple  game was implemented using 
