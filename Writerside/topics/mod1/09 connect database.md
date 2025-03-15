# Conectando com Banco de Dados

+ A conexão do Laravel com a base dados é configurada pelo arquivo `.env`;
+ Isso nos proporciona maior liberdade e também segurança na aplicação;
+ O Laravel utiliza um **ORM** (Object-Relational Mapping) chamada de **Eloquent**
+ E também para a criação de tabelas as **migrations**;

### Conectando 

- Para conectar com a base de dados deve-se configurar o arquivo `.env`
	+ Nele tem que definir alguns dados:
		DB_DATABASE=NOME_BANCO
		DB_USERNAME=root
		DB_PASSWORD=

- Em seguida, execute o comando, para criar as **migrations**:
	`php artisan migrate`

