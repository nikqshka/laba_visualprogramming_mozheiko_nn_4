# Отчёт по лабораторной работе №4. n8n

**Способ установки:** Docker Desktop (образ `n8nio/n8n:latest`)

**Команда запуска:**
<img width="885" height="502" alt="image" src="https://github.com/user-attachments/assets/03c388f0-c7d2-4159-8a3f-5f64e41969ef" />


## Краткое описание выполненного

В ходе работы были собраны и задеплоены следующие workflow:

| № | Файл | Что демонстрирует |
|---|---|---|
| 2.1 | flow-01-manual-set.json | Manual Trigger → Set → Code: базовый поток |
| 2.2 | flow-02-code.json | Code node: JS-логика (let/const, if/else, for, массивы, объекты) |
| 2.3 | flow-03-if.json | IF node: ветвление по payload |
| 2.4 | flow-04-set.json | Set node: Set topic, timestamp, payload |
| 2.5 | flow-05-http.json | HTTP Request: запрос к публичному API (chucknorris.io) |
| 2.6 | flow-06-schedule.json | Schedule Trigger: запуск по расписанию |
| 3.1 | flow-09-redis.json | Redis Set/Get: создание и чтение ключа |
| 3.2 | flow-10-redis.json | Redis Delete/Get: удаление и проверка отсутствия ключа |
| Ачивка 8 | flow-12-google-webhook.json | Webhook → Google Sheets: логирование запросов в таблицу |
| Ачивка 9 | flow-11-github.json | GitHub API: безопасное чтение README.md |


## Использованные AI-промпты (ключевые примеры)

1. **Генерация кода Code node для 2.2:**
   > «Напиши код для ноды Code в n8n, который использует let/const, if/else, цикл for, массив и объект. Функция должна возвращать объект с полем payload.»

2. **Настройка IF node для 2.3:**
   > «Как в n8n настроить ноду IF, чтобы она проверяла поле payload на соответствие строке "success" и пускала по ветке true, если совпадает?»

3. **Работа с Redis (3.1):**
   > «Как в n8n настроить credentials для Redis на localhost (host.docker.internal, port 6379) и использовать ноды Redis Set и Redis Get?»

4. **Чтение файла из GitHub (Ачивка 9):**
   > «Как в n8n через ноду GitHub получить содержимое файла README.md из репозитория и декодировать его из Base64 в обычный текст с помощью ноды Code?»
   
5. **Настройка Webhook для Ачивки 8:**
   > «Как в n8n настроить ноду Webhook, чтобы она принимала GET-запрос с параметром text в URL, и как потом вытащить этот текст в следующей ноде через expression `{{ $json.query.text }}`?»

6. **Авторизация Google Sheets (Ачивка 8):**
   > «Как получить Client ID и Client Secret в Google Cloud Console для подключения Google Sheets OAuth2 API в n8n, и какой Redirect URI нужно указать?»

## Освоенные ноды

**Триггеры:**
- `Manual Trigger` — ручной запуск workflow
- `Schedule Trigger` — запуск по расписанию
- `Webhook` — прием входящих HTTP-запросов (GET/POST)

**Функциональные (Core):**
- `Set` — установка и изменение полей
- `Code` — выполнение произвольного JS-кода
- `IF` — ветвление по условиям
- `NoOp` — узел-заглушка

**Сетевые и хранилища (Network & Storage):**
- `HTTP Request` — исходящие HTTP-запросы
- `Redis` — операции Set, Get, Delete
- `GitHub` — интеграция с API (чтение файлов)
- `Google Sheets` — добавление строк в таблицу (Append Row)

## Скриншоты

### Часть 1. Установка

- <img width="1316" height="736" alt="image" src="https://github.com/user-attachments/assets/ba42cb1a-bf4b-4938-bd81-862fffe5a968" />


### 2.1. Manual → Set → Code

- <img width="804" height="487" alt="image" src="https://github.com/user-attachments/assets/acdd733c-8c0a-4dc1-a189-d971ec6a0277" />


### 2.2. Code

- <img width="1919" height="831" alt="image" src="https://github.com/user-attachments/assets/03955aad-2fdc-43e1-a29a-4ae2c7ebd6ac" />



### 2.3. IF

- <img width="1917" height="867" alt="image" src="https://github.com/user-attachments/assets/779f2975-e944-400b-9c83-1d8d12e37373" />



### 2.4. Set

-    <img width="1918" height="716" alt="image" src="https://github.com/user-attachments/assets/46aa0b9e-aa06-4591-a10b-5a7c4abce9b4" />



### 2.5. HTTP Request

- <img width="1907" height="713" alt="image" src="https://github.com/user-attachments/assets/f6c18cf4-70e4-48f2-ac46-ee3c82661512" />


### 2.6. Schedule

- <img width="1910" height="714" alt="image" src="https://github.com/user-attachments/assets/d44aec18-244d-40ae-a97b-73f0487ffb2d" />


### 3.1. Redis (Set/Get)

- <img width="1280" height="428" alt="5456340175718916436" src="https://github.com/user-attachments/assets/7f0ff832-43e0-43dd-af16-8935904a3122" />

### 3.2. Redis (Delete/Get)

- <img width="1280" height="454" alt="5456340175718916435" src="https://github.com/user-attachments/assets/a2bc8c62-3f33-4c0d-b2ed-878528f67008" />


## Выводы

В ходе выполнения лабораторной работы я освоила n8n как low-code платформу автоматизации. Разобралась с запуском приложений через Docker Desktop, настройкой переменных окружения и volumes для сохранения данных. 

Изучила базовые и продвинутые ноды, научилась передавать данные между ними, настраивать ветвление (IF) и выполнять JavaScript-код (Code). Отдельно разобралась с работой Redis через ноды n8n. 

Работа с n8n показала, как можно быстро и визуально строить сложные интеграции, не тратя время на написание бэкенда с нуля. Опыт работы с Docker и API поможет мне в дальнейшем при создании собственных автоматизаций.

моя оценка: все было круто 
