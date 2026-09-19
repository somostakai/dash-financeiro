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
| Quanto ainda cabe em cada teto de gasto diário? | Seção "Quanto ainda cabe em cada teto" |

## As duas leituras do saldo

A célula `K4:K5` da aba `Set.` calcula `entradas − poupança − contas`, ou seja,
o saldo negativo já embute a poupança planejada. O painel separa as duas
leituras, que respondem a perguntas diferentes:

- **Saldo real** = entradas − contas = **−R$ 2.433,52**, o que falta para as contas fecharem
- **Poupança planejada** = **R$ 3.100,00**, o que falta buscar só para guardar
- **Saldo da planilha** (`K4:K5`) = **−R$ 5.533,52**, a soma dos dois

## Atualizar para outro mês

Os dados vivem em dois arrays no `<script>` do final de `index.html`: `contas` e
`poupanca`. Substitua os valores pelos da aba do mês desejado, ajuste as
constantes `ENTRADAS_TOTAL` e `CONTAS_TOTAL`, e os números citados no texto das
seções.

## Observação sobre a planilha

A célula `Q21` divide a poupança apenas pela entrada de `@takai` (célula `C9`),
resultando em 23,6%. Sobre as entradas líquidas de repasses, o percentual real de
outubro é 21,0%. O painel usa sempre o total de entradas como base, para que essenciais,
não essenciais e poupança sejam comparáveis entre si.

Na aba `Gastos Diários`, a linha *Disponível (dia)* usa
`=(disponível - SUM(C:AF))/COUNTBLANK(C:AF)`. Isso desconta de novo o que já foi
lançado e divide por um intervalo que começa em `C` (vazia) e para em `AF`, duas
colunas antes do fim do mês. O painel refaz a conta como disponível ÷ dias que
faltam até o último dia do bloco.

## Os tetos de gasto diário

A aba **Gastos Diários** guarda seis blocos (não essenciais, essenciais,
rolezinhos, empresa, supermercado e repasses), cada um com um mês por seção e
uma coluna por dia. Abaixo dos dias vêm quatro linhas de resumo: teto da frente,
parcelas já contratadas, disponível total e disponível por dia.

O painel lê essas linhas e mostra o supermercado em detalhe (parcelas contra
lançamentos do dia a dia) e os outros quatro tetos em uma escala única, para que
quem passou do teto apareça passando dele.

## Os repasses

A partir de outubro a planilha deixa `Repasses` e `INSS Gladys` sem `Tipo`, então
o `SUMIFS` das metas não os conta. Eles somam R$ 2.087,80 e batem exatamente com
as duas entradas `@repasses`: o dinheiro entra só para sair.

O painel trata isso em dois lugares:

- **totais e veredito** ficam brutos, iguais à planilha, porque esse caixa
  precisa mesmo entrar para poder sair
- **metas 50/30/20** usam a base líquida, entradas menos repasses
  (R$ 14.727,32), que é a única forma de essenciais, não essenciais e poupança
  serem comparáveis entre si

Na barra de comprometimento e no ranking os repasses aparecem em cinza neutro,
separados das duas categorias reais.
