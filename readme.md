
Modelagem Dimensional de Faculdade - Fato Atuação Docente

# Modelagem Dimensional de Faculdade - Fato Atuação Docente

## Objetivo do Repositório

Este repositório tem como objetivo apresentar o processo de conversão de um modelo relacional de uma faculdade para um modelo dimensional do tipo estrela, focado na análise da atuação dos professores (docentes). O modelo dimensional criado visa permitir análises sobre a quantidade de disciplinas ministradas, alunos atendidos e a distribuição dos professores entre cursos e departamentos.

## 1. Modelo Relacional Original

O modelo relacional utilizado como ponto de partida possuía as seguintes tabelas:

- **Professor**: idProfessor (INT), departamento_idDepartamento (INT)
- **Departamento**: idDepartamento (INT), nome (VARCHAR), campus (VARCHAR), idProfessor_coordenador (INT)
- **Disciplina**: idDisciplina (INT), Professor_idProfessor (INT)
- **Curso**: idCurso (INT), Departamento_idDepartamento (INT)
- **Disciplina_Curso**: Disciplina_idDisciplina (INT), Curso_idCurso (INT)
- **Pre_requisitos_das_Disciplinas**: Disciplina_idDisciplina (INT), Pre_requisitos_idPre_requisitos (INT)
- **Pre_requisitos**: idPre_requisitos (INT)
- **Matriculado**: Aluno_idAluno (INT), Disciplina_idDisciplina (INT)
- **Aluno**: idAluno (INT)

Esse modelo é voltado para operações transacionais e controle acadêmico, mas não é eficiente para análises gerenciais e relatórios sobre a atuação dos professores.

![Modelo Relacional Original](./modelo_relacional_original.png)

## 2. Processo de Negócio Identificado

O foco da análise dimensional está na atuação dos professores em relação aos cursos, disciplinas e quantidade de alunos atendidos. As principais perguntas de negócio levantadas incluem:

- Quantas disciplinas cada professor ministra?
- Quantos alunos cada professor atende?
- Qual professor leciona em mais cursos?
- Qual departamento possui maior carga de trabalho docente?
- Como os professores estão distribuídos entre os departamentos?

## 3. Conversão para o Modelo Dimensional

A partir do modelo relacional e das perguntas de negócio, foi desenvolvida uma modelagem dimensional do tipo estrela, com a tabela fato representando a atuação docente e dimensões relacionadas aos elementos de análise.

### 3.1 Tabela Fato

**Fato_Atuacao_Docente**:

- idProfessor (FK)
- idDisciplina (FK)
- idCurso (FK)
- idDepartamento (FK)
- qtdDisciplinas (INT)
- qtdAlunos (INT)

### 3.2 Dimensões

**Dim_Professor**:

- idProfessor
- nome
- tempo_de_casa
- titulacao

**Dim_Departamento**:

- idDepartamento
- nome
- campus

**Dim_Curso**:

- idCurso
- nome
- modalidade

**Dim_Disciplina**:

- idDisciplina
- nome
- carga_horaria

**Dim_Tempo** (Opcional para evoluções futuras):

- idTempo
- ano
- semestre

## 4. Esquema Estrela Final

               Dim_Tempo
                   |
                   |
Dim_Professor --- Fato_Atuacao_Docente --- Dim_Departamento
                   |
                   |
            Dim_Curso    Dim_Disciplina

Esse esquema facilita a geração de relatórios e análises de desempenho docente.

![Esquema Estrela Final](./esquema_estrela_final.png)

## 5. Conclusão

Esse modelo dimensional permite obter rapidamente insights sobre a atuação dos professores, quantidade de disciplinas ministradas, alunos atendidos e a relação entre professores, cursos e departamentos. Ele é adequado para análises gerenciais em instituições de ensino superior, otimizando a consulta e exploração dos dados.

Esse repositório servirá como base para estudos e aplicações práticas em projetos futuros.

## 📝 Contribuições

Fique à vontade para abrir **issues** ou enviar **pull requests** para melhorias ou sugestões. Toda contribuição é bem-vinda!

## 📧 Contato

Para mais informações ou dúvidas, entre em contato:

- LinkedIn: [Rodolfo Lovera](www.linkedin.com/in/rodolfo-lovera)
- E-mail: rodolfo.lovera@gmail.com
