pip install pygame
import pygame
import sys
# Initialize Pygame
pygame.init()
# Constants
WIDTH, HEIGHT = 800, 600
BALL_RADIUS = 20
BALL_COLOR = (255, 0, 0)
BACKGROUND_COLOR = (0, 0, 0)
GRAVITY = 0.5
FRICTION = 0.99
# Create the screen
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Ball Rolling Game")
# Initialize the ball
ball_x, ball_y = WIDTH // 2, HEIGHT // 2
ball_speed_x, ball_speed_y = 0, 0
# Main game loop
running = True
while running:
for event in pygame.event.get():
if event.type == pygame.QUIT:
running = False
# Handle user input
keys = pygame.key.get_pressed()
if keys[pygame.K_LEFT]:
ball_speed_x -= 2
if keys[pygame.K_RIGHT]:
ball_speed_x += 2
# Update ball position and speed
ball_speed_y += GRAVITY
ball_speed_x *= FRICTION
ball_x += ball_speed_x
ball_y += ball_speed_y
# Collision with screen boundaries
if ball_x < BALL_RADIUS:
ball_x = BALL_RADIUS
ball_speed_x = -ball_speed_x
if ball_x > WIDTH - BALL_RADIUS:
ball_x = WIDTH - BALL_RADIUS
ball_speed_x = -ball_speed_x
if ball_y < BALL_RADIUS:
ball_y = BALL_RADIUS
ball_speed_y = -ball_speed_y
if ball_y > HEIGHT - BALL_RADIUS:
ball_y = HEIGHT - BALL_RADIUS
ball_speed_y = -ball_speed_y
# Clear the screen
screen.fill(BACKGROUND_COLOR)
# Draw the ball
pygame.draw.circle(screen, BALL_COLOR, (int(ball_x), int(ball_y)), BALL_RADIUS)
# Update the display
pygame.display.flip()
# Cap the frame rate
pygame.time.delay(10)
# Quit Pygame
pygame.quit()
sys.exit()
