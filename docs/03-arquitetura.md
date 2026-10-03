# Arquitetura

## Decisão proposta

App nativo no Pixel, backend separado, diário local-first.

- App: Kotlin + Jetpack Compose. É o caminho que o Pixel ainda vai abrir daqui a vários anos, sem depender de engine de terceiros.
- Banco no aparelho: Room (SQLite). Funciona sem rede. Exporta JSON e CSV.
- Backend: Python + FastAPI + Postgres. Combina com o que você já tem (`friday-night-api`, `loot-control-api`).
- Sync: o aparelho é a fonte. O servidor é cópia. Conflito simples: last-write-wins por evento, com histórico imutável de hodômetro.
- Scanner: adaptador ELM327 Bluetooth, lido pelo app. O backend não fala com o carro.
- Fotos de nota: arquivo no aparelho e cópia no storage do backend.

Monorepo:

```
app/      Android (Kotlin, Compose, Room)
api/      FastAPI
docs/     este desenho
```

## Por que não Flutter agora

Flutter seria mais rápido se o alvo fosse Android e iOS juntos. O alvo declarado é o Pixel. Compose deixa OBD, permissão de Bluetooth e arquivo local mais previsíveis. Dá para rever se surgir um segundo aparelho.

## Por que não só backend

Posto e oficina costumam ter sinal ruim. O lançamento nasce offline e sobe depois.

## Auth da v1

Uma conta. Magic link ou senha. Sem multiusuário. O carro não é compartilhado.

## Exportação

Botão obrigatório desde o primeiro mês: zip com `veiculo.json`, `eventos.json`, `abastecimentos.csv`, `servicos.csv` e as fotos. Esse zip é o diário de verdade.
