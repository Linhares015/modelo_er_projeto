# Projeto de Modelagem de Banco de Dados E-Commerce

Este repositório contém um projeto de modelagem conceitual de banco de dados, especificamente voltado para um sistema de e-commerce. O objetivo é refinar um modelo apresentado anteriormente e incluir novas funcionalidades, como diferentes tipos de clientes (Pessoa Jurídica e Pessoa Física), múltiplas formas de pagamento, e controle de status de entregas.

## Objetivo

Refinar o modelo apresentado adicionando os seguintes pontos:

- **Cliente PJ e PF:** Uma conta pode ser do tipo PJ (Pessoa Jurídica) ou PF (Pessoa Física), mas não pode ser as duas simultaneamente.
- **Pagamento:** O sistema permite o cadastro de mais de uma forma de pagamento por cliente.
- **Entrega:** Cada entrega possui um status e código de rastreamento.

## Modelo Entidade-Relacionamento (ER)

Utilizamos o Mermaid para desenhar o modelo conceitual de banco de dados no formato ER. O diagrama visualiza as principais entidades e seus relacionamentos dentro do sistema de e-commerce.

### Diagrama ER:

```mermaid
erDiagram
    CLIENTE {
        int id_cliente
        string nome
        string tipo_pessoa
        string cpf_cnpj
    }
    
    PAGAMENTO {
        int id_pagamento
        string tipo_pagamento
        decimal valor
        int id_cliente
    }
    
    ENTREGA {
        int id_entrega
        string status
        string codigo_rastreio
        int id_cliente
    }
    
    CLIENTE ||--o{ PAGAMENTO : "realiza"
    CLIENTE ||--o{ ENTREGA : "recebe"
```

## Detalhes do Modelo

### Cliente
Os clientes podem ser de dois tipos: Pessoa Jurídica (PJ) ou Pessoa Física (PF). Cada cliente possui um identificador único, um nome e um campo exclusivo para CPF ou CNPJ, dependendo do tipo de cliente.

### Pagamento
Os clientes podem utilizar várias formas de pagamento, como cartão de crédito, boleto bancário, ou transferências eletrônicas. Cada pagamento está associado a um cliente e possui um valor e tipo de pagamento.

### Entrega
O sistema de entrega registra o status de cada envio, além de fornecer um código de rastreio para que o cliente possa acompanhar a entrega dos produtos. Cada entrega está vinculada a um cliente específico.

# Projeto de Modelagem de Banco de Dados - Oficina Mecânica

Este repositório contém o projeto de modelagem de banco de dados para um sistema de controle e gerenciamento de ordens de serviço (OS) em uma oficina mecânica. A modelagem foi feita com base em requisitos funcionais, detalhando o processo de execução de serviços em veículos, desde a entrada na oficina até a conclusão dos reparos.

## Objetivo

O objetivo do projeto é criar uma estrutura de banco de dados para gerenciar:

- **Ordens de serviço (OS):** Cada ordem contém informações sobre os serviços a serem executados, peças utilizadas, e o responsável pela execução.
- **Clientes:** Informações sobre os veículos e seus proprietários.
- **Mecânicos:** Equipes de mecânicos responsáveis por realizar os serviços.
- **Peças:** Registro das peças utilizadas nos serviços.

## Requisitos

A modelagem foi elaborada seguindo os seguintes requisitos:

- **Clientes levam veículos à oficina para conserto ou revisão.**
- **Cada veículo é designado a uma equipe de mecânicos, que define os serviços a serem executados.**
- **Os serviços e peças são registrados em uma OS, juntamente com a data de entrega prevista.**
- **Cada OS possui número, data de emissão, valor, status e data de conclusão.**
- **Uma OS pode conter vários serviços e uma mesma peça pode ser usada em mais de uma OS.**
- **Os mecânicos possuem código, nome, endereço e especialidade.**
- **Os serviços são calculados com base em uma tabela de referência de mão de obra, e o valor das peças também é adicionado à OS.**
- **O cliente autoriza a execução dos serviços antes que a equipe comece o trabalho.**

