# Backtest anual - Nuvens Happy Barra Anterior 1.10

## Escopo

Intervalo [27/10/2025, 27/10/2026), XAUUSD M30, modelo 4.
Deposito USD 3.000, lote fixo 0,10, spread maximo para entrada 0,40
(filtro em unidades de preco; nao spread fixo imposto aos ticks).
Stop inicial na ultima barra M30 fechada com buffer 0,05.
Take 10,00; trailing com ativacao 0,50 e distancia 0,30.
Janela servidor 03:00-19:00, sexta ate 12:00.
Limite diario 4%; drawdown do pico de equity 8%; sem resets mensais.
O bloqueio total de drawdown e persistente durante a execucao.

EA reconstruida, separada do EX5 original NuvensHappyScalp.
Nao houve ajuste de parametros ou otimizacao entre as duas execucoes anuais.

## Resultado exibido pelo MT5

| Indicador | Valor |
|---|---:|
| Lucro liquido apos comissoes | USD 2.787,78 |
| Retorno sobre deposito | 92,93% |
| Saldo final | USD 5.787,78 |
| Operacoes | 378 |
| Vencedoras / perdedoras apos comissoes | 346 / 32 |
| Acerto | 91,53% |
| Fator de lucro do MT5 | 2,26 |
| Drawdown maximo do saldo | USD 260,98 / 4,32% |
| Drawdown maximo da equity | USD 482,96 / 7,99% |

As 378 entradas e os stops iniciais foram auditados: todos utilizaram a barra
M30 anterior, com arredondamento para o tick negociavel de ate 0,01.
Nenhuma rejeicao de ordem foi registrada; uma entrada no maximo por barra.

## Limites da conclusao

O relatorio HTML mostra "100% de ticks reais", mas o journal contradiz essa
leitura: 48.389 de 350.546 minutos tiveram ticks reais descartados e uso de
geracao de ticks. Houve inconsistencias entre precos de ticks e barras em
47 dias de 2025. Isso compromete a validacao de entradas, spread e trailing
por tick nesse trecho, apesar do lucro exibido.

A primeira execucao ocorreu em .mt5-confluence-test. Para verificar se era
problema do cache, foi criada .mt5-happy-year-clean, com novo download das
barras e dos arquivos de ticks diretamente de FTMO-Demo. Ambas terminaram
com 378 operacoes, USD 2.787,78 e os mesmos alertas de historico.
O problema persistiu apos o novo download; sua causa exata nao foi determinada.

Primeira entrada: 27/10/2025 03:08:46 no horario do servidor.
Ultima entrada: 26/01/2026 16:58:32; ultima saida 26/01/2026 18:03:19.
O tester continuou ate 26/10/2026 23:49:58. Houve 39.104 cruzamentos bloqueados
por risco. De fevereiro a outubro nao houve operacoes: nao corresponde a
doze meses de atividade ininterrupta. O instante exato do bloqueio nao foi
registrado individualmente nesta versao.

O limite programado e 8%, enquanto a equity maxima reportada e 7,99%.
O resumo do MT5 nao fornece sozinho o tick exato que acionou o bloqueio.
Nao se deve inferir aprovacao em mesa a partir desses numeros.

## Fluxo de caixa mensal desta execucao continua

| Mes | Entradas | Liquido em USD |
|---|---:|---:|
| Outubro/2025 (a partir do dia 27) | 26 | 178,09 |
| Novembro/2025 | 125 | 1.651,99 |
| Dezembro/2025 | 141 | 933,69 |
| Janeiro/2026 (ate dia 26) | 86 | 24,01 |
| Fevereiro a outubro/2026 | 0 | 0,00 |

Nao houve reinicio de saldo ou desbloqueio entre os meses. Este quadro nao
simula compra de novas contas nem desafios mensais independentes.

## Arquivos e reproducao

- nuvens-happy-1ano-clean.htm: repeticao apos novo download de historico.
- nuvens-happy-1ano-clean.ini: configuracao da repeticao.
- nuvens-happy-barra-anterior-1ano.htm e .ini: primeira execucao anual.
- audit_previous_bar.py: conciliacao dos deals e verificacao dos stops.

SHA256 EX5: BF1C7DE79CDBC8CDF9C7B606B790889E87AED58C94A10D4B246454D420266BA6
O alias NuvensHappy_BarraAnterior_v110.ex5 e o mesmo binario da variante
NuvensHappy_BarraAnterior.ex5 instalada no terminal principal.

Journal da repeticao:
E:\IA\BROOKS\.mt5-happy-year-clean\Tester\logs\20261027.log

Auditoria a partir da raiz Happy_Gold_MT5:

```text
python research/audit_previous_bar.py research/nuvens-happy-1ano-clean.htm E:\IA\BROOKS\.mt5-happy-year-clean\Tester\logs\20261027.log
```
