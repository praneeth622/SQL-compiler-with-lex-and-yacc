# SQL Compiler with Lex and Yacc

This repository implements a basic **SQL compiler** using **Lex** and **Yacc**. It parses SQL queries, validates their syntax, and provides feedback on whether the queries are valid. The project supports basic SQL commands like `SELECT`, `FROM`, `WHERE`, and `ORDER BY`, including conditions and string literals with SQL-style escaped single quotes.

---

## **Features**

- **Supported SQL Syntax**:
  - `SELECT` statements with:
    - Single or multiple columns.
    - The `*` wildcard for all columns.
    - Conditions with operators like `=`, `<`, `>`, `<=`, `>=`, `<>`.
    - Logical operators (`AND`, `OR`).
    - String literals with escaped single quotes (`''`).
  - `FROM` clause with a table name.
  - `WHERE` clause for filtering rows.
  - `ORDER BY` clause for sorting.
- **Error Handling**:
  - Provides meaningful error messages for invalid SQL syntax.
  - Identifies unrecognized tokens and invalid query structures.

---

## **Getting Started**

### **Prerequisites**

- **Flex**: A lexical analyzer generator.
- **Bison**: A parser generator compatible with Yacc.
- **GCC**: A C compiler to build the executable.

Ensure that these tools are installed on your system. For Ubuntu/Debian:

```bash
sudo apt update
sudo apt install flex bison gcc
```

---

### **Installation**

1. Clone the repository:

   ```bash
   git clone https://github.com/praneeth622/SQL-compiler-with-lex-and-yacc.git
   cd SQL-compiler-with-lex-and-yacc
   ```

2. Compile the Lex and Yacc files:

   ```bash
   bison -d sql.y
   flex sql.l
   gcc -o sql_parser sql.tab.c lex.yy.c -lfl
   ```

3. Run the compiler:

   ```bash
   ./sql_parser
   ```

---

### **Usage**

1. Run the executable:

   ```bash
   ./sql_parser
   ```

2. Enter SQL queries at the prompt. Type `exit;` to quit.

3. Example Queries:

   - Valid Queries:
     ```sql
     SELECT name, age FROM users WHERE age > 30 ORDER BY name;
     SELECT * FROM products WHERE name = 'King''s Ale';
     SELECT id FROM employees WHERE salary >= 50000 AND department = 'Sales';
     ```

   - Invalid Queries:
     ```sql
     SELECT FROM WHERE;
     SELECT name age FROM users;
     ```

   **Output**:
   - For valid queries:
     ```
     SQL query parsed successfully.
     ```
   - For invalid queries:
     ```
     Error: syntax error
     ```

---

## **Code Structure**

### **Files**

- **`sql.l`**: The Lex file that defines token rules for SQL keywords, operators, identifiers, and literals.
- **`sql.y`**: The Yacc file that defines the grammar rules for SQL queries.
- **Generated Files**:
  - `sql.tab.c` and `sql.tab.h`: Generated by Bison from `sql.y`.
  - `lex.yy.c`: Generated by Flex from `sql.l`.

---

## **Features in Development**

- **Support for Additional SQL Commands**:
  - `INSERT`, `UPDATE`, `DELETE`.
  - `JOIN` clauses.
- **Semantic Analysis**:
  - Validate column and table names against predefined schemas.
- **Query Execution**:
  - Execute queries on a mock database.

---

## **Contributing**

Contributions are welcome! If you'd like to improve the compiler, follow these steps:

1. Fork the repository.
2. Create a feature branch (`git checkout -b feature-name`).
3. Commit your changes (`git commit -m "Add feature"`).
4. Push to the branch (`git push origin feature-name`).
5. Create a pull request.

---

## **License**

This project is licensed under the MIT License. See the `LICENSE` file for details.

---

## **Acknowledgments**

- [Flex](https://westes.github.io/flex/manual/): For lexical analysis.
- [Bison](https://www.gnu.org/software/bison/): For parsing.
- [SQL Syntax](https://en.wikipedia.org/wiki/SQL_syntax): For SQL query standards.
- Repository inspired by [MohamedAmineBoufares/SQL-compiler](https://github.com/MohamedAmineBoufares/SQL-compiler).

---

## **Contact**

For queries or suggestions, feel free to contact [Praneeth](https://github.com/praneeth622).