## Modelo Entidade-Relacionamento (ER)

A seguir, o diagrama ER do projeto, modelado em Mermaid:

### Diagrama ER:

```mermaid
erDiagram
    CLIENTE {
        int id_cliente
        string nome
        string endereco
        string telefone
    }
    
    VEICULO {
        int id_veiculo
        string placa
        string modelo
        int id_cliente
    }
    
    MECANICO {
        int id_mecanico
        string nome
        string endereco
        string especialidade
    }
    
    OS {
        int id_os
        date data_emissao
        date data_conclusao
        decimal valor
        string status
        int id_veiculo
        int id_mecanico
    }
    
    SERVICO {
        int id_servico
        string descricao
        decimal preco
        int id_os
    }
    
    PECA {
        int id_peca
        string descricao
        decimal preco
        int id_os
    }
    
    CLIENTE ||--o{ VEICULO : "possui"
    VEICULO ||--o{ OS : "tem"
    MECANICO ||--o{ OS : "executa"
    OS ||--o{ SERVICO : "inclui"
    OS ||--o{ PECA : "utiliza"
```

## Detalhes do Modelo

### Cliente
Os clientes são proprietários dos veículos que trazem à oficina. Cada cliente possui um identificador único, além de informações de contato.

### Veículo
Cada veículo está associado a um cliente. As informações sobre o veículo incluem a placa e o modelo.

### Mecânico
Os mecânicos realizam os serviços na oficina. Cada mecânico possui um código identificador, nome, endereço e especialidade (ex: motor, pintura, etc.).

### Ordem de Serviço (OS)
A OS é o centro do sistema, registrando os serviços prestados, as peças utilizadas, e os mecânicos envolvidos. Cada OS possui data de emissão, data de conclusão, valor total e status (ex: em andamento, concluída).

### Serviço
Os serviços executados na OS são registrados com descrição e preço. Uma OS pode incluir vários serviços.

### Peça
As peças utilizadas durante os serviços também são registradas na OS, com descrição e valor.

# Projeto de Modelagem de Banco de Dados para E-commerce

## Descrição do Desafio

O objetivo deste projeto é replicar a modelagem de banco de dados para um cenário de e-commerce, aplicando conceitos de modelagem lógica, incluindo definições de chaves primárias e estrangeiras, bem como constraints e relacionamentos presentes no modelo EER (Enhanced Entity-Relationship). Além disso, o projeto visa criar um script SQL para a criação do esquema de banco de dados, persistência de dados para testes e elaboração de consultas SQL complexas, seguindo as diretrizes estabelecidas no desafio.

## Diretrizes

- Realizar a modelagem lógica e física do banco de dados.
- Criar um script SQL para criar o esquema do banco, incluindo tabelas, chaves primárias, estrangeiras e constraints.
- Implementar a persistência de dados para realização de testes.
- Criar consultas SQL que demonstrem a manipulação e recuperação de dados de forma eficiente, utilizando cláusulas como `SELECT`, `WHERE`, `ORDER BY`, `HAVING`, e junções entre tabelas.
- Elaborar perguntas que possam ser respondidas através das consultas criadas.

## Cenário de Modelagem

### Requisitos

1. **Cliente PJ e PF**: Uma conta pode ser Pessoa Jurídica (PJ) ou Pessoa Física (PF), mas não pode ter ambas as informações.
2. **Pagamento**: Deve permitir o cadastro de mais de uma forma de pagamento por pedido.
3. **Entrega**: Deve incluir informações sobre status de entrega e código de rastreio.

## Exemplos de Perguntas a serem Respondidas pelas Consultas

- Quantos pedidos foram feitos por cada cliente?
- Algum vendedor também é fornecedor?
- Relação de produtos, fornecedores e seus respectivos estoques.
- Relação de nomes dos fornecedores e produtos oferecidos.

