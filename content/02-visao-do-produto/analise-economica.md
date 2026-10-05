---
title: Análise econômica
description: Custos mensais, economia potencial, retorno da implantação e premissas do cálculo.
tags:
  - visao
  - custos
---

> [!info] Conexões
> Detalha [[02-visao-do-produto/index]]. Fonte dos valores: [[atividades/atividade-2-custos-e-instalacao-llm]] (revisão de 29/09/2026). Usada na [[atividades/atividade-4-apresentacao-do-produto|apresentação]].

> [!warning] Estimativas de planejamento
> Os valores são estimativas, **a confirmar no piloto**. Gasto atual e faturamento foram informados pela empresa.

## Comparação de cenários

| Cenário | Custo mensal | Economia vs. hoje | Percentual |
| --- | --- | --- | --- |
| Situação atual (assinaturas) | R$ 10.000,00 | — | — |
| Híbrido (local + externas) | R$ 7.858,40 | R$ 2.141,60 | 21,4% |
| **Somente local** | **R$ 3.858,40** | **R$ 6.141,60** | **61,4%** |

## Composição do custo local

| Item | Valor mensal | Participação |
| --- | --- | --- |
| Suporte técnico | R$ 3.000,00 | 77,8% |
| Reserva de manutenção | R$ 500,00 | 13,0% |
| Monitoramento | R$ 200,00 | 5,2% |
| Energia e refrigeração | R$ 158,40 | 4,1% |
| **Total** | **R$ 3.858,40** | 100% |

O **suporte técnico** responde por quase 78% do custo: é a variável que mais pesa na decisão.

## Implantação e retorno

- **Implantação-base:** R$ 6.000,00 (40 h × R$ 150/h). GPU já existente, custo de aquisição zero.
- **Retorno (payback):** cerca de **1 mês** no cenário local (6.000 ÷ 6.141,60) e cerca de **2,8 meses** no híbrido (6.000 ÷ 2.141,60), ou seja, "1 a 3 meses". Esses prazos **não incluem** o orçamento da fila nem a compra de nobreak e disco, que alongam o retorno.
- **Fora do valor (orçamento separado):**
  - **Fila, painel de status e integração à API:** escopo adicional, *a orçar* (a implantação inicial é R$ 6.000 **+** o orçamento da fila).
  - **Nobreak e disco de dados:** compra a **definir com o cliente**.
  - **Expansão de hardware** (por exemplo, GPU de 48 GB para as 15 gerações simultâneas): só quando a demanda justificar, sujeita a cotação.

## Peso do gasto atual

R$ 10.000/mês correspondem a **1% do faturamento mensal** (R$ 1 milhão). O argumento é de **otimização**, e não de risco financeiro.

## O que pode mudar o resultado

| Fator | Efeito |
| --- | --- |
| Qualidade insuficiente do modelo de 14B | Mais uso das ferramentas externas, aproximando do cenário híbrido ou inviabilizando o local |
| Suporte técnico maior que o estimado | Reduz ou elimina a economia |
| Necessidade de hardware extra | Aumenta a implantação e o retorno |
| Fila excessiva no pico | Custo de ajuste e possível perda de produtividade |

## Validação dos cálculos

O simulador de custos foi validado em 05/10/2026 (20 cenários de memória, 66 verificações de cálculo). Isso valida a **conta**, e não o **desempenho real**, que será medido no servidor ([[03-requisitos/backlog-do-produto#Épico E7: Medição e validação do piloto|Épico E7]]).
