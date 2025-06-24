FROM python:3.11-slim

# Установка зависимостей
RUN apt update && apt install -y \
    openssh-client sshpass ansible openssh-server \
 && apt clean

# Создание рабочего каталога
WORKDIR /ansible

# Генерация SSH-ключей Ed25519 с сильным шифрованием
RUN mkdir -p /root/.ssh && \
    ssh-keygen -t ed25519 -a 100 -f /root/.ssh/id_ed25519 -N "" && \
    chmod 600 /root/.ssh/id_ed25519 && \
    chmod 644 /root/.ssh/id_ed25519.pub && \
    touch /root/.ssh/known_hosts

# Открыть доступ для ansible к этим ключам
ENV SSH_AUTH_SOCK=""

