# Sequelize CLI Operations

1. **Installation**

    ```bash
    npm install --save-dev sequelize-cli 
    npm install --save sequelize
    npx sequelize-cli init 
    ```

2. **Model Generation**

    Generate models using the command `npx sequelize-cli model:generate` with the appropriate attributes:

    ```bash
    npx sequelize-cli model:generate --name User --attributes firstName:string,lastName:string,email:string
    npx sequelize-cli model:generate --name Task --attributes user_id:integer,Title:string,details:string,status:string
    ```

3. **Migration**

    - Run migration:

        ```bash
        npx sequelize-cli db:migrate
        ```

    - Undo last migration:

        ```bash
        npx sequelize-cli db:migrate:undo
        ```

    - Undo all migrations:

        ```bash
        npx sequelize-cli db:migrate:undo:all
        ```

    - Remove a particular migration:

        ```bash
        npx sequelize-cli db:migrate:undo --name 20230418111008-create-user-1.js
        ```

    - Get the status of migrations:

        ```bash
        npx sequelize-cli db:migrate:status
        ```

4. **Seeding**

    Generate seed file and insert data:

    ```bash
    npx sequelize-cli seed:generate --name demo-user 
    npx sequelize-cli db:seed:all
    ```

    Undo the last seed:

    ```bash
    npx sequelize-cli db:seed:undo
    ```

    Undo all seeds:

    ```bash
    npx sequelize-cli db:seed:undo:all
    ```

5. **Adding & Removing Columns**

    - Generate a new migration:

        ```bash
        npx sequelize-cli migration:generate --name migration-skeleton
        ```

    - Add/remove columns by adding/removing them in the migration file, then run migration:

        ```bash
        npx sequelize-cli db:migrate
        ```

6. **Adding Foreign Key**

    - Generate a new migration:

        ```bash
        npx sequelize-cli migration:generate --name migration-skeleton
        ```

    - Add a foreign key to the migration file, then run migration:

        ```bash
        npx sequelize-cli db:migrate
        ```

## Additional resources

1. Sequelize documentation - [Migration](https://sequelize.org/docs/v6/other-topics/migrations/), [Query Interface](https://sequelize.org/api/v6/class/src/dialects/abstract/query-interface.js~queryinterface)

2. YouTube tutorials - [Sequelize with migration](https://www.youtube.com/watch?v=Y_3rGApZaao&list=PLIGDNOJWiL1-OJp8ZWBO2838ENa0tsy6H&index=21)

3. Blog posts - [CRUD operations](https://medium.com/@vinayak-singh/creating-crud-apis-with-node-js-and-sequelize-cli-8b90e8784422), [Insert data with Sequelize seeds & Faker](https://arjunphp.com/insert-data-sequelize-seeds-faker/), [Understanding Sequelize models](https://www.section.io/engineering-education/understanding-nodejs-sequelize-orm-models/)

4. StackOverflow thread - [How to add column in Sequelize existing model](https://stackoverflow.com/questions/49890998/how-to-add-column-in-sequelize-existing-model)

