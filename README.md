# **Star Schema - Análise de Professores**

Este projeto apresenta a criação de um **Star Schema** (Esquema em Estrela) para um cenário de análise focado nos **professores** e sua relação com cursos, disciplinas e departamentos. A modelagem foi realizada como parte do desafio proposto no curso, com o objetivo de criar uma estrutura dimensional otimizada para consultas analíticas.

---

## **Objetivo do Projeto**

O objetivo principal deste projeto foi criar um esquema dimensional em estrela que permita realizar análises relacionadas aos professores, abrangendo os seguintes aspectos:
- Professores e as disciplinas ministradas.
- Departamentos associados aos cursos e disciplinas.
- Datas de oferta e granularidades temporais relevantes para análises.

---

## **Descrição do Modelo**

O modelo criado possui uma tabela fato central (`Fato_Professor`) e diversas tabelas dimensão que complementam o contexto de análise. Abaixo estão os detalhes:

### **Tabela Fato**

**Fato_Professor**
- Representa os dados principais relacionados aos professores e suas atividades.
- Atributos:
  - `idProfessor` (INT, FK): Identificador do professor.
  - `idDisciplina` (INT, FK): Identificador da disciplina ministrada.
  - `idDepartamento` (INT, FK): Identificador do departamento associado.
  - `idCurso` (INT, FK): Identificador do curso.
  - `idTempo` (INT, FK): Relaciona-se com a dimensão de tempo.
  - **Medidas**:
    - `CargaHoraria` (FLOAT): Total de carga horária ministrada.
    - `QuantidadeCursos` (INT): Número de cursos ministrados.
    - `QuantidadeDisciplinas` (INT): Número de disciplinas ministradas.

---

### **Tabelas Dimensão**

1. **Dimensão Professor**
   - Atributos:
     - `idProfessor` (INT, PK): Identificador do professor.
     - `Nome` (VARCHAR(45)): Nome do professor.
     - `Especialidade` (VARCHAR(45)): Área de especialização.

2. **Dimensão Disciplina**
   - Atributos:
     - `idDisciplina` (INT, PK): Identificador da disciplina.
     - `Curso` (VARCHAR(45)): Curso ao qual a disciplina pertence.
     - `Descrição` (VARCHAR(45)): Breve descrição da disciplina.
     - `CargaHoraria` (FLOAT): Total de horas da disciplina.

3. **Dimensão Departamento**
   - Atributos:
     - `idDepartamento` (INT, PK): Identificador do departamento.
     - `NomeDepartamento` (VARCHAR(45)): Nome do departamento.
     - `Sigla` (VARCHAR(10)): Sigla do departamento.

4. **Dimensão Curso**
   - Atributos:
     - `idCurso` (INT, PK): Identificador do curso.
     - `NomeCurso` (VARCHAR(45)): Nome do curso.
     - `DepartamentoAssociado` (INT, FK): Relacionamento com o departamento.

5. **Dimensão Tempo**
   - Atributos:
     - `idTempo` (INT, PK): Identificador temporal.
     - `Ano` (INT): Ano da oferta.
     - `Semestre` (VARCHAR(10)): Semestre da oferta.
     - `DataInicio` (DATE): Data de início da oferta.
     - `DataFim` (DATE): Data de término da oferta.

---

### **Relacionamentos**

- A tabela fato `Fato_Professor` é conectada às tabelas dimensão por meio de chaves estrangeiras, criando o formato estrela. O modelo está otimizado para consultas analíticas, permitindo, por exemplo:
  - Análises de carga horária total por professor, curso, ou departamento.
  - Comparação de disciplinas e cursos entre diferentes períodos.
  - Agrupamentos e filtros por granularidades temporais.

---

## **Destaques do Modelo**

1. **Modelo Dimensional**: O Star Schema facilita consultas analíticas e relatórios ao organizar os dados em tabelas de fato e dimensão.
2. **Flexibilidade Temporal**: A inclusão da dimensão de tempo permite análises em diferentes granularidades (ano, semestre, etc.).
3. **Centralidade no Professor**: O modelo foca nas atividades e no impacto dos professores, permitindo insights detalhados sobre suas contribuições.

---

## **Como Reproduzir**

1. **Ferramentas Recomendadas**:
   - MySQL Workbench, DBDesigner, ou qualquer ferramenta de visualização de modelos dimensionais.
2. **Passos**:
   - Abra o diagrama fornecido na ferramenta.
   - Explore as tabelas fato e dimensão e analise os relacionamentos.
   - Utilize os dados simulados para testar consultas analíticas.

---

## **Possíveis Melhorias**

1. **Adição de Indicadores de Performance**
   - Incluir medidas como a média de alunos por disciplina, taxas de aprovação, ou outras métricas associadas.
2. **Integração com Dados Reais**
   - Popule o modelo com dados reais ou simulados para demonstrar análises práticas.
3. **Expansão Temporal**
   - Detalhar ainda mais a dimensão de tempo com granularidades como trimestres ou períodos semanais.

---

## **Sobre o Autor**

Este modelo foi desenvolvido como parte do desafio **"Criando um Star Schema para Cenários de Vendas"**, adaptado para análise de professores. O projeto é um exemplo prático de design de banco de dados dimensional, demonstrando habilidades em modelagem analítica.

---

### **Licença**
O projeto é de uso educacional e está disponível para consultas e referências.

--- 

Se precisar de ajustes ou mais informações, é só avisar!
