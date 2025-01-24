# Documentação do Projeto - **IA para Suporte Help-Desk**

## 1. Criação de Equipe

A equipe de desenvolvimento deste projeto acadêmico é composta pelos seguintes membros:

- **Mairan**: Responsável pelo tratamento dos dados e análise de desempenho dos modelos.
- **Marcus**: Focado na automação dos benchmarks, criação dos scripts para processamento de dados e testes com as IAs.
- **Mateus**: Responsável pela validação das respostas geradas pelas IAs e pela avaliação da precisão das respostas com base nos testes realizados.
- **Max**: Responsavel pela análise da interação dos modelos com os problemas de help-desk.

Este projeto visa criar uma solução automatizada para problemas comuns de help-desk, aproveitando tecnologias de IA de última geração para reduzir o tempo de resposta e melhorar a eficiência no suporte técnico.

## 2. Apresentação de Escopo de Projeto

O **projeto de IA para Suporte Help-Desk** tem como objetivo desenvolver uma inteligência artificial que auxilie na resolução de problemas técnicos simples enfrentados por usuários de TI, como questões relacionadas a sistemas, software e hardware. A IA será capaz de fornecer soluções rápidas através de um sistema de perguntas e respostas, onde as respostas são geradas automaticamente, baseadas em dados e tutoriais previamente alimentados no sistema.

### Objetivos:
- **Desenvolver um chatbot de suporte técnico** baseado em IA para fornecer soluções automatizadas para problemas comuns de help-desk.
- **Testar e comparar diferentes modelos de IA** (QWEN e Llama) para determinar o modelo com o melhor desempenho na geração de respostas precisas e úteis.
- **Automatizar o processo de benchmark** para avaliar o desempenho de cada modelo em termos de precisão e relevância das respostas.

### Metodologia:
- O projeto será conduzido em ciclos de treinamento e avaliação.
- Utilização de modelos pré-treinados (QWEN e Llama) e adaptação dos mesmos para responder a questões específicas de help-desk.
- Implementação de testes automáticos de performance e análise de resultados com base na similaridade semântica entre as respostas geradas pelos modelos e as respostas esperadas.

## 3. Apresentação de Benchmarks Iniciais

Para iniciar a avaliação de desempenho dos modelos, foram realizados testes com 25 perguntas, enviadas para os modelos em workspaces separados para evitar a influência mútua nas respostas. O modelo **Qwen 2.5** acertou 22 das 25 perguntas, mas com alguns problemas, como troca de idiomas (português para mandarim) e uso incorreto de ícones. Já o modelo **Llama 3.1** acertou 23 perguntas, mas tendia a fornecer respostas longas para questões simples.

Em uma segunda rodada de testes, com 100 perguntas, o modelo **Qwen 2.5** obteve uma taxa de acerto de **63,04%**, enquanto o **Llama 3.1** alcançou **59,4%** de acertos.

Esses benchmarks iniciais ajudaram a identificar as limitações e pontos fortes de cada modelo, proporcionando dados valiosos para o desenvolvimento e ajuste do sistema.

## 4. Automação de Processo de Benchmark e Novos Resultados

A automação do processo de benchmark foi implementada no script `Automacao_Ollama.py`, com o objetivo de facilitar a execução de testes repetitivos e a análise de resultados. O script lê as perguntas e respostas esperadas de um arquivo CSV, envia as perguntas para os modelos via terminal, compara as respostas geradas com as esperadas e calcula a similaridade semântica entre elas.

### Estrutura do Projeto

- **`Automacao_Ollama.py`**: Script principal responsável pela automação do benchmark.
- **`dataset.csv`**: Arquivo CSV contendo as perguntas e respostas esperadas para os testes.
- **`resultados_llama3.1.csv`**: Arquivo CSV gerado com os resultados do modelo Llama 3.1.
- **`resultados_qwen2.5.csv`**: Arquivo CSV gerado com os resultados do modelo Qwen 2.5.

### Dependências

- Python 3.6+
- `sentence-transformers`
- `subprocess`

### Passo a Passo

1. **Clonar o Repositório**:
    ```bash
    git clone https://github.com/ZzAlos/HelpDeskIA.git
    cd HelpDeskIA
    ```

