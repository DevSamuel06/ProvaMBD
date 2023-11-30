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





