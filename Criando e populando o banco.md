# BDII--atividade-de-seguranca

# Projeto criado para a disciplina de banco de dados II - Uni7.

## Sumário

- [Introdução](#introdução).
- [Pré-requisitos](#pré-requisitos).
- [Tabelas](#tabelas).
- [Criando o banco](#criando-o-banco).
- [Inserção de dados](#inserção-de-dados).
- [Criando o login](#criando-o-login).
- [Associar o usuario ao login](#criando-o-usuário-do-banco-de-dados-associado-ao-login).
- [Conectando ao SQL SERVER](#conectando-ao-sql-server).
- [Dando permissões com o GRANT](#dando-permissões-com-grant).
- [Removendo permissão com o REVOKE](#removendo-permissão-com-o-revoke).
- [Removendo o login do servidor](#removendo-o-login-do-servidor).


  
# Documentação do Banco de Dados da Minha Empresa

Projeto criado para a disciplina de banco de dados II - Uni7.

## Sumário

- [Introdução](#introdução).
- [Pré-requisitos](#pré-requisitos).
- [Tabelas](#tabelas).
- [Criando o banco](#criando-o-banco).
- [Inserção de dados](#inserção-de-dados).
  
## Introdução

O banco de dados foi projetado para armazenar informações sobre clientes, pedidos e produtos. Esta documentação fornecerá informações essenciais sobre a estrutura do banco de dados, instruções para a inserção de dados e exemplos de consultas SQL comuns.

## Pré-requisitos

- SQL Server Management Studio;
- Conhecimentos básicos de linguagem SQL.


# Tabelas
O banco de dados possui as seguintes tabelas:

- Tabela Clientes <br />
  <br /> 
  IDCliente (int): Identificação única do cliente. <br /> 
  Nome (varchar): Nome do cliente.<br /> 
  Email (varchar): Endereço de e-mail do cliente. <br /> 
  Telefone (varchar): Número de telefone do cliente. <br /> 

- Tabela Pedidos<br />
  <br /> 
  IDPedido (int): Identificação única do pedido. <br /> 
  DataPedido (date): Data em que o pedido foi feito. <br /> 
  IDCliente (int): Chave estrangeira relacionada ao cliente que fez o pedido.<br /> 
  ValorTotal (decimal): O valor total do pedido.<br /> 

- Tabela Produtos<br />
  <br /> 
  IDProduto (int): Identificação única do produto.<br /> 
  NomeProduto (varchar): Nome do produto.<br /> 
  PrecoUnitario (decimal): Preço unitário do produto.<br /> 

# Criando o banco

```sql

-- Criação do banco de dados
CREATE DATABASE MinhaEmpresa;

-- Usar o banco de dados
USE MinhaEmpresa;

-- Tabela de Clientes
CREATE TABLE Clientes (
    IDCliente INT PRIMARY KEY,
    Nome VARCHAR(50),
    Email VARCHAR(100),
    Telefone VARCHAR(15)
);

-- Tabela de Pedidos
CREATE TABLE Pedidos (
    IDPedido INT PRIMARY KEY,
    DataPedido DATE,
    IDCliente INT,
    ValorTotal DECIMAL(10, 2),
    FOREIGN KEY (IDCliente) REFERENCES Clientes(IDCliente)
);

-- Tabela de Produtos
CREATE TABLE Produtos (
    IDProduto INT PRIMARY KEY,
    NomeProduto VARCHAR(100),
    PrecoUnitario DECIMAL(10, 2)
);
```

# Inserção de dados

```sql

-- Inserindo 10 clientes de exemplo
INSERT INTO Clientes (IDCliente, Nome, Email, Telefone)
VALUES
    (1, 'João Silva', 'joao@email.com', '(11) 1234-5678'),
    (2, 'Maria Santos', 'maria@email.com', '(22) 9876-5432'),
    (3, 'Carlos Oliveira', 'carlos@email.com', '(33) 5555-9999'),
    (4, 'Ana Pereira', 'ana@email.com', '(44) 1111-2222'),
    (5, 'Lucas Mendes', 'lucas@email.com', '(55) 8888-7777'),
    (6, 'Isabel Lima', 'isabel@email.com', '(66) 7777-8888'),
    (7, 'Fernando Rocha', 'fernando@email.com', '(77) 6666-5555'),
    (8, 'Paula Vieira', 'paula@email.com', '(88) 2222-3333'),
    (9, 'Ricardo Pereira', 'ricardo@email.com', '(99) 3333-2222'),
    (10, 'Lúcia Gomes', 'lucia@email.com', '(10) 1111-0000');

-- Inserindo 10 produtos de exemplo
INSERT INTO Produtos (IDProduto, NomeProduto, PrecoUnitario)
VALUES
    (101, 'Produto A', 19.99),
    (102, 'Produto B', 24.99),
    (103, 'Produto C', 12.50),
    (104, 'Produto D', 34.99),
    (105, 'Produto E', 29.99),
    (106, 'Produto F', 15.00),
    (107, 'Produto G', 18.50),
    (108, 'Produto H', 28.75),
    (109, 'Produto I', 21.99),
    (110, 'Produto J', 17.25);

-- Inserindo 10 pedidos de exemplo
INSERT INTO Pedidos (IDPedido, DataPedido, IDCliente, ValorTotal)
VALUES
    (1001, '2023-10-25', 1, 39.98),
    (1002, '2023-10-26', 2, 49.98),
    (1003, '2023-10-27', 3, 29.95),
    (1004, '2023-10-28', 4, 54.75),
    (1005, '2023-10-29', 5, 62.49),
    (1006, '2023-10-30', 6, 19.50),
    (1007, '2023-10-31', 7, 42.99),
    (1008, '2023-11-01', 8, 37.75),
    (1009, '2023-11-02', 9, 63.25),
    (1010, '2023-11-03', 10, 27.99);


```