## Modelo EER

```mermaid
erDiagram
    CLIENTE {
        int cliente_id PK
        string nome
        string tipo_cliente "PJ/PF"
    }
    PAGAMENTO {
        int pagamento_id PK
        string forma_pagamento
    }
    PEDIDO {
        int pedido_id PK
        date data_pedido
        int cliente_id FK
    }
    ENTREGA {
        int entrega_id PK
        int pedido_id FK
        string status_entrega
        string codigo_rastreio
    }
    PRODUTO {
        int produto_id PK
        string nome_produto
        float preco
    }
    FORNECEDOR {
        int fornecedor_id PK
        string nome_fornecedor
    }
    ESTOQUE {
        int estoque_id PK
        int produto_id FK
        int quantidade
    }
    CLIENTE ||--o{ PEDIDO : "faz"
    PEDIDO ||--o{ PAGAMENTO : "tem"
    PEDIDO ||--o| ENTREGA : "contém"
    PRODUTO }o--o| ESTOQUE : "está em"
    FORNECEDOR ||--o{ PRODUTO : "fornece"
```

## Script de Criação do Banco de Dados

<details>
<summary>Clique para visualizar o script de criação</summary>

```sql
-- Criação da tabela de CLIENTES
CREATE TABLE CLIENTE (
    cliente_id INT PRIMARY KEY,
    nome VARCHAR(100),
    tipo_cliente ENUM('PJ', 'PF') NOT NULL
);

-- Criação da tabela de PAGAMENTOS
CREATE TABLE PAGAMENTO (
    pagamento_id INT PRIMARY KEY,
    forma_pagamento VARCHAR(50)
);

-- Criação da tabela de PEDIDOS
CREATE TABLE PEDIDO (
    pedido_id INT PRIMARY KEY,
    data_pedido DATE,
    cliente_id INT,
    FOREIGN KEY (cliente_id) REFERENCES CLIENTE(cliente_id)
);

-- Criação da tabela de ENTREGAS
CREATE TABLE ENTREGA (
    entrega_id INT PRIMARY KEY,
    pedido_id INT,
    status_entrega VARCHAR(50),
    codigo_rastreio VARCHAR(50),
    FOREIGN KEY (pedido_id) REFERENCES PEDIDO(pedido_id)
);

-- Criação da tabela de PRODUTOS
CREATE TABLE PRODUTO (
    produto_id INT PRIMARY KEY,
    nome_produto VARCHAR(100),
    preco DECIMAL(10, 2)
);

-- Criação da tabela de FORNECEDORES
CREATE TABLE FORNECEDOR (
    fornecedor_id INT PRIMARY KEY,
    nome_fornecedor VARCHAR(100)
);

-- Criação da tabela de ESTOQUES
CREATE TABLE ESTOQUE (
    estoque_id INT PRIMARY KEY,
    produto_id INT,
    quantidade INT,
    FOREIGN KEY (produto_id) REFERENCES PRODUTO(produto_id)
);
```

</details>

## Consultas SQL Complexas

<details>
<summary>1. Quantos pedidos foram feitos por cada cliente?</summary>

```sql
SELECT
    cliente_id,
    COUNT(pedido_id) AS total_pedidos
FROM
    PEDIDO
GROUP BY
    cliente_id;
```

</details>

<details>
<summary>2. Algum vendedor também é fornecedor?</summary>

```sql
SELECT
    CLIENTE.nome AS nome_cliente,
    FORNECEDOR.nome_fornecedor
FROM
    CLIENTE
JOIN
    FORNECEDOR ON CLIENTE.nome = FORNECEDOR.nome_fornecedor;
```

</details>

<details>
<summary>3. Relação de produtos, fornecedores e estoques</summary>

```sql
SELECT
    PRODUTO.nome_produto,
    FORNECEDOR.nome_fornecedor,
    ESTOQUE.quantidade
FROM
    PRODUTO
JOIN
    ESTOQUE ON PRODUTO.produto_id = ESTOQUE.produto_id
JOIN
    FORNECEDOR ON PRODUTO.produto_id = FORNECEDOR.fornecedor_id;
```

