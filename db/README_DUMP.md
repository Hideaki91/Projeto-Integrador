# Dump e Banco de Dados

Este diretório contém artefatos para replicar estrutura do banco.

## Arquivos
- `schema.sql`: dump de estrutura (DDL) gerado a partir do `prisma/schema.prisma`.

## Gerar novamente o dump (estrutura)
```bash
npx prisma migrate diff \
  --from-empty \
  --to-schema-datamodel prisma/schema.prisma \
  --script > db/schema.sql
```

## Aplicar no banco alvo
Opção recomendada (Prisma):
```bash
npx prisma generate
npx prisma db push
```

Opção SQL (se usar cliente psql):
```bash
psql "$DATABASE_URL" -f db/schema.sql
```
