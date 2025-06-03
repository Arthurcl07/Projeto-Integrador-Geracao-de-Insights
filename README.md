# Projeto Integrador: Geração de Insights a partir de Reclamações do Consumidor.gov.br (2023-2024)

Este repositório contém o trabalho desenvolvido no Projeto Integrador "Geração de Insights", focado na análise de dados de reclamações de consumidores extraídos do site Consumidor.gov.br para os anos de 2023 e 2024. O objetivo principal do projeto foi identificar padrões, tendências e fatores que influenciam a satisfação do consumidor e o desempenho das empresas na resolução de problemas, utilizando técnicas de análise de dados e agrupamento (clustering).

## Estrutura do Repositório

* `README.md`: Este arquivo, apresentando uma visão geral do projeto.
* `notebooks/`: Contém os notebooks Jupyter (`.ipynb`) com o código Python utilizado para a análise exploratória de dados, pré-processamento, análise de cluster e visualização de resultados.
* `graphs/`: Pasta para armazenar os gráficos gerados durante a análise.
* `tables/`: Pasta para armazenar tabelas e dados sumarizados.
* `relatorio_final.pdf`: O relatório final completo do projeto em formato PDF.

## Objetivo do Projeto

Desde a popularização dos canais de atendimento ao consumidor, reclamações registradas têm se tornado uma fonte valiosa de informações sobre a qualidade de produtos e serviços[cite: 3]. Este projeto investiga os elementos que diferenciam empresas com melhor desempenho na resolução de conflitos com clientes, combinando técnicas de análise de dados e geração de linguagem natural[cite: 4]. O objetivo final é extrair recomendações concretas para organizações sobre como aprimorar seu atendimento e aumentar a satisfação do consumidor[cite: 5].

## Dataset

O estudo baseou-se num resumo detalhado do dataset obtido do site Consumidor.gov.br. Foram coletados 1.048.575 registros[cite: 6, 31].

**Período:** 2023–2024 [cite: 7, 32]
**Campos-chave:** Região, UF, Cidade, Sexo, Faixa Etária, Data Finalização, Tempo Resposta, Nome Fantasia, Segmento de Mercado, Área, Assunto Grupo Problema, Como Comprou Contratou, Procurou Empresa, Respondida, Situação, Avaliação Reclamação, Nota do Consumidor[cite: 7, 32].

**Completeness:** O dataset apresenta cobertura de idade de 100% (desde “até 20 anos” à “mais de 70 anos”), país (100%), 44 diferentes segmentos de mercado, e inclui apenas reclamações finalizadas e públicas de 1196 empresas[cite: 8, 33]. Foi observado que os dados são mais esparsos nas primeiras quatro edições[cite: 9, 34].

**Limitações:** Limitações reconhecidas incluem a ausência de dados sobre canal de compras e dados sobre canal de reclamação físico ou online, além de considerar sem distinções as reclamações finalizadas avaliadas e as não avaliadas[cite: 9, 34].

## Análise Exploratória dos Dados (EDA)

A análise quantitativa foi dividida em quatro blocos[cite: 10, 35], e foi fundamental para entender a distribuição e as características do dataset, revelando insights importantes sobre o comportamento das reclamações.

### Principais Achados:

* **Relação entre Sexo e Tipo de Problema:** Em geral, o sexo feminino tende a reclamar mais de Cobrança/Contestação em relação ao sexo masculino[cite: 11, 36]. Já o Sexo masculino tende a reclamar mais do que o feminino sobre Contrato/Oferta e sobre Vício de Qualidade[cite: 12, 37].
* **Média da Nota do Consumidor por Assunto (15 piores):** A pior nota média dada pelos consumidores é referente a agências de turismo, excursões e pacotes de viagem em geral[cite: 13, 38].
* **Empresas com Mais Reclamações:**
    * Hurb - HotelUrbano (40.528 reclamações) [cite: 13, 38]
    * Google (37.180 reclamações) [cite: 13, 38]
    * 123 Milhas (35.686 reclamações) [cite: 13, 38]
    * Vivo (35.672 reclamações) [cite: 13, 38]
    * Claro (32.508 reclamações) [cite: 13, 38]
    * Tim (26.340 reclamações) [cite: 13, 38]
    Juntas essas empresas somam 207914 reclamações, o que representa 19,83% das reclamações[cite: 13, 38].
