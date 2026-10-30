---
name: envio-nfs
description: Envia por Slack, individualmente para cada analista de CX, o valor da NF do mês (base, bônus escala, hrs/dias extras, bônus QUALI, freela e total da NF), lendo a planilha de pagamentos. Use quando pedirem "envio NFs", "mandar valor da NF para os analistas", "enviar NFs do mês".
---

# Envio NFs

Lê a planilha de pagamentos dos analistas e manda a cada um, por DM no Slack, o valor para emissão da NF.

## Fonte

- Planilha: https://docs.google.com/spreadsheets/d/16oZtDPk1uCw00t6pzx0KDyDEWi5cb_wtwdgZgbz5-3g/edit
  (ID `16oZtDPk1uCw00t6pzx0KDyDEWi5cb_wtwdgZgbz5-3g`)
- Uma aba por mês, nomeada `<mês de referência>/<ano> (pg <mês do pagamento>)`.
  Ex.: referência outubro, pago em novembro de 2026 = `out/26 (pg nov)`.
  Liste as abas com `get_spreadsheet` (campos `sheets.properties.title`) e escolha a do mês pedido. Se o usuário não disser o mês, pergunte.
- Na aba, a segunda tabela (cabeçalho na linha com `base | bônus escala | hrs/dias extras | bônus QUALI | freela | NFs | caju | plano de saúde | total`) tem uma linha por analista. Leia `A1:K60` e use essa tabela, não a de horas semanais.
- Colunas usadas: C base, D bônus escala, E hrs/dias extras, F bônus QUALI, G freela, H NFs (valor da NF).
- Não incluir caju, plano de saúde nem total.

## Regra de sigilo (inegociável)

Os valores são sigilosos. Cada analista recebe **somente a própria mensagem**, por DM (use o `user_id` dele como `channel_id`). Nunca envie dados de um analista a outro, nem em canal, nem em mensagem agrupada. Uma mensagem por analista.

## Quem recebe

Antes de enviar, pergunte quem deve ficar de fora (o usuário normalmente exclui a si mesmo e eventualmente outras pessoas; na última vez foram Carol e Thiago). Não assuma a exclusão do mês anterior.

Se o usuário pedir uma prévia ("envie para mim"), mande as mensagens para o próprio usuário (`U026S5TFDU1`), uma por analista, antes do envio individual.

## Identificar no Slack

Use `slack_search_users` pelo primeiro nome. Confirme pelo e-mail `@flukeoperadora.com.br`. Mapeamentos já conhecidos (confira se ainda valem):

| Planilha | Slack | user_id |
|---|---|---|
| Ardson | Ardson | U05SSN24P3L |
| Suellen | Susu (suelen.rocha) | U09DP4LRD3J |
| Fran | Fran | U053D51DKLN |
| Katia | Katia Tchu | U07FJH2K7CK |
| Rachel | Rachel | U04UV4J6K9S |
| Amanda | Amanda | U0ACEA13YCR |
| Rubia | Ruby (rubia@) | U06C1J8MLDT |
| Virmaud | Virmaud | U08J6L5R1JQ |
| Vitor | Vitor (vitor.almeida@) | U032Y777M0B |
| Luiz | Luh (luiz.oliveira@) | U0A50NTMN3B |
| Simone | Simone | U0B08UH5WFR |
| Kaio | Kaio (kaio.luiz@) | U0B0QCQ6K5G |

Se um analista novo não for encontrado ou o nome for ambíguo, **não envie**: pergunte ao usuário, pois o dado é sigiloso.

## Formato da mensagem

```
oieee vindo aqui informar o valor para emissão da NF.

**NOME DO ANALISTA**
base: R$ X
bônus escala: R$ X
hrs/dias extras: R$ X
bônus QUALI: R$ X
freela: R$ X

**valor da NF: R$ X**
_caso tenha conta na fluke B2C, os 4 cupons já foram adicionados na sua conta_
```

- Nome e valor da NF em negrito; a frase dos cupons em itálico (sem asterisco na frente).
- Omita a linha de qualquer coluna (base, bônus escala, hrs/dias extras, bônus QUALI, freela) cujo valor seja zero, `R$ -` ou `-`/vazio.
- Valores no formato da planilha (`R$ 4.128,78`).
- Use o nome como está na planilha.

## Fim

Depois de enviar, informe ao usuário quem recebeu, quem ficou de fora e qualquer analista não enviado (por exemplo, não encontrado no Slack).
