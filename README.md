# 🧪 PQC Testbed (Docker)

Мини-лаборатория для тестирования постквантовой криптографии с использованием liboqs и OpenSSL внутри Docker.

## 📦 Структура

- `oqs-server`: TLS-сервер на базе Nginx + OpenSSL + liboqs.
- `oqs-client`: клиент с утилитами OpenSSL для тестирования.

## 🚀 Запуск

```bash
git clone https://github.com/youruser/pqc-testbed.git
cd pqc-testbed
docker-compose build
docker-compose up -d
