FROM python:3.9-alpine

COPY ./backend/sources/requirements.txt requirements.txt
RUN pip install -r requirements.txt

COPY ./backend/sources/ /app
WORKDIR /app/pscheduler
CMD python main.py
