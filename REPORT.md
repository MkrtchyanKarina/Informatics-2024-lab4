Лабораторная работа №4

  Приложение “aafire”
  
1. Создадим директорию лабораторной и перейдем в неё
   ``` mkdir lab4 && cd lab4 ```

2. Создадим Dockerfile и зайдем в редактор
   ``` touch Dockerfile && nano Dockerfile ```
   
4. В файле напишем следующий скрипт:
   ```
  FROM ubuntu:latest
  RUN apt-get update && \
      apt-get install -y libaa-bin fortune && \
      apt-get install iputils-ping -y && \
      rm -rf /var/lib/apt/lists/*
   ```
