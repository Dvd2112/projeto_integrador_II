---
title: "Atividade 2: Custo e instalação da LLM"
description: Modelo escolhido, dimensionamento de memória, simulador de custos e roteiro de instalação.
tags:
  - atividade
  - custos
  - llm
---

**Responsável:** José · **Atualizado em:** 05/10/2026

> [!success] Entrega concluída
> Levantamento dos custos, estudo do modelo e da memória necessária, simulador de custos e documentação da instalação.

> [!info] Conexões
> Roda sobre a plataforma da [[atividades/atividade-1-servidor-padrao|Atividade 1]]. Seus números de custo e capacidade são usados na [[atividades/atividade-3-infraestrutura-e-distribuicao|Atividade 3]], no pitch da [[atividades/atividade-4-apresentacao-do-produto|Atividade 4]] e na [[02-visao-do-produto/index|Visão do Produto]]. Histórias: [[03-requisitos/backlog-do-produto#Épico E2: Chat com a IA|E2]] e [[03-requisitos/backlog-do-produto#Épico E3: Fila de atendimento|E3]].

## Como a solução funciona

Uma IA instalada no servidor da empresa para **explicar código, corrigir erros e criar testes**. O modelo estudado é o **Qwen2.5-Coder 14B**, executado pelo **Ollama**, programa que carrega e disponibiliza a IA.

```mermaid
flowchart LR
  P["Pessoa faz o pedido"] --> F["Pedido entra na fila"]
  F --> I["IA processa"]
  I --> R["Resposta aparece na aplicação"]
```

- Atende **15 usuários, com uma resposta sendo gerada por vez**.
- Se todos enviarem pedidos juntos, um é atendido e até 14 aguardam.
- Cada usuário tem uma solicitação aberta, com os estados **Na fila**, **Em processamento** e **Concluído**, e pode **cancelar enquanto aguarda**.
- Limite de **8.192 tokens por conversa** (pergunta, histórico e resposta), com **prazo máximo** e aviso de falha ou indisponibilidade.
- O tempo total inclui a espera na fila e a geração; picos de demanda aumentam a espera.
- Equipamento considerado: **RTX 4090 (24 GB de VRAM) e 128 GB de RAM**.
- Com limite inicial de **8.192 tokens** (unidades de texto), a VRAM projetada para uma geração é de **12,9 GiB**.
- O equipamento e o tempo de resposta serão conferidos na implantação; ampliar o atendimento simultâneo depende desses testes.

## Quanto custa

Estimativas de planejamento, com reaproveitamento do equipamento e valores revisados em **29/09/2026**.

| Despesa mensal | Valor |
| --- | --- |
| Suporte técnico | R$ 3.000,00 |
| Energia e refrigeração | R$ 158,40 |
| Reserva de manutenção | R$ 500,00 |
| Monitoramento | R$ 200,00 |
| **Total local** | **R$ 3.858,40/mês** |
| Ferramentas externas opcionais | + R$ 4.000,00 |
| **Total híbrido (local + externas)** | **R$ 7.858,40/mês** |

**Implantação-base: R$ 6.000,00**, estimados em 40 horas a R$ 150/h. Compra inicial de GPU: **R$ 0**.

**Fora desse valor:** a **fila, o painel de status e a integração à API** são escopo adicional, **a orçar** (total inicial = R$ 6.000 + orçamento da fila); **nobreak e disco de dados** têm compra **a definir com o cliente**; qualquer expansão de hardware exige cotação.

Detalhes de cálculo: suporte = 20 h × R$ 150 = R$ 3.000; energia = 0,5 kW × 220 h × R$ 1,20/kWh = R$ 132,00, mais 20% de refrigeração (R$ 26,40), totalizando R$ 158,40.

### Comparação com o gasto atual

| Cenário | Custo mensal | Diferença para R$ 10.000 | Retorno da implantação |
| --- | --- | --- | --- |
| Situação atual | R$ 10.000,00 | — | — |
| Híbrido | R$ 7.858,40 | **R$ 2.141,60** | cerca de 2,8 meses |
| Somente local | R$ 3.858,40 | **R$ 6.141,60** (61%) | cerca de 1 mês |

A economia só se concretiza **caso seja possível substituir as ferramentas atuais**, o que depende dos testes de qualidade ([[referencias/criterios-de-avaliacao]]).

## Crescer com o uso

Hoje a RTX 4090 atende **1 geração ativa por vez** (≈ 12,9 GiB), com fila para os demais. Se a espera recorrente prejudicar o trabalho, primeiro se amplia o processamento **dentro da capacidade da RTX 4090** (2 ativos: 14,4 GiB; 4 ativos: 17,4 GiB). Se a demanda continuar acima disso, orça-se uma GPU com mais memória (**classe de 48 GB** comporta as 15 gerações simultâneas em 8 mil tokens, cerca de 32,9 a 34,9 GiB) ou outro servidor. A expansão é **investimento pontual em hardware**, e não nova assinatura por pessoa, e tem **orçamento próprio**.

## Como será a instalação

1. **Conferir o servidor:** sistema, placa de vídeo, memória, armazenamento e rede.
2. **Preparar a IA:** instalar Ollama, baixar o Qwen 14B e configurar uma geração por vez.
3. **Liberar acesso protegido:** autenticação e restrição de rede (a API local do Ollama, sozinha, não exige senha).
4. **Integrar a aplicação:** conectar chat, fila e estados de atendimento.
5. **Testar e registrar:** qualidade das respostas, espera, uso de memória, consumo e recuperação em caso de falha.

O roteiro está entregue. A execução no servidor é a etapa operacional do grupo, alinhada a infraestrutura e segurança ([[atividades/atividade-1-servidor-padrao|Atividade 1]] e [[atividades/atividade-5-seguranca|Atividade 5]]).

## Evidências

O simulador foi validado em **05/10/2026**: compilação e versão de produção aprovadas, **20 cenários de memória e 66 verificações de cálculo**. Isso comprova os **cálculos** do estudo; o **desempenho da IA** será medido no servidor.

**Qual valor usar:** os desta página e da proposta de 29/09. O Word e os gráficos preservam estimativas anteriores.

### Anexos

Os arquivos estão em [[Anexos/index|Anexos]].

| Arquivo | O que contém |
| --- | --- |
| `Proposta_IA_local_Qwen14B_com_fila.pdf` | Funcionamento (p. 1) e custos vigentes (p. 3) |
| `IA_local_graficos_e_hardware_15_pessoas.pdf` | Dimensionamento e alternativas (pp. 4–6) |
| `Custos_e_instalacao_da_solucao_LLM.docx` | Seção "Procedimentos de instalação e disponibilização", etapas 1–7 |
| `Evidencias_entrega_Jose_custos_instalacao_LLM.pdf` | Entregas (p. 1), cálculos (p. 2), validações e fontes (p. 3) |
| `registro-validacao-2026-10-05.txt` | Detalhe das verificações |

## Observação sobre a escolha do modelo

O Qwen2.5-Coder 14B **não consta** no quadro de [[referencias/modelos-candidatos|modelos candidatos]] da proposta original. A justificativa (qualidade próxima à do 32B com muito menos memória, e licença Apache 2.0) está em [[referencias/modelos-candidatos#Justificativa da escolha|Justificativa da escolha]].
