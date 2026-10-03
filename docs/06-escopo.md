# Escopo

Stack e hospedagem ficam para depois. Este arquivo é o contrato do que o Capô faz.

Uma pessoa, um Polo, o diário da vida dele. O critério de corte é durabilidade: se não ajuda a manter o carro ou a não perder o registro, não entra agora.

## V1 — o diário que dá para usar no dia da compra

- Ficha do carro: modelo, ano, câmbio, chassi, placa, data e km da compra, valor.
- Hodômetro: cada leitura com data. Não edita o passado. Leitura menor que a anterior é rejeitada, salvo correção com motivo.
- Abastecimento: data, km, posto, combustível (etanol, gasolina, misto), litros, preço, total, tanque cheio. Consumo só entre dois tanques cheios.
- Serviço feito: data, km, oficina, itens, peça, especificação, valor, foto da nota.
- Plano de manutenção: próximo vencimento por km e por data, o que chegar primeiro. Começa estimado e vira confirmado quando houver nota ou adesivo do cofre.
- Desgaste observado: pneu, pastilha, embreagem. Texto e foto bastam.
- Documentos: CRLV, seguro, nota da compra, com validade quando houver.
- Custo desde a compra: combustível, manutenção, total, R$/km. Calculado, não lançado à parte.
- Exportação: um zip com JSON, CSV e as fotos. Sem isso a v1 não fecha.

A v1 tem que funcionar com sinal ruim. Lançar no posto não pode depender da VM.

## V1.5 — cópia fora do celular

- Conta única.
- Cópia dos eventos e das fotos num servidor.
- O celular continua sendo a fonte. O servidor é backup e a forma de abrir o diário em outro aparelho.
- Deploy numa VM barata (Hostinger ou equivalente). Um processo, um banco, sem fila e sem Kubernetes.

## V2 — o que fica de fora até o diário estar redondo

- Scanner OBD e DTC. Entra depois, com a regra de nunca apagar código sem gravar antes.
- Lembrete push de revisão.
- Mais de um carro.
- Compartilhar o diário.
- Diagnóstico automático, marketplace, rede social, GPS contínuo.

## Fora do produto

- Escolha de linguagem.
- Escolha de nuvem além de “VM barata, um processo”.
- Arquivar os outros repositórios.
