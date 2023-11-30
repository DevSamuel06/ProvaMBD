# Prova Final Modelagem Banco De Dados  
Uma escola entrou em contato buscando a implementação de um sistema abrangente para gerenciar suas operações educacionais, incluindo informações sobre alunos, professores, cursos e matrículas. Cada aluno, como requisito essencial, terá um perfil detalhado com atributos como notas e dados de contato, enquanto cada professor terá um perfil associado, indicando disciplinas lecionadas e outros detalhes relevantes. Além disso, o sistema permitirá registrar e monitorar as matrículas dos alunos em diferentes turmas e cursos ao longo do tempo. Para atender a essas necessidades, a proposta é desenvolver o sistema utilizando o SQLServer como sistema de gerenciamento de banco de dados, assegurando uma estrutura sólida e eficiente para a gestão integrada das atividades educacionais.

# Criação do banco de dados

## Entidades:
Aluno<br>
Professor
Curso
Turma
Matrícula

## Atributos:
Aluno:
Nome (simples)
Data de Nascimento (simples)
Endereço (composto: rua, cidade, estado)
Telefone (multivalorado)
Nota Média (derivado)
ID do Aluno (atributo chave)

Professor:
Nome (simples)
Data de Nascimento (simples)
Endereço (composto: rua, cidade, estado)
Telefone (multivalorado)
Disciplina Lecionada (multivalorado)
ID do Professor (atributo chave)

Curso:
Nome do Curso (simples)
Código do Curso (simples)
Carga Horária (simples)
ID do Curso (atributo chave)

Turma:
Ano de Ingresso (simples)
Período (simples)
Sala (simples)
ID da Turma (atributo chave)

Matrícula:
Data de Matrícula (simples)
Situação da Matrícula (simples: ativa, trancada, concluída)
ID da Matrícula (atributo chave)





