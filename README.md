# Painel Financeiro, Setembro 2026

Painel de leitura única do mês seguinte, gerado a partir da planilha
*ganhos e gastos mensais [@karol e @tai], 2026*, aba **Set.**

`index.html` é um arquivo autocontido: sem dependências externas, sem build.
Basta abrir no navegador. Funciona em tema claro e escuro.

## O que o painel responde

| Pergunta | Onde está |
|---|---|
| Estou gastando demais? | Bloco de veredito e "Quanto da renda já está comprometido" |
| Quanto falta ganhar só para pagar as contas? | Veredito e "Quanto você ainda precisa ganhar", nível 1 |
| O que resolve o mês? | Seção "O que fecha a conta" |
| Quanto falta buscar só para a poupança? | Seção "A poupança, isolada" |
| Estou dentro das minhas metas 50/30/20? | Seção "Contra as suas metas" |
| Quando o caixa vira no mês? | Seção "Quando o dinheiro acaba" |
| O que mudou em relação ao mês corrente? | Seção "O que mudou de agosto para setembro" |

## As duas leituras do saldo

A célula `K4:K5` da aba `Set.` calcula `entradas − poupança − contas`, ou seja,
o saldo negativo já embute a poupança planejada. O painel separa as duas
leituras, que respondem a perguntas diferentes:

- **Saldo real** = entradas − contas = **−R$ 1.105,06**, o que falta para as contas fecharem
- **Poupança descoberta** = **R$ 2.300,00**, o que falta buscar só para guardar
- **Saldo da planilha** (`K4:K5`) = **−R$ 3.405,06**, a soma dos dois

## Atualizar para outro mês

Os dados vivem em dois arrays no `<script>` do final de `index.html`: `contas` e
`poupanca`. Substitua os valores pelos da aba do mês desejado, ajuste as
constantes `ENTRADAS_TOTAL` e `CONTAS_TOTAL`, e os números citados no texto das
seções.

## Observação sobre a planilha

A célula `Q21` divide a poupança apenas pela entrada de `@takai` (célula `C9`),
resultando em 16,7%. Sobre o total de entradas, o percentual real de setembro é
15,4%. O painel usa sempre o total de entradas como base, para que essenciais,
não essenciais e poupança sejam comparáveis entre si.
