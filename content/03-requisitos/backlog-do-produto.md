---
title: Backlog do Produto (histórias de usuário)
description: 44 histórias de usuário organizadas em 8 épicos, com prioridade, fase, origem e critérios de aceitação.
tags:
  - requisitos
  - backlog
---

> [!info] Conexões
> Faz parte de [[03-requisitos/index]]. Nasce da [[02-visao-do-produto/index|Visão do Produto]]. Qualidade e restrições em [[03-requisitos/requisitos-nao-funcionais]]. Cadeia história → origem em [[03-requisitos/rastreabilidade]].

## Como ler

- **Formato:** *Como [persona], quero [ação], para [benefício].*
- **Prioridade (MoSCoW):** **Must** (essencial), **Should** (importante), **Could** (desejável).
- **Fase:** 0 a 3, conforme [[02-visao-do-produto/escopo-e-fases|plano de implantação]].
- **Origem:** documento de onde a história foi derivada. Histórias marcadas com *(proposta do grupo)* **não constam literalmente nas fontes** e devem ser validadas.

### Personas

| Persona | Descrição |
| --- | --- |
| **Desenvolvedor** | Integrante de uma das três equipes que usa a IA no dia a dia |
| **Líder / diretoria** | Acompanha custo, uso e resultado |
| **Administrador de infraestrutura** | Mantém servidor, rede, contas e backup |
| **Responsável por segurança** | Define e confere política de acesso e dados |
| **Avaliador (testes)** | Mede qualidade, desempenho e custo no piloto |

## Panorama dos épicos

| Épico | Tema | Histórias | Fase principal |
| --- | --- | --- | --- |
| E1 | Acesso e autenticação | US-01 a US-03 | 1 e 2 |
| E2 | Chat com a IA | US-04 a US-09 | 1 |
| E3 | Fila de atendimento | US-10 a US-13, US-44 | 1 |
| E4 | Plataforma e infraestrutura | US-14 a US-18 | 0 |
| E5 | Segurança e privacidade | US-19 a US-22, US-36 a US-43 | 0 a 2 |
| E6 | Operação e monitoramento | US-23 a US-25 | 0 e 1 |
| E7 | Medição e validação do piloto | US-26 a US-30 | 1 a 3 |
| E8 | Evolução | US-31 a US-35 | 2 e 3 |

---

## Épico E1: Acesso e autenticação

#### US-01: Entrar com conta individual
> Como **desenvolvedor**, quero entrar com minha conta pelo navegador, para usar a IA sem instalar nada.