* **Estados com Mais Reclamações:** São Paulo (SP) lidera com 524.997 reclamações, seguido por Minas Gerais (MG) com 258.356 e Rio de Janeiro (RJ) com 223.817.
* **Setores Mais Reclamados:** Bancos, Financeiras e Administradoras de Cartão (611.906), Operadoras de Telecomunicações (291.034), Transporte Aéreo (151.345), Comércio Eletrônico (148.110), Viagens, Turismo e Hospedagem (147.517), Provedores de Conteúdo e Outros Serviços na Internet (115.937), Energia Elétrica (87.079), Seguros, Capitalização e Previdência (71.114), Empresas de Intermediação de Serviços / Negócios (70.453) e Empresas de Pagamento Eletrônico (87.559).
* **Diferença de Reclamações por Sexo:** Há mais reclamações do sexo masculino (1.278.567) do que do sexo feminino (886.358), com uma pequena parcela "O" (1.349).
* **Correlação Tempo de Resposta vs. Nota do Consumidor:** A correlação entre "Tempo Resposta" e "Nota do Consumidor" é de -0.024535, indicando uma correlação negativa muito fraca.

## Análise de Cluster (K-Means)

A aplicação do algoritmo K-Means, com base no "Gráfico do Cotovelo" que sugeriu 3 clusters como número ideal, permitiu agrupar as reclamações em segmentos com características distintas:

* **Cluster 0:** Média da Nota do Consumidor: 3.523618; Tempo de Resposta Médio: 6.394258. Setores predominantes: Bancos, Financeiras e Administradoras de Cartão (23.5%), Operadoras de Telecomunicações (19.17%). Tipos de Problema predominantes: Cobrança / Contestação (40.74%), Contrato / Oferta (17.62%).
* **Cluster 1:** Média da Nota do Consumidor: 1.088052; Tempo de Resposta Médio: 6.219962. Setores predominantes: Bancos, Financeiras e Administradoras de Cartão (26.6%), Viagens, Turismo e Hospedagem (12.05%). Tipos de Problema predominantes: Cobrança / Contestação (39.59%), Contrato / Oferta (19.79%).
* **Cluster 2:** Média da Nota do Consumidor: 5.000000; Tempo de Resposta Médio: 5.986188. Setores predominantes: Operadoras de Telecomunicações (26.83%), Bancos, Financeiras e Administradoras de Cartão (17.85%). Tipos de Problema predominantes: Cobrança / Contestação (39.54%), Contrato / Oferta (19.5%).

A análise dos clusters reforça que, embora o tempo de resposta seja um fator, a efetividade da resolução do problema e a qualidade do atendimento são cruciais para a satisfação do cliente, especialmente evidente no Cluster 1, que tem baixa nota apesar de tempo de resposta similar aos demais.

## Análise com IA Generativa (Simulação)

Para esta seção, seria necessário um modelo de IA Generativa (ex: Gemini) para analisar o texto das reclamações, identificando padrões de linguagem, palavras-chave frequentes e o sentimento predominante em relação a empresas ou categorias específicas[cite: 14, 15, 39, 40].

**Exemplo de insights que seriam gerados:**

* **Insight IA:** Reclamações sobre serviços financeiros frequentemente mencionam problemas relacionados à demora na resolução, indicando que a agilidade na resposta e na finalização do problema é um ponto crítico para a satisfação do cliente nesse setor[cite: 16, 41].
* **Insight IA:** O setor de e-commerce tem uma alta incidência de reclamações relacionadas à "entrega do produto", com muitos consumidores expressando insatisfação com atrasos e extravios.
* **Insight IA:** Apesar de um tempo de resposta médio razoável, as reclamações sobre "Vício de Qualidade" frequentemente contêm termos como "defeito" e "não funciona", sugerindo que a qualidade do produto em si é um fator crucial que leva à insatisfação, independentemente da velocidade do atendimento inicial.

## Recomendações

As recomendações são geradas com o auxílio da IA Generativa e baseadas nos insights obtidos, visando melhorias no atendimento ao cliente e redução de reclamações[cite: 17, 42].

* **Sugestões específicas para empresas mais reclamadas sobre melhorias no atendimento ao cliente:**
    * **Hurb - HotelUrbano e 123 Milhas:** Dada a alta incidência de reclamações e a baixa nota média para agências de turismo, é crucial implementar canais de comunicação mais eficazes e transparentes. A IA sugere foco na gestão de expectativas do cliente, comunicação proativa sobre status de reservas e reembolsos, e aumento da equipe de atendimento para lidar com o volume de demandas.
    * **Google, Vivo, Claro, Tim:** Para estas empresas de grande volume de reclamações, a IA aponta a necessidade de otimizar os processos de atendimento ao cliente, especialmente no que tange a "Cobrança/Contestação" e "Contrato/Oferta". Recomenda-se o uso de chatbots mais inteligentes para triagem de problemas comuns, e a capacitação aprimorada dos atendentes humanos para resolver questões complexas de forma ágil e satisfatória.
