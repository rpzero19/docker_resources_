#Dockerfile, Image, Container

From python:3

ADD main.py .

RUN pip install requests beautifulsoup4

CMD [ "python", "./main.py" ]


# FROM python:3

# WORKDIR /usr/src/app

# COPY requirements.txt ./
# RUN pip install --no-cache-dir -r requirements.txt

# COPY . .

# CMD [ "python", "./main.py" ]