# Roteiro: preencher tkts/hr e atualizar a escala

Para rodar no Claude Code ou no app desktop do seu computador, com a extensão do Chrome e o Intercom já logado. Cole o prompt da última seção na sessão de lá.

## Planilhas
- **tkts/hr:** https://docs.google.com/spreadsheets/d/1p-Ra_SBWMIXNBFuRFPLQgIeag9nsqY8W0uXLy8UXmJE
  - Aba `# tkts/hr`: uma linha por semana (coluna B = data da segunda, coluna A = total da semana). 24 colunas por dia, de segunda a domingo, com as horas de 0 a 23. Começa na coluna C.
  - Aba `DEMANDA escala [6 às 22h]`: um bloco por dia (SEG a DOM) com as linhas `hr`, `vol`, `acum`, `escala ideal` e `escala ajustada`. As horas de 0 a 23 ficam nas colunas C a Z.
  - Aba `Processo Atualização`: o passo a passo no Intercom.
- **Escala:** https://docs.google.com/spreadsheets/d/1gBJuSX-e0w5KSTRyUjZnatQFUE14nYsRgJoUQDOrofU
  - Aba da semana (hoje: `16 a 22/11`). Cada dia tem uma linha `demanda` no topo, com as horas de 6h em diante a partir da coluna C.

## Passos
1. **Intercom:** Relatórios > Suporte Humano > Conversas. Período "Última Semana". No filtro "Detalhe", retire "Melhor Envio" e "Comunicados Telecall". Abra o relatório custom (https://app.intercom.com/a/apps/a3qubsb2/reports/custom-reports/report/3036502), na seção "Distribuição horária de novas conversas". Anote o volume por hora (0 a 23) para cada dia, de segunda a domingo.
2. **`# tkts/hr`:** a última linha preenchida é a de 09/11. A semana de 16/11 ainda não existe. Insira uma linha nova logo abaixo da última e antes do bloco "SEGUNDA-FEIRA / úl. 6 semanas / média / mediana". Copie as fórmulas e a formatação da linha anterior (coluna A, que é o total, e os demais campos). Preencha a data (16/11) e os valores por hora e por dia.
3. **Semana incompleta:** se a semana ainda não terminou, preencha só os dias fechados. Não preencha dias futuros e não estime valores.
4. **`DEMANDA escala [6 às 22h]`:** confira se as linhas `vol`, `acum`, `escala ideal` e `escala ajustada` foram recalculadas. Cada bloco já usa fórmulas, então só confirme que o intervalo pegou a linha nova e não gerou `#REF!`.
5. **Planilha de escala:** copie a linha `escala ideal` de cada dia (SEG a DOM), das colunas das horas de 6h a 22h, para a linha `demanda` do mesmo dia na aba da semana. Cole só os valores, não as fórmulas. Em qualquer dúvida de alinhamento de coluna, pare e pergunte antes de colar.

## Regras
- Não repita a parte da "escala apoio". Ela já foi feita.
- Não altere abas ocultas nem as outras semanas.
- Ao final, informe: linha criada, dias preenchidos, e o que foi copiado para a escala.

## Prompt para colar na outra sessão
"Siga o roteiro-tkts-hr-semanal.md: abra o relatório do Intercom no meu Chrome, extraia a distribuição horária de novas conversas da semana de 16/11, preencha a aba `# tkts/hr` (inserindo a linha 16/11 antes do bloco de médias), confira a aba `DEMANDA escala [6 às 22h]` e copie a `escala ideal` para a linha `demanda` da aba `16 a 22/11` da planilha de escala. Não preencha dias que ainda não fecharam."
