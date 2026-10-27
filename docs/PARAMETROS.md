# Parâmetros recomendados para teste em demo

Use estes valores para reproduzir o teste intermediário:

```text
MaxSpreadPrice=0.50
UseInitialSoftStop=false
UseVirtualTrailing=true
TrailActivation=0.70
TrailDistance=0.50
UseBreakEven=false
MaxDailyLossPct=4.0
MaxDrawdownPct=8.0
```

Esta configuração não modifica a lógica de entrada. Ela apenas deixa a operação respirar mais antes de mover o trailing stop.
