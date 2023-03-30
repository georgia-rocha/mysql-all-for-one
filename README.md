## OBJETIVO
Colocar em prática os  conceitos de SQL abordados na segunda sessão de back-end usando Docker e utilizando o bando de dados Northwind.

<details>
<summary><strong>‼️ Antes de começar a desenvolver</strong></summary><br />

1. Clone o repositório
* `git clone git@github.com:georgia-rocha/mysql-all-for-one.git`
* Entre na pasta do repositório que você acabou de clonar:

2. Instale as dependências:
  * `npm install`

* Verifique se os testes estão executando:
  * `npm test` (os testes devem rodar e falhar)

3. Crie uma branch a partir da branch `master`

* Verifique que você está na branch `master`
  * Exemplo: `git branch`
* Se não estiver, mude para a branch `master`
  * Exemplo: `git checkout master`
* Agora, crie uma branch onde você vai guardar os commits do seu projeto
  * Exemplo:
    * `git checkout -b <nome>-project-docker-todo-list`

4. Cria os arquivos sql touch desafio{1..27}.sql;

5. Roda o compose docker-compose up -d;

6. Roda o container docker exec -it all_for_one bash;

7. Dentro do container instale as dependências com o npm install;
 
<details>   
<summary><strong>Usando Docker</strong></summary><br />

  **:warning: Antes de começar, seu docker-compose precisa estar na versão 1.29 ou superior. [Veja aqui](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-compose-on-ubuntu-20-04-pt) ou [na documentação](https://docs.docker.com/compose/install/) como instalá-lo. No primeiro artigo, você pode substituir onde está com `1.26.0` por `1.29.2`.**

  > :information_source: Rode os serviços `node` e `db` com o comando `docker-compose up -d`.

- Lembre-se de parar o `mysql` se estiver usando localmente na porta padrão (`3306`), ou adapte, caso queria fazer uso da aplicação em containers
- Esses serviços irão inicializar um container chamado `all_for_one` e outro chamado `all_for_one_db`.
- A partir daqui você pode rodar o container `all_for_one` via CLI ou abri-lo no VS Code.

  > :information_source: Use o comando `docker exec -it all_for_one bash`.

- Ele te dará acesso ao terminal interativo do container criado pelo compose, que está rodando em segundo plano.
- As credencias de acesso ao banco de dados estão definidas no arquivo `docker-compose.yml`, e são acessíveis no container através das variáveis de ambiente `MYSQL_USER` e `MYSQL_PASSWORD`. 💡

  > :information_source: Instale as dependências [**Caso existam**] com `npm install`. (Instale dentro do container)

- **:warning: Atenção:** Caso opte por utilizar o Docker, **TODOS** os comandos disponíveis no `package.json` (npm start, npm test, npm run dev, ...) devem ser executados **DENTRO** do container, ou seja, no terminal que aparece após a execução do comando `docker exec` citado acima.

- **:warning: Atenção:** O **git** dentro do container não vem configurado com suas credenciais. Ou faça os commits fora do container, ou configure as suas credenciais do git dentro do container.

- **:warning: Atenção:** Não rode o comando npm audit fix! Ele atualiza várias dependências do projeto, e essa atualização gera conflitos com o avaliador.

</details>
</details>

## Requisitos Obrigatórios 100%

### Desafios Iniciais

- [x] 1 - Exiba apenas os nomes dos produtos na tabela `products`.
- [x] 2 - Exiba os dados de todas as colunas da tabela `products`.
- [x] 3 - Escreva uma query que exiba os valores da coluna que representa a _primary key_ da tabela `products`.
- [x] 4 - Conte quantos registros existem na coluna `product_name` da tabela `products`.
- [x] 5 - Monte uma query que exiba os dados da tabela `products` a partir do quarto registro até o décimo terceiro.
- [x] 6 - Exiba os dados das colunas `product_name` e `id` da tabela `products` de maneira que os resultados estejam em ordem alfabética dos nomes.
- [x] 7 - Mostre apenas os ids dos 5 últimos registros da tabela `products` (a ordenação deve ser baseada na coluna `id`).
- [x] 8 - Faça uma consulta na tabela `employees` que retorne o nome completo da pessoa colaboradora (colunas `first_name` e `last_name`) com o nome `full_name` e também a localização completa (colunas `city`, `state_province` e `address`) com o nome `location`.

### Desafios sobre filtragem de dados

- [x] 9 - Mostre todos os valores de `notes` da tabela `purchase_orders` que não são nulos.
- [x] 10 - Mostre todos os dados da tabela `purchase_orders` em ordem decrescente, ordenados por `created_by` em que o `created_by` é maior ou igual a 3.
- [x] 11 - Exiba os dados da coluna `notes` da tabela `purchase_orders` em que seu valor de `Purchase generated based on Order` é maior ou igual a 30 e menor ou igual a 39.
- [x] 12 - Mostre as `submitted_date` de `purchase_orders` em que a `submitted_date` é do dia 26 de abril de 2006.
- [x] 13 - Mostre o `supplier_id` das `purchase_orders` em que o `supplier_id` seja 1 ou 3.
- [x] 14 - Mostre os resultados da coluna `supplier_id` da tabela `purchase_orders` em que o `supplier_id` seja maior ou igual a 1 e menor ou igual 3.
- [x] 15 - Mostre somente as horas (sem os minutos e os segundos) da coluna `submitted_date` de todos registros da tabela `purchase_orders`.
- [x] 16 - Exiba a `submitted_date` das `purchase_orders` que estão entre `2006-01-26 00:00:00` e `2006-03-31 23:59:59`.
- [x] 17 - Mostre os registros das colunas `id` e `supplier_id` das `purchase_orders` em que os `supplier_id` sejam tanto 1, ou 3, ou 5, ou 7.
- [x] 18 - Mostre todos os registros de `purchase_orders` que tem o `supplier_id` igual a 3 e `status_id` igual a 2.
- [x] 19 - Mostre a quantidade de pedidos que foram feitos na tabela `orders` pelo `employee_id` igual a 5 ou 6, e que foram enviados através do método(coluna) `shipper_id` igual a 2.

### Desafios de manipulação de tabelas

- [x] 20 - Adicione à tabela `order_details` um registro com `order_id`: 69, `product_id`: 80, `quantity`: 15.0000, `unit_price`: 15.0000, `discount`: 0, `status_id`: 2, `date_allocated`: NULL, `purchase_order_id`: NULL e `inventory_id`: 129.
- [x] 21 - Adicione com um único `INSERT`, duas linhas à tabela `order_details` com os mesmos dados do requisito 20.
- [x] 22 - Atualize todos os dados da coluna `discount`, na tabela `order_details`, para 15.
- [x] 23 - Atualize os dados da coluna `discount` da tabela `order_details` para 30, onde o valor na coluna `unit_price` seja menor que 10.0000.
- [x] 24 - Atualize os dados da coluna `discount` da tabela `order_details` para 45, onde o valor na coluna `unit_price` seja maior que 10.0000 e o id seja um número entre 30 e 40.
- [x] 25 - Delete todos os dados em que a `unit_price` da tabela `order_details` seja menor que 10.0000.
- [x] 26 - Delete todos os dados em que a `unit_price` da tabela `order_details` seja maior que 10.0000.
- [x] 27 - Delete todos os dados da tabela `order_details`.
