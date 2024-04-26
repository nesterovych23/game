import pygame
import sys

pygame.init()

WINDOW_WIDTH = 800
WINDOW_HEIGHT = 600
WINDOW_SIZE = (WINDOW_WIDTH, WINDOW_HEIGHT)

WHITE = (255, 255, 255)
BLACK = (0, 0, 0)

screen = pygame.display.set_mode(WINDOW_SIZE)
pygame.display.set_caption("Космічні Пригоди")

player_pos = [WINDOW_WIDTH // 2, WINDOW_HEIGHT // 2]

player_speed = 5

running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    keys = pygame.key.get_pressed()
    if keys[pygame.K_w]:
        player_pos[1] -= player_speed
    if keys[pygame.K_s]:
        player_pos[1] += player_speed
    if keys[pygame.K_a]:
        player_pos[0] -= player_speed
    if keys[pygame.K_d]:
        player_pos[0] += player_speed

    screen.fill(BLACK)
    pygame.draw.circle(screen, WHITE, player_pos, 20)
    pygame.display.flip()

    pygame.time.Clock().tick(60)

pygame.quit()
sys.exit()
