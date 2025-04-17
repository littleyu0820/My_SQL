# My_SQL
My_SQL Practice

## Basic Implement
```sql
	CREATE DATABASE `test_sql`;
    SHOW DATABASES;
    USE `test_sql`;
    
    
    CREATE TABLE `Student`(
    `student_id` INT, 
    `name` VARCHAR(50), 
    `major` VARCHAR(50),
    PRIMARY KEY(`student_id`)
    );
    
    DESCRIBE `Student`;
    
    ALTER TABLE `Student` ADD `gpa` DECIMAL(3,2);
    ALTER TABLE `Student` DROP COLUMN `gpa`;
```