</details>

<details>
<summary>4. Relação de nomes dos fornecedores e produtos</summary>

```sql
SELECT
    FORNECEDOR.nome_fornecedor,
    PRODUTO.nome_produto
FROM
    FORNECEDOR
JOIN
    PRODUTO ON FORNECEDOR.fornecedor_id = PRODUTO.produto_id;
```

</details>

## Objetivo

O objetivo deste desafio é refinar o modelo lógico de banco de dados para atender aos requisitos do cenário de e-commerce, aplicando boas práticas de modelagem e normalização, além de garantir uma implementação eficiente e funcional para atender às perguntas e casos de uso definidos.

## Conclusão

Este projeto é uma prática abrangente de modelagem e manipulação de dados em um cenário de e-commerce. A abordagem proposta permite implementar um banco de dados robusto e eficiente, além de fornecer insights úteis através de consultas SQL complexas.

# Projeto de Índices e Procedures em Banco de Dados

## Parte 1 – Criando Índices no Banco de Dados

Neste projeto, o foco é a otimização de consultas (queries) em um cenário de "Company", utilizando a criação de índices para melhorar a performance das buscas. As consultas definidas para recuperação de informações vão nortear a escolha e aplicação dos índices nas tabelas do banco de dados.

### Objetivo da Criação de Índices

A criação de índices deve ser realizada com base nos seguintes critérios:
- Dados mais acessados: Quais colunas são frequentemente usadas em consultas `SELECT`, `JOIN`, ou como filtro em `WHERE`.
- Dados mais relevantes no contexto: Quais informações são críticas para a performance do banco de dados.
  
A função dos índices é acelerar a busca e recuperação dos dados no SGBD (Sistema de Gerenciamento de Banco de Dados). No entanto, índices também consomem espaço e afetam o desempenho de operações de escrita (`INSERT`, `UPDATE`, `DELETE`). Portanto, devem ser criados apenas para as colunas realmente necessárias.

### Perguntas e Índices Criados

1. **Qual o departamento com maior número de pessoas?**
   - **Query**: Consulta que faz uma contagem de empregados por departamento e ordena para encontrar o maior.
   - **Índice Sugerido**: Índice na coluna `departamento_id` da tabela de empregados para agilizar a contagem e agrupamento.
     - **Tipo de Índice**: `B-TREE`, devido à necessidade de ordenação e contagem dos dados.
   
   <details>
   <summary>Script de Criação do Índice</summary>

   ```sql
   CREATE INDEX idx_empregados_departamento ON empregados(departamento_id) USING BTREE;
   ```

   </details>

2. **Quais são os departamentos por cidade?**
   - **Query**: Recupera uma lista de departamentos junto com a cidade onde estão localizados.
   - **Índice Sugerido**: Índice na coluna `cidade_id` da tabela de departamentos para melhorar a busca e a junção de dados entre departamentos e cidades.
     - **Tipo de Índice**: `B-TREE`, pois será utilizado para buscas e junções de dados.
   
   <details>
   <summary>Script de Criação do Índice</summary>

   ```sql
   CREATE INDEX idx_departamentos_cidade ON departamentos(cidade_id) USING BTREE;
   ```

   </details>

3. **Relação de empregados por departamento**
   - **Query**: Lista todos os empregados de cada departamento.
   - **Índice Sugerido**: Índice na coluna `departamento_id` da tabela de empregados (aproveitando o índice já criado para a primeira pergunta).
   
### Justificativas para os Índices Criados

- A coluna `departamento_id` é crucial para consultas que agrupam empregados por departamento, tornando-a uma candidata perfeita para um índice `B-TREE`.
- A coluna `cidade_id` na tabela de departamentos é frequentemente usada para relacionar cidades e departamentos, o que justifica a criação de um índice `B-TREE`.
  
