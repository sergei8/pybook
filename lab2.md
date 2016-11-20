# Лабораторная работа №2. Игра "Жизнь"


```python
import pygame
from pygame.locals import *


class GameOfLife:
    def __init__(self, width = 640, height = 480, cell_size = 10):
        self.width = width
        self.height = height
        self.cell_size = cell_size

        # Устанавливаем размер окна
        self.screen_size = width, height
        # Создание нового окна
        self.screen = pygame.display.set_mode(self.screen_size)
        
        # Вычисляем количество ячеек по вертикали и горизонтали
        self.cell_width = self.width // self.cell_size
        self.cell_height = self.height // self.cell_size
   
   
   def draw_grid(self):
        # http://www.pygame.org/docs/ref/draw.html#pygame.draw.line
        for x in range(0, self.width, self.cell_size):
            pygame.draw.line(self.screen, pygame.Color('black'), 
                (x, 0), (x, self.height))
        for y in range(0, self.height, self.cell_size):
            pygame.draw.line(self.screen, pygame.Color('black'), 
                (0, y), (self.width, y))
   
   
   def run(self):
        pygame.init()
        pygame.display.set_caption('Game of Life')
        self.screen.fill(pygame.Color('white'))
        running = True
        while running:
            for event in pygame.event.get():
                if event.type == QUIT:
                    running = False
            self.draw_grid()
            pygame.display.flip()
        pygame.quit()


if __name__ == '__main__':
    game = GameOfLife(320, 240, 20)
    game.run()
```

![](life_grid.png)

Каждая клетка может находиться в двух состояниях: "*живая*" или "*мертвая*". Нам нужно создать список (матрицу) клеток размером `cell_height` $$\times$$ `cell_width`, которые в дальнейшем мы будет отображать на нашем поле, окрашивая их в зеленый и белый цвета, для "живых" и "мертвых" клеток соответственно.


```python
def cell_list(self, randomize=False):
    """
    Создание списка клеток.
    
    Клетка считается живой, если ее значение равно 1. 
    В противном случае клетка считается мертвой, то 
    есть ее значение равно 0.
    Если параметр randomize = True, то создается список, где
    каждая клетка может быть равновероятно живой или мертвой.
    """
    pass
```

Теперь нам нужно окрашивать клетки в зеленый или белый цвета в зависимости от того живая клетка или мертвая. Каждая клетка на поле представлена прямоугольником размера `cell_size` $$\times$$ `cell_size`, который можно закрасить с помощью функции `pygame.draw.rect`. Эта функция принимает следующие параметры:

* `Surface` - где нужно отрисовать прямоугольник (в нашем случае это `screen`);
* `color` - цвет, которым следует закрасить прямоугольник (`pygame.Color('white')` или `pygame.Color('green')`);
* `Rect` - координаты прямоугольника в формате `(x, y, длина стороны a, длина стороны b)`.



```python
def draw_cell_list(self, rects):
    """
    Отображение списка клеток 'rects' с закрашиванием их в 
    соответствующе цвета
    """
    pass
```
