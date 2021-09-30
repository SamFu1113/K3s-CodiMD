FROM gcc:10.2

RUN  mkdir /usr/src/hw4

COPY lab4.c /usr/src/hw4

WORKDIR /usr/src/hw4

RUN apt update

RUN apt install gcc

RUN gcc lab4.c -o lab4

CMD ["./lab4"]

