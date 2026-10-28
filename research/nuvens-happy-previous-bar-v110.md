# Nuvens Happy Barra Anterior 1.10

Backtest executado no terminal MT5 isolado, conta de dados FTMO-Demo.
XAUUSD M30, intervalo [2026-10-05, 2026-10-19), deposito USD 3.000,
lote fixo 0,10, modelo 4, qualidade reportada: 100% de ticks reais.

## Correcao

- Atualiza os ultimos pivos confirmados a cada nova barra M30.
- Confirma cruzamento por tick: Ask para compra, Bid para venda.
- Consome o pivo somente depois da execucao confirmada da ordem.
- Limita a uma entrada por barra M30 e uma posicao por simbolo.
- Stop inicial: minima da ultima barra M30 fechada menos 0,05 na compra;
  maxima da ultima barra M30 fechada mais 0,05 na venda. Ajuste para o tick
  negociavel, com arredondamento para fora de ate 0,01 no teste.
- Verifica a distancia minima permitida pela corretora antes de enviar stops.
- Gerencia trailing somente em posicoes com o Magic desta variante.

## Parametros do teste

Filtro de spread maximo: 0,40 em unidades de preco, usando Bid/Ask historicos
dos ticks. Isso NAO define um spread fixo de 0,40 para todos os ticks.
TakeDistance=10,00; trailing ativa em 0,50 com distancia 0,30.
O parametro herdado InpUseVirtualTrailing nesta variante modifica o SL no
servidor; nao implementa trailing virtual local.
Janela no horario do servidor: 03:00 <= horario < 19:00;
sexta encerra novas entradas as 12:00.
Limites de novas entradas: perda diaria 4%, drawdown do pico de equity 8%.
Esses bloqueios nao liquidam automaticamente posicoes ja abertas.

## Resultado

| Medida | Valor |
|---|---:|
| Operacoes | 42 |
| Lucro liquido, incluindo comissoes | USD 171,14 |
| Retorno sobre deposito | 5,70% |
| Saldo final | USD 3.171,14 |
| Drawdown maximo do saldo | USD 78,03 / 2,45% |
| Drawdown maximo da equity | USD 97,18 / 3,12% |
| Fator de lucro do relatorio MT5 | 2,56 |
| Vencedoras apos comissoes de entrada e saida | 38 |
| Perdedoras apos comissoes de entrada e saida | 4 |

O MT5 exibe 39 vencedoras / 3 perdedoras. O auditor reconcilia cada par de
deals e inclui ambas as comissoes, encontrando 38 / 4. A soma e USD 171,14.

Auditoria: 42 stops iniciais vinculados a barra M30 anterior, nenhuma barra
com duas entradas e nenhuma rejeicao de ordem. Contadores de cruzamentos
bloqueados: spread 950, sessao 139, gap 1, exposicao 12, stops invalidos 5,
risco 0. Esses numeros sao cruzamentos, nao oportunidades independentes.

Este e o teste da variante reconstruida, cujo codigo de entrada tambem foi
corrigido. O resultado nao isola a vantagem de alterar somente o stop em
relacao ao EX5 original da Nuvens Happy.

## Reproducao e identidade

Config: nuvens-happy-previous-bar-v110.ini. O alias v110 identifica o mesmo
binario instalado como NuvensHappy_BarraAnterior.ex5.
SHA256 EX5: BF1C7DE79CDBC8CDF9C7B606B790889E87AED58C94A10D4B246454D420266BA6
SHA256 MQ5: 422D332E37F0DD8B74BFF10D02A452ECC716EFD228335C7F8710B053D093F0C9
Compilacao: 0 erros, 0 avisos.

Auditoria reproduzivel no diretorio research:

```text
python audit_previous_bar.py nuvens-happy-previous-bar-v110.htm nuvens-happy-previous-bar-v110-audit.log
```

O arquivo audit.log e um extrato das linhas de inicializacao, entrada,
contadores e encerramento do log original do tester. O log integral esta
em E:\IA\BROOKS\.mt5-confluence-test\Tester\logs\20261027.log.
