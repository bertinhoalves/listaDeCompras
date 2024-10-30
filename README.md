# listaDeCompras

# Casos de Uso

- Cadastrar Produto: 
O usuário deve ser capaz de inserir o nome do produto e o seu valor, e o sistema deve ser capaz de inserir no banco de dados

- Consultar produto: 
O usuário deve inserir palavras para encontrar o produto em lista

- Alterar dados dos produtos: 
O usuário deve ser capaz de alterar o nome do produto, e o sistema deve ser capaz de armazenar a alteração

- Remover o produto: 
O usuário deve ser capaz de remover o produto 

- Cadastrar lista: 
O usuário deve ser capaz de cadastrar lista com os seguintes dados 
. Local 
. Valor 
. data 

- Editar lista: 
O usuário deve ser capaz de editar dados de uma lista

- Inserir produtos na lista: 
O usuário deve ser capaz de inserir um produto em uma determinada lista

- Remover lista: 
O usuário deve ser capaz de remover um produto de uma lista.

- Fechamento de custo: 
O usuário deve ser capaz de visualizar o fechamento da lista com a somatória do valor de cada produto d lista.



SCRIPT DAS RELAÇÕES ENTRE AS TABELAS:
```sql
-- MySQL Workbench Forward Engineering

SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0; 
SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0; 
SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION';

-- Schema ListaSupermercado

CREATE SCHEMA IF NOT EXISTS ListaSupermercado DEFAULT CHARACTER SET utf8 ; 
USE ListaSupermercado ;

-- Table ListaSupermercado.Produto

CREATE TABLE IF NOT EXISTS ListaSupermercado.Produto ( 
    idProduto INT NOT NULL, 
    nome VARCHAR(45) NULL, 
    PRIMARY KEY (idProduto)
) ENGINE = InnoDB;

-- Table ListaSupermercado.Lista

CREATE TABLE IF NOT EXISTS ListaSupermercado.Lista ( 
    idLista INT NOT NULL, 
    data DATE NOT NULL, 
    nomeMercado VARCHAR(45) NULL, 
    valorTotal DOUBLE NULL, 
    status INT NULL, 
    PRIMARY KEY (idLista)
) ENGINE = InnoDB;

-- Table ListaSupermercado.ItemLista

CREATE TABLE IF NOT EXISTS ListaSupermercado.ItemLista ( 
    idItemLista INT NOT NULL, 
    quantidade VARCHAR(45) NULL, 
    preco VARCHAR(45) NULL, 
    concluido VARCHAR(45) NULL, 
    Lista_idLista INT NOT NULL, 
    Produto_idProduto INT NOT NULL, 
    PRIMARY KEY (idItemLista, Lista_idLista, Produto_idProduto), 
    INDEX fk_ItemLista_Lista_idx (Lista_idLista ASC) VISIBLE, 
    INDEX fk_ItemLista_Produto1_idx (Produto_idProduto ASC) VISIBLE, 
    CONSTRAINT fk_ItemLista_Lista FOREIGN KEY (Lista_idLista) REFERENCES ListaSupermercado.Lista (idLista) ON DELETE NO ACTION ON UPDATE NO ACTION, 
    CONSTRAINT fk_ItemLista_Produto1 FOREIGN KEY (Produto_idProduto) REFERENCES ListaSupermercado.Produto (idProduto) ON DELETE NO ACTION ON UPDATE NO ACTION
) ENGINE = InnoDB;

SET SQL_MODE=@OLD_SQL_MODE; 
SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS; 
SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS;
```
