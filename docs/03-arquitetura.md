# Arquitetura

## Fechado para a bancada

API em FastAPI. A web de teste não é outro app: as páginas saem do mesmo processo, com template HTML. Um deploy na VM, o navegador do Pixel abre a conta, o upload e a confirmação da FIPE.

Motivo: o corte desta fase é ler o PDF e travar a versão, não ter um frontend separado. FastAPI já é a stack dos outros backends. PDF se lê em Python. Svelte fica para se a tela crescer além do formulário.

## Ainda de fora

- App nativo no Pixel. Entra quando a ficha confirmar sem erro. Aí o lançamento offline deixa de caber numa página.
- Banco. Para a bancada, SQLite no mesmo processo chega. Postgres só se a cópia da v1.5 pedir.
- Scanner, Bluetooth, fila, segundo serviço.

## Restrições que continuam

- O diário de longo prazo é a exportação (JSON, CSV, fotos), não o framework.
- CPF cifrado, e não sai para API de placa.
- Versão `confirmada` só com CRLV-e e escolha da linha FIPE.
