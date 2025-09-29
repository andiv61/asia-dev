# Tech Index
Последнее обновление: YYYY-MM-DD HH:MM TZ


## Инвентарь сервисов
(краткий список как в разделе Tech Index)


## Соглашения
- PG через PgBouncer/TLS …
- Webhooks n8n …


## Долги/ToDo
- …

Короткая техническая шпаргалка «для ИИ» с маркерами на историю. Держим кратко, без воды.

Инвентарь сервисов

K8s (Docker Desktop): ingress‑nginx, cert‑manager (self‑signed). [RCC-2025-09-11-10]

Postgres: Zalando Operator → Patroni/Spilo‑14 (pods: patroni1, patroni2), PgBouncer (asia-pg-pooler), HAProxy. Порты: 5432/5433; HAProxy 5000/7000. [MSC-5]

Redis: ExternalName redis-dev → host.docker.internal. [MSC-2]

MinIO: ExternalName minio-dev → host.docker.internal (9000). [MSC-2], [RCC-2025-09-15-8]

n8n: queue‑mode (main, worker, Redis), ingress n8n.dev.asia.local; webhooks активируются. [RCC-2025-09-18-5]

Appsmith: контейнер appsmith/appsmith-ce:release, порт 8080:80, APPSMITH_ALLOWED_HOSTS включает host.docker.internal, n8n.dev.asia.local. [RCC-2025-09-18-4]

excel‑ingest: деплой в asia-dev, образ временный (busybox→FastAPI), подключение к PG через PgBouncer/TLS; MinIO схемы uploads/{org_id}/…, results/{org_id}/…. [MSC-3], [MSC-7]

Ключевые соглашения

Секреты PG: брать из n8n-user.asia-pg.credentials.postgresql.acid.zalan.do (пример получения пароля через kubectl ... jsonpath). [RCC-2025-09-05-16]

Webhook n8n: prod‑URL требует активный workflow; 404 = не активирован. [RCC-2025-09-18-5]

PowerShell curl: использовать curl.exe или Invoke-WebRequest. [RCC-2025-09-22-1]

Долги

GHCR CI/CD для excel‑ingest (build/push), Helm/values, probes. [MSC-7]

ADR оформить (см. список ниже). [все]

Persist volumes для n8n/Appsmith. [RCC-2025-09-09-14]

Excel-ingest: env-переменные в деплое содержат расхождения (DB_NAME=app против postgres). Привели к созданию схем в разных БД. Нужно унифицировать: оставить postgres + excel_ingest schema для продакшена. [RCC-2025-09-26-3]

Добавлен source_key и индекс idx_excel_ingest_raw_ingest_source_key. [MSC-8]