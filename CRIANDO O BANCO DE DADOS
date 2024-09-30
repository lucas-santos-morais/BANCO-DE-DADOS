# BANCO-DE-DADOS
Fala pessoal! segue um código em MY SQL, meu primeiro código segue os passos para usar:

-- criando o banco de dados
create database db_faculdade;

-- usar o banco de dados criado
use db_faculdade;

-- verificar se foi criado
show DATABASE;

-- criando tabela pessoa 
create table tbl_pessoa (

id int not null primary key auto_increment,
nome varchar (45) not null,
sexo varchar (10),
email varchar (255) not null,
data_registro date not null,
data_nascimento date,
CPF varchar (20) not null,
RG varchar (20) not null
);

-- criando tabela endereço 
create table tbl_endereco (

id int not null primary key auto_increment,
logradouro varchar (45) not null,
CEP varchar (45) not null,
bairro varchar (45) not null,
cidade varchar (45) not null,
estado varchar (45) not null,
id_pessoa int not null,

-- relacionando com tabela pessoa
constraint fk_pessoa_endereco
foreign key (id_pessoa)
references tbl_pessoa (id)
);

-- criando tabela telefone
create table tbl_telefone(

id int not null primary key auto_increment,
numero varchar (45) not null,
id_pessoa int not null,

-- relacionando com tabela pessoa 
constraint fk_pessoa_telefone
foreign key (id_pessoa)
references tbl_pessoa (id)
);

-- criando tabela professor
create table tbl_professor(

id int not null primary key auto_increment,
especializacao varchar (45) not null,
salario decimal (10, 2) not null,
CFEP varchar (45) not null,
id_pessoa int not null,

-- relacionando com tabela pessoa
constraint fk_pessoa_professor
foreign key (id_pessoa)
references tbl_pessoa (id)
);

-- criando tabela coordenadores 
create table tbl_coordenadores(

id int not null primary key auto_increment,
quantidade_cursos int,
data_coordenador date,
id_professor int not null,

-- relacionando com tabela professor
constraint fk_professor_coordenadores
foreign key (id_professor)
references tbl_professor (id)
);

-- criando tabela materia 
create table tbl_materia(

id int not null primary key auto_increment,
nome_materia varchar (100) not null,
emenda text not null,
tempo_materia varchar (50) not null,
pre_requisito text not null,
plano_ensino text not null,
frequencia_minima varchar (45),
id_professor int not null,

-- relacionando com tabela professor
constraint fk_professor_materia
foreign key (id_professor)
references tbl_professor (id)
);

-- criando tabela curso 
create table tbl_curso(

id int not null primary key auto_increment,
nome_curso varchar (100) not null,
carga_horaria varchar (45) not null,
nivel varchar (30) not null,
id_materia int not null,
id_coordenadores int not null,

-- relacionando com tabela materia
constraint fk_materia_curso
foreign key (id_materia)
references tbl_materia (id),

-- relacionando com tabela coordenadores
constraint fk_coordenadores_curso
foreign key (id_coordenadores)
references tbl_coordenadores (id)
);

-- criando tabela campus 
create table tbl_campus(

id int not null primary key auto_increment,
nome_campus varchar (200) not null,
id_curso int not null,

-- relacionando tabela curso
constraint fk_curso_campus
foreign key (id_curso)
references tbl_curso (id)
);

-- criando tabela modalidade
create table tbl_modalidade(

id int not null primary key auto_increment,
tipo varchar (30) not null,
periodo varchar (45) not null,
metodologia varchar (45) not null,
id_curso int not null,


-- relacionando tabela curso
constraint fk_curso_modalidade
foreign key (id_curso)
references tbl_curso (id)
);

-- criando tabela turma 
create table tbl_turma(

id int not null primary key auto_increment,
semestre varchar (20) not null,
turno varchar (30) not null,
ano date,
id_professor int not null,


-- relacionando tabela professor
constraint fk_professor_turma
foreign key (id_professor)
references tbl_professor (id)
);


-- criando tabela aluno 
create table tbl_aluno(

id int not null primary key auto_increment,
matricula int not null,
desconto varchar (50) not null,
id_pessoa int not null,
id_curso int not null,

-- relacionando tabela pessoa
constraint fk_pessoa_aluno
foreign key (id_pessoa)
references tbl_pessoa (id),

-- relacionando tabela curso
constraint fk_curso_aluno
foreign key (id_curso)
references tbl_curso (id)
);

-- criando tabela aluno e turma
create table tbl_aluno_e_turma(
id_aluno int not null,
id_turma int not null,

-- relaciondando tabela aluno 
constraint fk_aluno_aluno_e_turma
foreign key (id_aluno)
references tbl_aluno (id),

-- relaciondando tabela turma
constraint fk_turma_aluno_e_turma
foreign key (id_turma)
references tbl_turma (id)
);

-- criando tabela nota
create table tbl_nota(

id int not null primary key auto_increment,
valor float not null,
data_avaliacao date not null,
tipo_nota varchar (30) not null,
id_aluno int not null,
id_turma int not null,
id_materia int not null,

-- relaciondando tabela aluno 
constraint fk_aluno_nota
foreign key (id_aluno)
references tbl_aluno (id),

-- relaciondando tabela turma
constraint fk_turma_nota
foreign key (id_turma)
references tbl_turma (id),

-- relaciondando tabela materia
constraint fk_materia_nota
foreign key (id_materia)
references tbl_materia (id)
);

-- criando tabela perfil 
create table tbl_perfil(

id int not null primary key auto_increment,
usuario varchar (100) not null,
senha varchar (255) not null,
nivel_acesso varchar (45) not null,
data_criacao date not null,
tipo_usuario varchar (45) not null,
email_recuperacao varchar (255),
ultimo_acesso date not null,
id_aluno int,
id_professor int,

-- relaciondando tabela aluno 
constraint fk_aluno_perfil
foreign key (id_aluno)
references tbl_aluno (id),

-- relaciondando tabela prefessor 
constraint fk_professor_perfil
foreign key (id_professor)
references tbl_professor (id),


-- restrição para garantir que apenas um dos campos seja preenchido  
constraint chk_aluno_professor CHECK (  
    (id_aluno IS NOT NULL AND id_professor IS NULL) OR  
    (id_aluno IS NULL AND id_professor IS NOT NULL)  
) 
);
 -- para visualisar as tabelas
show tables;
