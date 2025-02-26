


# Laboratório: Introdução Base Dados


## Objectivos

O laboratório de bases de dados tem como objectivo principal proporcionar aos estudantes um ambiente prático para a aplicação dos conceitos teóricos adquiridos durante as aulas, desenvolvendo competências essenciais para o desenho, implementação e gestão de bases de dados. Este espaço fomenta a aprendizagem activa e orientada para a resolução de problemas, permitindo uma compreensão mais aprofundada dos temas abordados.

### Objectivos Específicos:

1. **Desenvolver Competências Técnicas:** 
   Capacitar os estudantes para a utilização eficiente de Sistemas de Gestão de Bases de Dados (SGBD), incluindo a criação, modificação e gestão de tabelas, bem como a execução de consultas SQL.

2. **Promover a Compreensão de Conceitos Fundamentais:** 
   Garantir que os estudantes compreendem conceitos-chave como integridade dos dados, normalização, relações entre tabelas e restrições de integridade.

3. **Resolver Problemas Reais:** 
   Aplicar os conhecimentos em cenários práticos que simulam situações do mundo real, incentivando o pensamento crítico e a tomada de decisões baseadas em dados.

4. **Desenvolver Competências de Análise e Optimização:**
   Ensinar técnicas para analisar o desempenho das bases de dados e implementar melhorias, garantindo a eficiência e escalabilidade dos sistemas.

5. **Incentivar o Trabalho Colaborativo:**
   Promover o trabalho em equipa através da execução de projectos em grupo, incentivando a partilha de ideias e a aprendizagem colaborativa.

## Descrição

Uma base de dados universitária centraliza e organiza informações relacionadas com estudantes, disciplinas, turmas, notas e pré-requisitos, facilitando a gestão académica e administrativa. O sistema permite registar dados essenciais como o nome, número de estudante, ano académico, disciplinas, carga horária, e relações de pré-requisitos. Também armazena notas e estabelece conexões entre os vários tipos de dados, assegurando integridade, consistência e acessibilidade. Esta estrutura promove eficiência operacional, suporta análises estratégicas e facilita a tomada de decisões na gestão universitária.
## Tabelas

### **Tabela: ESTUDANTE (STUDENT)**
| Nome   | Número_Estudante | Classe | Curso (Major) |
|--------|-------------------|--------|---------------|
| Smith  | 17                | 1      | CS            |
| Brown  | 8                 | 2      | CS            |

---

### **Tabela: DISCIPLINA (COURSE)**
| Nome_Disciplina                   | Código_Disciplina | Créditos | Departamento |
|-----------------------------------|-------------------|----------|--------------|
| Introdução à Informática          | CS1310           | 4        | CS           |
| Estruturas de Dados               | CS3320           | 4        | CS           |
| Matemática Discreta               | MATH2410         | 3        | MATH         |
| Base de Dados                     | CS3380           | 3        | CS           |

---

### **Tabela: TURMA (SECTION)**
| Código_Turma | Código_Disciplina | Semestre  | Ano | Docente   |
|--------------|--------------------|-----------|-----|-----------|
| 85           | MATH2410          | Outono    | 07  | King      |
| 92           | CS1310            | Outono    | 07  | Anderson  |
| 102          | CS3320            | Primavera | 08  | Knuth     |
| 112          | MATH2410          | Outono    | 08  | Chang     |
| 119          | CS1310            | Outono    | 08  | Anderson  |
| 135          | CS3380            | Outono    | 08  | Stone     |

---

### **Tabela: HISTÓRICO DE NOTAS (GRADE_REPORT)**
| Número_Estudante | Código_Turma | Nota |
|------------------|--------------|------|
| 17               | 112          | B    |
| 17               | 119          | C    |
| 8                | 85           | A    |
| 8                | 92           | A    |
| 8                | 102          | B    |
| 8                | 135          | A    |

---

### **Tabela: PRÉ-REQUISITOS (PREREQUISITE)**
| Código_Disciplina | Código_Pré-Requisito |
|-------------------|-----------------------|
| CS3380            | CS3320               |
| CS3380            | MATH2410             |
| CS3320            | CS1310               |

---

## Questões


### **1.1. Defina os seguintes termos**
Explique os seguintes conceitos relacionados a bases de dados:
- Dados  
- Base de dados  
- SGBD (Sistema de Gestão de Base de Dados)  
- Sistema de base de dados  
- Catálogo da base de dados  
- Independência programa-dados  
- Vista de utilizador  
- Administrador de Base de Dados (DBA)  
- Utilizador final  
- Transação pré-definida  
- Sistema dedutivo de base de dados  
- Objeto persistente  
- Metadados  
- Aplicação de processamento de transações  

---

### **1.2. Quais são os quatro principais tipos de ações que envolvem bases de dados?**
Explique brevemente cada uma das quatro ações principais realizadas em bases de dados.

---

### **1.3. Quais são as principais características da abordagem de bases de dados?**
Compare a abordagem de bases de dados com os sistemas tradicionais de ficheiros.

---

### **1.4. Quais são as responsabilidades do DBA e dos arquitectos de bases de dados?**
Identifique as funções e responsabilidades de ambos os papéis no contexto da gestão de bases de dados.

---

### **1.5. Quais são os diferentes tipos de utilizadores finais de bases de dados?**
Diferencie os tipos de utilizadores finais e descreva as suas principais atividades.

---

### **1.6. Quais capacidades devem ser fornecidas por um SGBD?**
Liste e explique as funcionalidades essenciais que um Sistema de Gestão de Base de Dados deve fornecer.

---

### **1.7. Quais são as diferenças entre sistemas de bases de dados e sistemas de recuperação de informação?**
Discuta as distinções fundamentais entre estes dois tipos de sistemas.

---

### **1.8. Quais consultas e operações de atualização podem ser aplicadas à base de dados?**
Forneça exemplos de consultas informais e operações de atualização que podem ser realizadas.

---

### **1.9. Qual é a diferença entre redundância controlada e não controlada?**
Explique a diferença entre ambos os conceitos e inclua exemplos para ilustrar.

---

### **1.10. Quais relações existem entre os registos da base de dados?**
Especifique todas as relações existentes entre os registos da base de dados apresentada.

---

### **1.11. Que vistas adicionais podem ser necessárias?**
Sugira algumas vistas que poderiam ser úteis para diferentes grupos de utilizadores.

---

### **1.12. Que restrições de integridade podem ser aplicadas?**
Cite exemplos de restrições de integridade que podem ser relevantes para a base de dados apresentada.

---

### **1.13. Quando usar processamento tradicional de ficheiros em vez de bases de dados?**
Identifique cenários em que o processamento de ficheiros pode ser mais adequado.

---

### **1.14. Alterações no departamento de "CS"**
a. Identifique todas as colunas que precisam de ser atualizadas caso o nome do departamento "CS" mude para "CSSE".  
b. Proponha uma reestruturação para que apenas uma coluna precise ser atualizada em caso de alterações semelhantes.
