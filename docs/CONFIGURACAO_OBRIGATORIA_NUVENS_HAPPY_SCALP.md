# Nuvens Happy Scalp — configuração obrigatória e evidências

> Este documento é a referência principal do repositório. Não alterar os parâmetros abaixo sem executar um novo backtest comparável.

## 1. Parâmetros obrigatórios do teste de referência

### Ambiente

| Item | Valor |
|---|---|
| EA | `NuvensHappyScalp.ex5` |
| Ativo | `XAUUSD` |
| Timeframe | `M30` |
| Modelo | `4` — ticks reais |
| Período de referência | 01/01/2026 a 31/01/2026 |
| Depósito | US$ 3.000 |
| Alavancagem | 1:100 |

### Entradas da EA

```text
ExecutionMode=1
MagicNumber=26101673
ShowPanel=false
BlockOtherSymbolPositions=true
FixedLot=0.10
HardStopDistance=2.40
TakeDistance=10.00
OneTradePerM30=true
SignalTimeframe=30
PivotOlderBars=2
PivotNewerBars=1
ScanBars=300
EntryOffset=0.00
MaxEntryGap=0.70
StartHour=3
EndHour=19
FridayEndHour=12
MaxSpreadPrice=0.50
CooldownAfterLossSeconds=0
UseInitialSoftStop=false
InitialSoftStopDistance=0.25
UseVirtualTrailing=true
TrailActivation=1.50
TrailDistance=0.50
UseBreakEven=false
BreakEvenTrigger=0.30
BreakEvenOffset=0.00
MaxHoldingSeconds=0
MaxRiskPerTradePct=1.0
MaxDailyLossPct=4.0
MaxDrawdownPct=8.0
MaxDeviationPoints=30
TraceSignals=false
ResetRiskStateOnInit=false
TraceSpreadAudit=false
OneTradePerPivot=true
```

## 2. Regra crítica do trailing

Os valores padrão recomendados para esta versão são:

- `UseVirtualTrailing=true`
- `TrailActivation=1.50`
- `TrailDistance=0.50`

O teste que apresentou o melhor resultado entre as variações avaliadas usou ativação 1,50 e distância 0,50. Não substituir por 0,70/0,50, 1,00/0,50 ou outros valores sem novo teste.

## 3. Proteções que não devem ser removidas

- `MaxSpreadPrice=0.50`: rejeita entradas quando o spread em preço ultrapassa o limite configurado.
- `MaxDailyLossPct=4.0`: limite diário da EA.
- `MaxDrawdownPct=8.0`: limite global de drawdown da EA.
- `OneTradePerM30=true` e `OneTradePerPivot=true`: impedem duplicação de entradas no mesmo contexto.
- `BlockOtherSymbolPositions=true`: evita conflito com outras posições do símbolo.

## 4. Atenção sobre risco e interpretação

O backtest da EA usou `FixedLot=0.10`. Portanto, `MaxRiskPerTradePct=1.0` não deve ser interpretado como se a EA tivesse dimensionado automaticamente cada lote pelo risco percentual.

As simulações das mesas foram uma camada de análise sobre a sequência de resultados:

- Fase de aprovação: stop de -2% e ganho de +4%, com no máximo duas operações por conta.
- Janeiro de 2026: 3 contas aprovadas entre 6.
- Continuação: risco de 0,25% e ganho de 0,50% mantendo R:R 1:2.
- Distribuição correta da continuação: rodízio entre as contas aprovadas — uma operação na Conta 1, depois Conta 2, depois Conta 5, repetindo.

Esses percentuais da simulação não foram calculados pelo lote fixo do EX5; são uma normalização para avaliar o cenário de mesas proprietárias.

## 5. Evidências no repositório

Relatórios HTML do Strategy Tester, com os gráficos incorporados pelo MT5:

- [Janeiro de 2026 — configuração de referência](../research/reports/NHS_2026_January_Trail150.htm)
- [Trail 1,50 / Distância 0,50](../research/reports/NHS_2026_Trail150_Dist050.htm)
- [Trail 1,00 / Distância 0,50](../research/reports/NHS_2026_Trail100_Dist050.htm)
- [Trail 1,50 / Distância 0,75](../research/reports/NHS_2026_Trail150_Dist075.htm)
- [Trail 2,00 / Distância 0,50](../research/reports/NHS_2026_Trail200_Dist050.htm)
- [Configuração anterior de referência](../research/reports/NHS_2026_Trail030.htm)

Configuração usada no teste de janeiro:

- [tester_2026_january_nhs_trail150.ini](../research/tester_2026_january_nhs_trail150.ini)
- [Preset recomendado](../research/NuvensHappyScalp_Trail150_Dist050.preset.txt)

Análises de contas:

- [Simulação de 6 contas](../research/simulacao_6_contas_janeiro_2026.md)
- [Continuação em rodízio das contas aprovadas](../research/simulacao_continuacao_3_contas_rodizio_janeiro_2026.md)

Gráficos exportados e relatórios históricos adicionais estão na pasta [`research`](../research/).

## 6. Limitação do pacote

O repositório contém apenas o binário `NuvensHappyScalp.ex5`; o código-fonte original `.mq5` não foi recuperado. Por isso, o default interno do EX5 não pode ser recompilado por este repositório. Ao instalar em outro MT5, carregar o preset ou conferir manualmente todos os valores desta página, principalmente trailing, spread e limites de perda.

Resultados históricos não garantem aprovação em mesa proprietária. Validar em demo com o spread real da corretora antes de operar qualquer conta.