- **Critérios:** só integrantes das três equipes entram; o acesso é por HTTPS na porta 443 do gateway; não há acesso anônimo; cada conta é individual.
- **Prioridade:** Must · **Fase:** 1 · **Origem:** [[atividades/atividade-3-infraestrutura-e-distribuicao#Regras de acesso|Atividade 3]]

#### US-02: Acessar de fora pela VPN
> Como **desenvolvedor**, quero acessar o mesmo endereço pela VPN da empresa, para trabalhar remotamente sem expor o servidor.

- **Critérios:** o endereço é o mesmo da rede interna; sem VPN, o servidor não responde; o servidor não fica exposto na internet.
- **Prioridade:** Should · **Fase:** 2 · **Origem:** [[atividades/atividade-3-infraestrutura-e-distribuicao#Canais|Atividade 3]]

#### US-03: Revogar conta no desligamento
> Como **administrador**, quero revogar o acesso de quem sai da empresa, para que nenhuma conta antiga continue válida.

- **Critérios:** existe procedimento escrito; após a revogação a pessoa não consegue entrar no gateway nem por SSH; a ação fica registrada.
- **Prioridade:** Must · **Fase:** 1 · **Origem:** [[atividades/atividade-1-servidor-padrao|Atividade 1]] (etapa 8) e pré-pitch

---

## Épico E2: Chat com a IA

#### US-04: Perguntar sobre programação
> Como **desenvolvedor**, quero fazer uma pergunta técnica em linguagem natural, para obter orientação rápida.

- **Critérios:** a pergunta é enviada pela interface; a resposta aparece na mesma tela; há indicação de carregamento enquanto aguarda.
- **Prioridade:** Must · **Fase:** 1 · **Origem:** [[contexto/proposta-e-delimitacao#Foco do protótipo|foco do protótipo]]

#### US-05: Pedir explicação de um trecho de código
> Como **desenvolvedor**, quero colar um trecho de código e receber uma explicação, para entender código que não escrevi.

- **Critérios:** aceita trechos de código colados; a explicação é compreensível e correspondente ao trecho; respeita o limite de contexto de 8.192 tokens, com aviso se o texto for maior.
- **Prioridade:** Must · **Fase:** 1 · **Origem:** [[atividades/atividade-2-custos-e-instalacao-llm|Atividade 2]]

#### US-06: Receber sugestão de correção de erro
> Como **desenvolvedor**, quero enviar um erro ou um código com defeito e receber uma sugestão de correção, para resolver o problema com mais rapidez.

- **Critérios:** a sugestão vem com explicação; a sugestão pode ser verificada pelo avaliador e o resultado registrado (aprovada ou não).
- **Prioridade:** Must · **Fase:** 1 · **Origem:** [[contexto/proposta-e-delimitacao#Foco do protótipo|foco do protótipo]]

#### US-07: Gerar testes para um código
> Como **desenvolvedor**, quero pedir testes para uma função, para aumentar a cobertura sem escrever tudo à mão.

- **Critérios:** o teste retornado é executável no ambiente do desenvolvedor, ou aponta o que falta para isso; a qualidade entra na avaliação do piloto.
- **Prioridade:** Should · **Fase:** 1 · **Origem:** [[atividades/atividade-2-custos-e-instalacao-llm|Atividade 2]]

#### US-08: Ver código de forma legível
> Como **desenvolvedor**, quero ver trechos de código formatados e poder copiá-los, para reaproveitar a resposta sem retrabalho.

- **Critérios:** blocos de código têm fonte monoespaçada e realce; há botão de copiar; respostas longas rolam sem quebrar o layout.
- **Prioridade:** Should · **Fase:** 1 · **Origem:** papel de frontend em [[equipe/papeis-e-atividades]]

#### US-09: Avaliar se a resposta foi útil
> Como **avaliador**, quero que o desenvolvedor marque cada resposta como útil ou não útil, para medir a qualidade com dados.

- **Critérios:** cada resposta tem a marcação; o voto é gravado ligado ao pedido, **sem guardar o conteúdo**; é possível calcular o percentual de respostas úteis por período.
- **Prioridade:** Must · **Fase:** 1 · **Origem:** [[atividades/atividade-3-infraestrutura-e-distribuicao#Premissas a validar no piloto|premissa de qualidade ≥ 70%]]

---

## Épico E3: Fila de atendimento

#### US-10: Acompanhar o estado do pedido
> Como **desenvolvedor**, quero ver se meu pedido está na fila, em processamento ou concluído, para saber se devo esperar.

- **Critérios:** os três estados **Na fila**, **Em processamento** e **Concluído** aparecem na tela; o estado atualiza sem recarregar a página.
- **Prioridade:** Must · **Fase:** 1 · **Origem:** [[atividades/atividade-2-custos-e-instalacao-llm|Atividade 2]]

#### US-11: Manter um pedido aberto por usuário
> Como **administrador**, quero limitar cada usuário a um pedido aberto, para que ninguém monopolize a GPU.

- **Critérios:** um segundo pedido enquanto há um aberto é recusado com mensagem clara; com 15 pedidos simultâneos, um é atendido e 14 aguardam.
- **Prioridade:** Must · **Fase:** 1 · **Origem:** [[atividades/atividade-2-custos-e-instalacao-llm|Atividade 2]] e [[atividades/atividade-3-infraestrutura-e-distribuicao#Regras de acesso|Atividade 3]]

#### US-12: Ver posição e tempo estimado na fila *(proposta do grupo)*
> Como **desenvolvedor**, quero saber minha posição na fila e uma estimativa de espera, para decidir se aguardo ou volto depois.

- **Critérios:** a posição é exibida; a estimativa usa o tempo médio recente das respostas e é rotulada como estimativa.
- **Prioridade:** Could · **Fase:** 2 · **Origem:** tabela de espera da [[atividades/atividade-3-infraestrutura-e-distribuicao#Tempo de espera (estimativa; medir no piloto)|Atividade 3]]

#### US-13: Receber mensagem clara em erro ou indisponibilidade
> Como **desenvolvedor**, quero uma mensagem compreensível quando a IA estiver indisponível ou o pedido falhar, para saber o que fazer.

- **Critérios:** há **prazo máximo** de espera e de geração, com aviso de falha ou indisponibilidade; erros de conexão, tempo esgotado e indisponibilidade têm mensagens distintas; a mensagem indica a alternativa (tentar de novo ou usar a ferramenta externa de contingência); o pedido falho libera a vaga do usuário.
- **Prioridade:** Must · **Fase:** 1 · **Origem:** papéis de backend e frontend em [[equipe/papeis-e-atividades]]

#### US-44: Cancelar um pedido enquanto aguarda na fila
> Como **desenvolvedor**, quero cancelar meu pedido enquanto ele está na fila, para liberar minha vaga se eu não precisar mais da resposta.

- **Critérios:** o botão de cancelar aparece enquanto o estado é **Na fila**; o cancelamento libera a vaga e o usuário pode abrir novo pedido; pedido **Em processamento** não pode ser cancelado, ou o comportamento é explicitado.
- **Prioridade:** Should · **Fase:** 1 · **Origem:** [[Anexos/index|Proposta com fila (29/09/2026)]]

---

## Épico E4: Plataforma e infraestrutura

#### US-14: Ter servidor seguro com GPU em container
> Como **administrador**, quero um servidor Ubuntu com a GPU acessível em containers, para que a equipe de LLM instale a IA sem mexer no sistema.

- **Critérios:** `nvidia-smi` funciona dentro de um container, sem sudo, executado por integrante da equipe de LLM; `/srv/ia` é gravável pelo grupo `equipe-llm`, em disco de dados NVMe de pelo menos 500 GB (**compra a definir com o cliente**, se não houver); versões de Ubuntu, kernel, driver, CUDA, Docker e toolkit conferidas.
- **Prioridade:** Must · **Fase:** 0 · **Origem:** [[atividades/atividade-1-servidor-padrao#Checklist de entrega à equipe de LLM|checklist da Atividade 1]]

#### US-15: Aprovar o servidor em teste de 24 horas
> Como **administrador**, quero comprovar que o servidor aguenta carga contínua, para não descobrir falhas em produção.

- **Critérios:** 24 h combinadas de CPU, memória e GPU sem reinício, travamento ou erro; gpu-burn sem erros Xid; temperatura estável; volta sozinho após reinício e queda de energia simulada.
- **Prioridade:** Must · **Fase:** 0 · **Origem:** [[atividades/atividade-1-servidor-padrao#Testes e critérios de aprovação|Atividade 1]]

#### US-16: Executar o modelo com Ollama em container
> Como **administrador**, quero o Ollama em container com o Qwen2.5-Coder 14B, uma geração por vez, para operar de forma isolada e previsível.

- **Critérios:** modelo carregado em `/srv/ia`; `OLLAMA_NUM_PARALLEL=1`; uso de VRAM medido e próximo de 12,9 GiB com contexto 8.192; reinício automático do container.
- **Prioridade:** Must · **Fase:** 0 · **Origem:** [[atividades/atividade-1-servidor-padrao#Integração com a Atividade 2|Atividade 1]] e [[atividades/atividade-2-custos-e-instalacao-llm|2]]

#### US-17: Ter backup com restauração testada
> Como **administrador**, quero backup do ambiente e restauração comprovada, para recuperar o servidor após uma falha.

- **Critérios:** backup com restic executado e mantido **em local separado do servidor principal, com acesso restrito**; restauração testada com sucesso (e repetida periodicamente); reinstalação segue o roteiro documentado.
- **Prioridade:** Must · **Fase:** 0 · **Origem:** [[atividades/atividade-1-servidor-padrao|Atividade 1]] (etapa 8)

#### US-18: Proteger contra queda de energia
> Como **administrador**, quero nobreak com desligamento seguro, para evitar corromper dados.

- **Critérios:** nobreak senoidal de 1.200 W reais (ou o que a medição indicar); desligamento seguro via NUT testado; religamento automático testado. **A compra do nobreak será definida com o cliente.**
- **Prioridade:** Should · **Fase:** 0 · **Origem:** [[atividades/atividade-3-infraestrutura-e-distribuicao#Hardware|Atividade 3]] *(compra a definir com o cliente)*

---

## Épico E5: Segurança e privacidade

#### US-19: Não guardar o conteúdo do código
> Como **responsável por segurança**, quero que gateway e aplicação não gravem o corpo das requisições, para que o código dos clientes não fique armazenado.

- **Critérios:** inspeção dos logs mostra metadados, mas nenhum trecho de código ou resposta; vale também para os votos de utilidade (US-09).
- **Prioridade:** Must · **Fase:** 1 · **Origem:** [[atividades/atividade-3-infraestrutura-e-distribuicao#Regras de acesso|Atividade 3]]; política final em [[atividades/atividade-5-seguranca]]

#### US-20: Registrar quem pediu, quando e quanto tempo levou
> Como **líder**, quero um registro de uso sem conteúdo, para medir o desempenho e acompanhar o piloto.

- **Critérios:** cada pedido gera usuário, horário e duração; os dados alimentam as medições do Épico E7.
- **Prioridade:** Must · **Fase:** 1 · **Origem:** [[atividades/atividade-3-infraestrutura-e-distribuicao#Regras de acesso|Atividade 3]]

#### US-21: Manter o Ollama inacessível pela rede
> Como **responsável por segurança**, quero que a API do Ollama aceite apenas conexões locais, para que ninguém a use sem autenticação.

- **Critérios:** porta 11434 publicada só em `127.0.0.1`; teste de outra máquina da rede não consegue conectar; o único caminho para o modelo é o gateway.
- **Prioridade:** Must · **Fase:** 0 · **Origem:** [[atividades/atividade-1-servidor-padrao#Segurança aplicada no servidor|Atividade 1]]

#### US-22: Restringir o acesso administrativo ao servidor
> Como **administrador**, quero SSH só por chave, firewall fechado por padrão e bloqueio de tentativas repetidas, para reduzir o risco de invasão.

- **Critérios:** login por senha desabilitado; root bloqueado; só o grupo `ssh-users` entra; ufw nega por padrão e libera SSH só na rede interna; fail2ban bloqueia o IP por 1 h após 5 erros; **contas administrativas separadas das contas comuns**; mudanças relevantes de configuração documentadas.
- **Prioridade:** Must · **Fase:** 0 · **Origem:** [[atividades/atividade-1-servidor-padrao#Segurança aplicada no servidor|Atividade 1]]

#### US-36: Proteger as sessões e as tentativas de login
> Como **responsável por segurança**, quero sessões que expirem e bloqueio de tentativas repetidas, para reduzir o risco de uso indevido de uma conta.

- **Critérios:** a sessão expira após inatividade (prazo a definir); após N tentativas falhas o acesso é temporariamente bloqueado; o bloqueio gera registro.
- **Prioridade:** Must · **Fase:** 1 · **Origem:** [[atividades/atividade-5-seguranca|Atividade 5]], seção 1

#### US-37: Controlar o acesso por equipe e por projeto
> Como **responsável por segurança**, quero perfis por equipe e, quando necessário, por projeto, para aplicar o menor privilégio.

- **Critérios:** cada usuário pertence a uma equipe; recursos de projeto restritos só aparecem a quem participa; mudança de função altera o acesso de imediato.
- **Prioridade:** Should · **Fase:** 2 · **Origem:** [[atividades/atividade-5-seguranca|Atividade 5]], seção 1

#### US-38: Auditar acessos e falhas
> Como **responsável por segurança**, quero registro de login e logout, de erros e de tentativas de acesso indevido, para investigar incidentes sem guardar o código.

- **Critérios:** eventos de login e logout, usuário e equipe, horário, quantidade de solicitações, tempo de processamento e erros são registrados; **tentativa de acesso indevido gera alerta**; o log não contém prompt nem resposta.
- **Prioridade:** Should · **Fase:** 1 · **Origem:** [[atividades/atividade-5-seguranca|Atividade 5]], seção 7

#### US-39: Não registrar segredos em logs
> Como **responsável por segurança**, quero que senhas, tokens e chaves nunca apareçam em logs, para que os registros não vazem credenciais.

- **Critérios:** inspeção dos logs do gateway, da aplicação e do servidor não encontra segredos; a configuração de log exclui cabeçalhos de autorização.
- **Prioridade:** Must · **Fase:** 1 · **Origem:** [[atividades/atividade-5-seguranca|Atividade 5]], seções 4 e 11

#### US-40: Detectar e mascarar dados sensíveis antes do processamento
> Como **responsável por segurança**, quero que o Hub identifique credenciais, chaves, dados pessoais e strings de conexão no texto enviado, para alertar, mascarar ou bloquear antes de chegar ao modelo.

- **Critérios:** categorias e ações conforme a tabela de DLP da Atividade 5; o usuário é avisado do que foi mascarado ou bloqueado; falsos positivos podem ser revisados.
- **Prioridade:** Should · **Fase:** 2 · **Origem:** [[atividades/atividade-5-seguranca|Atividade 5]], seção 5 (evolução)

#### US-41: Reduzir o risco de prompt injection
> Como **responsável por segurança**, quero separar as instruções do sistema do conteúdo do usuário e revisar as respostas antes de aplicá-las, para que o texto enviado não altere as regras do sistema.

- **Critérios:** instruções do sistema, regras de segurança, solicitação e código ficam em partes separadas do pedido; o modelo não tem acesso a arquivos ou sistemas internos; nenhuma alteração de código é aplicada automaticamente; comportamentos anômalos são monitorados.
- **Prioridade:** Should · **Fase:** 1 · **Origem:** [[atividades/atividade-5-seguranca|Atividade 5]], seção 6

#### US-42: Definir retenção e restringir o acesso aos registros
> Como **responsável por segurança**, quero um prazo de retenção e acesso restrito aos logs e históricos, para não acumular dados além do necessário.

- **Critérios:** prazo de retenção definido e aprovado; só pessoas autorizadas leem logs e históricos; descarte automático após o prazo.
- **Prioridade:** Should · **Fase:** 1 · **Origem:** [[atividades/atividade-5-seguranca|Atividade 5]], seção 4 *(prazo em aberto)*

#### US-43: Publicar a política de uso da IA
> Como **responsável por segurança**, quero uma política clara do que pode ser enviado à IA, para que os desenvolvedores saibam o que é permitido, principalmente em projetos de bancos.

- **Critérios:** política escrita e divulgada às três equipes; lista de exemplos do que não enviar (segredos, dados pessoais, dados de clientes específicos); aceite registrado de cada usuário antes do primeiro acesso.
- **Prioridade:** Must · **Fase:** 1 · **Origem:** [[atividades/atividade-5-seguranca|Atividade 5]], seção 4 *(proposta do grupo quanto ao aceite)*

---

## Épico E6: Operação e monitoramento

#### US-23: Monitorar o servidor e receber alertas
> Como **administrador**, quero métricas de host e GPU com alertas, para agir antes que o serviço pare.

- **Critérios:** métricas de CPU, RAM, disco e GPU; alerta de temperatura acima de 85 °C; alerta quando o serviço cai; alertas chegam à infraestrutura e aos desenvolvedores.
- **Prioridade:** Must · **Fase:** 0 · **Origem:** [[atividades/atividade-1-servidor-padrao|Atividade 1]] (etapa 8) e [[atividades/atividade-3-infraestrutura-e-distribuicao#Continuidade|Continuidade]]

#### US-24: Manter contingência com ferramentas externas
> Como **desenvolvedor**, quero continuar usando a ferramenta externa se o servidor parar, para não perder produtividade.

- **Critérios:** ferramentas externas permanecem disponíveis durante o piloto; o procedimento de contingência está documentado; uma parada gera alerta automático.
- **Prioridade:** Must · **Fase:** 1 · **Origem:** [[atividades/atividade-3-infraestrutura-e-distribuicao#Continuidade|Atividade 3]]

#### US-25: Atualizar o sistema sem quebrar driver nem Docker
> Como **administrador**, quero atualizações automáticas de segurança que preservem driver e Docker, para não derrubar a GPU sem aviso.

- **Critérios:** atualizações diárias ativas; driver NVIDIA e Docker com versão fixada; `dkms status` conferido antes de reinícios.
- **Prioridade:** Should · **Fase:** 0 · **Origem:** [[atividades/atividade-1-servidor-padrao#Riscos principais|riscos da Atividade 1]]

---

## Épico E7: Medição e validação do piloto

#### US-26: Medir tempo de resposta e espera
> Como **avaliador**, quero medir a duração dos pedidos e a espera na fila, para verificar se atendem ao critério.

- **Critérios:** espera ≤ 30 s em 95% dos pedidos; tempo médio de resposta comparado ao alerta de ≈ 12 s; resultados em uso normal e em pico.
- **Prioridade:** Must · **Fase:** 1 · **Origem:** [[atividades/atividade-3-infraestrutura-e-distribuicao#Implantação em fases|Atividade 3]]

#### US-27: Medir VRAM e capacidade simultânea
> Como **avaliador**, quero medir a memória de vídeo com 1, 2 e 4 gerações, para confirmar quantas cabem na GPU.

- **Critérios:** `nvidia-smi` registrado em cada configuração; comparação com 12,9 / 14,4 / 17,4 GiB estimados; indicação do ponto em que o desempenho cai.
- **Prioridade:** Must · **Fase:** 1 · **Origem:** [[atividades/atividade-3-infraestrutura-e-distribuicao#Capacidade|Atividade 3]]

#### US-28: Avaliar a qualidade das respostas
> Como **avaliador**, quero um conjunto fixo de tarefas de programação avaliadas, para comprovar se as respostas ajudam.

- **Critérios:** conjunto de tarefas definido antes do teste; sugestões de código executadas e o resultado registrado; ≥ 70% de respostas úteis; lacunas em relação às ferramentas atuais listadas.
- **Prioridade:** Must · **Fase:** 1 · **Origem:** [[referencias/criterios-de-avaliacao]]

#### US-29: Medir a disponibilidade
> Como **líder**, quero acompanhar quanto tempo o serviço fica no ar, para decidir com segurança.

- **Critérios:** disponibilidade ≥ 98% no horário comercial, medida pelo monitoramento, com 15 a 18 pessoas.
- **Prioridade:** Should · **Fase:** 2 · **Origem:** [[atividades/atividade-3-infraestrutura-e-distribuicao#Premissas a validar no piloto|Atividade 3]]

#### US-30: Consolidar custo real e decidir (local, híbrido ou inviável)
> Como **líder**, quero o custo real da operação comparado ao gasto atual, para decidir com números.

- **Critérios:** relatório de uso e custo com energia, manutenção, administração e ferramentas externas remanescentes; recomendação entre local, híbrido e inviável; sem prometer economia não demonstrada.
- **Prioridade:** Must · **Fase:** 3 · **Origem:** [[02-visao-do-produto/analise-economica]]

---

## Épico E8: Evolução

#### US-31: Ajustar as gerações simultâneas com base em medições
> Como **administrador**, quero aumentar as gerações simultâneas se os testes permitirem, para reduzir a espera no pico.

- **Critérios:** alvo de 4 gerações com contexto de 8.192 tokens; só avança se US-26 e US-27 aprovarem; com contexto de 16.384, a capacidade é reavaliada.
- **Prioridade:** Should · **Fase:** 2 · **Origem:** [[atividades/atividade-3-infraestrutura-e-distribuicao#Capacidade|Atividade 3]]

#### US-32: Usar a IA pela IDE (somente chat)
> Como **desenvolvedor**, quero usar a IA dentro do VS Code ou JetBrains, para não sair do editor.

- **Critérios:** extensão (ex.: Continue) usando a API compatível com OpenAI, **pelo gateway**, com token individual; sem autocompletar; mesmas regras de fila e limite.
- **Prioridade:** Could · **Fase:** 3 · **Origem:** [[atividades/atividade-3-infraestrutura-e-distribuicao#Canais|Atividade 3]]

#### US-33: Rotear demandas complexas e sem sigilo para ferramentas externas
> Como **líder**, quero que demandas complexas sem dado sensível possam usar APIs externas, para manter qualidade onde o modelo local é fraco.

- **Critérios:** existe regra escrita do que é sensível; dado sensível nunca sai; o roteamento é registrado.
- **Prioridade:** Could · **Fase:** além da 3 · **Origem:** Fase 2 do [[02-visao-do-produto/escopo-e-fases|pré-pitch]]; depende da [[atividades/atividade-5-seguranca|Atividade 5]]

#### US-34: Ver cotas e métricas por equipe e por projeto
> Como **líder**, quero um painel de uso por equipe e por projeto, para ter visibilidade e controle.

- **Critérios:** pedidos por equipe e por projeto; cotas configuráveis; sem exibir conteúdo.
- **Prioridade:** Could · **Fase:** além da 3 · **Origem:** Fase 2 do [[02-visao-do-produto/escopo-e-fases|pré-pitch]]

#### US-35: Indexar o acervo técnico de 20 anos
> Como **desenvolvedor**, quero que a IA sugira código no padrão da empresa, para reaproveitar soluções históricas.

- **Critérios:** acervo indexado só com autorização; respeita sigilo contratual dos clientes; sugestões indicam a origem.
- **Prioridade:** Could · **Fase:** além da 3 · **Origem:** Fase 2 do [[02-visao-do-produto/escopo-e-fases|pré-pitch]]
