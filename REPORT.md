Лабораторная работа №4

  Приложение “aafire”
  
1. Создадим директорию лабораторной и перейдем в неё
   ```
   mkdir lab4 && cd lab4
   ```

3. Создадим Dockerfile и зайдем в редактор
   ```
   touch Dockerfile && nano Dockerfile
   ```
   
5. В файле напишем следующий скрипт:
   ``` bash
    FROM ubuntu:latest
    RUN apt-get update && \
        apt-get install -y libaa-bin fortune && \
        apt-get install iputils-ping -y && \
        rm -rf /var/lib/apt/lists/*
   ```
![Снимок экрана 2024-11-24 144001](https://github.com/user-attachments/assets/a23ab924-d946-4130-893d-ddeb1ef2a2ef)
