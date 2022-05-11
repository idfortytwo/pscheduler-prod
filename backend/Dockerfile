FROM python:3.9-alpine

COPY ./sources/ /app
WORKDIR /app

RUN pip install -r requirements.txt

WORKDIR pscheduler
CMD python main.py
