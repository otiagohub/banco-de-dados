## Referências de comandos CRUD SQL

```sql
-- Inserindo fornecedor
INSERT INTO fornecedores (nome) 
VALUES('Eletrônicos TechMaster');

INSERT INTO fornecedores (nome) VALUES
('Vestuário Moda Fina'),
('Alimentos Sabor Brasil'),
('Livros Cultura Global');
```

```sql
-- Inserindo produtos
INSERT INTO produtos(nome, descricao, preco, quantidade, fornecedor_id)
VALUES(
	'Smartphone Galaxy S23', 
	'Smartphone com Android e câmera de alta resolução',
	1599.99,
	50,
	1
);
```

```sql
INSERT INTO produtos(nome, descricao, preco, quantidade, fornecedor_id)
VALUES(
	'Camiseta Algodão Premium', 
	'Camiseta masculina de algodão orgânico',
	49.90,
	200,
	2
), (
	'Arroz integral 1kg',
	'Alimento orgânico, rico em fibras',
	7.50,
	300,
	3
), (
	'Livro "Cem Anos de Solidão"',
	'Romance clássico de Gabriel Garcia Márquez',
	39.90,
	100,
	4
), (
	'Notebook Dell XPS 13',
	'Equipamento ultrafino com processador Inter Core i7',
	5457.23,
	20,
	1
);
```

```sql
-- Inserindo produtos (colocando valor null para descrição)
INSERT INTO produtos (nome, descricao, preco, quantidade, fornecedor_id)
VALUES('Calça Jeans Skinny', null, 89.90, 150, 2);
```

```sql
-- Inserindo produtos (omitindo a coluna descrição)
INSERT INTO produtos (nome, preco, quantidade, fornecedor_id)
VALUES('Feijão Carioca', 6.80, 250, 3);
```

```sql
-- Inserindo produtos
INSERT INTO produtos (nome, descricao, preco, quantidade, fornecedor_id)
VALUES('Livro 1984', 'Romance distópico de George Orwell', 34.90, 80, 4);
```

---

```sql
-- Inserindo detalhes dos produtos
INSERT INTO detalhes_produto (peso, dimensoes, codigo_barras, data_validade, produto_id)
VALUES(0.3, '15x8x2', '7891234567890', null, 1);
```

```sql
-- Inserindo detalhes dos produtos
INSERT INTO detalhes_produto (peso, dimensoes, codigo_barras, data_validade, produto_id)
VALUES
	(0.2, '30x20x5', '7899876543210', null, 2),
	(1, '20x10x5', '7894561237895', '2025-07-29', 3),
	(0.5, '25x15x3', '7893216549876', null, 4),
	(1.2, '32x22x4', '7896549871234', null, 5),
	(0.4, '35x25x6', '7897412589630', null, 6),
	(1, '20x10x5', '7893692581472', '2025-09-11', 7),
	(0.5, '25x15x3', '7898529637415', null, 8);
```

---

```sql
-- Inserindo lojas
INSERT INTO lojas (nome) VALUES
('Loja Bravado'),
('Loja Shopping Cygnus'),
('Loja 2112'),
('Loja Hemispheres');
```

---

```sql
-- Inserindo estoques de produtos em lojas
INSERT INTO lojas_produtos(loja_id, produto_id, estoque)
VALUES(1, 1, 30);
```

```sql
-- Inserindo estoques de produtos em lojas
INSERT INTO lojas_produtos(loja_id, produto_id, estoque)
VALUES
(4, 6, 10),
(3, 1, 20),
(2, 2, 50),
(4, 2, 100),
(1, 3, 150),
(3, 3, 100),
(2, 4, 40),
(3, 5, 10),
(1, 7, 200),
(2, 8, 60);
```

---

```sql
-- Atualizando um registro em lojas
UPDATE lojas SET nome = 'Loja Cygnus'
WHERE id = 2;
```

```sql
-- Atualizando o preço e a quantidade de um produto
UPDATE produtos SET preco = 1100, quantidade = 70
WHERE id = 1;
```

---

```sql
-- Excluindo registro de estoque de um determinado produto
DELETE FROM lojas_produtos WHERE produto_id = 8;
```

```sql
-- Excluindo um produto
DELETE FROM produtos WHERE id = 8;
```
