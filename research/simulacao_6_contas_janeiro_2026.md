# Simulação de 6 contas — janeiro de 2026

## Regra aplicada

- Conta inicial: US$ 3.000 (referência do backtest).
- Cada operação vencedora: +4%.
- Cada stop: -2%.
- Máximo de duas operações por conta.
- Dois ganhos consecutivos: conta aprovada (+8% nominal).
- Qualquer stop: conta reprovada e rotação para a próxima conta.
- A sequência de operações é a sequência real de resultados do backtest; o resultado financeiro original da EA não foi usado para substituir o risco percentual definido nesta simulação.

## Resultado

| Conta | Operações usadas | Sequência | Resultado |
|---:|---:|:---:|:---|
| 1 | 2 | W-W | Aprovada (+8%) |
| 2 | 2 | W-W | Aprovada (+8%) |
| 3 | 1 | L | Reprovada (-2%) |
| 4 | 2 | W-L | Reprovada (+2% antes do stop, mas não aprovada) |
| 5 | 2 | W-W | Aprovada (+8%) |
| 6 | 2 | W-L | Reprovada (+2% antes do stop, mas não aprovada) |

## Resumo

- Contas aprovadas: **3 de 6**.
- Contas reprovadas: **3 de 6**.
- Taxa de aprovação no cenário: **50%**.
- Operações consumidas até encerrar as 6 contas: **11**.
- Primeiro resultado: 02/01/2026 às 04:50 (horário do relatório do MT5).

Fonte: `NHS_2026_January_Trail150.htm`, NuvensHappyScalp, `TrailActivation=1.50`, `TrailDistance=0.50`, XAUUSD M30.
