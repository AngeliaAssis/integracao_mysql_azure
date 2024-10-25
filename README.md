
# Relatório corporativo integração MySQL e Azure

Desafio de projeto "Criando um relatório corporativo com integração MySQL e Azure" - DIO


## Objetivo do projeto
1. Criação de uma instância na Azure para MySQL.

2. Criar o Banco de dados com base disponível no GitHub. (https://github.com/julianazanelatto/power_bi_analyst/tree/main/M%C3%B3dulo%203/Desafio%20de%20Projeto)

3. Integração do Power BI com MySQL no Azure.

4. Verificar problemas na base a fim de realizar a transformação dos dados.

## Aplicações utilizadas
Cloud Shell Azure

Power Query

## Etapas de extração
1. Alteração da base de dados disponível para adequação ao Cloud Shell.

Durante as inserções realizadas foram retornados erros que impediam a criação das tabelas e inserção de valores no banco de dados.

Solução: remoção das indentações e das constrainst foreign Keys permitiram a criação das tabelas e inserção dos valores. As foreign keys podem ser inseridas posteriormente à criação das tabelas.

2. Conexão do Power BI com o banco de dados MySQL na Azure.

## Etapas de transformação
1. Verificação do cabeçalho, tipo de dado e nomeação das colunas.

Solução: valores monetários foram alterados para o tipo número decimal fixo e nomeação das colunas foram alteradas para simplificação.

2. Alterações na tabela 'employee'

Solução:

a. 'Primeiro Nome' e 'Sobrenome' foram mesclados para criação de uma única coluna 'Nome'

b. coluna 'Endereço' - separação de coluna complexa criando novas colunas 'Cidade' e 'UF' com atributos simples

3. Criação de novas tabelas

Tabelas novas criadas através da função 'mesclar consultas'

a. 'mesclar consultas' tabelas 'employee' e 'department' com coluna de junção (correspondente) 'ID Departamento'. Resultado: tabela 'employee_department' com o nome dos departamento associados aos colaboradores. Colunas expandidas 'Nome Departamento e 'Gerente_ssn'.

b. 'mesclar consultas' tabelas 'employee_department' e 'employee' com coluna de junção (correspondente) em 'Gerente_ssn' e 'ID Colaborador'. Resultado: tabela 'employee_manager' com o nome dos colaboradores associados aos respectivos gerentes. Coluna expandida 'Nome'. 

c.  'mesclar consultas' tabelas 'dept_location' e 'department' com coluna de junção (correspondente) 'ID Departamento'. Resultado: tabela 'local_departamento'. Coluna expandida 'Nome Departamento'. Após, mescla de coluna 'Localização Departamento' e 'Nome Departamento' gerando a combinação local - departamento.

4. Remoção de colunas desnecessárias.

5. Uso da função 'mesclar consultas'

As junções presentes do projeto foram feitas através de mescla das consultas.

*acrescentar/combinar consultas = concatena linhas de 2 tabelas em uma tabela nova

*mesclar consultas = cria uma tabela mesclada a partir de colunas correspondentes

## Criação do relatório
Após a criação do relatório foi possível observar:
- a somatória de horas de trabalho por departamento;
- a quantidade de projetos por departamento;
- a distribuição dos salários por departamento;
- a quantidade de colaboradores por gerente.

## Conclusão do projeto
Trabalhando no projeto de ponta-a-ponta foi possível observar a relevância do tratamento dos dados para o resultado final do visual, o que inclui a nomeação das colunas, a eliminação dos valores nulos, a correta mescla entre as tabelas e remoção as colunas desnecessárias para facilitar a manipulação dos dados.

