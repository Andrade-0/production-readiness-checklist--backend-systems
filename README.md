# Production Readiness Checklist — Backend Systems

---

## 1. API & Contratos

- APIs versionadas (`/v1/...`, `/v2/...`)
- Contratos bem definidos e documentados (OpenAPI / Swagger)
- Consistência de naming e padrões de resposta
- Uso correto de HTTP status codes

---

## 2. Resiliência & Comunicação

- Timeouts configurados para chamadas externas
- Retry com exponential backoff + jitter
- Circuit breaker para dependências críticas
- Fallbacks quando necessário
- Evitar chamadas síncronas desnecessárias

---

## 3. Idempotência & Segurança de Operações

- Idempotency keys em operações críticas
- Proteção contra duplicação de requests
- Validação forte de input (server-side)
- Controle de acesso (authN/authZ)

---

## 4. Observabilidade

- Logs estruturados (JSON)
  - correlationId
  - traceId
  - serviceId
- Métricas expostas (RED / USE)
- Health checks:
  - `/health/live`
  - `/health/ready`
- Tracing distribuído quando aplicável

---

## 5. Performance & Recursos

- Timeouts em DB e APIs externas
- Cache quando necessário
- Limites de CPU e memória definidos
- Evitar N+1 queries

---

## 6. Banco de Dados

- Migrações versionadas (Flyway / Liquibase)
- Sem scripts manuais em produção
- Estratégia de rollback definida
- Índices otimizados para queries críticas

---

## 7. Segurança

- Secrets nunca hardcoded
- Uso de Vault / Secrets Manager
- Comunicação segura (HTTPS/TLS)
- Validação e sanitização de inputs
- Princípio do menor privilégio

---

## 8. Deploy & Infraestrutura

- Containers não executam como root
- Configuração separada por ambiente
- Variáveis de ambiente bem definidas
- Deploy reproduzível (IaC quando possível)

---

## Nota

Este checklist é um baseline de produção. Ele não substitui revisão de arquitetura, testes ou validação de negócio.
