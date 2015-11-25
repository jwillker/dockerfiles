FROM python:3.4
MAINTAINER John Willker <frazao.jhonn@gmail.com>

RUN apt-get update && apt-get install -y \
		gcc \
		gettext \
		mysql-client libmysqlclient-dev \
		postgresql-client libpq-dev \
		sqlite3 \
	--no-install-recommends && rm -rf /var/lib/apt/lists/*

ENV DJANGO_VERSION 1.7
ENV DEBUG=True

RUN pip install mysqlclient psycopg2
RUN pip install -r requirements.txt