* **Propostas gerais para setores econômicos visando redução das principais reclamações identificadas:**
    * **Setor de Telecomunicações:** Com um grande volume de reclamações, a IA sugere a revisão das políticas de contratação e cancelamento de serviços, com foco na clareza das informações e na simplificação dos processos[cite: 18, 43].
    * **Setor Financeiro:** Devido à alta incidência de problemas de "Cobrança/Contestação" e "Dados Pessoais e Privacidade", a IA recomenda o investimento em segurança de dados, bem como a implementação de sistemas de alerta precoce para identificar e corrigir erros de cobrança antes que se tornem reclamações.
    * **Comércio Eletrônico:** Para mitigar problemas de "Entrega do Produto", a IA propõe aprimorar a logística, fornecer informações de rastreamento mais precisas e em tempo real, e estabelecer parcerias com transportadoras de melhor desempenho.
* **Exemplos práticos de implementação dessas sugestões, sempre conectados aos insights obtidos nas análises anteriores:**
    * **Implementação de FAQ inteligente:** Criar uma base de conhecimento com perguntas frequentes e respostas claras, alimentada por IA para autoatendimento eficiente, reduzindo o volume de chamadas para problemas simples[cite: 19, 44].
    * **Análise Preditiva de Reclamações:** Utilizar modelos de IA para prever quais clientes ou transações têm maior probabilidade de gerar reclamações, permitindo uma intervenção proativa das empresas.
    * **Feedback em Tempo Real:** Implementar sistemas de feedback rápido após a resolução de um problema, permitindo que as empresas coletem insights instantâneos sobre a satisfação do cliente e façam ajustes rápidos.
    * **Monitoramento de Sentimento nas Redes Sociais:** Usar IA para monitorar menções à marca nas redes sociais e identificar tendências de sentimento, permitindo que as empresas respondam rapidamente a problemas emergentes e gerenciem a reputação.

## Conclusão

Este projeto, através da análise de um vasto dataset de reclamações do Consumidor.gov.br, forneceu insights valiosos sobre os padrões de insatisfação dos consumidores brasileiros em 2023 e 2024. As análises exploratórias destacaram os segmentos, empresas e tipos de problemas mais recorrentes, como a predominância de reclamações de "Cobrança/Contestação" e a baixa satisfação com serviços de turismo. A segmentação de clientes por clusters revelou grupos com diferentes níveis de satisfação e tempos de resposta, indicando que a nota do consumidor não se correlaciona diretamente apenas com a agilidade na resposta, mas também com a efetividade da resolução.

A avaliação crítica do processo de análise aponta para a necessidade de dados mais detalhados sobre os canais de compra e reclamação, o que poderia enriquecer ainda mais os insights. A ausência de distinção entre reclamações avaliadas e não avaliadas também representa uma limitação[cite: 20, 45].

Para futuras investigações, sugere-se a incorporação de técnicas de Processamento de Linguagem Natural (PLN) mais avançadas para extrair nuances e emoções das descrições textuais das reclamações. Além disso, a análise temporal em maior profundidade, com a identificação de sazonalidades e eventos específicos que impactam o volume e tipo de reclamações, seria um complemento valioso. A construção de modelos preditivos da satisfação do cliente, considerando os fatores identificados neste estudo, também seria uma direção promissora para futuras melhorias[cite: 21, 46].

## Como Executar o Projeto

1.  Clone este repositório:
    `git clone https://github.com/Arthurcl07/Projeto-Integrador-Geracao-de-Insights.git`
2.  Navegue até o diretório do projeto:
    `cd Projeto-Integrador-Geracao-de-Insights`
3.  Baixe o arquivo "dados_consolidados2", presente nesse repositorio e coloque-o no seu google drive
4.   Abra um notebook no Google Colab
5.  Importe o arquivo .ipynb que está neste repositório
6.  Substitua nas linhas de código que tenham o caminho para o arquivo do google drive pelo caminho do arquivo que você colocou no seu drive
7.  Rode todas as linhas de código na ordem para que todas as funções necessárias sejam importadas 
8.  Explore a analise feita

---
