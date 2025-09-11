FROM ubuntu:latest

ENV DEBIAN_FRONTEND=noninteractive

# Update, upgrade, install Python/pip, et fix EXTERNALLY-MANAGED
RUN apt-get update && apt-get upgrade -y && \
    apt-get install -y python3 python3-pip && \
    rm -f /usr/lib/python*/EXTERNALLY-MANAGED || true

# Dépendances Python
RUN pip3 install --no-cache-dir flask flask-cors

# App
WORKDIR /app
COPY ./api.py /app/api.py

# (optionnel) documenter le port utilisé
EXPOSE 5252

CMD ["python3", "/app/api.py"]
