## 1. Justificativas Técnicas da Modelagem — Mercado Santana : 
Nos banco de dados foi estruturado com as entidades Categoria, Produto, Fornecedor, Entrada, Item_Entrada, Venda, Item_Venda e Movimentacao_Estoque. As entidades Item_Entrada e Item_Venda possuem atributos do tipo FLOAT para representar valores numéricos, como quantidades e valores financeiros. Já as chaves estrangeiras (FK) foram definidas com o tipo INT, permitindo estabelecer os relacionamentos entre as tabelas e garantir a integridade dos dados.

**1. Movimentacao_Estoque:** É responsável pelo controle das entradas, saídas, custos e demais movimentações dos produtos no estoque.

**1.1 Item_Entrada e Item_Venda:** Representam os itens relacionados às operações de compra e venda, permitindo registrar as quantidades e os valores correspondentes a cada operação.

**1.2 Tipo de dado FLOAT:** Foi utilizado para representar valores numéricos com casas decimais, permitindo registrar quantidades e valores relacionados às operações de compra, venda e movimentação de estoque.

**1.3 Chaves estrangeiras (FK) do tipo INT:** Foram utilizadas para estabelecer os relacionamentos entre as tabelas por meio dos identificadores correspondentes, permitindo vincular os registros e preservar a integridade referencial do banco de dados.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
## 2. Coerência DER vs. Modelo Lógico:
**O mapeamento das tabelas funcionou?**
Sim! Nos relacionamentos "refere-se" e "possui", o mapeamento funcionou perfeitamente. O relacionamento "refere-se" serve para ligar as tabelas `Produto`, `Item_Entrada` e `Item_Venda` através de chaves estrangeiras (`FK`), identificando pelo ID qual mercadoria está sendo movimentada. Já o relacionamento "possui" liga a tabela `Venda` com a tabela `Item_Venda`, identificando exatamente em qual cupom fiscal aquela compra foi registrada, não deixando nenhuma informação solta no sistema do mercado.

**Como as linhas do desenho viraram código?** 
No código, a tabela produto se liga à entidade pai por meio da coluna id_categoria INT NOT NULL, que atua como chave estrangeira.

**As tabelas de "Item" estão certas?** 
 Na transposição do modelo conceitual para o lógico, foram criadas corretamente as tabelas intermediárias item_venda e item_entrada. Elas funcionam unindo as chaves estrangeiras (id_produto com id_venda ou id_entrada) para registrar os dados de cada movimentação, como no caso do cupom ou nota fiscal, mapeando atributos específicos como quantidade, preco_unitario e subtotal.
 
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
## 3. Decisões de Engenharia de Dados: 
 **1. Escolha da Tipagem para Valores Monetários (DECIMAL vs FLOAT):**
Utilizamos o tipo **`DECIMAL(10,2)`** em campos como `preco_venda` e `valor_total` em vez do tipo `FLOAT`. Não usamos ambos porque queremos precisão financeira nos dados de custos e despesas. Essa decisão garante que atributos como `custo_unitario`, `preco_unitario` e os resultados de valores totais como `subtotal` fiquem com os valores exatos, sem erros de arredondamento no fechamento do caixa do mercado.

**2. Uso do Mecanismo de Armazenamento (Engine):**
Foi utilizada a configuração `AUTO_INCREMENT` nas chaves primárias (`PRIMARY KEY`), permitindo que os identificadores sejam gerados automaticamente pelo banco de dados a cada novo registro. Os campos foram definidos com o tipo `INT`, garantindo a identificação única dos registros. Esses identificadores também permitem estabelecer relacionamentos entre as tabelas por meio das chaves estrangeiras (`FOREIGN KEY`), como `id_produto` e `id_venda`.

**3. Padronização de Caracteres e Acentuação:**
Na tabela Categoria, foi utilizada a configuração DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci, permitindo o armazenamento adequado de caracteres especiais, acentos e diferentes idiomas. O conjunto de caracteres utf8mb4 oferece suporte a uma ampla variedade de caracteres, incluindo letras acentuadas.
Já a configuração utf8mb4_0900_ai_ci utiliza uma regra de comparação que ignora diferenças entre letras maiúsculas e minúsculas (ci) e diferenças de acentuação (ai). Dessa forma, ao pesquisar uma categoria como Limpeza, o banco de dados também consegue reconhecer variações como limpeza e LIMPEZA, facilitando as consultas e a localização dos registros.


