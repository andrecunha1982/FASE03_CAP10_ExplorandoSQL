# Projeto: Cap 10 - Explorando SQL e tipos de dados na Oracle

## Objetivo

Aplicar os conceitos de modelagem de dados aprendidos nos capítulos 7, 8, 9 e 10 da Fase 03 para criar um modelo de banco de dados que armazene e analise informações sobre a produção agrícola no Brasil, utilizando dados do públicos brasileiros.

Os dados escolhidos foram extraidos do site do IBGE (Instituto Brasileiro de Geografia e Estatística), especificamente os dados do Levantamento Sistemático de Produção Agrícola [https://sidra.ibge.gov.br/tabela/6588], de 2020 até 2024 (Setembro).

## Estrutura do Banco de Dados (MER)

### Entidades e Atributos:

**ENTIDADE EXPSQL_CULTURA**
  - **ID_CULTURA (PK):** Identificador único de cultura.
  - **CULTURA:** Nome da cultura.
  - **TIPO_CULTURA:** Categoria da cultura.
  - **AJU_QUANTIDADE_AGUA:** Quantidade de água aplicada no ajuste.
  - **AJU_QUANTIDADE_NUTRIENTES:** Quantidade de nutrientes aplicados no ajuste (string para representar NPK).

**ENTIDADE EXPSQL_REGIAO**
  - **ID_ESTADO (PK):** Identificador único de casa estado.
  - **ESTADO:** Nome do Estado.
  - **REGIAO:** Região do Estado.

**ENTIDADE EXPSQL_VARIAVEIS**
  - **ID_VARIAVEL (PK):** Identificador único da variavel de registro.
  - **VARIAVEL:** Nome da variavel de registro (Área plantada, Área colhida, Produção ou Rendimento médio).
  - **METRICA_VARIAVEL:** Metrica utilizada por cada variavel de registro.

**ENTIDADE EXPSQL_REGISTROS**
  - **ID_REGISTRO (PK):** Identificador único de cada registro.
  - **ID_CULTURA (FK):** Referência à cultura relacionada ao registro.
  - **ID_ESTADO (FK):** Referência ao estado relacionado ao registro.
  - **ID_VARIAVEL (FK):** Referência a variavel relacionada ao registro.
  - **PERIODO:** Mês de referencia de cada informação.
  - **VALOR:** Valor registrado (metrica de acordo com variavel definida).

### Relacionamentos

**REGISTROS**
  - **CULTURA (1) --- (N) REGISTROS:** Uma cultura pode ter vários registros, mas cada registro está relacionada a uma única cultura.
  - **REGIAO (1) --- (N) REGISTROS:** Uma região pode ter vários registros, mas cada registro é feita em uma única região.
  - **VARIAVEIS (1) --- (N) REGISTROS:** Uma variável pode ter vários registros, mas cada registro é feita em uma única variável.

## Diagrama MER

![image](https://github.com/user-attachments/assets/1bbacc9a-f0eb-4995-bfc6-4816996aa4b0)

## Tecnologias Utilizadas

- **SQL Oracle Cloud** para o desenvolvimento do código.
- **Autonomous Transactional Oracle Database** como banco de dados transacional.
- **SQLDesigner** e **Data Modeler** para criar o diagrama de Entidade-Relacionamento (MER).
- **Markdown** para a documentação no GitHub.
- **GitHub** para versionamento de código.

## Configuração do Ambiente de Desenvolvimento

### Requisitos:

1. **Autonomous Transactional Oracle Database** como banco de dados transacional.

### Configuração do Banco de Dados Oracle:

1. Configurar conta Free Tier em https://www.oracle.com/cloud/free/
2. Provisionar **Autonomous Transactional Oracle Database**
3. Abrir SQL Console
4. Executar o script CREATE_SCRIPT.sql
5. Utilizar os arquivos EXCEL para as cargas nas respectivas tabelas.

Caso queira ajustar/testar o script CREATE_SCRIPT.sql, foi gerado o script DROP_ALL.sql que derruba todas as tabelas, dados e views.
