# Arquitetura

## Fechado

API em FastAPI. Web de prototipagem em SvelteKit, na pasta `web/`. Os dois sobem na mesma VM, são processos diferentes e o mesmo repositório.

A web é onde as funcionalidades nascem: conta, cadastro, upload, FIPE, e depois o desenho 3D do carro e das peças. Não é um template HTML dentro da API. Formulario com 3D não cabe em página servida pelo FastAPI.

SvelteKit porque o Friday Night web já era Svelte. O 3D não muda o framework: é Three.js, com Threlte por cima. React teria o ecossistema 3D maior (react-three-fiber), e não compensa trocar de stack por isso.

O 3D não entra no primeiro corte. Primeiro a ficha confirma sem erro. Modelo do Polo e peça explodida vêm quando existir versão confirmada para pendurar a geometria.

## Ainda de fora

- App nativo no Pixel. Entra quando o lançamento tiver que funcionar sem sinal.
- Banco da bancada: SQLite no processo da API. Postgres só se a cópia da v1.5 pedir.
- Scanner, Bluetooth, fila.

## Restrições que continuam

- O diário de longo prazo é a exportação (JSON, CSV, fotos), não o framework.
- CPF cifrado, e não sai para API de placa.
- Versão `confirmada` só com CRLV-e e escolha da linha FIPE.
