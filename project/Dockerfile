FROM python:3.14.2-slim-bookworm

WORKDIR /usr/src/app

ENV PYTHONDONTWRITEBYCODE=1
ENV PYTHONUNBUFFERED=1

RUN apt-get update \
  && apt-get -y install netcat-traditional gcc postgresql \
  && apt-get clean

RUN pip install --upgrade pip
COPY ./requirements.txt .
RUN pip install -r requirements.txt

COPY . .

COPY ./entrypoint.sh .
RUN chmod +x /usr/src/app/entrypoint.sh

ENTRYPOINT ["/usr/src/app/entrypoint.sh"]