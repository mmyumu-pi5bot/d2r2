FROM python:3.10.0-slim-bullseye

WORKDIR /root
RUN mkdir /root/logs

RUN pip install --upgrade "setuptools>=78.1.1" "wheel>=0.38.1"
COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .

CMD ["gunicorn", "-w", "1", "--bind", "0.0.0.0:10002", "--access-logfile", "/root/logs/access.log", "--error-logfile", "/root/logs/error.log", "--log-level", "debug", "wsgi:app"]
