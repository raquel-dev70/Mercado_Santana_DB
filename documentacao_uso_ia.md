# Documentação do Uso de Inteligência Artificial (IA)

## 1. Interação sobre Engenharia de Dados e Tipagem Financeira

**Contexto / Prompt enviado:**
"Desenvolver as justificativas técnicas da modelagem do banco de dados do Mercado Santana, considerando as tabelas de itens e movimentação de estoque e definindo os tipos de dados para valores numéricos e financeiros."

**Retorno da IA:**
A Inteligência Artificial apresentou sugestões para a estrutura das tabelas associativas `item_venda` e `item_entrada`, além da tabela `movimentacao_estoque`. Entretanto, uma das sugestões foi utilizar o tipo de dado `FLOAT` para atributos monetários, como preços unitários e subtotais.

**Análise e correção aplicada (intervenção humana):**
Durante a revisão técnica, identifiquei que o tipo `FLOAT` utiliza representação numérica de ponto flutuante, podendo apresentar pequenas imprecisões em operações financeiras.
Para evitar problemas de arredondamento nos valores de compras, vendas e fechamento do caixa, foi adotado o tipo `DECIMAL(10,2)` nos campos monetários.
Essa correção permitiu estabelecer maior precisão no armazenamento dos valores financeiros, mantendo a coerência das informações registradas no banco de dados.


## 2. Interação sobre a Seção de Business Intelligence (BI) e IA

**Contexto / Prompt enviado:**
"Quero entender melhor a lógica e os detalhes da sua parte, pois vou analisar os códigos. A parte de BI & IA não significa apenas que está tudo concluído. É necessário que os seus códigos estejam de acordo com a proposta de BI & IA e que essa integração seja demonstrada na documentação do meu README."
**Retorno da IA:**
A IA sugeriu indicadores gerenciais, como Ticket Médio, Giro de Estoque e Margem de Lucro. Entretanto, apresentou uma estrutura baseada na utilização de ferramentas comerciais específicas de visualização e análise de dados.

**Análise e correção aplicada (intervenção humana):**
Após avaliar a proposta, foi necessário ajustar a documentação à realidade do projeto e às ferramentas efetivamente utilizadas pelo grupo.

As referências a softwares comerciais que não faziam parte do desenvolvimento foram retiradas, priorizando os fundamentos de Business Intelligence (BI), as consultas SQL e os indicadores gerenciais.

Também foi considerada uma proposta de arquitetura para separar o processamento analítico do banco de dados operacional (OLTP), evitando que futuras operações de Inteligência Artificial comprometam o desempenho das atividades do sistema.

Essa separação foi apresentada como possibilidade de evolução, incluindo a utilização futura de estruturas específicas para armazenar informações de previsão de demanda, como a tabela `previsoes_demanda`.


## 3. Interação sobre Validação e Integração Analítica dos Dados

**Contexto / Prompt enviado:**
"Refinar a comunicação sobre a documentação do README, destacando a necessidade de analisar os códigos e verificar se a estrutura desenvolvida realmente atende às propostas de BI e IA."

**Retorno da IA:**

A IA ajudou a organizar a comunicação sobre a relação entre o banco de dados, os códigos desenvolvidos e as possibilidades de aplicação de BI e IA.

**Análise e correção aplicada (intervenção humana):**

A partir dessa análise, foi reforçado que a conclusão do banco de dados não significa, automaticamente, que todas as funcionalidades de BI e IA estejam implementadas.

Os códigos precisam ser analisados e validados conforme as regras de negócio, os relacionamentos e os indicadores definidos na documentação.

Os dados fictícios utilizados nos testes, relacionados ao trabalho da Pessoa 4, servem como base para demonstrar o funcionamento das consultas e permitir a avaliação dos indicadores gerenciais.

Dessa forma, a documentação do README precisa apresentar uma relação coerente entre a estrutura do banco de dados, os códigos SQL, os dados utilizados e as possibilidades analíticas propostas.



## 4. Conclusão do Relatório

A Inteligência Artificial foi utilizada como ferramenta de apoio durante o desenvolvimento do projeto, principalmente por meio do ChatGPT, para a geração de ideias, sugestões, esclarecimento de dúvidas e elaboração de rascunhos iniciais. Também foram realizados testes e consultas com outras ferramentas, como o Gemini. Entretanto, algumas respostas apresentaram inconsistências e precisaram ser analisadas, questionadas e corrigidas.

Assumi uma participação ativa na organização, análise e revisão dos detalhes técnicos do projeto, desde a documentação até a estrutura do banco de dados. Esse processo envolveu a modelagem das tabelas, os relacionamentos, a definição dos tipos de dados, a precisão dos valores financeiros, as regras de negócio e a elaboração das consultas SQL.

A experiência demonstrou que o desenvolvimento do projeto exigiu dedicação, paciência e atenção aos detalhes. Foi necessário analisar informações, esclarecer dúvidas, testar possibilidades e realizar diversas correções para garantir a coerência entre a documentação, o banco de dados e as consultas SQL do Mercado Santana. Esse trabalho reforçou a importância de compreender cada etapa, em vez de simplesmente aceitar as sugestões fornecidas pela Inteligência Artificial.

Por fim, o projeto contribuiu para ampliar meus conhecimentos técnicos, desenvolver meu pensamento crítico e fortalecer minha autonomia na análise e resolução de problemas. Também compreendi a importância da revisão humana e da responsabilidade na utilização de ferramentas de Inteligência Artificial.

Registro de responsabilidade: A Inteligência Artificial foi utilizada como recurso complementar ao desenvolvimento. As análises, verificações, correções e decisões técnicas foram realizadas mediante avaliação humana, com responsabilidade sobre o conteúdo final apresentado.
