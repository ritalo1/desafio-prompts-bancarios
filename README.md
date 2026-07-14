# desafio-prompts-bancarios
 Tarefa para o Bootcamp Bradesco DIO.

# Desafio Criativo: Extraindo Insights de Feedbacks Bancários com IA.

 Este repositório contém a resolução do Desafio Criativo proposto pela DIO (Digital Innovation One). O objetivo é estruturar um prompt de alta performance para orientar uma Inteligência Artificial a analisar feedbacks de clientes de canais digitais bancários, respeitando as boas práticas de análise de dados, negócios e segurança (LGPD).

---

# Estrutura do Prompt Desenvolvido

 O prompt foi construído seguindo três pilares essenciais: **Intenção Clara**, **Contexto com Restrições (LGPD)** e **Instruções de Formatação de Saída**.

# O Prompt Final
```text
Atue como Analista Sênior de Dados e Experiência do Cliente (CX) em uma instituição bancária.

Sua tarefa é analisar feedbacks de clientes sobre canais digitais (aplicativo mobile, Pix, login/segurança e transição para o atendimento humano) para identificar as principais dores de usabilidade, falhas operacionais e o sentimento dos usuários.

Contexto: O resultado desta análise será consumido pela equipe de Operações e Experiência do Cliente (CX). O objetivo é apoiar a tomada de decisão estratégica na priorização de correções de bugs (hotfixes) no aplicativo e na melhoria dos fluxos de atendimento humano e digital.

Dados disponíveis: Você receberá uma base contendo os seguintes campos por registro: [ID_Feedback], [Data_Registro], [Canal_Origem] (ex: Play Store, App Store, Reclame Aqui, SAC), [Texto_Feedback_Bruto] e [Dispositivo_Cliente] (iOS/Android).

Instruções de análise:
1. Classifique cada feedback de acordo com os seguintes critérios:
   - Categoria do Problema: Usabilidade, Erro Técnico, Falha Operacional ou Qualidade do Atendimento.
   - Nível de Urgência: Alto (impede movimentação ou acesso), Médio (causa lentidão/desvio de fluxo) ou Baixo (dúvidas ou sugestões).
   - Sentimento Predominante: Frustração, Raiva, Confusão ou Neutro.
2. Identifique padrões recorrentes nos textos e isole as principais dores dos clientes.
3. Sugira ações práticas e imediatas (quick wins) para mitigar os problemas encontrados.

Formato da resposta:
- Resumo Executivo: Um parágrafo direto de até 5 linhas com o diagnóstico geral dos feedbacks.
- Tabela de Análise: Contendo as colunas [Tema/Categoria] | [Nível de Urgência] | [Exemplo de Fala Anonimizada] | [Impacto no Negócio] | [Ação Corretiva Recomendada].
- Plano de Ação Rápido: Lista com as 3 principais prioridades que o time de tecnologia e atendimento deve focar imediatamente.

Restrições e Cuidados de Segurança:
- Conformidade LGPD: Omitir ou mascarar obrigatoriamente qualquer dado pessoal identificável (nomes, CPFs, e-mails, telefones ou números de conta) usando marcações como [NOME OCULTADO] ou [CONTA OCULTADA].
- Fidelidade Absoluta: Trabalhe estritamente com as informações fornecidas. Não invente números, causas de falhas de infraestrutura não mencionadas ou conclusões sem evidências nos textos.
- Tom de Comunicação: Use uma linguagem corporativa limpa, direta, sem jargões desnecessários e totalmente focada em tomadores de decisão (estilo Executive Summary).

```

## Demonstração de Execução (Caso de Teste)

 Para validar a eficácia do prompt, foi realizada uma simulação utilizando uma base de dados fictícia contendo cenários comuns do dia a dia bancário e dados sensíveis que precisavam ser tratados.

### 📊 Input de Teste (Dados Brutos)

* **[ID_001]** | Play Store | *"Fui tentar fazer um Pix de R$150 para minha mãe, a Sra. Maria Souza, e o app fechou sozinho. Tentei três vezes no meu Samsung S23 e nada. Se eu não conseguir pagar ela hoje pelo CPF [CPF_OCULTADO_NA_ORIGEM], vou ter problemas. Palhaçada!"*
  
* **[ID_002]** | SAC | *"Olá, meu nome é Carlos Eduardo e minha conta é 44321-9. Quero saber como faço para cadastrar a chave Pix de celular, não achei de jeito nenhum esse botão no novo menu. O design antigo era mais fácil."*
  
* **[ID_003]** | Reclame Aqui | *"O chat de vocês é horrível. Fiquei 40 minutos falando com aquele robô inútil tentando contestar uma compra que não fiz no cartão. Quando finalmente disse que ia me passar para um humano, a conexão caiu e tive que começar tudo do zero. Um lixo de atendimento!"*

— — — 

# Output Gerado pela IA

#### Resumo Executivo

 "A análise dos feedbacks revela gargalos críticos na estabilidade do aplicativo Android (fechamento inesperado em transações Pix) e na experiência de atendimento no chat híbrido (queda de conexão na transição para o humano). Adicionalmente, mudanças recentes de layout geraram atrito de usabilidade na navegação básica do iOS. A mitigação rápida dessas dores é vital para conter o detrimento da nota nas lojas e reduzir o volume de reclamações em canais públicos de alta visibilidade, como o Reclame Aqui."

#### Tabela de Análise

| Tema/Categoria | Nível de Urgência | Exemplo de Fala Anonimizada | Impacto no Negócio | Ação Corretiva Recomendada |

| --- | --- | --- | --- | --- |

| **Erro Técnico** *(Pix / Crash no App)* | **Alto** | *"Fui tentar fazer um Pix (...) e o app fechou sozinho. Tentei três vezes no meu [DISPOSITIVO]..."* | Impedimento de transação financeira, gerando perda transacional e atrito severo na Play Store. | Acionar time de Dev/QA para analisar logs de crash específicos do modelo de aparelho na versão atual. |


| **Qualidade do Atendimento** *(Transição de Chat)* | **Alto** | *"Fiquei 40 minutos falando com aquele robô (...) quando finalmente disse que ia me passar para um humano, a conexão caiu..."* | Sobrecarga do SAC telefônico por transbordo de canais e abertura de queixas em órgãos de defesa do consumidor. | Revisar a fila de transbordo da API de chat e implementar persistência de histórico de sessão em caso de queda de sinal. |


| **Usabilidade** *(Arquitetura de Informação)* | **Médio** | *"...quero saber como faço para cadastrar a chave Pix (...) não achei de jeito nenhum esse botão no novo menu."* | Aumento de chamados simples no SAC sobre dúvidas de navegação após atualização de interface. | Implementar uma dica visual ativa (tooltip) ou tutorial rápido (walkthrough) na tela inicial do app destacando o novo menu de chaves Pix. |


#### Plano de Ação Rápido (Top 3 Prioridades)

1. **Hotfix de Estabilidade do Pix:** Priorizar a investigação do crash report no fluxo de confirmação de transações no Android.
   
2. **Correção de Persistência no Chat:** Ajustar o sistema de atendimento para que, em caso de queda de conexão na fila humana, a sessão do cliente permaneça ativa por até 5 minutos sem perda do histórico.
   
3. **Reforço de Ajuda na Interface (UX/UI):** Inserir um banner temporário ou seção de "Dúvidas Frequentes" direto na área de Pix para reduzir o atrito causado pelo novo redesign de menus.
