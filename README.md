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

```sql
    CREATE TABLE `Student`(
    `student_id` INT AUTO_INCREMENT, //自動增加
    `name` VARCHAR(50), 
    `major` VARCHAR(50),
    PRIMARY KEY(`student_id`)
    );
    
    DROP TABLE `Student`;
    
 
    INSERT INTO `Student`(`name`, `major`) VALUES('老白', '通訊'); //無須再加入studnet_id
    INSERT INTO `Student`(`name`, `major`) VALUES('老王', '英語');
   
    DESCRIBE `Student`;
    SELECT * FROM `Student`;
```

```sql
    SET SQL_SAFE_UPDATES = 0; //可以更新
    CREATE TABLE `Student`(
    `student_id` INT AUTO_INCREMENT, 
    `name` VARCHAR(50), 
    `major` VARCHAR(50),
    `score` INT,
    PRIMARY KEY(`student_id`)
    );
    
    DROP TABLE `Student`;
    
    INSERT INTO `Student`(`name`, `major`, `score`) VALUES('老王', '英文', 98);
    INSERT INTO `Student`(`name`, `major`, `score`) VALUES('老白', '自然', 92);
    INSERT INTO `Student`(`name`, `major`, `score`) VALUES('老楊', '數學', 93);
    INSERT INTO `Student`(`name`, `major`, `score`) VALUES('老李', '國語', 90);
    INSERT INTO `Student`(`name`, `major`, `score`) VALUES('老陳', '社會', 96);
    INSERT INTO `Student`(`name`, `major`, `score`) VALUES('老黃', '英文', 96);
    
    
    UPDATE `Student` SET `major` = '英語' WHERE `major` = '英文'; //更新
    UPDATE `Student` SET `name` = '老蕭', `major` = '化學' WHERE `student_id` = 1; //多格更新
    DELETE FROM `Student` WHERE `student_id` = 6; //刪除
    
    DESCRIBE `Student`;
    SELECT * FROM `Student`;
```
```sql
    SELECT * FROM `Student` ORDER BY `score` ASC; //升序 預設
    SELECT * FROM `Student` ORDER BY `score` DESC; //降序
    SELECT * FROM `Student` ORDER BY `score`, `student_id`; 先排序score再排序student_id
    SELECT * FROM `Student` LIMIT 3; //限制資料數量
    SELECT * FROM `Student` ORDER BY `score` LIMIT 3; //混用 先排序再限制輸出數量
    SELECT * FROM `Student` WHERE `major` <> '自然'; //不等於
    SELECT * FROM `Student` WHERE `major` IN('自然','英文','國語') //等價於 =自然 and 英文 and 國語
```

## 創建公司資料(練習題)
```sql
    CREATE DATABASE `test_sql`;
    SHOW DATABASES;
    USE `test_sql`;
    
    SET SQL_SAFE_UPDATES = 0;
    CREATE TABLE `Employee`(
    `emp_id` INT,
    `name` CHAR(50),
    `birth` DATE,
    `sex` CHAR(5),
    `salary` INT,
    `branch_id` INT,
    `sup_id` INT,
    PRIMARY KEY(`emp_id`)
    );

    CREATE TABLE `Branch`(
    `branch_id` INT,
    `branch_name` CHAR(50),
    `manager_id` INT,
    FOREIGN KEY(`manager_id`) REFERENCES `Employee`(`emp_id`) ON DELETE SET NULL,
    PRIMARY KEY(`branch_id`)
    );
    
    
    ALTER TABLE `Employee` ADD FOREIGN KEY(`branch_id`) REFERENCES `Branch`(`branch_id`) ON DELETE SET NULL;
    ALTER TABLE `Employee` ADD FOREIGN KEY(`sup_id`) REFERENCES `Employee`(`emp_id`) ON DELETE SET NULL;
    
    CREATE TABLE `Client`(
    `client_id` INT,
    `client_name` CHAR(50),
    `phone` CHAR(50),
    PRIMARY KEY(`client_id`)
    );
    
    CREATE TABLE `Work_With`(
    `emp_id` INT,
    `client_id` INT,
    `total_sales` INT,
    FOREIGN KEY(`emp_id`) REFERENCES `Employee`(`emp_id`) ON DELETE CASCADE,
    FOREIGN KEY(`client_id`) REFERENCES `Client`(`client_id`) ON DELETE CASCADE,
    PRIMARY KEY(`emp_id`, `client_id`)
    );
    
    
    INSERT INTO `Branch` VALUES(1, '研發', NULL);
	INSERT INTO `Branch` VALUES(2, '行政', NULL);
    INSERT INTO `Branch` VALUES(3, '資訊', NULL);
    
    INSERT INTO `Employee` VALUES(206,'小黃','1999-01-01', 'F', 50000, 1, NULL);
    INSERT INTO `Employee` VALUES(207,'小白','1999-08-01', 'M', 55000, 2, 206);
    INSERT INTO `Employee` VALUES(208,'小黑','1989-02-13', 'F', 45000, 3, 206);
    INSERT INTO `Employee` VALUES(209,'小綠','2001-11-13', 'F', 35000, 3, 207);
    INSERT INTO `Employee` VALUES(210,'小洪','1992-05-28', 'M', 50800, 1, 207);
    
    UPDATE `Branch` SET `manager_id` = 206 WHERE `branch_name` = '研發';
	UPDATE `Branch` SET `manager_id` = 207 WHERE `branch_name` = '行政';
	UPDATE `Branch` SET `manager_id` = 208 WHERE `branch_name` = '資訊';
    
    
    INSERT INTO `Client` VALUES(400, '阿狗', '123456789');
    INSERT INTO `Client` VALUES(401, '阿貓', '223456789');
    INSERT INTO `Client` VALUES(402, '阿鳥', '323456789');
    INSERT INTO `Client` VALUES(403, '阿帥', '523456789');
    INSERT INTO `Client` VALUES(404, '阿美', '623456789');
    
    INSERT INTO `Work_With` VALUES(206,400,70000);
    INSERT INTO `Work_With` VALUES(207,401,24000);
    INSERT INTO `Work_With` VALUES(208,402,9800);
    INSERT INTO `Work_With` VALUES(209,403,24000);
    INSERT INTO `Work_With` VALUES(210,404,88000);
    
    SHOW DATABASES;
    DESCRIBE `Employee`;
    SELECT * FROM `Employee`;
	DESCRIBE `Branch`;
    SELECT * FROM `Branch`;
    DESCRIBE `Client`;
    SELECT * FROM `Client`;
    DESCRIBE `Work_With`;
    SELECT * FROM `Work_With`;
    
    
    SELECT * FROM `Employee` ORDER BY `salary` DESC LIMIT 3;
    SELECT `name` FROM `Employee`;
    SELECT DISTINCT `sex` FROM `Employee`; //不顯示重複數據
    SELECT COUNT(*) FROM `employee`;

    SELECT AVG(`salary`) FROM `employee`; //平均
    SELECT SUM(`salary`) FROM `employee`; //總和
    SELECT MAX(`salary`) FROM `employee`; //最大
    SELECT MIN(`salary`) FROM `employee`; //最小
    
    
    
    
```
