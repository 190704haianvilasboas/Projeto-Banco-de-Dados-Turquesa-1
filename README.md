# Projeto-Banco-de-Dados-Turquesa-1
A partir da criação de relacionamentos, cardinalidade, entidades e atributos criadas com o suporte do BR modelo, pudemos dar inicio a criação do nosso script SQL.
create table cliente ( 
 nome INT,  
 cpf INT ,  
 telefone INT,  
 ID_Cliente INT ,  
 primary key (nome,ID_Cliente)
); 

CREATE TABLE Colaborador 
( 
 Nome INT,  
 CPF INT,  
 ID_Colab INT ,  
 Dados_bank INT,  
 Tefelone INT,  
 primary key (ID_Colab)
); 

CREATE TABLE Produto 
( 
 Quant INT,  
 Cod_prod INT,  
 Identificação INT,  
 Preco INT, 
 primary key (Cod_prod)
); 

CREATE TABLE Pagamento 
( 
 pix INT,  
 Boleto INT,  
 Dinheiro INT,  
 Credito INT,  
 Id_pagamento INT ,  
 idCliente INT,  
 primary key (Id_pagamento)
); 

CREATE TABLE Filial 
( 
 Nome INT,  
 ID_FIlial INT ,  
 Endereco INT,  
 CNPJ INT ,
 primary key (ID_FIlial,CNPJ)
); 

CREATE TABLE Servico 
( 
 Especialidades INT,  
 Cod_Serv INT ,  
 Valor INT, 
 primary key (Cod_Serv )
); 

CREATE TABLE Turquesa 
( 
 Nome INT,  
 Endereco INT,  
 CNPJ INT ,  
primary key ( CNPJ)
); 


CREATE TABLE Franqueado 
( 
 ID_Fran INT ,  
 CPF INT,  
 Nome INT,  
 idFilial INT,  
primary key (ID_Fran)
); 

CREATE TABLE Prestacao_contratacao 
( 
 CPF INT ,  
 idProduto INT ,  
 Cod_Serv INT ,  
primary key (CPF,idProduto, Cod_Serv )
); 

CREATE TABLE Franquia 
( 
 ID_FIlial INT ,  
 CNPJ INT ,  
primary key (ID_FIlial, CNPJ )
); 

CREATE TABLE Contrata 
( 
 ID_Fran INT ,  
 ID_Colab INT,  
primary key (ID_Fran)
); 

CREATE TABLE Presta 
( 
 ID_Colab int,  
 Cod_Serv int ,  
primary key (ID_Colab,Cod_Serv)
); 

CREATE TABLE Avalia 
( 
 CPF INT ,  
 Cod_Serv INT,  
primary key (CPF, Cod_Serv)
); 

CREATE TABLE Vende 
( 
 idProduto INT ,  
 ID_Colab INT ,  
primary key (idProduto,ID_Colab )
); 

ALTER TABLE Pagamento ADD FOREIGN KEY(idCliente) REFERENCES Cliente (idCliente);
ALTER TABLE Franqueado ADD FOREIGN KEY(idFilial) REFERENCES Filial (idFilial);
ALTER TABLE Prestacao_contratacao ADD FOREIGN KEY(CPF) REFERENCES Cliente (CPF);
ALTER TABLE Prestacao_contratacao ADD FOREIGN KEY(idProduto) REFERENCES Produto (idProduto);
ALTER TABLE Prestacao_contratacao ADD FOREIGN KEY(Cod_Serv) REFERENCES Servico (Cod_Serv);
ALTER TABLE Franquia ADD FOREIGN KEY(ID_FIlial) REFERENCES Filial (ID_FIlial);
ALTER TABLE Franquia ADD FOREIGN KEY(CNPJ) REFERENCES Turquesa (CNPJ);


ALTER TABLE Contrata ADD FOREIGN KEY(ID_Fran) REFERENCES Franqueado (ID_Fran);
ALTER TABLE Contrata ADD FOREIGN KEY(ID_Colab) REFERENCES Colaborador (ID_Colab);
ALTER TABLE Presta ADD FOREIGN KEY(ID_Colab) REFERENCES Colaborador (ID_Colab);
ALTER TABLE Presta ADD FOREIGN KEY(Cod_Serv) REFERENCES Servico (Cod_Serv);
ALTER TABLE Avalia ADD FOREIGN KEY(CPF) REFERENCES Cliente (CPF);
ALTER TABLE Avalia ADD FOREIGN KEY(Cod_Serv) REFERENCES Servico (Cod_Serv);

ALTER TABLE Vende ADD FOREIGN KEY(idProduto) REFERENCES Produto (idProduto);
ALTER TABLE Vende ADD FOREIGN KEY(ID_Colab) REFERENCES Colaborador (ID_Colab);

select avalia from CPF;
