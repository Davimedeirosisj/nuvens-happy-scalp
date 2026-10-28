# Nuvens Happy Scalp

EA compilada para MetaTrader 5, baseada no operacional Happy Scalp.

## Estado do pacote

- Inclui o binário `MQL5/Experts/NuvensHappyScalp.ex5`.
- O código-fonte `.mq5` não foi recuperado nesta versão; portanto, este repositório não é um pacote-fonte recompilável.
- Os parâmetros podem ser ajustados diretamente nas entradas da EA.
- A configuração obrigatória está em [`docs/CONFIGURACAO_OBRIGATORIA_NUVENS_HAPPY_SCALP.md`](docs/CONFIGURACAO_OBRIGATORIA_NUVENS_HAPPY_SCALP.md).

## Configuração testada

- Símbolo: XAUUSD
- Timeframe de sinal: M30
- Spread máximo: 0,50
- Soft stop inicial: desligado
- Trailing: ativação 1,50; distância 0,50
- Break-even: desligado
- Perda diária máxima: 4%
- Drawdown máximo: 8%

## Backtest de referência

Período de referência: 01/01/2026 a 31/01/2026, depósito inicial de US$ 3.000.

| Ativação | Distância | Resultado líquido | Drawdown | Operações |
|---:|---:|---:|---:|---:|
| 1,00 | 0,50 | +US$ 2.844,10 | 7,92% | 982 |
| **1,50** | **0,50** | **+US$ 2.991,00** | 7,93% | 638 |
| 1,50 | 0,75 | +US$ 2.937,90 | 7,91% | 635 |
| 2,00 | 0,50 | +US$ 2.388,30 | 7,92% | 637 |

Os resultados são históricos e não garantem aprovação em mesa proprietária. O teste contínuo registrou acionamento do limite de drawdown em algum momento; valide primeiro em demo.

Relatórios HTML do Strategy Tester, gráficos e simulações estão na pasta [`research`](research/).
