Документация: https://docs.onerpa.ru/mcp-servery-1c/servery/graph-metadata-search

Для запуска:

1) Отредактируйте .env файл и настройте ОБЯЗАТЕЛЬНЫЕ параметры:
   - LICENSE_KEY    — лицензионный ключ (уже заполнен)
   - METADATA_HOST_PATH — путь к вашему отчету по метаданным (например: E:/OneAPAReport)
   - OPENAI_API_KEY — ключ API (OpenAI, OpenRouter, или любой совместимый)
   - OPENAI_API_BASE — URL API (если используете не OpenAI, например http://127.0.0.1:1234/v1)

2) Выберите вариант Docker-образа в .env (параметр IMAGE_TAG):
   - latest — полный образ с поддержкой локальных embeddings (~2.5 ГБ)
   - light  — лёгкий образ, embeddings только через API (~500 МБ)
   - arm64  — для Apple Silicon / AWS Graviton / Raspberry Pi

   По умолчанию используется latest. Для смены:
   IMAGE_TAG=light

3) Выполните команду:
   docker-compose up -d

ВАЖНО: Индексация может занять значительное время. Данные Neo4j сохраняются
в Docker volume автоматически.

На Linux и в Windows 11 если видеокарта Nvidia можно добавить параметр
--gpus all
Есть вероятность что контейнер начнёт использовать видеокарту.
