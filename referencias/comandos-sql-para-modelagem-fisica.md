# Referência de comandos SQL para Modelagem Física

```sql
-- Tabela Fornecedores
CREATE TABLE fornecedores(
	id INTEGER PRIMARY KEY AUTOINCREMENT,
	nome TEXT NOT NULL
);
```

```sql
-- Tabela Produtos
CREATE TABLE produtos (
	id INTEGER PRIMARY KEY AUTOINCREMENT,
	nome TEXT NOT NULL,
	descricao TEXT,
	preco DECIMAL(10,2) NOT NULL CHECK (preco >= 0),
	quantidade INTEGER NOT NULL CHECK (quantidade >= 0),
	fornecedor_id INTEGER NOT NULL,
	FOREIGN KEY (fornecedor_id) REFERENCES fornecedores(id)
);
```

```sql
-- Tabela detalhes_produto
CREATE TABLE detalhes_produto (
	id INTEGER PRIMARY KEY AUTOINCREMENT,
	peso DECIMAL(7,2),
	dimensoes TEXT,
	codigo_barras TEXT UNIQUE,
	data_validade DATE,
	produto_id INTEGER NOT NULL,
	
	-- Se um produto for excluído, os detalhes dele também serão apagados
	FOREIGN KEY (produto_id) REFERENCES produtos(id) ON DELETE CASCADE
);
```

```sql
-- Tabela Lojas
CREATE TABLE lojas (
	id INTEGER PRIMARY KEY AUTOINCREMENT,
	nome TEXT NOT NULL
);
```

```sql
-- Tabela intermediária lojas_produtos
CREATE TABLE lojas_produtos (
	loja_id INTEGER NOT NULL,
	produto_id INTEGER NOT NULL,
	estoque INTEGER NOT NULL CHECK (estoque >= 0),
	
	-- Definindo a PK composta
	PRIMARY KEY (loja_id, produto_id),
	
	-- Se uma loja for excluída, os estoques dela também são removido
	FOREIGN KEY (loja_id) REFERENCES lojas(id) ON DELETE CASCADE,
	
	-- Se um produto for excluído, o banco impedirá a exclusão 
	-- caso ainda existam registros vinculados a ele neste tabela
	FOREIGN KEY (produto_id) REFERENCES produtos(id) ON DELETE RESTRICT
);
```

---

```sql
-- Exemplos adicionais de alterações diversas em uma tabela

ALTER TABLE exemplo RENAME TO clientes;
ALTER TABLE clientes RENAME COLUMN nome TO nome_completo;
ALTER TABLE clientes ADD COLUMN email TEXT;
ALTER TABLE clientes ADD COLUMN idade INTEGER NOT NULL DEFAULT 0;
ALTER TABLE clientes ADD COLUMN telefone TEXT;
DROP TABLE clientes;
```
