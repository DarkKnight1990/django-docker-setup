FROM python:3.9.3-alpine

ENV PYTHONUNBUFFERED=1
ENV PYTHONDONTWRITEBYTECODE=1

RUN apk update && apk add \
    postgresql-dev \
    gcc \
    python3-dev \
    musl-dev

WORKDIR /usr/src/app

# install dependencies
RUN pip install --upgrade pip
COPY ./requirements.txt /usr/src/app/requirements.txt
RUN pip install -r /usr/src/app/requirements.txt

# copy project
COPY . /usr/src/app

# create the app user
RUN adduser -D djangouser
# change to the app user
USER djangouser

# run entrypoint.sh
ENTRYPOINT ["/usr/src/app/entrypoint.sh"]
