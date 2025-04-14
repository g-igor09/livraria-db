-- Cria o banco de dados
CREATE DATABASE livraria_db;
USE livraria_db;

-- Tabela de produtos (livros)
CREATE TABLE produtos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    titulo VARCHAR(100) NOT NULL,
    autor VARCHAR(100) NOT NULL,
    preco DECIMAL(10, 2) NOT NULL,
    estoque INT NOT NULL,
    data_cadastro TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Tabela de pedidos
CREATE TABLE pedidos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    cliente_nome VARCHAR(100) NOT NULL,
    produto_id INT NOT NULL,
    quantidade INT NOT NULL,
    data_pedido TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    status VARCHAR(20) DEFAULT 'pendente',
    FOREIGN KEY (produto_id) REFERENCES produtos(id)
);

-- Insere alguns livros
INSERT INTO produtos (titulo, autor, preco, estoque) VALUES
('Dom Casmurro', 'Machado de Assis', 29.90, 15),
('1984', 'George Orwell', 45.50, 8),
('O Pequeno Príncipe', 'Antoine de Saint-Exupéry', 24.99, 20);

-- Insere pedidos de exemplo
INSERT INTO pedidos (cliente_nome, produto_id, quantidade) VALUES
('João Silva', 1, 2),
('Maria Oliveira', 3, 1),
('Carlos Souza', 2, 1);# livraria-db
