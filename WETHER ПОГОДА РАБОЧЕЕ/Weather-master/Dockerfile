FROM python:3.12.4


SHELL ["/bin/bash", "-c"]

# set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONNUNBUFFERED 1

RUN pip install --uprade pip

RUN apt update && apt -qy install gcc libjpeg-dev libxslt-dev \
    libpq-dev libmariadb-dev-compat gettext cron openssh-client flake8 locales vim

RUN useradd -rms /bin/bash/ yt && chmod 777 /opt /run

WORKDIR /yt

RUN mkdir /yt/static && mkdir /yt/madia && chown -R yt:yt && chmod 755 /yt

COPY --chown=yt:yt . .

RUN pip install -r requirements.txt

USER yt

CMD ["gunicorn", "-b", "0.0.0.0:8001", "soaqaz.wsgi:application"]