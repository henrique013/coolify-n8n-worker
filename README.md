# coolify-n8n-worker

Repositório de deploy Git-based do `n8n-worker` no Coolify.

Este recurso executa workers do n8n em queue mode com um task runner sidecar. Ele não publica domínio público.

## Responsabilidade

- Subir `n8n-worker` com `command: worker`.
- Subir `task-runner` junto do worker.
- Conectar no mesmo Postgres externo do `n8n-main`.
- Conectar no mesmo Redis dedicado do `n8n-main`.
- Servir como unidade móvel de escala para VPSs adicionais.
- Persistir `/home/node/.n8n` em bind mount informado por `N8N_DATA_SOURCE`.

## Fora do repositório

- `.env` real.
- Segredos.
- Postgres.
- Redis.
- UI/API pública do n8n.
- Domínio público.

As variáveis reais devem ser configuradas no recurso Git-based do Coolify.
O recurso deve ficar com `Connect to Predefined Network` habilitado para acessar Postgres e Redis gerenciados pelo Coolify.
