---
title: Rastreabilidade
description: Matriz que liga cada épico ao problema, à atividade de origem e aos critérios de avaliação.
tags:
  - requisitos
  - rastreabilidade
---

> [!info] Conexões
> Complementa [[03-requisitos/index]]. Mostra como a [[02-visao-do-produto/index|visão]] se desdobra em histórias e como cada uma será verificada.

## Matriz épico → origem → verificação

| Épico | Problema que endereça | Atividade de origem | Critério de avaliação |
| --- | --- | --- | --- |
| **E1** Acesso e autenticação | Sigilo e controle de quem usa | [[atividades/atividade-3-infraestrutura-e-distribuicao\|3]], [[atividades/atividade-1-servidor-padrao\|1]] | Segurança |
| **E2** Chat com a IA | Produtividade das equipes | [[atividades/atividade-2-custos-e-instalacao-llm\|2]] | Qualidade, adequação ao trabalho |
| **E3** Fila de atendimento | Atender 15 a 18 pessoas com uma GPU | [[atividades/atividade-2-custos-e-instalacao-llm\|2]], [[atividades/atividade-3-infraestrutura-e-distribuicao\|3]] | Desempenho, capacidade |
| **E4** Plataforma | Aproveitar o hardware existente com segurança | [[atividades/atividade-1-servidor-padrao\|1]] | Desempenho, segurança |
| **E5** Segurança e privacidade | Código bancário fora da rede; LGPD | [[atividades/atividade-5-seguranca\|5]], [[atividades/atividade-1-servidor-padrao\|1]] | Segurança |
| **E6** Operação | Servidor único precisa de contingência | [[atividades/atividade-1-servidor-padrao\|1]], [[atividades/atividade-3-infraestrutura-e-distribuicao\|3]] | Disponibilidade |
| **E7** Medição | Provar a viabilidade, e não afirmá-la | [[referencias/criterios-de-avaliacao]] | Todos |
| **E8** Evolução | Governança e reuso de acervo | [[02-visao-do-produto/escopo-e-fases\|Visão (Fase 2)]] | Custo total |

## Objetivos da visão e histórias

| Objetivo da visão | Histórias principais |
| --- | --- |
| Reduzir o custo com ferramentas externas | US-30, US-16, US-26 |
| Proteger o código dos clientes | US-01, US-19, US-21, US-22, US-36, US-39, US-40, US-41, US-43 |
| Atender as três equipes | US-10, US-11, US-27, US-31 |
| Dar governança e visibilidade | US-20, US-34, US-37, US-38, US-42 |
| Reaproveitar 20 anos de acervo | US-35 |

## Histórias por fase

| Fase | Histórias |
| --- | --- |
| **0. Servidor pronto** | US-14, US-15, US-16, US-17, US-18, US-21, US-22, US-23, US-25 |
| **1. Piloto** | US-01, US-03, US-04, US-05, US-06, US-07, US-08, US-09, US-10, US-11, US-13, US-19, US-20, US-24, US-26, US-27, US-28, US-36, US-38, US-39, US-41, US-42, US-43, US-44 |
| **2. Três equipes** | US-02, US-12, US-29, US-31, US-37, US-40 |
| **3. IDE e decisão** | US-30, US-32 |
| **Além da Fase 3** | US-33, US-34, US-35 |
