import pygame
import random

# กำหนดขนาดหน้าจอ
screen_width = 800
screen_height = 600

# เริ่ม pygame
pygame.init()

# สร้างหน้าจอ
screen = pygame.display.set_mode((screen_width, screen_height))
pygame.display.set_caption('สร้างหิน')

# กำหนดสี
WHITE = (255, 255, 255)
GREY = (169, 169, 169)

# สร้างหิน
def create_rock():
    rock_width = random.randint(50, 100)
    rock_height = random.randint(30, 80)
    x_position = random.randint(0, screen_width - rock_width)
    y_position = random.randint(0, screen_height - rock_height)
    return pygame.Rect(x_position, y_position, rock_width, rock_height)

# ฟังก์ชันหลัก
def main():
    running = True
    clock = pygame.time.Clock()
    rocks = []

    while running:
        screen.fill(WHITE)
        
        # ฟังเหตุการณ์ต่าง ๆ
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                running = False

        # สร้างหินใหม่
        if random.random() < 0.05:  # 5% ของความน่าจะเป็นที่จะสร้างหินใหม่
            rocks.append(create_rock())

        # วาดหิน
        for rock in rocks:
            pygame.draw.rect(screen, GREY, rock)

        pygame.display.flip()
        clock.tick(60)

    pygame.quit()

if __name__ == "__main__":
    main()
