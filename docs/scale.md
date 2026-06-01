# Escala do n8n-worker

## Configuração no Coolify

Criar uma aplicação Git-based com:

```text
Repository: henrique013/coolify-n8n-worker
Branch: main
Build Pack: Docker Compose
Base Directory: /
Docker Compose Location: docker-compose.yml
```

## Variáveis obrigatórias

As variáveis reais ficam somente no Coolify:

```text
N8N_IMAGE
N8N_RUNNERS_IMAGE
GENERIC_TIMEZONE
N8N_ENCRYPTION_KEY
N8N_DATA_VOLUME
N8N_WORKER_CONCURRENCY
QUEUE_HEALTH_CHECK_ACTIVE
N8N_POSTGRES_HOST
N8N_POSTGRES_PORT
N8N_POSTGRES_DATABASE
N8N_POSTGRES_USER
N8N_POSTGRES_PASSWORD
N8N_REDIS_HOST
N8N_REDIS_PORT
N8N_REDIS_PASSWORD
N8N_REDIS_DB
N8N_RUNNERS_AUTH_TOKEN
N8N_RUNNERS_MAX_CONCURRENCY
N8N_RUNNERS_AUTO_SHUTDOWN_TIMEOUT
```

`N8N_DATA_VOLUME` deve apontar para um volume Docker externo já existente. Para workers em outra VPS, crie e configure um volume equivalente ou mova binários para storage externo suportado antes de depender de arquivos locais.

O recurso Coolify deve ficar com `Connect to Predefined Network` habilitado para alcançar Postgres e Redis externos na rede privada gerenciada pelo Coolify.

## Escala para VPS adicional

Antes de criar worker remoto:

1. Garantir rede privada/VPN entre a VPS worker e Postgres/Redis.
2. Validar acesso privado ao Postgres.
3. Validar acesso privado ao Redis.
4. Criar o recurso Git-based a partir deste repositório.
5. Configurar as mesmas variáveis críticas do ambiente atual.
6. Fazer deploy.
7. Validar worker e task runner.

Não abra Postgres ou Redis publicamente para escalar worker.
