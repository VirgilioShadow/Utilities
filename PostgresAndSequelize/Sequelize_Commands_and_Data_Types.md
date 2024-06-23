# Sequelize Commands and Data Types

## Useful Sequelize Commands

### Setup and Configuration

1. **Initialize a new Sequelize project**:

   ```sh
   npx sequelize-cli init
   ```

2. **Create a new Sequelize model**:

   ```sh
   npx sequelize-cli model:generate --name ModelName --attributes attr1:type1,attr2:type2
   ```

3. **Create a new migration**:
   ```sh
   npx sequelize-cli migration:generate --name migration_name
   ```

### Database Operations

4. **Run all migrations**:

   ```sh
   npx sequelize-cli db:migrate
   ```

5. **Undo the last migration**:

   ```sh
   npx sequelize-cli db:migrate:undo
   ```

6. **Undo all migrations**:

   ```sh
   npx sequelize-cli db:migrate:undo:all
   ```

7. **Seed the database**:

   ```sh
   npx sequelize-cli db:seed:all
   ```

8. **Undo the last seeding**:

   ```sh
   npx sequelize-cli db:seed:undo
   ```

9. **Undo all seedings**:
   ```sh
   npx sequelize-cli db:seed:undo:all
   ```

### Model Commands

10. **Find all instances of a model**:

    ```js
    const instances = await ModelName.findAll();
    ```

11. **Find one instance of a model**:

    ```js
    const instance = await ModelName.findOne({ where: { attribute: value } });
    ```

12. **Create a new instance**:

    ```js
    const instance = await ModelName.create({ attr1: value1, attr2: value2 });
    ```

13. **Update an instance**:

    ```js
    await ModelName.update({ attr1: newValue1 }, { where: { attr2: value2 } });
    ```

14. **Delete an instance**:

    ```js
    await ModelName.destroy({ where: { attr: value } });
    ```

15. **Raw Queries**:
    ```js
    const results = await sequelize.query("YOUR SQL QUERY HERE", {
      type: sequelize.QueryTypes.SELECT,
    });
    ```

### Associations

16. **Define associations** (e.g., one-to-many):
    ```js
    ModelA.hasMany(ModelB);
    ModelB.belongsTo(ModelA);
    ```

### Transactions

17. **Using transactions**:
    ```js
    const transaction = await sequelize.transaction();
    try {
      // Your transactional operations
      await transaction.commit();
    } catch (error) {
      await transaction.rollback();
    }
    ```

## Sequelize Data Types

### String Types

- **STRING**: A variable-length string.

  ```js
  Sequelize.STRING;
  ```

- **STRING(length)**: A string with a maximum length.

  ```js
  Sequelize.STRING(1234);
  ```

- **TEXT**: A long text field.
  ```js
  Sequelize.TEXT;
  ```

### Number Types

- **INTEGER**: An integer.

  ```js
  Sequelize.INTEGER;
  ```

- **BIGINT**: A large integer.

  ```js
  Sequelize.BIGINT;
  ```

- **FLOAT**: A floating-point number.

  ```js
  Sequelize.FLOAT;
  ```

- **DOUBLE**: A double-precision floating-point number.

  ```js
  Sequelize.DOUBLE;
  ```

- **DECIMAL**: A decimal number with a specified precision and scale.
  ```js
  Sequelize.DECIMAL(10, 2);
  ```

### Boolean Type

- **BOOLEAN**: A boolean value.
  ```js
  Sequelize.BOOLEAN;
  ```

### Date and Time Types

- **DATE**: A date and time.

  ```js
  Sequelize.DATE;
  ```

- **DATEONLY**: A date without a time component.

  ```js
  Sequelize.DATEONLY;
  ```

- **TIME**: A time without a date component.
  ```js
  Sequelize.TIME;
  ```

### JSON Types

- **JSON**: A JSON object.

  ```js
  Sequelize.JSON;
  ```

- **JSONB**: A JSON object stored in binary format (specific to PostgreSQL).
  ```js
  Sequelize.JSONB;
  ```

### Binary Types

- **BLOB**: A binary large object.
  ```js
  Sequelize.BLOB;
  ```

### UUID

- **UUID**: A universally unique identifier.
  ```js
  Sequelize.UUID;
  ```

### Enumeration

- **ENUM**: An enumeration type.
  ```js
  Sequelize.ENUM("value1", "value2", "value3");
  ```

### Range Types (PostgreSQL specific)

- **RANGE**: A range of values.
  ```js
  Sequelize.RANGE(Sequelize.INTEGER);
  ```

### Geometric Types (PostgreSQL specific)

- **GEOMETRY**: A geometric type.
  ```js
  Sequelize.GEOMETRY;
  ```

### Array Type (PostgreSQL specific)

- **ARRAY**: An array of values.
  ```js
  Sequelize.ARRAY(Sequelize.STRING);
  ```

### Example Usage

Here’s an example of defining a Sequelize model with various data types:

```js
const { Sequelize, DataTypes } = require("sequelize");
const sequelize = new Sequelize("database", "username", "password", {
  host: "localhost",
  dialect: "postgres",
});

const ExampleModel = sequelize.define("ExampleModel", {
  stringAttr: {
    type: DataTypes.STRING,
    allowNull: false,
  },
  textAttr: {
    type: DataTypes.TEXT,
  },
  integerAttr: {
    type: DataTypes.INTEGER,
    allowNull: false,
  },
  floatAttr: {
    type: DataTypes.FLOAT,
  },
  booleanAttr: {
    type: DataTypes.BOOLEAN,
    defaultValue: true,
  },
  dateAttr: {
    type: DataTypes.DATE,
  },
  jsonAttr: {
    type: DataTypes.JSON,
  },
  enumAttr: {
    type: DataTypes.ENUM("value1", "value2", "value3"),
  },
  uuidAttr: {
    type: DataTypes.UUID,
    defaultValue: DataTypes.UUIDV4,
  },
});

sequelize.sync();
```

This example demonstrates how you can use different data types in Sequelize to define the attributes of your models.
