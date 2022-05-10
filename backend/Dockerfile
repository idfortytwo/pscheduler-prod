FROM python:3.9-alpine

COPY . /app
WORKDIR app/backend/sources

RUN pip install -r requirements.txt

WORKDIR pscheduler
CMD python main.py