### Exemplos de Consultas SQL

<details>
<summary>1. Consulta para encontrar o departamento com maior número de pessoas</summary>

```sql
SELECT 
    departamento_id,
    COUNT(empregado_id) AS total_empregados
FROM 
    empregados
GROUP BY 
    departamento_id
ORDER BY 
    total_empregados DESC
LIMIT 1;
```

</details>

<details>
<summary>2. Consulta para listar departamentos por cidade</summary>

```sql
SELECT 
    d.nome_departamento,
    c.nome_cidade
FROM 
    departamentos d
JOIN 
    cidades c ON d.cidade_id = c.cidade_id;
```

</details>

<details>
<summary>3. Relação de empregados por departamento</summary>

```sql
SELECT 
    e.nome_empregado,
    d.nome_departamento
FROM 
    empregados e
JOIN 
    departamentos d ON e.departamento_id = d.departamento_id;
```

</details>

---

## Parte 2 – Utilização de Procedures para Manipulação de Dados

O objetivo desta parte é criar uma `procedure` que realize operações de inserção, atualização e remoção de dados no banco de dados, baseando-se em uma variável de controle para determinar qual ação executar.

### Estrutura da Procedure

A procedure deve conter:
- Instruções para **inserção**, **atualização** e **remoção** de dados, encapsuladas em estruturas condicionais como `CASE` ou `IF`.
- Uma variável de controle para selecionar a operação desejada: 
  - **1 – SELECT**
  - **2 – UPDATE**
  - **3 – DELETE**

### Exemplo de Procedure

<details>
<summary>Script SQL para a Criação da Procedure</summary>

```sql
DELIMITER //

CREATE PROCEDURE manipula_dados(
    IN acao INT,
    IN id INT,
    IN nome VARCHAR(100),
    IN departamento_id INT
)
BEGIN
    CASE acao
        WHEN 1 THEN -- SELECT
            SELECT * FROM empregados WHERE empregado_id = id;
        WHEN 2 THEN -- UPDATE
            UPDATE empregados SET nome = nome, departamento_id = departamento_id WHERE empregado_id = id;
        WHEN 3 THEN -- DELETE
            DELETE FROM empregados WHERE empregado_id = id;
        ELSE
            SIGNAL SQLSTATE '45000' SET MESSAGE_TEXT = 'Ação inválida';
    END CASE;
END //

DELIMITER ;
```

</details>

### Como Utilizar a Procedure

- **Para Selecionar um Empregado**: 
   ```sql
   CALL manipula_dados(1, 10, NULL, NULL);
   ```
   Retorna o registro do empregado com `id = 10`.

- **Para Atualizar um Empregado**: 
   ```sql
   CALL manipula_dados(2, 10, 'Novo Nome', 3);
   ```
   Atualiza o nome do empregado e seu departamento.

- **Para Deletar um Empregado**: 
   ```sql
   CALL manipula_dados(3, 10, NULL, NULL);
   ```
   Remove o registro do empregado com `id = 10`.

---

## Conclusão

Neste projeto, trabalhamos com a criação de índices para otimizar consultas de um cenário "Company", levando em consideração o acesso e relevância dos dados. Além disso, desenvolvemos uma `procedure` flexível para manipulação de dados, que permite operações de `SELECT`, `UPDATE` e `DELETE` de forma dinâmica.

# Projeto de Customização de Acessos com Views e Gatilhos para E-commerce

## Parte 1 – Personalizando Acessos com Views

Neste desafio, o objetivo é criar views (visões) para simplificar o acesso a informações importantes relacionadas aos empregados, departamentos e projetos. As views permitem a definição de regras de acesso personalizadas, melhorando a segurança e a usabilidade dos dados no banco.

### Objetivos

1. Criar views para os seguintes cenários:
   - **Número de empregados por departamento e localidade**
   - **Lista de departamentos e seus gerentes**
   - **Projetos com maior número de empregados** (ordenados de forma decrescente)
   - **Lista de projetos, departamentos e seus respectivos gerentes**
   - **Identificar quais empregados possuem dependentes e se são gerentes**

