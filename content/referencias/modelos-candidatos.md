---
title: Modelos de IA locais candidatos
description: Modelos avaliados para execução local via Ollama e o modelo efetivamente adotado.
tags:
  - referencia
  - modelos
---

> [!note] Como ler os tamanhos
> Os tamanhos são dos **arquivos disponibilizados no Ollama**, nas versões indicadas. **Não representam o consumo total de memória em uso**: é preciso reservar memória para processar as conversas e as solicitações simultâneas.

## Quadro dos candidatos da proposta original

| Modelo | Para que avaliar no projeto | Versão e tamanho aproximado |
| --- | --- | --- |
| **Qwen3.6 27B** | Desenvolvimento de funcionalidades, análise de projetos e tarefas de frontend; melhorias em programação e raciocínio sobre repositórios | Q4_K_M: **18 GB**. Testar com controle do tamanho das conversas |
| **Qwen3-Coder 30B-A3B** | Assistente dedicado à programação; integração com ferramentas de desenvolvimento | Q4_K_M: **19 GB**. Especializado, mas deixa menos espaço para conversas longas e paralelismo na GPU |
| **Devstral Small 2 24B (Mistral)** | Projetos existentes, exploração de arquivos e alterações em vários arquivos com um agente de programação | Q4_K_M: **15 GB**. Apresentado como adequado a execução local, inclusive RTX 4090 |
| **Qwen3.5 9B** | Alternativa leve para o primeiro protótipo: explicações, dúvidas técnicas e tarefas menores; aceita imagens | Q4_K_M: **6,6 GB**. Referência de menor consumo |
| **gpt-oss-20b (OpenAI)** | Assistente geral para raciocínio, dúvidas técnicas e tarefas de desenvolvimento | MXFP4: **14 GB**. Pode operar com 16 GB de memória em configurações compatíveis |

## Modelo adotado nos estudos

A [[atividades/atividade-2-custos-e-instalacao-llm|Atividade 2]] e a [[atividades/atividade-3-infraestrutura-e-distribuicao|Atividade 3]] trabalham com o **Qwen2.5-Coder 14B** (Apache 2.0), via Ollama:

- ≈ **12,9 GiB** de VRAM com uma geração e contexto de 8.192 tokens;
- cerca de 1,5 GiB extras por geração simultânea.

> [!note] Relação com o quadro acima
> O Qwen2.5-Coder 14B **não está** no quadro de candidatos da proposta original: ele foi escolhido nos estudos de custo e capacidade, e a justificativa está abaixo. Uma comparação direta com os cinco candidatos acima, nos mesmos testes, ainda não foi feita.

### Justificativa da escolha

A escolha foi pelo **equilíbrio entre qualidade e tamanho**. No teste público de programação *BigCodeBench-Instruct Full*, o 14B fica muito próximo do 32B, que é bem maior:

| Modelo | Acertos |
| --- | --- |
| Qwen2.5-Coder 32B | 49,6% |
| **Qwen2.5-Coder 14B (adotado)** | **48,4%** |
| Qwen2.5-Coder 7B | 41,0% |
| DeepSeek Coder V2 Lite | 36,8% |

> [!warning] Leitura correta do resultado
> Os números são dos **modelos originais**, e não da versão Q4 usada no projeto, que pode ter resultado diferente. Fonte: Qwen2.5-Coder Technical Report (2024), tabela 16. Isso **não** mede a qualidade no servidor da empresa: o piloto é que fará essa medição ([[referencias/criterios-de-avaliacao]]).

Complementam a justificativa: a licença **Apache 2.0**, compatível com uso comercial, e o consumo de VRAM que deixa margem dentro dos 24 GB.

## Critérios sugeridos para a comparação

Alinhados a [[referencias/criterios-de-avaliacao]]: qualidade em tarefas de programação, consumo de VRAM (margem para paralelismo), tempo de resposta, licença para uso comercial e facilidade de operação.
