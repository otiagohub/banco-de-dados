# Referências de comando SELECT para query/queries (Consultas)

```sql
--Exibir todos os produtos e seus preços
SELECT nome, preco FROM produtos;
```

```sql
-- Exibir os produtos e preços e quantidades, mas apenas daqueles que custam acima de 100 reais.
SELECT nome, preco, quantidade FROM produtos
WHERE preco > 100;
```

```sql
-- Exibir os produtos e preços, mas apenas daqueles que custam entre 50 e 150 reais.
SELECT nome, preco FROM produtos
WHERE preco BETWEEN 50 AND 150;
```

```sql
-- Produtos que custam acima de 100 e com estoque/quantidade abaixo de 100
SELECT nome, preco, quantidade FROM produtos
WHERE preco > 100 AND quantidade < 100;
```

```sql
-- Exibir produtos de determinados fornecedores (1, 4 e 5)
SELECT nome, preco, fornecedor_id FROM produtos
-- WHERE fornecedor_id = 1 OR fornecedor_id = 4 OR fornecedor_id = 5; 
WHERE fornecedor_id IN (1, 4, 5);
```

```sql
-- Exibir os produtos que possuem data de validade definida
SELECT produto_id, data_validade FROM detalhes_produto
WHERE data_validade IS NOT NULL;
```

```sql
-- Exibir os produtos com validade até 30/09/2025
SELECT produto_id, data_validade FROM detalhes_produto
WHERE data_validade <= '2025-09-30';
```

```sql
-- Pesquisa por produtos que comecem com a letra P
SELECT nome FROM produtos
WHERE nome LIKE 'P%';
```

```sql
-- Exibir nome, preco dos produtos em ordem decrescente de preço
SELECT nome, preco FROM produtos
ORDER BY preco DESC;
```

```sql
-- Exibir produtos pela data de validade
SELECT produto_id, data_validade FROM detalhes_produto
WHERE data_validade IS NOT NULL
ORDER BY data_validade ASC;
```

```sql
-- Resumo estatístico de todos os produtos: total de produtos, média dos preços, maior preço e menor preço.
SELECT 
	COUNT(*) AS total_produtos,
	ROUND(AVG(preco), 2) AS "Média dos Preços",
	MAX(preco) AS preco_mais_caro,
	MIN(preco) AS preco_mais_barato,
	SUM(quantidade) AS estoque_geral
FROM produtos;
```

```sql
-- Listar os produtos com o nome de seus fornecedores
SELECT 
	produtos.nome AS Produto, 
	fornecedores.nome AS Fornecedor
FROM produtos JOIN fornecedores	
ON produtos.fornecedor_id = fornecedores.id;
```

```sql
-- Listar os produtos que não estão em nenhuma loja
SELECT produtos.nome AS Produto
FROM produtos LEFT JOIN lojas_produtos
ON produtos.id = lojas_produtos.produto_id
WHERE lojas_produtos.produto_id IS NULL;
```

```sql
-- Listar todos os fornecedores e os produtos que cada um fornece
SELECT 
	fornecedores.nome AS Fornecedor,
	produtos.nome AS Produto
FROM fornecedores LEFT JOIN produtos
ON fornecedores.id = produtos.fornecedor_id;	
```

```sql
-- Mostrar quantos produtos cada fornecedor fornece
SELECT 
	fornecedores.nome AS Fornecedor,
	COUNT(produtos.id) AS "Total de Produtos"
FROM produtos RIGHT JOIN fornecedores
ON produtos.fornecedor_id = fornecedores.id
GROUP BY fornecedores.id;	
```

```sql
-- Mostrar quantos produtos cada fornecedor fornece, mas apenas os fornecedores com mais de 3 produtos cadastrados
SELECT 
	fornecedores.nome AS Fornecedor,
	COUNT(produtos.id) AS "Total de Produtos"
FROM produtos RIGHT JOIN fornecedores
ON produtos.fornecedor_id = fornecedores.id
GROUP BY fornecedores.id
HAVING COUNT(produtos.id) > 3;
```

```sql
-- Exibir fornecedores que têm produtos custando acima de 120
SELECT nome FROM fornecedores
WHERE id IN (
	SELECT fornecedor_id FROM produtos WHERE preco > 120
);
```