**4. Estrutura de Chaves e Relacionamentos:**
A estrutura das tabelas Item_Entrada e Item_Venda permite estabelecer relacionamentos do tipo Muitos para Muitos (N) entre produtos e operações de entrada e venda. Para isso, foram utilizadas chaves estrangeiras (FOREIGN KEY), como a restrição CONSTRAINT item_venda_ibfk_1 FOREIGN KEY (id_produto) REFERENCES produto (id_produto), que vincula os produtos registrados na tabela Item_Venda aos seus respectivos registros na tabela Produto.

Essa restrição impede que seja registrado um item de venda com um id_produto inexistente na tabela Produto, garantindo a integridade referencial. Além disso, o mecanismo de armazenamento ENGINE=InnoDB, em conjunto com as chaves estrangeiras, ajuda a preservar a consistência dos dados e a integridade do histórico de vendas e das notas fiscais de entrada.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
## 4. Seção de BI & IA: 
**Informações comparativas entre a pesquisa de campo e a massa sintética de teste**

| Informação | Pesquisa de campo | Massa sintética de teste |
| :--- | :--- | :--- |
| **Produtos ativos/cadastrados** | Mais de 50; sem contagem exata | 52 produtos |
| **Entradas por mês** | 20 (anotação) | 20 entradas em outubro/2026 |
| **Vendas por mês** | 200 (anotação; período/significado a confirmar) | 200 vendas em outubro/2026 |
| **Faturamento mensal** | Aproximadamente R$ 36.000,00 | R$ 36.257,17 |
| **Ticket médio** | Não informado | R$ 181,29 |
| **Valor de compras** | Não informado | R$ 29.079,24 |
| **Produto de maior giro** | "Pães" | Pão francês: 1.020 unidades vendidas |
| **Devoluções** | Aproximadamente 12 por mês | Não registradas na massa |


**Consultas SQL gerenciais**:
**Consultas G01 a G06 aplicadas às tabelas do script SQL**

**G01-Quantidades de produtos cadastrados:**

```SQL
SELECT
  COUNT(*) AS total_produtos
FROM produtos;  
```

**G02-Quantidades de entrada por mês:**
</>SQL
```sql
SELECT
   DATE_FORMAT(data_entrada,'%Y-%m')AS mes,
   COUNT(*) AS total_entradas
FROM entrada
GROUP BY DATE_FORMAT(data_entrada,'%Y-%m')
ORDER BY mes;
```
**G03-Quantidades de vendas, faturamento e ticket médio por mês:**
```SQL
SELECT
  DATE_FORMAT(data_hora,'%Y-%m')AS mes,
  COUNT(*) AS total_vendas;
  SUM(valor_total)AS faturamento,
  AVG(valor_total)AS ticket_medio
FROM venda
GROUP BY DATE_FORMAT(data_hora,'%Y-%m')
ORDER BY mes;
```
**G04-Valor total de compras por mês:**
```SQL
SELECT
 DATE_FORMAT(data_entrada,'%Y-%m')AS mes,
 SUM(valor_total)AS total_compras
FROM entrada
GROUP BY DATE_FORMAT(data_entrada,'%Y-%m')
ORDER BY mes;
```
**G05-Produtos que mais vendidos:**
```SQL
SELECT 
 p.nome AS produto,
 SUM(iv.quantidade)AS quantidade_vendida
FROM item_vendas AS iv
INNER JOIN produto AS p
   ON iv.id_produto=p.id_produto
GROUP BY id_produto, p.nome
ORDER BY quantidade_vendida DESC;
```
**G06-Produtos que precisam de reposição:**
```SQL
SELECT
  nome,
  quantidade_estoque,
  estoque_minimo
FROM produto
WHERE quantidade_estoque<=estoque_minimo
ORDER BY quantidade_estoque ASC, nome;
```
