# My_SQL
My_SQL 基本練習

## 基本操作
```sql
    CREATE DATABASE `test_sql`; //創建資料庫
    SHOW DATABASES; //顯示
    USE `test_sql`; //使用
    
    
    CREATE TABLE `Student`(
    `student_id` INT, 
    `name` VARCHAR(50), 
    `major` VARCHAR(50),
    PRIMARY KEY(`student_id`)
    ); //創建表格
    
    DESCRIBE `Student`; //顯示
    
    ALTER TABLE `Student` ADD `gpa` DECIMAL(3,2); //新增
    ALTER TABLE `Student` DROP COLUMN `gpa`; //刪除
```
