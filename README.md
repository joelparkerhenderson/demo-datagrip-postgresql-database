# Demo DataGrip PostgreSQL database

<img src="README.png" alt="DataGrip + PostgresSQL" style="width: 100%;"/>

This demo show how to use:

  * DataGrip database management software by JetBrains.

  * PostgreSQL database management system.

  * A demo database, schema, table, and columns.

Contents:

* [Connect PostgreSQL as a data source](#connect-postgresql-as-a-data-source)
* [Connect to your local PostgreSQL DBMS](#connect-to-your-local-postgresql-dbms)
* [Create a demo database](#create-a-demo-database)
* [Create a public schema](#create-a-public-schema)
* [Create a demo table and columns](#create-a-demo-table-and-columns)
* [Conclusion](#conclusion)


## Connect PostgreSQL as a data source

Use the menus:

  * Menu > File > New Project

  * Menu > File > Data Sources > PostgreSQL > Download Driver > OK

  * Menu > View > Tool Wndows > Database

  * Database > + > Data Source > PostgreSQL


## Connect to your local PostgreSQL DBMS

In the window "Data Sources and Drivers", do these:

  * Name: postgres@localhost

  * Host: localhost

  * Port: 5342

  * Datbase: postgres

  * Click: Test Connection

  * Output: DBMS: PostgreSQL (ver. 10.5) ...

  * Click: OK


## Create a demo database

Create a demo database by using the "Database" window:

  * Database > + > Database > e.g. "demo_datagrip_database"

SQL script:

```sql
create database demo_datagrip_database;
```

Then:

  * Action: Execute in Database

  * Click: Execute

The "Database" window now shows the new database name.

However, if you click the new database name, then the dropdown arrow, the tool does not show inner information, such as access methods.

  * Click: Refresh icon

Now, if you click the new database name, then click the dropdown arrow, the tool does show inner information, including access methods and extensions.

  * Database > Refresh icon


## Create a public schema

Does your database already have a public schema?

  * Click the new database name, then click the dropdown arrow.

  * Do you see an folder name "schemas", and within it, a schema name "public"?

If so, good.

If not, then create it:

  * Database > + > Schema

  * Name: public

SQL script:

```sql
create schema public;
```

Then:

  * Action: Execute in Database

  * Click: Execute

Caution: in our version of DataGrip, we see an error message "The schema already exists", and then shows the folder name "schemas", and within it, the schema name "public". As far as we know, this is a bug, and also is harmless.


## Create a demo table and columns

In the "Database" window:

  * Database > + > Table > e.g. "demo_table"

  * Click: Execute

SQL script:

```sql
create table demo_table
(
);
```

Create a primary key, such as a column name "id", and a type "serial":

  * Create New Table > Columns tab > +

    * Name: id

    * Type: serial

    * Check: Primary Key

  * Note that a primary key automatically implies a unique not-null value, and that a serial data type automatically implies an auto-increment value. You do not need to check these checkboxes in the DataGrip window.

SQL script:

```sql
create table demo_table
(
	id serial
		constraint demo_table_pk
			primary key
);
```

Create a column for typical data entry, such as a column name "info", and a type "text".

  * Create New Table > Columns tab > +

    * Name: info

    * Type: text

  * Note: PostgreSQL implements the data type "text" and "varchar" by using "varlena" (variable length array). Some DBMSes (e.g. MySQL) treat the data types differently, such as storing "text" outside the table vs. "varchar" inside the table. Some software frameworks (e.g. Ruby on Rails) treat the data types differently, such as showing a web page view with a HTML web form textarea multi-line box for a "text" type vs. a web form input field one-line box for a "varchar" field.

SQL script:

```sql
create table demo_table
(
  id serial
    constraint demo_table_pk
      primary key,
  info varchar(max)
);
```

Then:

  * Action: Execute in Database

  * Click: Execute

The Database window should now show you:

  * demo_datagrip_database > schemas > public > tables > demo_table

    * id

    * info

    * demo_table_pk (id)

    * demo_table_pk (id) UNIQUE


## Conclusion

Congratulations, the demo is complete!
