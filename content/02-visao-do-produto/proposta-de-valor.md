---
title: Proposta de valor e diferenciais
description: Para quem é o Hub de IA Local, quais benefícios entrega e como trata segurança e conformidade.
tags:
  - visao
  - valor
  - seguranca
---

> [!info] Conexões
> Detalha [[02-visao-do-produto/index]]. Segurança aprofundada em [[atividades/atividade-5-seguranca]]; comparação completa em [[atividades/atividade-3-infraestrutura-e-distribuicao#Diferenciais|Diferenciais da Atividade 3]].

## Para quem é

| Perfil | Necessidade | O que o produto oferece |
| --- | --- | --- |
| **Desenvolvedor** (15 a 18 pessoas, 3 equipes) | Ajuda rápida para entender, corrigir e testar código | Chat com IA pelo navegador, sem instalação |
| **Líder de equipe / diretoria** | Controlar custo e saber quem usa | Custo fixo; métricas e cotas na evolução (Fase 2) |
| **Infraestrutura** | Operar com segurança e previsibilidade | Plataforma documentada, monitorada, com backup |
| **Clientes finais** (bancos, universidade) | Confidencialidade do código | Processamento dentro da rede da empresa |

## Benefícios

1. **Sigilo.** Nenhum código enviado a servidores de terceiros no cenário local.
2. **Custo previsível.** R$ 3.858,40/mês (local) ou R$ 7.858,40/mês (híbrido), contra ≈ R$ 10.000/mês variável ([[02-visao-do-produto/analise-economica]]).
3. **Sem cota por pedido.** Não há cobrança por usuário nem por uso.
4. **Controle.** A empresa escolhe modelo, versão e configuração, e o fornecedor não muda termos.
5. **Aproveitamento.** Usa hardware que a empresa já tem.
6. **Funciona na rede interna.** Não depende de internet.
7. **Personalização futura.** Padrões de código da empresa e acervo de 20 anos (Fase 2).

## Segurança e conformidade por desenho

- Processamento e dados dentro da rede interna.
- Acesso por autenticação e rede interna; a API local, isoladamente, **não** exige senha, por isso fica restrita à própria máquina.
- Contas documentadas, com procedimento formal de revogação no desligamento.
- Menos dados fora da empresa significa menos superfície de risco sob a **LGPD** nos contratos que exigem confidencialidade.

> [!warning] Segurança não é garantia automática
> "Código não sai da empresa" vale para o cenário **local**. No cenário **híbrido**, parte das demandas continua indo para ferramentas externas, e é preciso uma regra clara do que pode sair ([[atividades/atividade-5-seguranca#Pontos em aberto|pontos em aberto da Atividade 5]]).

## Limites que fazem parte da proposta

- Um modelo de 14B é **inferior aos comerciais de ponta** em tarefas complexas.
- Servidor único: a contingência são as ferramentas externas mantidas.
- Fila nos horários de pico.

Esses limites e seus tratamentos estão em [[atividades/atividade-3-infraestrutura-e-distribuicao#Limitações e tratamento|Limitações e tratamento]].
