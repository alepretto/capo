# Cadastro da conta e do veículo

A certeza da versão não vem da placa. Vem do documento mais a confirmação do usuário.

## Conta

E-mail e CPF. O CPF é do dono do diário, não a chave do carro. Serve para conferir o proprietário do CRLV-e e, no futuro, a consulta oficial do Senatran, que pede CPF do proprietário junto com placa e RENAVAM.

O CPF não vai para API de placa. É dado de LGPD: guarda cifrado e só usa na conta.

## Três chaves, não uma

- Documento: placa, RENAVAM, chassi, string marca/modelo/versão do Detran.
- FIPE: código confirmado pelo usuário. É o que puxa preço e histórico.
- Mecânica: motor e câmbio. É o que puxa peça. A FIPE não é catálogo de peça.

Consulta por placa, como a da Zul+, devolve o palpite mais provável de uma base comercial. Quando existem duas linhas FIPE no mesmo ano, a API escolhe uma. Isso serve de sugestão. Não grava sozinho.

## O que o CRLV-e traz

O dono exporta o PDF na Carteira Digital de Trânsito, ou no gov.br, e faz upload. A Resolução 788/2020 do Contran define os campos: placa, RENAVAM, chassi, marca/modelo/versão, ano de fabricação, ano-modelo, combustível, potência/cilindrada, número do motor, cor, CPF do proprietário e QR Code gerado a partir do RENAVAM.

A conferência oficial do QR é no app Vio. O Capô guarda o arquivo e lê o texto. Não finge validar o QR.

O campo versão do documento é a string do Detran, em geral `VW/POLO TSI`, não Comfortline e não o código FIPE. Ele corta a lista. Não fecha a linha de preço.

## Dois níveis

Sem documento, o carro existe. Aceita hodômetro e abastecimento. A versão fica `nao_confirmada`. FIPE e peça não são fato.

Com o PDF, o app lê os campos, confere se o CPF do documento é o da conta e guarda o arquivo. Mostra só as linhas FIPE compatíveis com marca, ano e combustível. O usuário escolhe uma. Só então a versão vira `confirmada`.

O documento não é a porta de entrada. É a trava da versão. Nota fiscal da concessionária, se existir, entra como anexo: ela costuma ter o nome comercial.

## O que fica gravado

- Arquivo do CRLV-e.
- Placa, RENAVAM, chassi, marca/modelo/versão do documento, anos, combustível, potência/cilindrada, número do motor.
- Código FIPE, só depois da escolha.
- Motor e câmbio, confirmados na mesma tela.
- Estado: `nao_confirmada` ou `confirmada`.
