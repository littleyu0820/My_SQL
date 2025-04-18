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
    
    DESCRIBE `Student`; //顯示表格內欄位的屬性
    
    ALTER TABLE `Student` ADD `gpa` DECIMAL(3,2); //新增
    ALTER TABLE `Student` DROP COLUMN `gpa`; //刪除
```
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
    
    
    INSERT INTO `Student` VALUES(1, '老王', '電機'); //新增表格內資料
    INSERT INTO `Student` VALUES(2, '老李', '資訊');
    INSERT INTO `Student` VALUES(3, '老楊', NULL);
    INSERT INTO `Student`(`name`, `major`, `student_id`) VALUES('老白', '通訊', 4);
    INSERT INTO `Student`(`major`, `student_id`) VALUES('通訊', 5);
    DESCRIBE `Student`;
    SELECT * FROM `Student`; //顯示表格內欄位的所有資料
```

```sql
    CREATE TABLE `Student`(
    `student_id` INT, 
    `name` VARCHAR(50) NOT NULL,  //不能為空
    `major` VARCHAR(50) UNIQUE,  //不能重複
    PRIMARY KEY(`student_id`)
    );
```

```sql
    CREATE TABLE `Student`(
    `student_id` INT, 
    `name` VARCHAR(50), 
    `major` VARCHAR(50) DEFAULT '歷史', //預設值
    PRIMARY KEY(`student_id`)
    );
```
