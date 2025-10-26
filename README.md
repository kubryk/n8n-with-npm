# n8n з NPM пакетами

Цей проект надає Docker-контейнер n8n з додатковими NPM пакетами для розширених можливостей автоматизації.

### NPM пакети

- **qrcode** - генерація QR кодів
- **axios** - HTTP клієнт для API запитів

### Як почати?

#### 1. Клонування репозиторію

```bash
git clone https://github.com/kubryk/n8n-with-npm
cd n8n-with-npm
```

#### 2. Збірка Docker образу

```bash
docker-compose build
```

#### 3. Запуск контейнера

```bash
docker-compose up -d
```

#### 4. Доступ до n8n

Відкрийте браузер: `http://localhost:5678`

## 📚 Використання пакетів

### QR Code генерація

```javascript
const QRCode = require("qrcode");
const qrCodeDataURL = await QRCode.toDataURL("Hello World!");
```

### HTTP запити з Axios

```javascript
const axios = require("axios");
const response = await axios.get("https://api.example.com/data");
```

### Як додати пакети?

Щоб додати нові NPM пакети до вашого n8n контейнера:

#### 1. Відредагуйте DockerFile

```dockerfile
FROM n8nio/n8n:latest

USER root
RUN npm install -g qrcode axios [новий-пакет]
USER node
```

#### 2. Перебудуйте контейнер

```bash
# Зупиніть поточний контейнер
docker-compose down

# Перебудуйте образ з новими пакетами
docker-compose build --no-cache

# Запустіть знову
docker-compose up -d
```
