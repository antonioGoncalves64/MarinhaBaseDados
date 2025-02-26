== Prática: modelo Relacional (Solução)





*Objectivos*



Introdução ao modelo relacional, conversão do modelo ER para o modelo relacional.


*Exercício 1*




*Chaves primárias:*

- FUNCIONÁRIO: NumCC
- ESPAÇO: CodEspaço



*Chaves externas:*

- FUNCIONÁRIO.Supervisor → FUNCIONÁRIO.NumCC
- FUNCIONÁRIO.Espaço → ESPAÇO.CodEspaço
- ESPAÇO.Gestor → FUNCIONÁRIO.NumCC

*Perguntas*

[cols="1,1",options="header"]
|===
| Operação | Violação

| INSERE FUNCIONÁRIO(ABCDEF, Roberto Pires, CP, 12345678,...)
| Integridade de domínio para FUNCIONÁRIO.NumCC: ABCDEF não é um número.

| INSERE FUNCIONÁRIO(12345678, Roberto Pires, CP, 22444552,...)
| Integridade de chave para FUNCIONÁRIO: 12345678 identifica um funcionário já existente (José Silva).

| INSERE FUNCIONÁRIO(23884312, Roberto Pires, CP, 12345679,...)
| Integridade referencial: o supervisor com NumCC=12345679 não existe.

| INSERE ESPAÇO(NULL, Null All Night, ...)
| Integridade de entidade: NULL não pode ser usado como valor para chave primária.

| REMOVE ESPAÇO(CP)
| Integridade referencial: vários funcionários referem-se ao espaço com código CP.

| REMOVE FUNCIONÁRIO(12345678)
| Integridade referencial: funcionário 12345678 (José Silva) é supervisor de 22444552 (Roberta Rodrigues).

| REMOVE FUNCIONÁRIO(18923444)
| Integridade referencial: funcionário 18923444 (Fátima Lopes) é gestor do espaço MH e supervisor de 10345553 (Roberta Rodrigues).

| ACTUALIZA FUNCIONÁRIO(22444552, Espaço → XPTO)
| Integridade referencial: espaço com código XPTO não existe.

| ACTUALIZA ESPAÇO(CP, Nome → NULL)
| Integridade de domínio: Nome não é um atributo opcional (relembrar isso dos requisitos).

| ACTUALIZA ESPAÇO(MH, Gestor → 12345679)
| Integridade referencial: funcionário 12345679 não existe.
|===

*Exercício 2*

image::desenho_esquema_vert.png[]

*Resolução*

__Considerando 1º entidades-tipo__

- Atributos derivados no modelo ER não são transpostos para modelo relacional.
- Mantenho a notação *Opcional?* no modelo relacional.
- Atributos multi-valor (NumTelef) dão origem a uma tabela. Notar que a tabela NUM_TELEF tem como chave primária o par (NumCC, Num).
- Atributos compostos são decompostos nos seus sub-atributos do modelo relacional.

image::ex3_entidades.png[]

__Considerando depois relacionamentos, alterações a amarelo__

- Relação M:N TEM_LUGAR dá-nos uma tabela de "referências cruzadas". Notar que chave primária é o par (CodEvento, CodEspaço).
- Relação 1:1 GERE, sendo total para ESPAÇO, é transposta para atributo ESPAÇO.Gestor.
- Relação N:1 TRABALHA, sendo total para FUNCIONÁRIO, é transposta para atributo FUNCIONÁRIO.ESPAÇO.
- Análogo para SUPERVISOR, mas aí atributo é opcional (dada participação ser parcial por parte de supervisionado). Alternativa possível: tabela de referências cruzadas nesse caso sem atributos opcionais (seria mais "económica" se o relacionamento envolvesse poucos funcionários entre si).

image::ex3_entidades_e_rel.png[]

*Exercício 3*

image::ex4.png[]

*Exercício 4*


[source]
----
table FUNCIONÁRIO
(
    _ NumCC _,
    Nome,
    DataNasc,
    Cargo,
    Email ?,
    Espaço --> ESPAÇO.CodEspaço,
    Supervisor ? --> FUNCIONÁRIO.NumCC
)

table TELEFONES 
(
    _ NumCC _ --> FUNCIONÁRIO.NumCC,
    _ Telefone _ 
)

table ESPAÇO
(
    _ CodEspaço _,
    MRua,
    MNum,
    MAndar ?,
    MCP,
    MLocalidade,
    Gestor --> FUNCIONÁRIO.NumCC
)

table EVENTO
(
    _ CodEvento _,
    Nome,
    DataInício,
    DataFim 
)

table TEM_LUGAR
(
    _ CodEvento _ --> EVENTO.CodEvento,
    _ CodEspaço _ --> ESPAÇO.CodEspaço,
    DataInício,
    DataFim
)
----

image::ex3_dbdia.svg[]



[source]
----
table UTILIZADOR
(
  _ Login _,
  Nome,
  Email
)

table SEGUE
(
  _ Seguidor _ --> UTILIZADOR.Login,
  _ Seguido _ --> UTILIZADOR.Login
)

table POST 
(
  _ Id _,
  Autor --> UTILIZADOR.Login,
  Texto
)

table HASHTAGS
( 
  _ Post _ --> POST.Id,
  _ HashTag _
)

table GOSTO 
(
  _ Utilizador _ --> UTILIZADOR.Login,
  _ Post _ --> POST.Id
)

table COMENTÁRIO
(
  _ Post _ --> POST.Id,
  _ Ordem _ ,
  Autor --> UTILIZADOR.Login,
  Texto 
)
----

image::ex4_dbdia.svg[]
