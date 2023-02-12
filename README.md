# The project is under development
# ChatGPT Telegram Bot: **Fast. No daily limits. Special chat modes + DALL-E**

<a href='https://t.me/maidaritsydenov'><img src="https://github.com/maidaritsydenov/telegram_bot_chatGPT/blob/main/static/avatar%20for%20gh.png" width="300" 
   height="300" alt="Пример"></a>

<p align="center">
<a href="https://t.me/ai_open_gpt_chat_bot" alt="Run Telegram Bot shield"><img src="https://img.shields.io/badge/RUN-Telegram%20Bot-blue" /></a>
</p>

We all love [chat.openai.com](https://chat.openai.com), but... It's TERRIBLY laggy, has daily limits, and is only accessible through an archaic web interface.

This repo is ChatGPT re-created with GPT-3.5 LLM as Telegram Bot. **And it works great.**

You can deploy your own bot, or use mine: [@ai_open_gpt_chat_bot](https://t.me/ai_open_gpt_chat_bot)

## Features
- Low latency replies (it usually takes about 3-5 seconds) 
- No request limits
- Code highlighting
- Special chat modes: 👩🏼‍🎓 Assistant, 👩🏼‍💻 Code Assistant, 🎬 Movie Expert. More soon
- List of allowed Telegram users
- Track $ balance spent on OpenAI API

## Bot commands
- `/retry` – Regenerate last bot answer
- `/new` – Start new dialog
- `/mode` – Select chat mode
- `/balance` – Show balance
- `/help` – Show help

## Setup на свой сервер
1. Get your [OpenAI API](https://openai.com/api/) key

2. Get your Telegram bot token from [@BotFather](https://t.me/BotFather)


3. * Репозиторий **chatgpt_telegram_bot.git >> Settings >> Secrets and variables > Actions**
* Указать следующие переменные:

**.env**
- ```TELEGRAM_TOKEN```
- ```OPENAI_API_KEY```
- ```BOT_DOMAIN```
- ```ALLOWED_TELEGRAM_USERNAMES```= []  # if empty, the bot is available to anyone
- ```NEW_DIALOG_TIMEOUT```= 600  # new dialog starts after timeout (in seconds)

**DOCKER**
- ```DOCKER_USERNAME``` - никнейм в DockerHub
- ```DOCKER_PASSWORD``` - пароль от DockerHub

**SERVER**
- ```HOST``` - публичный IPv4 сервера
- ```USER``` - никнейм пользователя
- ```SSH_KEY``` - приватный ssh ключ (cat ~/.ssh/id_rsa)
- ```PASSPHRASE``` - кодовая фраза для ssh-ключа

**DB**
- ```MONGODB_PATH```=./mongodb  # local path where to store MongoDB
- ```MONGODB_PORT```=27017  # MongoDB port

- ```MONGO_EXPRESS_PORT```=8081  # Mongo Express port
- ```MONGO_EXPRESS_USERNAME```=username  # Mongo Express username
- ```MONGO_EXPRESS_PASSWORD```=password  # Mongo Express password

**TELEGRAM**
- ```TELEGRAM_TO``` - id от телеграмм аккаунта
- ```TELEGRAM_TOKEN``` - токен бота


# Локально:
4. Запустить докер композ
```
docker compose up -d --build
```



# Деплой на сервер:
4. * Передать файлы docker-compose.yml на свой сервер
```
scp docker-compose.yml <username>@<host>:/home/<username>/docker-compose.yml
scp docker-compose.yml maidaritsydenov@51.250.7.30:/home/maidaritsydenov/docker-compose.yml
```

5. * Зайти на сервер
```
ssh username@server_address
```

6. * Обновить установленные пакеты:
```
sudo apt update
sudo apt upgrade -y
```

7. * Установить Docker и Docker-compose:
```
sudo apt install docker.io
```
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
```
sudo chmod +x /usr/local/bin/docker-compose
```

8. * Выйти из сервера
```
exit
```

9. * Запушить изменения на GitHub
```
git add .
git commit -m 'start'
git push
```

Добавить про sudo nano /etc/mongod.conf

# Каркас взят из репозитория https://github.com/karfly/chatgpt_telegram_bot. Спасибо!
