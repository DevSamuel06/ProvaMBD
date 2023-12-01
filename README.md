# Prova Final Modelagem Banco De Dados  

## Cenario:
Uma escola entrou em contato buscando a implementação de um sistema abrangente para gerenciar suas operações educacionais, incluindo informações sobre alunos, professores, cursos e matrículas. Cada aluno, como requisito essencial, terá um perfil detalhado com atributos como notas e dados de contato, enquanto cada professor terá um perfil associado, indicando disciplinas lecionadas e outros detalhes relevantes. Além disso, o sistema permitirá registrar e monitorar as matrículas dos alunos em diferentes turmas e cursos ao longo do tempo. Para atender a essas necessidades, a proposta é desenvolver o sistema utilizando o SQLServer como sistema de gerenciamento de banco de dados, assegurando uma estrutura sólida e eficiente para a gestão integrada das atividades educacionais.

# Modelagem Conceitual

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

## D.E.R (Diagrama Entidade Relacionamento)

![Captura de tela 2023-11-30 124538](https://github.com/DevSamuel06/ProvaMBD/assets/124092317/ab3afe24-4dd7-49f7-ab9e-1d1baf29aa4e)

# Modelagem Lógica 

![Captura de tela 2023-11-30 212001](https://github.com/DevSamuel06/ProvaMBD/assets/124092317/3f243216-c963-42e2-ae26-07d13d727306)


# Dados
## Criando Tabelas
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

## Inserindo dados

INSERT INTO Aluno (Nome, DataNascimento, EnderecoRua, EnderecoCidade, EnderecoEstado, Telefone, NotaMedia)<br>
VALUES<br>
    ('João Silva', '1990-05-15', 'Rua A', 'Cidade X', 'Estado Y', '123456789', 8.5),<br>
    ('Maria Oliveira', '1992-08-22', 'Rua B', 'Cidade Z', 'Estado W', '987654321', 9.2),<br>
    ('Ana Souza', '1995-04-12', 'Rua C', 'Cidade X', 'Estado Y', '123456789', 8.8),<br>
    ('Pedro Santos', '1993-11-30', 'Rua D', 'Cidade Y', 'Estado X', '555666777', 7.5),<br>
    ('Mariana Lima', '1994-07-17', 'Rua E', 'Cidade Z', 'Estado W', '111222333', 8.0),<br>
    ('Lucas Pereira', '1991-02-05', 'Rua F', 'Cidade X', 'Estado Y', '444555666', 9.5),<br>
    ('Julia Costa', '1990-09-20', 'Rua G', 'Cidade Z', 'Estado W', '999888777', 7.9),<br>
	('Maria Oliveira', '1992-08-22', 'Rua B', 'Cidade Z', 'Estado W', '987654321', 9.2),<br>
    ('Gabriel Oliveira', '1993-06-15', 'Rua H', 'Cidade Y', 'Estado X', '222333444', 8.2),<br>
    ('Larissa Silva', '1996-01-25', 'Rua I', 'Cidade X', 'Estado Y', '777888999', 9.0),<br>
    ('Felipe Santos', '1992-03-18', 'Rua J', 'Cidade Z', 'Estado W', '666777888', 7.7),<br>
    ('Camila Lima', '1994-10-10', 'Rua K', 'Cidade Y', 'Estado X', '333444555', 8.7),<br>
    ('Rafael Oliveira', '1993-08-08', 'Rua L', 'Cidade Z', 'Estado W', '123987456', 8.9),<br>
    ('Bianca Pereira', '1995-12-03', 'Rua M', 'Cidade X', 'Estado Y', '456789012', 9.1),<br>
    ('Vinicius Costa', '1991-04-30', 'Rua N', 'Cidade Z', 'Estado W', '789012345', 7.4),<br>
    ('Fernanda Santos', '1990-07-22', 'Rua O', 'Cidade Y', 'Estado X', '234567890', 8.4),<br>
    ('Eduardo Lima', '1992-11-15', 'Rua P', 'Cidade X', 'Estado Y', '567890123', 9.3),<br>
    ('Carolina Oliveira', '1994-05-01', 'Rua Q', 'Cidade Z', 'Estado W', '890123456', 7.2),<br>
    ('Guilherme Santos', '1993-09-28', 'Rua R', 'Cidade Y', 'Estado X', '345678901', 8.6),<br>
    ('Amanda Lima', '1991-06-20', 'Rua S', 'Cidade Z', 'Estado W', '012345678', 9.4),<br>
    ('Thiago Costa', '1995-02-14', 'Rua T', 'Cidade X', 'Estado Y', '876543210', 7.6);<br>

INSERT INTO Professor (Nome, DataNascimento, EnderecoRua, EnderecoCidade, EnderecoEstado, Telefone, DisciplinaLecionada)<br>
VALUES<br>
    ('Carlos Santos', '1980-03-10', 'Rua D', 'Cidade Y', 'Estado X', '111222333', 'Matemática'),<br>
    ('Ana Pereira', '1975-12-05', 'Rua E', 'Cidade Z', 'Estado W', '444555666', 'História'),<br>
    ('Paulo Oliveira', '1985-06-18', 'Rua F', 'Cidade X', 'Estado Y', '777888999', 'Física'),<br>
    ('Larissa Costa', '1982-10-30', 'Rua G', 'Cidade Z', 'Estado W', '123987456', 'Química'),<br>
    ('Ricardo Santos', '1978-09-15', 'Rua H', 'Cidade Y', 'Estado X', '222333444', 'Biologia'),<br>
    ('Fernanda Lima', '1983-04-22', 'Rua I', 'Cidade X', 'Estado Y', '789012345', 'Geografia'),<br>
    ('Lucas Costa', '1987-01-08', 'Rua J', 'Cidade Z', 'Estado W', '345678901', 'Educação Física'),<br>
    ('Mariana Oliveira', '1989-08-03', 'Rua K', 'Cidade Y', 'Estado X', '012345678', 'Artes'),<br>
    ('Eduardo Pereira', '1981-05-12', 'Rua L', 'Cidade Z', 'Estado W', '456789012', 'Inglês'),<br>
    ('Camila Santos', '1984-11-25', 'Rua M', 'Cidade X', 'Estado Y', '876543210', 'Português'),<br>
    ('Vinicius Lima', '1986-07-19', 'Rua N', 'Cidade Z', 'Estado W', '234567890', 'História da Arte'),<br>
    ('Amanda Oliveira', '1988-02-14', 'Rua O', 'Cidade Y', 'Estado X', '567890123', 'Matemática Aplicada'),<br>
    ('Thiago Costa', '1990-09-28', 'Rua P', 'Cidade X', 'Estado Y', '987654321', 'Sociologia'),<br>
    ('Carolina Pereira', '1992-04-05', 'Rua Q', 'Cidade Z', 'Estado W', '345678901', 'Filosofia'),<br>
    ('Guilherme Lima', '1994-11-20', 'Rua R', 'Cidade Y', 'Estado X', '012345678', 'Espanhol'),<br>
    ('Bianca Santos', '1996-06-15', 'Rua S', 'Cidade Z', 'Estado W', '345678901', 'Economia'),<br>
    ('Fernando Oliveira', '1989-03-01', 'Rua T', 'Cidade X', 'Estado Y', '987654321', 'Psicologia'),<br>
    ('Isabela Lima', '1991-08-08', 'Rua U', 'Cidade Z', 'Estado W', '234567890', 'Computação'),<br>
    ('Rafael Pereira', '1993-01-25', 'Rua V', 'Cidade Y', 'Estado X', '567890123', 'Engenharia'),<br>
    ('Juliana Costa', '1995-06-10', 'Rua X', 'Cidade Z', 'Estado W', '789012345', 'Medicina');<br>

INSERT INTO Curso (NomeCurso, CodigoCurso, CargaHoraria)<br>
VALUES<br>
    ('Engenharia Civil', 'EC101', 4000),<br>
    ('História da Arte', 'HA201', 300),<br>
    ('Administração', 'AD301', 3500),<br>
    ('Ciência da Computação', 'CC401', 4200),<br>
    ('Biologia', 'BI501', 3800),<br>
    ('Economia', 'EC601', 3200),<br>
    ('Psicologia', 'PS701', 4000),<br>
    ('Medicina', 'ME801', 6000),<br>
    ('Arquitetura', 'AR901', 4500),<br>
    ('Direito', 'DI1001', 4200),<br>
    ('Engenharia Elétrica', 'EE1101', 4800),<br>
    ('Matemática', 'MA1201', 3500),<br>
    ('Comunicação Social', 'CS1301', 3000),<br>
    ('Nutrição', 'NU1401', 3600),<br>
    ('Fisioterapia', 'FI1501', 4000),<br>
    ('Engenharia Química', 'EQ1601', 4200),<br>
    ('Letras', 'LE1701', 3200),<br>
    ('Gastronomia', 'GA1801', 2800),<br>
    ('DSM', 'MV2004', 8200);<br>

INSERT INTO Turma (AnoIngresso, Periodo, Sala, CursoID)<br>
VALUES<br>
    (2022, '1ºSemestre', 'A101', 1),<br>
    (2023, '2ºSemestre', 'B201', 2),<br>
    (2022, '1ºSemestre', 'C301', 3),<br>
    (2023, '2ºSemestre', 'D401', 4),<br>
    (2022, '1ºSemestre', 'E501', 5),<br>
    (2023, '2ºSemestre', 'F601', 6),<br>
    (2022, '1ºSemestre', 'G701', 7),<br>
    (2023, '2ºSemestre', 'H801', 8),<br>
    (2022, '1ºSemestre', 'I901', 9),<br>
    (2023, '2ºSemestre', 'J1001', 10),<br>
    (2022, '1ºSemestre', 'K1101', 11),<br>
    (2023, '2ºSemestre', 'L1201', 12),<br>
    (2022, '1ºSemestre', 'M1301', 13),<br>
    (2023, '2ºSemestre', 'N1401', 14),<br>
    (2022, '1ºSemestre', 'O1501', 15),<br>
    (2023, '2ºSemestre', 'P1601', 16),<br>
    (2022, '1ºSemestre', 'Q1701', 17),<br>
    (2023, '2ºSemestre', 'R1801', 18),<br>
    (2022, '1ºSemestre', 'S1901', 19),<br>
    (2023, '2ºSemestre', 'T2001', 20);<br>

INSERT INTO Matricula (DataMatricula, SituacaoMatricula, AlunoID, TurmaID)<br>
VALUES<br>
    ('2022-01-15', 'Ativa', 1, 47),<br>
    ('2023-03-20', 'Trancada', 2, 48),<br>
    ('2022-02-10', 'Ativa', 3, 49),<br>
    ('2023-04-25', 'Concluída', 4, 50),<br>
    ('2022-03-18', 'Ativa', 5, 51),<br>
    ('2023-05-15', 'Trancada', 6, 52),<br>
    ('2022-04-22', 'Ativa', 7, 53),<br>
    ('2023-06-30', 'Concluída', 8, 54),<br>
    ('2022-05-12', 'Ativa', 9, 55),<br>
    ('2023-07-20', 'Trancada', 10, 56),<br>
    ('2022-06-15', 'Ativa', 11, 57),<br>
    ('2023-08-10', 'Concluída', 12, 58),<br>
    ('2022-07-22', 'Ativa', 13, 59),<br>
    ('2023-09-05', 'Trancada', 14, 60),<br>
    ('2022-08-08', 'Ativa', 15, 61),<br>
    ('2023-10-15', 'Concluída', 16, 62),<br>
    ('2022-09-20', 'Ativa', 17, 63),<br>
    ('2023-11-18', 'Trancada', 18, 64),<br>
    ('2022-10-12', 'Ativa', 19, 65),<br>
    ('2023-12-30', 'Concluída', 20, 66);<br>

## CRUD

Insert:<br>
![Captura de tela 2023-11-30 163322](https://github.com/DevSamuel06/ProvaMBD/assets/124092317/cce22d62-d095-4200-9410-3913cce7c371)

SELECT:<br>
![Captura de tela 2023-11-30 163357](https://github.com/DevSamuel06/ProvaMBD/assets/124092317/afe62a6e-4ea1-4c5b-a196-323668b98b38)

UPDATE:<br>
![Captura de tela 2023-11-30 163419](https://github.com/DevSamuel06/ProvaMBD/assets/124092317/a1b09c56-34ce-4613-96cc-60c0ab17225d)

DELETE:<br>
![Captura de tela 2023-11-30 163610](https://github.com/DevSamuel06/ProvaMBD/assets/124092317/27195ceb-541f-4277-bfb2-c6520a1b09bf)

# Relatorios

Listar todos os alunos e suas matrículas:<br>
![Captura de tela 2023-11-30 172801](https://github.com/DevSamuel06/ProvaMBD/assets/124092317/e41faf52-c5dc-4bcc-8712-a6734ce68277)

Mostrar todos os cursos e as turmas associadas:<br>
![Captura de tela 2023-11-30 172823](https://github.com/DevSamuel06/ProvaMBD/assets/124092317/28769e9b-a50f-42f1-b889-6f665300808f)

Mostrar todos os alunos que estão em turmas do ano de 2022:<br>
![Captura de tela 2023-11-30 173337](https://github.com/DevSamuel06/ProvaMBD/assets/124092317/a0e6712b-d3c9-46ab-a027-ceff12482403)

Listar todos os alunos ordenados por nota média decrescente:<br>
![Captura de tela 2023-11-30 173401](https://github.com/DevSamuel06/ProvaMBD/assets/124092317/a392b30c-3bd5-42aa-bb2d-468362b83306)

Mostrar alunos que estão em turmas do período '1º Semestre':<br>
![Captura de tela 2023-11-30 173434](https://github.com/DevSamuel06/ProvaMBD/assets/124092317/44da1b08-1c18-475d-9686-d0aa3da2b5c8)

Exibir os cursos ordenados por carga horária crescente:<br>
![Captura de tela 2023-11-30 173455](https://github.com/DevSamuel06/ProvaMBD/assets/124092317/43b39521-b389-4b26-be19-1238aeeedcaa)

Listar todas as matrículas ativas e os alunos associados:<br>
![Captura de tela 2023-11-30 173516](https://github.com/DevSamuel06/ProvaMBD/assets/124092317/17812a0e-8723-4023-8091-54946adfe5f8)

Listar todas as matrículas concluídas e os alunos associados:<br>
![Captura de tela 2023-11-30 173626](https://github.com/DevSamuel06/ProvaMBD/assets/124092317/b95add7b-0af2-4563-9973-90b18ab622d7)

Mostrar todos os alunos que não estão matriculados em nenhuma turma:<br>
![Captura de tela 2023-11-30 173720](https://github.com/DevSamuel06/ProvaMBD/assets/124092317/0ac72bec-36d4-4df8-9283-12d7566209ec)

Lista todos os cursos com a contagem de alunos matriculados em cada curso:<br>
![Captura de tela 2023-11-30 174659](https://github.com/DevSamuel06/ProvaMBD/assets/124092317/17fbcc10-4305-4a95-879f-ef96a691ffa2)
