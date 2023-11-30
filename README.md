# Prova Final Modelagem Banco De Dados  
Uma escola entrou em contato buscando a implementação de um sistema abrangente para gerenciar suas operações educacionais, incluindo informações sobre alunos, professores, cursos e matrículas. Cada aluno, como requisito essencial, terá um perfil detalhado com atributos como notas e dados de contato, enquanto cada professor terá um perfil associado, indicando disciplinas lecionadas e outros detalhes relevantes. Além disso, o sistema permitirá registrar e monitorar as matrículas dos alunos em diferentes turmas e cursos ao longo do tempo. Para atender a essas necessidades, a proposta é desenvolver o sistema utilizando o SQLServer como sistema de gerenciamento de banco de dados, assegurando uma estrutura sólida e eficiente para a gestão integrada das atividades educacionais.

# Criação do banco de dados

## Entidades:
Aluno<br>
Professor<br>
Curso<br>
Turma<br>
Matrícula<br>

## Atributos:
Aluno:<br>
Nome (simples)<br>
Data de Nascimento (simples)<br>
Endereço (composto: rua, cidade, estado)<br>
Telefone (multivalorado)<br>
Nota Média (derivado)<br>
ID do Aluno (atributo chave)<br>

Professor:<br>
Nome (simples)<br>
Data de Nascimento (simples)<br>
Endereço (composto: rua, cidade, estado)<br>
Telefone (multivalorado)<br>
Disciplina Lecionada (multivalorado)<br>
ID do Professor (atributo chave)<br>

Curso:<br>
Nome do Curso (simples)<br>
Código do Curso (simples)<br>
Carga Horária (simples)<br>
ID do Curso (atributo chave)<br>

Turma:<br>
Ano de Ingresso (simples)<br>
Período (simples)<br>
Sala (simples)<br>
ID da Turma (atributo chave)<br>

Matrícula:<br>
Data de Matrícula (simples)<br>
Situação da Matrícula (simples: ativa, trancada, concluída)<br>
ID da Matrícula (atributo chave)<br>

## Relacionamentos:

Aluno e Matrícula (Muitos para Muitos - N:N):<br>
 Um aluno pode se matricular em vários cursos.<br>
 Uma matrícula pode envolver vários alunos.<br>

Aluno e Turma (Muitos para Muitos - N:N):<br>
 Um aluno pode pertencer a várias turmas.<br>
 Uma turma pode ter vários alunos.<br>

Curso e Turma (Um para Muitos - 1:N):<br>
 Um curso pode ter várias turmas.<br>
 Uma turma pertence a apenas um curso.<br>

Professor e Curso (Um para Muitos - 1:N):<br>
 Um professor pode lecionar vários cursos.<br>
 Um curso é lecionado por apenas um professor.<br>

Turma e Matrícula (Um para Muitos - 1:N):<br>
 Uma turma pode ter várias matrículas.<br>
 Uma matrícula pertence a apenas uma turma<br>

# D.E.R (Diagrama Entidade Relacionamento)

![Captura de tela 2023-11-30 124538](https://github.com/DevSamuel06/ProvaMBD/assets/124092317/ab3afe24-4dd7-49f7-ab9e-1d1baf29aa4e)

# Modelagem Lógica 


# Modelagem física

## Criação de Tabelas

CREATE TABLE Aluno (<br>
    AlunoID INT PRIMARY KEY IDENTITY(1,1),<br>
    Nome VARCHAR(255),<br>
    DataNascimento DATE,<br>
    EnderecoRua VARCHAR(255),<br>
    EnderecoCidade VARCHAR(255),<br>
    EnderecoEstado VARCHAR(255),<br>
    Telefone VARCHAR(20),<br>
    NotaMedia FLOAT<br>
);<br>

CREATE TABLE Professor (<br>
    ProfessorID INT PRIMARY KEY IDENTITY(1,1),<br>
    Nome VARCHAR(255),<br>
    DataNascimento DATE,<br>
    EnderecoRua VARCHAR(255),<br>
    EnderecoCidade VARCHAR(255),<br>
    EnderecoEstado VARCHAR(255),<br>
    Telefone VARCHAR(20),<br>
    DisciplinaLecionada VARCHAR(255)<br>
);<br>

CREATE TABLE Curso (<br>
    CursoID INT PRIMARY KEY IDENTITY(1,1),<br>
    NomeCurso VARCHAR(255),<br>
    CodigoCurso VARCHAR(20),<br>
    CargaHoraria INT<br>
);<br>

CREATE TABLE Turma (<br>
    TurmaID INT PRIMARY KEY IDENTITY(1,1),<br>
    AnoIngresso INT,<br>
    Periodo VARCHAR(10),<br>
    Sala VARCHAR(10),<br>
    CursoID INT,<br>
    FOREIGN KEY (CursoID) REFERENCES Curso(CursoID)<br>
);<br>

CREATE TABLE Matricula (<br>
    MatriculaID INT PRIMARY KEY IDENTITY(1,1),<br>
    DataMatricula DATE,<br>
    SituacaoMatricula VARCHAR(20),<br>
    AlunoID INT,<br>
    TurmaID INT,<br>
    FOREIGN KEY (AlunoID) REFERENCES Aluno(AlunoID),<br>
    FOREIGN KEY (TurmaID) REFERENCES Turma(TurmaID)<br>
);<br>
