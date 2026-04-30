# KnoweldgeGraphTicketIT

# Análise de Arquiteturas Multi-Agentes e LLMs aplicadas à Automação e Suporte

## Membros do Grupo
- Larissa Kelmer
- Marília Costa Muniz
- Samuel Amico

## Descrição do Projeto
Este projeto consiste em um estudo de caso prático focado na extração e estruturação de conhecimento a partir de literatura científica utilizando ferramentas de análise de dados (EdgeQuake e Graphify). O objetivo é investigar como soluções baseadas em Large Language Models (LLMs) e Sistemas Multi-Agentes estão sendo aplicadas para resolver problemas complexos na automação de processos de suporte e gestão.

## Tema Escolhido
O estudo de caso vincula-se diretamente aos seguintes temas da disciplina:
- Knowledge Graph
- Agents / Multi-Agents
- LLM / SLM

## O Problema
**O que está sendo resolvido?** A dificuldade de mapear, relacionar e extrair conhecimento técnico estruturado a partir de múltiplos artigos científicos extensos que propõem inovações de Inteligência Artificial em ambientes operacionais.

**Por que isso é relevante?** A aplicação de ferramentas de extração permite transformar um grande volume de texto não estruturado em insights claros e grafos de conhecimento, facilitando o entendimento de como arquiteturas complexas (como RAG e protocolos Multi-Agentes) interagem para resolver problemas da vida real de forma automatizada.

## Abordagem
Neste trabalho, as ferramentas Graphify e EdgeQuake foram utilizadas como soluções investigativas e meios para extrair valor da base de dados, e não como um fim em si mesmas. Inserimos o corpus de artigos científicos nas ferramentas para processamento lógico e geração de conexões de conhecimento técnico, promovendo uma análise comparativa:
- **Graphify:** Utilizado para uma extração profunda e inferência semântica ("Bottom-Up").
- **EdgeQuake:** Utilizado para um mapeamento taxonômico e direto ("Top-Down").

## Base de Dados (Fontes)
Foram utilizados dados realistas baseados nos seguintes artigos científicos disponibilizados:
1. **STELLAR:** Arquitetura estruturada, confiável e explicável baseada em Grafos Acíclicos Direcionados (DAG) e liderada por LLMs para suporte ao cliente.
2. **Smart Serve:** Sistema de tickets impulsionado por IA para redefinir o suporte ao cliente utilizando modelos como o Gemini.
3. **TickIt:** Framework baseado em grandes modelos de linguagem focado no escalonamento e roteamento automatizado de tickets.
4. **LLM Agents for Smart City Management:** Uso de sistemas multi-agentes para suportar a tomada de decisões na gestão urbana inteligente.
5. **LLM-Based Multi-Agent Architecture for Transport Network Automation:** Arquitetura multi-agente utilizando os protocolos MCP (Model Context Protocol) e A2A (Agent-to-Agent) para automação de redes de transporte.
6. **AIMT Agent:** Sistema de suporte acadêmico conversacional integrado ao Moodle.

## Evidências e Insights
Abaixo estão exemplos de insights técnicos extraídos dos textos através da análise automatizada:
- **Identificação de "God Nodes" (Graphify):** A análise de redes revelou que "Large language models" e "Multi-agent systems" orbitam como os nós mais densos da literatura. Visualmente, isso comprova que os LLMs estão sendo tratados como motores centrais (hubs), enquanto os agentes são ramificações de implementação específicas.
- **Inferência Semântica:** A ferramenta Graphify não apenas extraiu dados diretos (68% das relações), mas inferiu conexões lógicas de alto nível (29%), como a aresta inferida `"Large language models" --enable--> "Multi-agent systems"`.
- **Dinâmica de Tickets:** Identificou-se que sistemas como o TickIt realizam o escalonamento automatizado dinâmico explorando relações entre tickets similares e atualizando o estado dos chamados ao longo da conversa.
- **Protocolos de Agentes:** Soluções Multi-Agentes demonstram vantagens sobre agentes únicos ao dividir tarefas complexas, utilizando protocolos como MCP e A2A para comunicação e delegação padronizada entre diferentes frameworks.
- **RAG em Smart Cities:** Na gestão urbana, a tecnologia RAG combinada com múltiplos agentes LLM eleva a precisão das respostas, acessando bancos de documentos e regulações locais para fundamentar tomadas de decisão.

## Limitações e Trade-offs
- **O que não funcionou:** A extração profunda via Graphify sofreu com perda de contexto contínuo em alguns momentos, gerando 6 nós completamente isolados (ex: `Explainable LLM-led architecture`). Além disso, o modelo teve dificuldade em resolver certas nuances semânticas, classificando como "Ambígua" a diferença entre automação de tickets e escalação humana. O EdgeQuake, por sua vez, falhou em gerar cruzamentos entre os conceitos, limitando-se a ligar o artigo à sua palavra-chave.
- **Trade-offs da Abordagem:** Existe um trade-off claro entre *profundidade e ruído*. O Graphify é excelente para descobrir conexões ocultas e gerar clusters de comunidades (como separar as arquiteturas MCP das arquiteturas de Customer Support), mas gera ruído analítico. O EdgeQuake gera um grafo perfeitamente limpo, restrito a uma taxonomia direta, porém superficial e que exige validação manual para identificar como as tecnologias convergem.
- **Melhorias Futuras:** A adoção de ferramentas de extração exige uma padronização de granularidade. Uma melhoria arquitetural importante em projetos futuros seria a implementação de uma camada intermediária de *Reasoning* (um prompt de revisão acoplado via LangChain/LangGraph, por exemplo) antes da consolidação do grafo, com o objetivo de fundir sinônimos técnicos e forçar o modelo a justificar as arestas ambíguas.

## Estrutura do Repositório
Conforme exigido nas diretrizes para submissão, este repositório contém todos os artefatos gerados ao longo do trabalho:
- `/slides`: Apresentação preparada para os 15 minutos em sala de aula.
- `/imagens`: Capturas de tela das análises e redes geradas no EdgeQuake e Graphify.
- `/dados`: Referências e artigos científicos (PDFs/Links) utilizados no processamento.
- `/resultados`: Exportações de arquivos de análises (`.json` e `.md`) e outputs produzidos pelas ferramentas.
