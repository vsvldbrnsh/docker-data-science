#1 скачиваем докер локально
docker pull jupyter/datascience-notebook:latest

#2 запускаем докер на порт 8888
sudo docker run -p 8888:8888 jupyter/datascience-notebook

#3 зайти в контейнер через command line --> sudo docker exec -it <container_id> bash
sudo docker exec -it bf5ac6046d44 bash

#4 поместить файл в контейнер --> docker cp foo.txt container_id:/foo.txt
sudo docker cp ~/Downloads/titanic.csv bf5ac6046d44:home/jovyan/work/titanic.csv

#5 подключаем к контейнеру папку на локале
sudo docker run -v /home/vsvld/Projects/dockers/ds:/home/jovyan/work/ -p 8888:8888 jupyter/datascience-notebook

#6 запускаем контейнер + монтируем volume + запускаемся через Dockerfile
docker build -t my_notebook .
# после -p 8888:8888 необходимо указать container_id который выведет на печать после docker build
sudo docker run -v /home/vsvld/Projects/dockers/ds:/home/jovyan/work/ -p 8888:8888 my_notebook

#7 запускаем с помощью docker-compose
sudo docker-compose up --build