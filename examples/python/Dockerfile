FROM python:3.7-slim

COPY . /app
WORKDIR /app

# pip does not like being run as root, so create a user
RUN useradd --create-home jina

USER jina

RUN pip install -r requirements.txt

# command to run on container start
CMD [ "python", "app.py" ]
