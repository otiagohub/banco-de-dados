# MER: Modelo Entidade Relacionamento

## Entidades e Atributos

### FORNECEDOR
- identificador
- nome do fornecedor

### PRODUTO 
- identificador
- nome do produto
- descrição
- preço
- quantidade

### DETALHES DO PRODUTO
- identificador
- peso
- dimensões
- código de barras
- data de validade

### LOJA
- identificador
- nome da loja
- estoque

## Relacionamentos

### FORNECEDOR fornece PRODUTO (1:N)

**UM** fornecedor pode fornecer **MUITOS** produtos

**UM** produto é fornecido por **UM** fornecedor

### PRODUTO possui DETALHE (1:1)

**UM** produto possui **UM** detalhe

**UM** detalhe pertence a **UM** produto

### LOJA vende PRODUTO (N:N)

**UMA** loja pode vender **MUITOS** produtos

**UM** produto pode ser vendido por **MUITAS** lojas






