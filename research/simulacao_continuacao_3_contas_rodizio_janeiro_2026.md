# Continuação das contas aprovadas em rodízio — janeiro de 2026

Este arquivo **substitui** a simulação anterior que aplicava todas as operações às três contas simultaneamente.

## Regra corrigida

A partir da próxima operação após o encerramento da conta 6 (**06/01/2026 às 04:15:39**):

1. próxima operação fechada → Conta 1;
2. operação seguinte → Conta 2;
3. operação seguinte → Conta 5;
4. volta para a Conta 1 e repete o ciclo.

Cada operação é atribuída a somente uma conta. O risco é 0,25% e, mantendo R:R 1:2, cada ganho equivale a +0,50% e cada stop a -0,25%, com capitalização por conta.

## Resultado

| Conta | Trades | Ganhos | Stops | Saldo inicial | Saldo final | Retorno | DD máximo |
|---:|---:|---:|---:|---:|---:|---:|---:|
| 1 | 35 | 22 | 13 | US$ 3.240,00 | US$ 3.499,98 | +8,02% | 0,75% |
| 2 | 34 | 20 | 14 | US$ 3.240,00 | US$ 3.456,58 | +6,68% | 1,00% |
| 5 | 34 | 23 | 11 | US$ 3.240,00 | US$ 3.535,14 | +9,11% | 0,50% |

## Consolidado

- Operações distribuídas: **103**.
- Saldo combinado inicial: **US$ 9.720,00**.
- Saldo combinado final: **US$ 10.491,70**.
- Retorno combinado: **+7,94%**.
- Todas as três contas terminaram positivas.

Fonte: `NHS_2026_January_Trail150.htm`, XAUUSD M30, continuação após 06/01/2026 04:15:39.
