# Domínio

Tudo gira em torno de um evento com data e hodômetro.

## Veiculo

Identidade estável. Um registro. VIN, placa, ano, motor, câmbio, cor, data e km da compra.

## LeituraHodometro

Não se edita o passado. Cada leitura é um ponto: km, data, origem (`manual`, `abastecimento`, `manutencao`, `scanner`). O km atual é a maior leitura válida. Leituras menores que a anterior são rejeitadas, salvo correção explícita com motivo.

## Abastecimento

Data, km, posto, combustível (`etanol`, `gasolina`, `misto`), litros, preço por litro, total, tanque cheio (sim/não). Consumo só é calculado entre dois tanques cheios. Mistura fica de fora da conta de km/l até haver regra própria.

## PlanoManutencao

Item recorrente. Exemplos: óleo, filtro de óleo, filtro de ar, filtro de combustível, velas, fluido de freio, correia de acessórios, correia dentada, fluido de câmbio. Cada item tem intervalo em km, intervalo em meses, e o que vale primeiro. Origem: `manual`, `adesivo`, `nota`, `estimado`.

## Servico

O que foi feito. Data, km, oficina, itens, peças (marca, código, especificação), valor, foto da nota. Ao salvar, empurra o próximo vencimento do plano.

## Desgaste

Estado observado, não só troca. Pneu (mm ou foto), pastilha, disco, embreagem. Serve para não ser pego de surpresa.

## LeituraScanner

Sessão OBD. Adaptador, protocolo, km, DTCs com descrição, freeze frame, PIDs escolhidos (temperatura do líquido, rotação, carga, LTFT, voltagem). Apagar código é uma ação separada e fica registrada. Nunca apaga sem ter gravado antes.

## Documento

Tipo, validade, arquivo. CRLV, seguro, nota fiscal, laudo.

## Custo

Derivado. Não se lança custo solto se ele já nasce de abastecimento ou serviço. Relatório: R$/km de combustível, R$/km de manutenção, total desde a compra.
