---
title: Requisitos não funcionais
description: Metas de desempenho, capacidade, disponibilidade, segurança, custo e demais qualidades do produto.
tags:
  - requisitos
  - rnf
---

> [!info] Conexões
> Complementa o [[03-requisitos/backlog-do-produto|Backlog]]: as histórias dizem **o que** o sistema faz; estes requisitos dizem **com que qualidade**. Cada um aponta as histórias que o verificam.

| ID | Categoria | Requisito | Meta | Verificado em | Fonte |
| --- | --- | --- | --- | --- | --- |
| RNF-01 | Desempenho | Espera na fila no piloto | ≤ 30 s em 95% dos pedidos | US-26 | [[atividades/atividade-3-infraestrutura-e-distribuicao]] |
| RNF-02 | Desempenho | Tempo médio de resposta | ≈ 10 s; alerta acima de ≈ 12 s | US-26 | [[atividades/atividade-3-infraestrutura-e-distribuicao]] |
| RNF-03 | Capacidade | Usuários atendidos | 15 a 18 pessoas, 3 equipes | US-11, US-26 | [[contexto/empresa-e-problema]] |
| RNF-04 | Segurança | A API do modelo não é acessível pela rede | Só `127.0.0.1:11434` | US-21 | [[atividades/atividade-1-servidor-padrao]] |
| RNF-05 | Segurança | Tráfego protegido e porta única | HTTPS, porta 443 do gateway | US-01 | [[atividades/atividade-3-infraestrutura-e-distribuicao]] |
| RNF-06 | Segurança | Acesso administrativo | SSH só por chave, firewall fechado por padrão | US-22 | [[atividades/atividade-1-servidor-padrao]] |
| RNF-07 | Privacidade | Conteúdo do código não armazenado; segredos nunca em logs | Logs sem corpo de requisição e sem credenciais | US-19, US-39 | [[atividades/atividade-3-infraestrutura-e-distribuicao]] |
| RNF-08 | Conformidade | Atender à LGPD e ao sigilo contratual | Dados na rede interna; política de registros definida | US-19, US-20 | [[atividades/atividade-5-seguranca]] |
| RNF-09 | Disponibilidade | Serviço no ar no horário comercial | ≥ 98% | US-29 | [[atividades/atividade-3-infraestrutura-e-distribuicao]] |
| RNF-10 | Confiabilidade | Servidor aprovado em estresse | 24 h combinadas sem erro | US-15 | [[atividades/atividade-1-servidor-padrao]] |
| RNF-11 | Recuperação | Restauração a partir de backup | Restauração testada | US-17 | [[atividades/atividade-1-servidor-padrao]] |
| RNF-12 | Qualidade | Respostas úteis | ≥ 70% | US-09, US-28 | [[referencias/criterios-de-avaliacao]] |
| RNF-13 | Recursos | Memória de vídeo | ≈ 12,9 GiB com 1 geração (contexto 8.192); ≤ 24 GB no total | US-16, US-27 | [[atividades/atividade-2-custos-e-instalacao-llm]] |
| RNF-14 | Custo | Operação mensal | Abaixo de R$ 10.000; referência local R$ 3.858,40 | US-30 | [[02-visao-do-produto/analise-economica]] |
| RNF-15 | Custo | Implantação-base | R$ 6.000 (40 h × R$ 150) | US-30 | [[atividades/atividade-2-custos-e-instalacao-llm]] |
| RNF-16 | Licenciamento | Uso comercial permitido | Ollama (MIT); Qwen2.5-Coder 14B (Apache 2.0) | Conferência de licenças | [[atividades/atividade-3-infraestrutura-e-distribuicao]] |
| RNF-17 | Usabilidade | Sem instalação para o desenvolvedor | Acesso pelo navegador | US-01 | [[atividades/atividade-3-infraestrutura-e-distribuicao]] |
| RNF-18 | Manutenibilidade | Ambiente reproduzível | Containers, versões fixadas, roteiro documentado | US-14, US-25 | [[atividades/atividade-1-servidor-padrao]] |
| RNF-19 | Observabilidade | Alertas de saúde | Temperatura > 85 °C e serviço fora do ar | US-23 | [[atividades/atividade-1-servidor-padrao]] |
| RNF-20 | Auditabilidade | Eventos de acesso registrados sem o conteúdo | Login/logout, usuário, equipe, horário, erros e acesso indevido (com alerta) | US-38 | [[atividades/atividade-5-seguranca]] |
| RNF-21 | Retenção | Prazo definido para logs e históricos | **A definir** | US-42 | [[atividades/atividade-5-seguranca]] |

> [!note]
> Metas marcadas com ≈ vêm de estimativas e **precisam ser confirmadas no piloto** ([[atividades/atividade-3-infraestrutura-e-distribuicao#Premissas a validar no piloto|premissas]]).
