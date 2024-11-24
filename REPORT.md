# Лабораторная работа №4

## Приложение “aafire”
  
1. Создадим директорию лабораторной и перейдем в неё
   ```
   mkdir lab4 && cd lab4
   ```

2. Создадим Dockerfile и зайдем в редактор
   ```
   touch Dockerfile && nano Dockerfile
   ```
   
3. В файле напишем следующий скрипт:
   ``` bash
    FROM ubuntu:latest
    RUN apt-get update && \
        apt-get install -y libaa-bin fortune && \
        apt-get install iputils-ping -y && \
        rm -rf /var/lib/apt/lists/*
   ```
    ![Снимок экрана 2024-11-24 144001](https://github.com/user-attachments/assets/a23ab924-d946-4130-893d-ddeb1ef2a2ef)

4. Сохраняем файл Ctrl+O и выходим из редактора Ctrl+X
5. В терминале в папке с этим файлом запускаем команду сборки образа с тегом "libaa-bin"
   ```
   docker build -t libaa-bin .
   ```
   ![Снимок экрана 2024-11-24 144229](https://github.com/user-attachments/assets/f01eb8c0-c11b-4d20-97dd-e828b440293e)
6. Запустим контенер и подключимся к нему с помощью команды
   ```
   docker run -it libaa-bin
   ```
8. Ведем команду aafire и запустим приложение
   
   ![Снимок экрана 2024-11-24 144433](https://github.com/user-attachments/assets/6b49a50f-c87d-477f-b72b-fe60585dc9ae)

9. Получим такой результат
   ![Снимок экрана 2024-11-24 144445](https://github.com/user-attachments/assets/72bec1eb-b760-4d29-94ae-1e20a9f23bbd)

10. Во втором окне терминала - переключимся с помощью сочетания клавиш Ctrl+Alt+F2 - выполним предыдущие команды и запустим приложение
   ```
   docker run -it libaa-bin
   aafire
   ```
11. В третьем окне терминала - переключимся с помощью сочетания клавиш Ctrl+Alt+F3 - с помощью  команды ```docker ps``` выведем запущенные контенеры
    ![Снимок экрана 2024-11-24 144533](https://github.com/user-attachments/assets/6d424582-40eb-4af0-8e51-1d4852a69eec)
12. Затем создадим сеть и подключим оба контенера к ней
    ```
    docker network create myNet
    docker network connect myNet flamboyant_gould
    docker network connect myNet silly_dijkstra
    ```
13. Выведем информацию о сети при помощи команды
    ```
    docker network inspect myNet
    ```
    ![Снимок экрана 2024-11-24 144801](https://github.com/user-attachments/assets/6be31851-6ff3-4bff-bfce-db1f83a03c86)

14. С помощью команды ```ping``` проверим наличие соединения с контенерами
    
    Первый контенер:
    
    ![Снимок экрана 2024-11-24 144833](https://github.com/user-attachments/assets/08e5044d-fd9b-4dfc-a859-bd0fba4f4eeb)
    
    Второй:

    ![Снимок экрана 2024-11-24 144901](https://github.com/user-attachments/assets/96f8d8fe-55b4-4707-bab2-9d2f0148f3db)

15. Отключим контенеры с помощью сочетания клавиш Ctrl+X, а с помощью команды ```exit``` выйдем из псевдо-режима ubuntu
16. После этого в третьем окне снова проверим соединение с контенерами
    ![Снимок экрана 2024-11-24 145225](https://github.com/user-attachments/assets/54c41c5f-ced7-41ff-b1f4-57798e06e172)

    Пакеты не пришли обратно, тк контенеры выключены
17. Чтобы очистить память после отработки контенеров, используем команду
    ```
    docker system prune
    ```
    ![Снимок экрана 2024-11-24 145535](https://github.com/user-attachments/assets/585dbd36-43e4-499c-a875-dc068ef19a12)

