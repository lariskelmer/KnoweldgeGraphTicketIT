# Trabalho 02 - Parte 02: Data-Driven Knowledge Graph com LLM

**Disciplina:** TÓPICOS ESPECIAIS EM PROCESSAMENTO INTELIGENTE DA INFORMAÇÃO – PPGEEC2327 [1]
**Professor:** Ivanovitch Medeiros Dantas da Silva [1]
**Discentes:** Marília Muniz, Larissa Kelmer e Samuel Amico [1]

---

## 1. Definição do Problema
O uso direto e isolado (*standalone*) de Grandes Modelos de Linguagem (LLMs) em sistemas de suporte ao cliente e operações corporativas críticas apresenta falhas graves [2, 3]. Os principais desafios a serem resolvidos incluem:
*   **Confiabilidade e Alucinações:** Geração de respostas plausíveis, porém factualmente incorretas, que comprometem decisões de alto risco [1, 2, 4, 5].
*   **Falta de Explicabilidade:** Dificuldade em fornecer caminhos auditáveis e rastreáveis sobre o raciocínio do modelo [2, 4, 6].
*   **Manutenção de Contexto e Defasagem:** Problemas para preservar o histórico em diálogos longos e a dependência de bases de treinamento desatualizadas (limitadas por um *knowledge cutoff*) [1, 4, 6, 7].
*   **Inconsistência em Tarefas Complexas:** Dificuldade em executar processos de raciocínio lógico que exigem múltiplas etapas ou a integração com sistemas externos de forma determinística [3, 5, 8].

## 2. Abordagem e Metodologia
O objetivo principal deste projeto é investigar como orquestrações avançadas (como Agentes e KGs) superam a limitação temporal dos LLMs, estruturam dados não-estruturados, reduzem alucinações e otimizam sistemas RAG (Geração Aumentada por Recuperação) tradicionais [1, 7]. 

A metodologia da equipe envolveu uma triagem literária de artigos-chave, seleção crítica de três arquiteturas focadas nesse problema, sintonia dos dados extraídos e testes em diferentes ferramentas de RAG para extrair *insights* baseados na análise de grafos e similaridade vetorial [7, 9].

### 2.1 Ferramentas de Análise Utilizadas [9, 10]
*   **EdgeQuake:** Aplicado como RAG sobre o *corpus*, garantindo alta profundidade técnica e rastreabilidade focado na análise técnica detalhada.
*   **Graphify:** Utilizado como RAG sobre grafo, ideal para visualizar a visão estrutural, o mapa do domínio e as conexões entre diferentes conceitos.
*   **NotebookLM:** Usado como referência de RAG com citações, oferecendo altíssima segurança contra alucinações, através de uma ancoragem direta e verificável nos textos.

---

## 3. Análise dos Artigos Selecionados

### 3.1. STELLAR: Arquitetura Guiada por LLM para Suporte Confiável
*   **O que resolve:** Propõe um *blueprint* (modelo) abrangente e previsível para o design de sistemas inteligentes de suporte [11, 12]. 
*   **Como funciona:** Estrutura o sistema como um Grafo Acíclico Direcionado (DAG) com 9 módulos funcionais (como classificador, verificador de conformidade, coletor de feedback) e fluxos rígidos de atendimento, impedindo comportamentos aleatórios [9, 13, 14]. O Módulo 2 utiliza uma estratégia de RAG Híbrida combinada com re-ranqueamento via LLM (HS+R) [15-17].
*   **Evidências de Sucesso:** A arquitetura alcançou 97% de precisão (especificamente 97,5% no Módulo 4) na tarefa crítica de classificação e roteamento de tickets de suporte, comprovando a viabilidade de restringir rigorosamente os LLMs [17, 18].

### 3.2. TickIt: Escalonamento Automatizado de Tickets
*   **O que resolve:** Resolve as deficiências de análises estatísticas antigas, que não compreendiam a natureza real, dinâmica e variada das reclamações e incidentes dos clientes em plataformas de nuvem [17, 19].
*   **Como funciona:** Implementa roteamento multiclasse guiado por tópicos e atua de forma contínua (*online*) durante a conversa [19, 20]. Utiliza técnicas de *Chain of Thought* para raciocínio semântico profundo, compara vetores (*embeddings*) para agrupar e deduplicar incidentes similares e melhora seu próprio modelo via *Supervised Fine-Tuning* (SFT) com feedback humano [20-23].
*   **Evidências de Sucesso:** Alcançou um F1 score de 86,2% no escalonamento e reduziu o *Mean Time to Repair* (MTTR) de incidentes críticos em 39% [20, 24, 25].

### 3.3. LLM Agents for Smart City Management
*   **O que resolve:** Melhora o processo de tomada de decisões estratégicas em gestão urbana, operando fontes de dados heterogêneas e não padronizadas [20, 26, 27].
*   **Como funciona:** Utiliza uma arquitetura multiagente hierárquica dividida em Interface, Orquestração (*Agent-conductor*) e Processamento (com agentes de RAG, chamadas de APIs de serviços da cidade e validação) [28-30].
*   **Evidências de Sucesso:** Conseguiu entre 94% e 99% de precisão no roteamento de consultas aos agentes [28, 31, 32]. A integração RAG + APIs urbanas aumentou a qualidade das respostas (*G-Eval score*) de 0.30–0.38 (modelo *standalone*) para 0.68–0.74, ao mesmo tempo em que reduziu o tempo de execução de dias para horas [31, 33, 34].

---

## 4. Evidências e Insights Gerais Extraídos
Por meio do processamento nas ferramentas (Graphify, EdgeQuake, etc.), constatou-se que as falhas de Modelos *Standalone* (puros) são sistêmicas. Sem acesso a RAG ou ferramentas externas, as LLMs tendem a inventar dados (alucinações) e não oferecem garantia de conformidade ou verificação [35, 36]. 
A aplicação prática revelou que combinar bases vetoriais de documentos (RAG) com o acionamento via APIs (*Tool Calling* / Agentes) e Grafos de Conhecimento resolve significativamente as deficiências semânticas e operacionais [33, 37, 38].

## 5. Limitações e Trade-offs Observados
*   **Custo e Latência (O que poderia ser melhorado):** A adoção de RAG híbrido com LLM *re-ranking* (HS+R), como visto no STELLAR, alcança altíssima precisão (97%), mas aumenta bastante a latência e custo computacional. É necessário um *trade-off* com buscas híbridas sem re-ranqueamento em cenários que exijam resposta imediata [39, 40].
*   **Data-Driven KGs (O que não funciona sozinho):** A transformação dos dados unicamente via *Data-Driven Knowledge Graphs* tem suas limitações. Requer o envolvimento de Especialistas no Domínio (*SME - Subject Matter Experts*) para garantir a curadoria adequada, dependendo de abordagens complementares ou semi-automatizadas para manter os grafos úteis e escaláveis [41, 42].
