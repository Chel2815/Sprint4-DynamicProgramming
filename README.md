# Sprint 4 Dynamic Programming

Alunos:
Marchel Augusto - RM 99856
Matheus Riccioti - RM 556930
Guilherme Lunghini - RM 555892
Matheus Bortolotto - RM 555189
Luan Ramos - RM 558537

## Como o código funciona

Este repositório modela o problema de *previsão/controle de consumo de insumos* em unidades de diagnóstico com Programação Dinâmica. Inclui três implementações: recursiva pura, recursiva com *memoização* e *iterativa (bottom‑up)* — e um teste que *comprova a equivalência* dos resultados.

## Formulação
- *Estado* S = (dia, estoque), onde dia ∈ {0..n} e estoque ∈ {0..max_cap}.  
- *Decisão* q ∈ {0..max_cap - estoque} é a *quantidade a pedir* no início do dia.  
- *Transição* estoque' = min(max_cap, max(0, estoque + q - consumo[dia])).  
- *Custo imediato* c(estoque,q,d) = estoque*c_estoque + 1_{q>0}*c_pedido + falta*c_falta,  
  com falta = max(0, consumo[d] - (estoque + q)).  
- *Objetivo* minimizar Σ_d c(estoque_d, q_d, d) ao longo do horizonte.

> Interpretação: pedimos que no começo do dia, pagamos custo fixo de pedido se q>0, sofremos custo de estocar as unidades remanescentes e penalizamos faltas de atendimento.

## Estruturas / Algoritmos
- *Recursiva pura*: implementação direta da equação de Bellman (didática, exponencial).  
- *Recursiva com memoização: usa @lru_cache para **guardar subproblemas* (dia, estoque).  
- *Iterativa (bottom-up)*: preenche tabela dp[d][e] para d = n..0 e e = 0..max_cap.

As três versões *devem produzir o mesmo custo ótimo*; o script inclui um assert que verifica isso.

## Como executar
1. Requer *Python 3.8+*.  
2. Rode:
   bash
   python dp_insumos.py
   
   Saída esperada (valores iguais):
   
   Recursiva pura : XX
   Recursiva memo : XX
   Bottom-up      : XX
   

## Ajustando o cenário
No final do arquivo dp_insumos.py, na função exemplo(), altere:
- consumo (lista diária),  
- max_cap (capacidade),  
- c_estoque, c_pedido, c_falta (parâmetros de custo),  
- estoque_ini.

## Complexidade
- *Bottom-up*: O(n * max_cap * max_q) com max_q ≤ max_cap.  
- *Memoização: mesma ordem no pior caso, mas normalmente visita **menos estados* do que a recursiva pura.

- *Relatório: copiar a seção *Formulação e Estruturas/Algoritmos, e colar a saída do programa mostrando a *equivalência* entre as três abordagens (prints).

---
