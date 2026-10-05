---
title: Caracterização da empresa e do problema
description: Quem é a empresa analisada, qual é o cenário atual de uso de IA e qual problema o projeto investiga.
tags:
  - contexto
  - problema
---

> [!info] Onde esta página se encaixa
> Ponto de partida de todo o trabalho. O problema descrito aqui alimenta a [[01-bmad/index|documentação BMAD]], que leva à [[02-visao-do-produto/index|Visão do Produto]] e aos [[03-requisitos/index|Requisitos]].

## A empresa

Fábrica de software com cerca de **20 anos de mercado**. Desenvolve sistemas sob demanda para outras organizações e, ao final de cada projeto, **entrega o sistema e o código-fonte ao cliente**, que passa a ser responsável pela manutenção.

| Característica | Dado informado |
| --- | --- |
| Modelo de negócio | Fábrica de software (sistemas sob demanda) |
| Clientes | Instituições bancárias, uma universidade, uma empresa do setor de acervos e uma agência de viagens |
| Equipes de desenvolvimento | 3, com cerca de 5 a 6 profissionais cada (15 a 18 pessoas) |
| Faturamento | Cerca de **R$ 1 milhão por mês** |
| Gasto com IA | Cerca de **R$ 10 mil por mês** (ferramentas externas, em uso há aproximadamente 1 ano) |
| Hardware já disponível | Máquina com GPU de alto desempenho (**RTX 4090, 24 GB de VRAM**) e **128 GB de RAM** (confirmado). **Nobreak** e **disco de dados** não estão garantidos: a compra será definida com o cliente |

## O cenário

Há cerca de um ano as equipes passaram a usar ferramentas de Inteligência Artificial para ganhar produtividade e reduzir custos operacionais. Esse uso hoje representa um gasto recorrente de aproximadamente R$ 10 mil por mês. Como a empresa já possui uma máquina com GPU potente, surgiu o interesse em avaliar uma **solução interna de IA** que aproveite essa infraestrutura e atenda as três equipes.

## O problema

> [!question] Desafio do projeto
> Analisar a **viabilidade técnica e econômica** de uma solução interna de IA, considerando a capacidade do equipamento, a qualidade das respostas, o atendimento a múltiplos usuários e os custos de implantação, operação e manutenção.

O problema tem três dimensões, que reaparecem em todo o projeto:

1. **Custo.** Há uma despesa recorrente com ferramentas externas e uma infraestrutura própria parcialmente ociosa.
2. **Sigilo.** Os clientes incluem bancos. Trechos de código enviados a ferramentas externas saem da rede da empresa (ver [[atividades/atividade-5-seguranca|segurança]]).
3. **Capacidade e qualidade.** Não se sabe se uma única GPU atende 15 a 18 pessoas com respostas boas o suficiente (ver [[referencias/criterios-de-avaliacao|critérios de avaliação]]).

## Como dimensionar o gasto de forma honesta

R$ 10 mil por mês correspondem a **1% do faturamento mensal** informado. Portanto o argumento do projeto **não** é que essa despesa ameace a empresa. O argumento é que existe uma **oportunidade de otimização** a investigar, com benefícios adicionais de sigilo e controle.

> [!warning] Ponto de atenção para a apresentação
> O material de pitch compara o gasto com "12% do faturamento anual (R$ 1 milhão)". Isso mistura período: R$ 1 milhão é o faturamento **mensal**. Em base anual, R$ 120 mil de gasto sobre R$ 12 milhões de faturamento também dá **1%**. A apresentação deve usar **1%**.

## Próximo passo

Delimitação do que será feito: [[contexto/proposta-e-delimitacao|Proposta e delimitação]].
