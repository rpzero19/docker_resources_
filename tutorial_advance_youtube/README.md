## Tutorial to use Docker advance from youtuber: Python Engineer

REF: https://www.youtube.com/watch?v=bi0cKgmRuiA

Using FASTAPI.

Tu run we can use 
uvicorn main:app --reload

Or another way, by importing uvicorn lib, 

And test it on localport.

If everything working, then pip freeze > requirement.txt

To Dockerizing
    - Dockerfile
    - Docker-image
    - Container

# Dockerfile
    In root folder, create a file 'Dockerfile'

# create a Docker Image
    - FROM python:3.8

    - WORKDIR /fastapi-app or
        WORKDIR /usr/src/app

    - COPY requirement.txt .

    - RUN pip install -r requirement.txt or
        RUN pip install --no-cache-dir -r requirements.txt

    - COPY ./app ./app or
        COPY . .

    - CMD ["python", "./app/main.py"]

# run the container
    - docker run python-fastapi
    or
    - docker run -t -i python-fastapi(-t: Pseudo terminal, -i: interactive)
    or
    - docker run -d -p 8000:8000 python-fastapi (-d, detached mode, -p: port mapping from host port to container port)


Make sure run specify port in your app as well, in last line
    uvicorn.run(app, port=8000, host="0.0.0.0")


To view the docker, 
- docker ps(list all running container)
- docker exec -it dockerid /bin/sh

Now, you are inside your docker container structure.