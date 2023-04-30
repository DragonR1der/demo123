import pygame

pygame.init()

# Задаем размеры экрана
screen_width = 1800
screen_height = 1000
screen = pygame.display.set_mode((screen_width, screen_height))

# Задаем цвета
black = (0, 0, 0)
white = (255, 255, 255)
red = (255, 0, 0)

# Создаем переменные для хранения координат курсора мыши и радиуса волны
mouse_x = 0
mouse_y = 0
radius = 10

# Создаем переменную для хранения времени последнего появления волны
last_wave_time = 0

# Название программы
pygame.display.set_caption("Эффект Доплера")

# Основной цикл программы
while True:
    # Обрабатываем события
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            quit()
        elif event.type == pygame.MOUSEMOTION:
            # Обновляем координаты курсора мыши
            mouse_x, mouse_y = event.pos

    # Очищаем экран
    screen.fill(black)

    # Рисуем круги вокруг курсора мыши
    current_time = pygame.time.get_ticks()



    if current_time - last_wave_time > 490:

        pygame.draw.circle(screen, red, (mouse_x, mouse_y), radius, 3)
        radius = 1
        last_wave_time = current_time
    else:
        pygame.draw.circle(screen, red, (mouse_x, mouse_y), radius, 3)
        radius += 1

    # Обновляем экран
    pygame.display.update()