2. Definir permissões de acesso às views de acordo com o tipo de conta de usuário:
   - **Usuário Gerente**: Acesso a todas as informações de empregados e departamentos.
   - **Usuário Empregado**: Acesso restrito, sem permissão para visualizar dados relacionados aos departamentos ou gerentes.

### Exemplos de Views

<details>
<summary>1. Número de empregados por departamento e localidade</summary>

```sql
CREATE VIEW vw_num_empregados_depto_localidade AS
SELECT 
    d.nome_departamento,
    d.localidade,
    COUNT(e.empregado_id) AS total_empregados
FROM 
    departamentos d
JOIN 
    empregados e ON d.departamento_id = e.departamento_id
GROUP BY 
    d.nome_departamento, d.localidade;
```

</details>

<details>
<summary>2. Lista de departamentos e seus gerentes</summary>

```sql
CREATE VIEW vw_deptos_gerentes AS
SELECT 
    d.nome_departamento,
    e.nome AS nome_gerente
FROM 
    departamentos d
JOIN 
    empregados e ON d.gerente_id = e.empregado_id;
```

</details>

<details>
<summary>3. Projetos com maior número de empregados</summary>

```sql
CREATE VIEW vw_projetos_maior_num_empregados AS
SELECT 
    p.nome_projeto,
    COUNT(pe.empregado_id) AS total_empregados
FROM 
    projetos p
JOIN 
    projeto_empregado pe ON p.projeto_id = pe.projeto_id
GROUP BY 
    p.nome_projeto
ORDER BY 
    total_empregados DESC;
```

</details>

<details>
<summary>4. Lista de projetos, departamentos e gerentes</summary>

```sql
CREATE VIEW vw_projetos_deptos_gerentes AS
SELECT 
    p.nome_projeto,
    d.nome_departamento,
    e.nome AS nome_gerente
FROM 
    projetos p
JOIN 
    departamentos d ON p.departamento_id = d.departamento_id
JOIN 
    empregados e ON d.gerente_id = e.empregado_id;
```

</details>

<details>
<summary>5. Empregados com dependentes e se são gerentes</summary>

```sql
CREATE VIEW vw_empregados_dependentes_gerentes AS
SELECT 
    e.nome AS nome_empregado,
    COUNT(d.dependente_id) AS total_dependentes,
    CASE 
        WHEN e.gerente_id IS NOT NULL THEN 'Sim'
        ELSE 'Não'
    END AS eh_gerente
FROM 
    empregados e
LEFT JOIN 
    dependentes d ON e.empregado_id = d.empregado_id
GROUP BY 
    e.nome, e.gerente_id;
```

</details>

### Definição de Permissões de Acesso

- **Usuário Gerente**: Pode visualizar todas as views criadas.
  ```sql
  CREATE USER 'gerente'@'%' IDENTIFIED BY 'senha_gerente';
  GRANT SELECT ON vw_num_empregados_depto_localidade TO 'gerente'@'%';
  GRANT SELECT ON vw_deptos_gerentes TO 'gerente'@'%';
  GRANT SELECT ON vw_projetos_maior_num_empregados TO 'gerente'@'%';
  GRANT SELECT ON vw_projetos_deptos_gerentes TO 'gerente'@'%';
  GRANT SELECT ON vw_empregados_dependentes_gerentes TO 'gerente'@'%';
  ```

- **Usuário Empregado**: Acesso limitado apenas a informações de empregados, sem permissão para acessar dados de departamentos ou gerentes.
  ```sql
  CREATE USER 'empregado'@'%' IDENTIFIED BY 'senha_empregado';
  GRANT SELECT ON vw_empregados_dependentes_gerentes TO 'empregado'@'%';
  ```

---

## Parte 2 – Criando Gatilhos para o Cenário de E-commerce

