
FROM python:3.11.3-slim-buster

# set work directory
WORKDIR /usr/src/app

# set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# install dependencies
RUN pip install --upgrade pip

RUN pip install pika requests
RUN pip install werkzeug
RUN pip install ortools

#RUN git clone https://github.com/google/or-tools
#RUN apt-get install gcc -y
#RUN apt-get install build-essential -y
#RUN apt-get install make -y
#RUN cd ./or-tools
#RUN make third_party

RUN apt-get update && apt-get install -y netcat
RUN apt-get update && apt-get install -y dos2unix


COPY . /usr/src/app/
RUN chmod +x /usr/src/app/entrypoint.sh
RUN dos2unix /usr/src/app/entrypoint.sh && apt-get --purge remove -y dos2unix && rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["/usr/src/app/entrypoint.sh"] 