# SQL Commands

## Basic Commands

```sql
SHOW DATABASES; # Shows all DBs
CREATE DATABASE [database_name]; # Creates a DB
USE [database_name]; # Selects a DB

SHOW TABLES # Shows all tables within a selected DB
CREATE TABLE [table_name] { id type, #comment }; # Creates a table within a DB

# Example
CREATE TABLE pets
(
  id              INT unsigned NOT NULL AUTO_INCREMENT, # Unique ID for the record
  name            VARCHAR(150) NOT NULL,                # Name of the cat
  owner           VARCHAR(150) NOT NULL,                # Owner of the cat
  birth           DATE NOT NULL,                        # Birthday of the cat
  PRIMARY KEY     (id)                                  # Make the id the primary key
);

# shows information on all columns of a table
DESCRIBE [table_name];
INSERT INTO cats (name, owner, birth) VALUES
  ( 'Siggy', 'Harold', '2018-01-05' ),
  ( 'Freya', 'Gutenberg', '2017-11-10' ),
  ( 'Patches', 'Charlie', '2015-05-15' );


SELECT * FROM [table_name] # Selects all

# Specific Example
SELECT name FROM cats WHERE owner = 'Charlie';
DELETE FROM cats WHERE name='Freya';

ALTER TABLE cats ADD gender CHAR(1) AFTER name
ALTER TABLE cats DROP gender

SHOW CREATE TABLE cats\G # Gives more details
```