2. **Criar e Ativar Ambiente Virtual**:
    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```

3. **Instalar as Dependências**:
    ```bash
    pip install -r requirements.txt
    ```

4. **Rodar o Script de Benchmark**:
    ```bash
    python Automacao_Ollama.py
    ```

5. **Analisar os Resultados**:
    - Os resultados serão salvos nos arquivos `resultados_llama3.1.csv` e `resultados_qwen2.5.csv`.

### Funções Principais

#### [carregar_perguntas(arquivo_csv)]

Carrega as perguntas e respostas esperadas do arquivo CSV para os testes.

#### [enviar_para_ollama_terminal(pergunta, modelo)]

Envia uma pergunta ao modelo via terminal e retorna a resposta gerada.

#### [calcular_similaridade_semantica(resposta_modelo, resposta_esperada)]

Calcula a similaridade semântica entre as respostas geradas e as esperadas usando o modelo de embeddings `sentence-transformers`.

#### [processar_perguntas(arquivo_csv, arquivo_saida, modelo)]

Processa as perguntas, compara as respostas e salva os resultados em um arquivo CSV.

### Resultados dos Testes

A seção a seguir apresenta uma pequena amostra de perguntas realizadas durante os testes com os modelos Llama 3.1 e Qwen 2.5. Essas perguntas estavam relacionadas a problemas comuns de TI e manutenção de computadores. As respostas geradas pelos modelos foram comparadas com as respostas esperadas, e a similaridade entre elas foi calculada, oferecendo uma visão sobre a precisão dos modelos na resolução de questões de suporte técnico. A taxa de similaridade reflete o quão próximas as respostas geradas estão das respostas ideais.

#### Resultados do Modelo Llama 3.1

Abaixo, temos uma pequena amostra de perguntas realizadas com o modelo Llama 3.1 e as respectivas similaridades das respostas:

| Pergunta | Similaridade |
|----------|---------------|
| O que devo fazer se fiz alguma alteração recente no meu computador? | 0.55 |
| Como posso melhorar a segurança do meu Wi-Fi? | 0.58 |
| Quais são os passos para configurar uma VPN? | 0.60 |
| Como posso recuperar arquivos deletados do meu computador? | 0.62 |
| O que devo fazer se meu computador estiver lento? | 0.63 |
| Como posso proteger meu computador contra vírus? | 0.64 |
| Quais são as melhores práticas para criar senhas seguras? | 0.65 |
| Como posso configurar um backup automático dos meus arquivos? | 0.66 |
| O que devo fazer se meu computador não ligar? | 0.67 |
| Como posso limpar meu computador para liberar espaço? | 0.68 |

**Taxa de Acerto do Modelo Llama 3.1**: 62.8%

#### Resultados do Modelo Qwen 2.5

Aqui estão os resultados de uma amostra das perguntas realizadas com o modelo Qwen 2.5:

| Pergunta | Similaridade |
|----------|---------------|
| Como posso melhorar a segurança do meu Wi-Fi? | 0.58 |
| O que devo fazer se meu computador estiver lento? | 0.60 |
| Como posso proteger meus dados pessoais online? | 0.62 |
| Quais são as melhores práticas para criar senhas seguras? | 0.63 |
| Como posso evitar phishing e fraudes online? | 0.64 |
| O que devo fazer se meu computador não ligar? | 0.65 |
| Como posso configurar uma rede doméstica segura? | 0.66 |
| Quais são os sinais de que meu computador pode estar infectado por malware? | 0.67 |
| Como posso fazer backup dos meus dados? | 0.68 |
| O que devo fazer se meu computador estiver superaquecendo? | 0.69 |

**Taxa de Acerto do Modelo Qwen 2.5**: 66.8%

#### Pontos a Melhorar

Embora ambos os modelos apresentem taxas de acerto satisfatórias e tenham sido capazes de gerar respostas precisas na maioria das perguntas, ainda há espaço para melhorias significativas. O modelo **Llama 3.1**, por exemplo, apresentou uma tendência de fornecer respostas mais longas do que o necessário, o que pode afetar a clareza e a eficiência das respostas, especialmente em questões simples. Por outro lado, o modelo **Qwen 2.5** demonstrou problemas como troca inesperada de idiomas e falhas no uso de ícones, o que afetou a consistência das respostas.

Esses pontos negativos ainda precisam ser abordados para garantir uma maior precisão e eficiência nas respostas, especialmente em um contexto de suporte técnico onde a clareza e a precisão são fundamentais para o bom atendimento ao usuário. Com melhorias nesses aspectos, ambos os modelos têm potencial para fornecer respostas ainda mais eficazes e confiáveis.