Gatilhos (ou triggers) são utilizados para automatizar ações no banco de dados antes ou depois de operações de `INSERT`, `UPDATE`, ou `DELETE`. Neste projeto, serão criados triggers para tratar casos específicos de remoção e atualização de dados.

### Objetivo dos Gatilhos

1. **Triggers de Remoção (`BEFORE DELETE`)**: 
   - Quando um usuário decide excluir sua conta, o trigger deve criar uma cópia dos dados antes da remoção para evitar a perda de informações importantes.
   
   <details>
   <summary>Exemplo de Trigger para Remoção</summary>

   ```sql
   CREATE TRIGGER trg_before_delete_usuario
   BEFORE DELETE ON usuarios
   FOR EACH ROW
   BEGIN
       INSERT INTO usuarios_excluidos (usuario_id, nome, data_exclusao)
       VALUES (OLD.usuario_id, OLD.nome, NOW());
   END;
   ```

   </details>

2. **Triggers de Atualização (`BEFORE UPDATE`)**: 
   - Ao inserir novos colaboradores ou atualizar o salário base de um empregado, o trigger deve assegurar que o registro é atualizado corretamente, evitando inconsistências de dados.

   <details>
   <summary>Exemplo de Trigger para Atualização</summary>

   ```sql
   CREATE TRIGGER trg_before_update_empregado
   BEFORE UPDATE ON empregados
   FOR EACH ROW
   BEGIN
       -- Validar aumento salarial maior que 0
       IF NEW.salario < 0 THEN
           SIGNAL SQLSTATE '45000' SET MESSAGE_TEXT = 'Salário inválido';
       END IF;
   END;
   ```

   </details>

---

## Conclusão

Este projeto aborda a criação de views para facilitar o acesso a dados sensíveis e melhorar a performance de consultas, ao mesmo tempo em que define regras de acesso personalizadas para diferentes tipos de usuários. Além disso, são implementados gatilhos (triggers) para garantir a integridade dos dados durante operações de remoção e atualização.

# Projeto de Transações, Procedures, Backup e Recovery no MySQL

## PARTE 1 – Trabalhando com Transações

O objetivo desta etapa do projeto é praticar o uso de transações no MySQL para realizar operações de consulta e modificação de dados no banco de dados. Transações são usadas para garantir que um conjunto de operações no banco de dados seja executado de forma atômica, ou seja, todas as operações são concluídas com sucesso ou nenhuma alteração é realizada, garantindo a consistência dos dados.

### Passos para a Criação de Transações

1. **Desabilitar o Autocommit**
   - Antes de iniciar uma transação, é necessário desabilitar o autocommit no MySQL. Isso impede que cada instrução SQL seja confirmada automaticamente.
   - **Exemplo de Código**:
   
   ```sql
   SET autocommit = 0;
   START TRANSACTION;
   ```

2. **Executar Statements Dentro da Transação**
   - Realizar operações de `INSERT`, `UPDATE` ou `DELETE` dentro da transação para modificar dados de forma controlada.
   - **Exemplo de Código**:
   
   ```sql
   -- Inserção de um novo cliente
   INSERT INTO clientes (nome, email) VALUES ('Paula Santos', 'paula@exemplo.com');

   -- Atualização de um pedido existente
   UPDATE pedidos SET status = 'Enviado' WHERE pedido_id = 101;

   -- Verificação dos dados alterados
   SELECT * FROM clientes;
   ```

3. **Confirmação ou Cancelamento da Transação**
   - Após executar todas as operações necessárias, finalize a transação usando `COMMIT` para confirmar as alterações ou `ROLLBACK` para desfazer caso ocorra algum erro.
   - **Exemplo de Código**:
   
   ```sql
   COMMIT;
   -- Caso algo dê errado:
   -- ROLLBACK;
   ```

---

## PARTE 2 – Transação com Procedure

Nesta parte, você deve criar uma transação dentro de uma `procedure`, incluindo uma verificação de erro que possa disparar um `ROLLBACK` total ou parcial (utilizando `SAVEPOINT`).

