# ADR-0001: MVP Architecture
Date: YYYY-MM-DD


## Status
Accepted


## Context
(почему выбрали такой стек)


## Decision
(K8s + Patroni + PgBouncer + MinIO + Redis + n8n queue-mode + excel-ingest + Appsmith)


## Consequences
(плюсы/минусы; что отложено)


## References
[RCC-…]


ADR‑0001 — MVP Architecture: K8s (Docker Desktop) + Postgres(Zalando/Patroni) + PgBouncer + HAProxy + Redis + MinIO + n8n(queue‑mode) + excel‑ingest(FastAPI) + Appsmith(UI).
Маркеры: [MSC‑1..7], [RCC‑2025‑09‑18‑4/5], [RCC‑2025‑09‑16‑7].

ADR‑0002 — MinIO как файловое хранилище: схемы путей uploads/{org} / results/{org}; хранение оригиналов и производных; политика именования.
Маркеры: [MSC‑3], [RCC‑2025‑09‑16‑7].

ADR‑0003 — Подключение к PG через PgBouncer/TLS: единая точка входа, секреты от Zalando, PGSSLMODE=require.
Маркеры: [MSC‑5], [RCC‑2025‑09‑23‑2].

ADR‑0004 — n8n queue‑mode: отделение main и worker, prod/test webhooks, HITL‑петли.
Маркеры: [RCC‑2025‑09‑18‑5], [RCC‑2025‑09‑10‑13].

ADR‑0005 — Отложить GitOps/Helm/ArgoCD до пост‑MVP: минимизировать WIP.
Маркеры: [RCC‑2025‑09‑20‑21], [MSC‑6].

ADR‑0006 — ExternalName для локальных зависимостей: быстро связать кластер с локальными MinIO/Redis.
Маркеры: [MSC‑2].

ADR‑0007 — Appsmith как временный UI: заменить собственную админку на готовый UI в dev.
Маркеры: [RCC‑2025‑09‑18‑4].

ADR‑0008 — Отказ от Zapier/VoiceFlow на этапе MVP: сосредоточиться на n8n + кастомные микросервисы.
Маркеры: [RCC‑2025‑09‑20‑21], [RCC‑2025‑09‑05‑17].

ADR‑0009 — Нормализация артикулов и индекс normalized_key: brand:number как ключ кросс‑поиска.
Маркеры: [MSC‑4].

ADR‑0010 — HITL‑подход: оператор может перехватить диалог или подсказать ответ → сохраняем в kb_answers.
Маркеры: [MSC‑1], [MSC‑9].