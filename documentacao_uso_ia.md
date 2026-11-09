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

A Inteligência Artificial foi utilizada como ferramenta de apoio na geração de ideias, sugestões e rascunhos iniciais. Durante o desenvolvimento do projeto, também foram realizados testes e consultas em diferentes ferramentas de IA, como Gemini e ChatGPT. Entretanto, algumas respostas apresentaram inconsistências e precisaram ser analisadas, questionadas e corrigidas.

Assumi uma participação ativa na organização, análise e revisão de diversos detalhes técnicos do projeto, desde a documentação até a estrutura do banco de dados. Esse processo exigiu atenção à modelagem das tabelas, aos relacionamentos, à precisão dos valores financeiros, às regras de negócio e à coerência entre os códigos e a documentação.

A experiência demonstrou que utilizar Inteligência Artificial não significa aceitar todas as respostas como corretas. Foi necessário buscar esclarecimentos, compreender as orientações, testar possibilidades e realizar correções para alcançar um resultado coerente com a proposta do Mercado Santana.

Por fim, o projeto contribuiu para ampliar meus conhecimentos técnicos, desenvolver meu pensamento crítico e compreender a importância da revisão humana na utilização de ferramentas de Inteligência Artificial.


**Registro de responsabilidade:** A utilização das ferramentas de IA foi complementar ao desenvolvimento. As análises, verificações, correções e decisões técnicas descritas neste documento foram realizadas mediante avaliação humana.
