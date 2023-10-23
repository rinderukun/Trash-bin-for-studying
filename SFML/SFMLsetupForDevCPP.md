# Использование SFML и Dev-C++ 5.11
SFML обеспечивает простой интерфейс для различных компонентов вашего ПК, упрощая разработку игр и мультимедийных приложений. Он состоит из пяти модулей: системного, оконного, графического, аудио и сетевого.
## Загрузка SFML
Для начала нужно загрузить zip файл с библиотекой sfml отсюда: [Официальный сайт версии 2.4.0](https://www.sfml-dev.org/download/sfml/2.4.0/)
Загружаем **GCC 4.9.2 TDM (SJLJ) - 64-bit**
Потому что в Dev-C++ у нас тоже в компиляторе написано **TDM-GCC 4.9.2 64-bit Release**
Распаковываем zip-архив в удобном для нас месте.
Мой пример:

```
C:\Users\user\Documents\Chip8test\sfmltest\SFML-2.4.0
```

## Настройка проекта и подключение SFML
Теперь создаем новый проект/открываем проект и заходим в его настройки **Проектр -> Параметры проекта**.
В открывшемся окне, заходим в **Параметры**. В **Linker** прописываем:

```
-lsfml-audio
-lsfml-graphics
-lsfml-window
-lsfml-system
```

Переходим во вкладку **Файлы/каталоги** и в вкладке **Библиотек** прописываем путь до папки из библиотеки SFML.
Мой пример:
```
C:\Users\user\Documents\Chip8test\sfmltest\SFML-2.4.0\lib
```
И не забываем нажать кнопку **Добавить**.
Здесь же в **Файлы/каталоги** переходим во вкладку **Файлы включения**.
По аналогии с библиотеками, добавляем:
```
C:\Users\user\Documents\Chip8test\sfmltest\SFML-2.4.0\include
```
Подтверждаем и сохраняем изменения в настройках проекта.

Теперь мы сами должны перейти в директорию SFML библиотеки в папку **bin**
```
C:\Users\user\Documents\Chip8test\sfmltest\SFML-2.4.0\bin
```
И из нее скориповать все файлы в **корневую папку проекта**.
Файлы:
```
openal32.dll
sfml-audio-2.dll
sfml-audio-d-2.dll
sfml-graphics-2.dll
sfml-graphics-d-2.dll
sfml-network-2.dll
sfml-network-d-2.dll
sfml-system-2.dll
sfml-system-d-2.dll
sfml-window-2.dll
sfml-window-d-2.dll
```

Готово!

## Тестовый код

``` cpp
#include <SFML/Graphics.hpp>

int main()
{
    sf::RenderWindow window(sf::VideoMode(200, 200), "SFML works!");
    sf::CircleShape shape(100.f);
    shape.setFillColor(sf::Color::Green);

    while (window.isOpen())
    {
        sf::Event event;
        while (window.pollEvent(event))
        {
            if (event.type == sf::Event::Closed)
                window.close();
        }

        window.clear();
        window.draw(shape);
        window.display();
    }

    return 0;
}
```

SFML подключен к проекту.