### Passos para Criar uma Transação com Procedure

1. **Criar a Procedure**
   - Crie uma `procedure` para realizar operações de modificação de dados e encapsular a lógica da transação.
   - Inclua uma variável para capturar possíveis erros e realizar um `ROLLBACK` em caso de falha.
   
   **Exemplo de Código**:
   
   ```sql
   DELIMITER //

   CREATE PROCEDURE transacao_modificacao(
       IN pedido_id INT,
       IN novo_status VARCHAR(50)
   )
   BEGIN
       DECLARE EXIT HANDLER FOR SQLEXCEPTION
       BEGIN
           ROLLBACK; -- Reverte todas as alterações em caso de erro
           SIGNAL SQLSTATE '45000' SET MESSAGE_TEXT = 'Erro na transação';
       END;

       -- Desabilitar autocommit
       SET autocommit = 0;

       START TRANSACTION;

       -- Atualizar status do pedido
       UPDATE pedidos SET status = novo_status WHERE pedido_id = pedido_id;

       -- Verificar condição para criar SAVEPOINT
       IF novo_status = 'Cancelado' THEN
           SAVEPOINT antes_do_cancelamento;
           -- Lógica adicional, se necessário
       END IF;

       COMMIT; -- Confirma as alterações se tudo estiver correto
   END //

   DELIMITER ;
   ```

2. **Chamar a Procedure**
   - Utilize a `CALL` para executar a `procedure` com os parâmetros desejados.
   - **Exemplo de Código**:
   
   ```sql
   CALL transacao_modificacao(101, 'Em Preparação');
   ```

---

## PARTE 3 – Backup e Recovery

A última parte do desafio consiste em realizar o backup e recovery do banco de dados e-commerce. A ferramenta `mysqldump` será utilizada para realizar essas operações, permitindo a exportação de dados e sua recuperação futura.

### Passos para Executar o Backup e Recovery

1. **Backup do Banco de Dados**
   - Utilize o `mysqldump` para realizar um backup completo do banco de dados e-commerce.
   - **Exemplo de Código para Backup**:
   
   ```bash
   mysqldump -u usuario -p nome_do_banco > backup_ecommerce.sql
   ```

   Isso irá criar um arquivo `.sql` contendo todos os dados e estrutura do banco de dados.

2. **Incluir Recursos Adicionais no Backup**
   - É possível realizar o backup de procedimentos, eventos e outras funções.
   - **Exemplo de Código para Backup com Recursos Adicionais**:
   
   ```bash
   mysqldump -u usuario -p nome_do_banco --routines --events > backup_completo_ecommerce.sql
   ```

3. **Restaurar o Backup (Recovery)**
   - Para restaurar o banco de dados, utilize o arquivo `.sql` gerado pelo backup.
   - **Exemplo de Código para Recovery**:
   
   ```bash
   mysql -u usuario -p nome_do_banco < backup_ecommerce.sql
   ```

4. **Adicionar o Arquivo de Backup ao GitHub**
   - Adicione o arquivo de backup ao repositório GitHub juntamente com os scripts SQL criados anteriormente.

---

## Conclusão

Este projeto cobre o uso de transações no MySQL para modificação de dados, a criação de `procedures` para encapsular transações com lógica de verificação de erros e a realização de backup e recovery do banco de dados utilizando o `mysqldump`. A aplicação dessas práticas garante a integridade dos dados e a capacidade de recuperação em casos de falhas.

## Autor

Este projeto foi desenvolvido como parte de um desafio de modelagem de banco de dados para e-commerce, seguindo diretrizes propostas por um expert em modelagem de dados.

## Como Usar

1. Clone este repositório para sua máquina local.
2. Analise o diagrama ER para entender a estrutura conceitual do banco de dados.
3. Utilize o diagrama como base para a implementação do modelo físico no banco de dados relacional de sua escolha.
