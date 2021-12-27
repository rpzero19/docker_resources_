# Docker basics

Docker is an open platform for **developing**, **shipping**, and **running applications**. 
Docker enables you to separate your applications from your infrastructure so you can deliver software quickly.

## 3 Main Parts
-   Dockerfile
-   Dockerimage
-   Dockercontainer


### Dockerfile
    In root folder, create a file 'Dockerfile'

### create a Docker Image   

Inside the docker file, create instruction to create DockerImage

-   Basic dockerfile instruction

``` 
    From python:3

    ADD main.py .

    RUN pip install requests beautifulsoup4

    CMD [ "python", "./main.py" ] 
    
```


Advance Dockerfile instruction

```
    FROM python:3.8

    WORKDIR /fastapi-app

    COPY requirement.txt .

    RUN pip install -r requirement.txt

    COPY ./app ./app

    CMD ["python", "./app/main.py"]

```


-    FROM python:3.8(pulls the image from docker hub)

-  WORKDIR /fastapi-app or WORKDIR /usr/src/app

-    COPY requirement.txt .

-   RUN pip install -r requirement.txt or
        RUN pip install --no-cache-dir -r requirements.txt

-   COPY ./app ./app or
        COPY . .

-   CMD ["python", "./app/main.py"]

### Build the container

-   `docker build -t dockername`(-t: tags the image)
    
    Run the container

-    `docker run python-fastapi`
    or
-   `docker run -t -i python-fastapi`(-t: Pseudo terminal, -i: interactive)`
    or
-   `docker run -d -p 8000:8000 python-fastapi` (-d, detached mode, -p: port mapping from host port to container port)


Make sure run specify port in your app as well, in last line
    uvicorn.run(app, port=8000, host="0.0.0.0")


To view the docker, 
- `docker ps`(list all running container)
- `docker exec -it dockerid /bin/sh`

Now, you are inside your docker container structure.

### Docker resources for Python

1.  Folder *tutorial_youtube*
It has basic docker app.
Used code for sample from these 
[github](https://github.com/python-engineer/python-fun, ), [youtube](https://www.youtube.com/watch?v=bi0cKgmRuiA)



2.  Folder *tutorial_advance_youtube* from [youtube](https://www.youtube.com/watch?v=bi0cKgmRuiA)


## Tutorial to use Docker advance from youtuber: 
[Python Engineer](https://www.youtube.com/watch?v=bi0cKgmRuiA)


    Using FASTAPI.

    Tu run we can use 
    uvicorn main:app --reload

    Or another way, by importing uvicorn lib, 

    And test it on localport.

    If everything working, then pip freeze > requirement.txt

    Then start Dockerizing


