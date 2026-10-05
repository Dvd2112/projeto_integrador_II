---
title: Critérios de avaliação do resultado
description: O que o grupo precisa demonstrar para provar (ou refutar) a viabilidade da solução.
tags:
  - referencia
  - avaliacao
---

O trabalho fica mais consistente com **evidências de viabilidade**, e não apenas com uma interface funcionando.

| Critério | Pergunta que o projeto deve responder | Meta definida | Histórias |
| --- | --- | --- | --- |
| **Qualidade** | As respostas ajudam a resolver as tarefas de programação escolhidas? As sugestões de código funcionam quando verificadas? | ≥ 70% das respostas úteis | US-04 a US-09, US-28 |
| **Desempenho** | Qual o tempo de resposta e como muda com várias pessoas? | Espera ≤ 30 s em 95% dos pedidos | US-26 |
| **Capacidade** | Quantos usuários simultâneos a configuração atende de modo aceitável? | 15–18 pessoas; 1 → 4 gerações | US-27, US-31 |
| **Custo total** | Quanto custa operar considerando energia, manutenção, administração e ferramentas externas que continuem necessárias? | Abaixo de R$ 10.000/mês | US-30 |
| **Adequação ao trabalho** | O protótipo atende às atividades prioritárias ou deixa de fora funções importantes das ferramentas atuais? | Avaliação da equipe piloto | US-28 |
| **Segurança** | Quem acessa? O que fica armazenado? Como são tratados os códigos e informações enviados? | Nenhum incidente | US-19 a US-22 |
| **Disponibilidade** | O serviço está no ar quando as equipes precisam? | ≥ 98% no horário comercial | US-29 |

## Desfechos possíveis

> [!abstract] Todos são resultados válidos
> - **Substituição parcial** das ferramentas externas.
> - **Uso combinado** de ferramentas internas e externas (híbrido).
> - **Inviabilidade** da configuração testada.
>
> O compromisso é avaliar com critérios claros, e não garantir de antemão uma economia.

## Ligação com o restante do trabalho

- Metas e premissas: [[atividades/atividade-3-infraestrutura-e-distribuicao#Premissas a validar no piloto|premissas do piloto]].
- Custos: [[02-visao-do-produto/analise-economica]].
- Histórias de medição: [[03-requisitos/backlog-do-produto#Épico E7: Medição e validação do piloto|Épico E7]].
