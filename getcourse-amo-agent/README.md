# 🚀 Развёртывание AI-агента GetCourse × AmoCRM

Полная инструкция для деплоя на **Vercel** (бесплатно, ~5 минут).

## Что вы получите

После развёртывания у вас будет постоянный URL (например `your-agent.vercel.app`), где живёт ваш AI-агент. API-ключ хранится **на сервере** — его никто не увидит.

---

## Шаг 1. Создайте аккаунт на Vercel

1. Откройте **vercel.com**
2. Нажмите **Sign Up**
3. Войдите через **GitHub** (если нет аккаунта GitHub — создайте на github.com)

## Шаг 2. Создайте новый ключ Anthropic

⚠️ Старый ключ (тот что вы показали в чате) надо удалить — он скомпрометирован.

1. Откройте **console.anthropic.com**
2. **API Keys** → удалите старый ключ
3. **Create Key** → скопируйте новый (начинается с `sk-ant-...`)

## Шаг 3. Загрузите проект на GitHub

**Вариант А — через сайт (проще):**

1. Зайдите на **github.com** → нажмите **+** → **New repository**
2. Имя: `getcourse-amo-agent` → нажмите **Create repository**
3. На странице репозитория нажмите **uploading an existing file**
4. Перетащите файлы из папки `getcourse-amo-agent`:
   - `index.html`
   - `vercel.json`
   - папку `api` (вместе с файлом `chat.js` внутри)
5. Внизу нажмите **Commit changes**

## Шаг 4. Деплой на Vercel

1. Зайдите на **vercel.com/new**
2. Найдите ваш репозиторий **getcourse-amo-agent** → нажмите **Import**
3. **ВАЖНО:** разверните секцию **Environment Variables** и добавьте:
   - **Name:** `ANTHROPIC_API_KEY`
   - **Value:** ваш новый ключ `sk-ant-...`
4. Нажмите **Deploy**
5. Подождите 30-60 секунд

## Шаг 5. Готово! 🎉

Vercel даст вам ссылку вида `https://getcourse-amo-agent-xxx.vercel.app` — это ваш агент.

Откройте её в любом браузере, заполните настройки, нажмите «Запустить агент» — и всё работает.

---

## Что внутри проекта

```
getcourse-amo-agent/
├── index.html        ← интерфейс агента
├── vercel.json       ← конфиг Vercel
└── api/
    └── chat.js       ← прокси для Anthropic API
```

## Если что-то не работает

- **"API key not configured"** — забыли добавить переменную `ANTHROPIC_API_KEY` в Vercel. Зайдите в Project Settings → Environment Variables → добавьте, потом Redeploy.
- **Долго грузит** — первый запрос после простоя может занять 5-10 секунд (Vercel "будит" функцию).
- **Хочу свой домен** — Vercel позволяет привязать любой домен бесплатно: Project Settings → Domains.
