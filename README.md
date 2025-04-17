# My_SQL
My_SQL 基本練習

## 基本操作(創建/顯示/刪除/使用 資料庫, 創建/顯示/新增/刪除 表格/欄位)
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
