# Nuvens Happy Scalp

EA compilada para MetaTrader 5, baseada no operacional Happy Scalp.

## Estado do pacote

- Inclui o binário `MQL5/Experts/NuvensHappyScalp.ex5`.
- O código-fonte `.mq5` não foi recuperado nesta versão; portanto, este repositório não é um pacote-fonte recompilável.
- Os parâmetros podem ser ajustados diretamente nas entradas da EA.

## Configuração testada

- Símbolo: XAUUSD
- Timeframe de sinal: M30
- Spread máximo: 0,50
- Soft stop inicial: desligado
- Trailing: ativação 0,70; distância 0,50
- Break-even: desligado
- Perda diária máxima: 4%
- Drawdown máximo: 8%

## Backtest de referência

Período: 01/01/2026 a 19/10/2026, depósito inicial de US$ 3.000.

| Ativação | Distância | Resultado | Drawdown | Operações |
|---:|---:|---:|---:|---:|
| 0,50 | 0,30 | +78,48% | 7,95% | 970 |
| 0,70 | 0,50 | +92,40% | 7,92% | 863 |
| 0,90 | 0,70 | +95,54% | 7,93% | 681 |

Os resultados são históricos e não garantem aprovação em mesa proprietária. O teste contínuo registrou acionamento do limite de drawdown em algum momento; valide primeiro em demo.
