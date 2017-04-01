#### 数据库和表
- 进入`mysql`:`mysql -uroot -p`

![mysql.png](http://upload-images.jianshu.io/upload_images/2050891-a5d6e911361b610e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 查看数据库:`show databases;`

![show_databases.png](http://upload-images.jianshu.io/upload_images/2050891-a852168c02144b12.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 删除数据库:`drop database dbname;`

![drop_database.png](http://upload-images.jianshu.io/upload_images/2050891-93693eef7639f132.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 创建数据库:`create database dbname;`

![create_database.png](http://upload-images.jianshu.io/upload_images/2050891-c142e2e51c86e21c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 创建指定编码和字符集的数据库:`CREATE DATABASE test DEFAULT CHARACTER SET utf8 DEFAULT COLLATE utf8_general_ci;`

![create_database_utf8.png](http://upload-images.jianshu.io/upload_images/2050891-b3f115641a351613.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 指定要使用数据库:`use dbname`，查看数据库中的数据表:`show tables`

![use_show.png](http://upload-images.jianshu.io/upload_images/2050891-4bab0db0be134ad7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 删除数据表:`drop table table_name;`

![drop_table.png](http://upload-images.jianshu.io/upload_images/2050891-c7d01e56dc8a5e04.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 创建一张表:
```
CREATE TABLE IF NOT EXISTS test_users(
id INT(11) UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY COMMENT '用户编号',
username VARCHAR(255) NOT NULL DEFAULT '' COMMENT '用户名',
password CHAR(40) NOT NULL DEFAULT '10470c3b4b1fed12c3baac014be15fac67c6e815' COMMENT '密码',
realname VARCHAR(255) NOT NULL DEFAULT '' COMMENT '姓名',
sex ENUM('male', 'female', 'secret') NOT NULL DEFAULT 'secret' COMMENT '性别',
age TINYINT(1) NOT NULL DEFAULT 0 COMMENT '年龄',
introduce TEXT COMMENT '介绍',
created DATETIME NOT NULL DEFAULT NOW() COMMENT '记录创建时间',
modified DATETIME COMMENT '记录修改时间',
UNIQUE INDEX index_username(username)
)ENGINE=InnoDb DEFAULT CHARACTER SET = utf8 COMMENT '用户表';
```

![create_table.png](http://upload-images.jianshu.io/upload_images/2050891-14c2085e12a61c77.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 查看建表语句:`show create table table_name;`

![show_create_table.png](http://upload-images.jianshu.io/upload_images/2050891-1da5711f614bccbf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 查看表结构:`desc table_name;`

![desc_table.png](http://upload-images.jianshu.io/upload_images/2050891-4deb28a8a2a8c778.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 不指定字段向表中插入一条记录:`insert into tablename values(全部字段值列表)`
```
insert into test_users values(null, 'stone', '10470c3b4b1fed12c3baac014be15fac67c6e815', '刘备', 'male', 50, '刘皇叔', now(), null);
```
![insert_one_value.png](http://upload-images.jianshu.io/upload_images/2050891-c4b79bfcadef9bdf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 不指定字段向表中插入多条记录:`insert into tablename values(全部字段值列表), (全部字段值列表)`
```
insert into test_users values(null, 'jack', '10470c3b4b1fed12c3baac014be15fac67c6e815', '关羽', 'male', 49, '关云长', now(), null), (null, 'tony', '10470c3b4b1fed12c3baac014be15fac67c6e815', '张飞', 'male', 48, '张翼德', now(), nu
ll);
```
![insert_multiple_values.png](http://upload-images.jianshu.io/upload_images/2050891-4850549a836cdb3f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 向一个表中添加一个字段:`alter table tablename add column_name type ...`
`alter table test_users add status tinyint(1) unsigned not null default 2 comment '记录状态:0-删除, 1-禁用, 2-启用' after introduce;`

![add_column_after.png](http://upload-images.jianshu.io/upload_images/2050891-32d7bba28a905ec9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

`alter table test_users add modified_by int(11) not null comment '记录修改者';`

![add_column.png](http://upload-images.jianshu.io/upload_images/2050891-29561087d6a81fca.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

`alter table test_users add created_by int(11) unsigned not null default 0 comment '记录创建者' first;`

![add_column_first.png](http://upload-images.jianshu.io/upload_images/2050891-afc2629abd30901e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 指定字段向表中插入一条记录:`insert into tablename(字段列表) values(字段值列表)`
```
insert into test_users(username, password, realname, sex, age, introduce) values('stone', '10470c3b4b1fed12c3baac014be15fac67c6e815', '赵云', 'male', 40, '赵子龙');
```

![insert_one_no_default.png](http://upload-images.jianshu.io/upload_images/2050891-b2b63c8b5fdb843b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

```
insert into test_users(username, password, realname, sex, age, introduce, modified_by) values('stone', '10470c3b4b1fed12c3baac014be15fac67c6e815', '赵云', 'male', 40, '赵子龙', 1);
```

![insert_one_duplicate_entry.png](http://upload-images.jianshu.io/upload_images/2050891-9da66dea67b0f890.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

```
insert into test_users(username, password, realname, sex, age, introduce, modified_by) values('tom', '10470c3b4b1fed12c3baac014be15fac67c6e815', '赵云', 'male', 40, '赵子龙', 1);
```

![insert_one_row.png](http://upload-images.jianshu.io/upload_images/2050891-0b616c5e89d831cb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

```
insert into test_users(username, password, realname, sex, age, introduce, modified_by) values('mike', '10470c3b4b1fed12c3baac014be15fac67c6e815', '马超', 'male', 38, '马孟起', 1), ('client', '10470c3b4b1fed12c3baac014be15fac67c6e815', '黄忠', 'male', 55, '黄汉升', 1);
```

![](//upload-images.jianshu.io/upload_images/2050891-d62b25b711695ddc.png)

- 删除字段:`alter table tablename drop column column_name`
```
alter table test_users add column test_small smallint not null default 0 comment '小整型字段';
alter table test_users drop column teat_small;
```
![](//upload-images.jianshu.io/upload_images/2050891-3bbb30009c063303.png)

- 修改字段类型:`alter table tablename modify column_name type ...`
```
alter table test_users modify modified_by int(11) unsigned not null default 0 comment '记录修改者';
```

![](//upload-images.jianshu.io/upload_images/2050891-386c0db900eba400.png)

- 删除数据表记录:`delete from tablename where column_name1 = column_value1 AND column_name2 = column_value2 ...`
```
delete from test_users where id = 1 and username = 'stone';
```

![](//upload-images.jianshu.io/upload_images/2050891-c0b58ee0b8230485.png)

```
delete from test_users;
```

![](//upload-images.jianshu.io/upload_images/2050891-e1a78682ef752048.png)

![](//upload-images.jianshu.io/upload_images/2050891-b1c6e7f7cf00c05b.png)

- 清空表:`truncate tablename`
```
truncate test_users;
```

![](//upload-images.jianshu.io/upload_images/2050891-29867984d3a8fa5b.png)

- 更改字段:`alter table table_name change column_name new_column_name type ...`
```
alter table test_users change created_by created_by_id int(11) unsigned zerofill not null default 0 comment '记录创建者';
```

![](//upload-images.jianshu.io/upload_images/2050891-9baf9e0dca7b3d0d.png)

#### 字段类型
###### 数字类型
- BIT[(M)]:比特数据类型是一种特殊的数字类型，其中`M`指示了一个值可以占用多少比特，取值范围是1-64，如果没有指定`M`，则默认值是1。将数字保存到比特类型字段中将会被转化为数字对应的ascii字符。
```
CREATE TABLE IF NOT EXISTS test_bit(
bit_test BIT NOT NULL DEFAULT 0 COMMENT '比特测试字段'
)ENGINE=InnoDB DEFAULT CHARACTER SET=utf8 COMMENT '比特类型测试表';
```
![bit_1.png](http://upload-images.jianshu.io/upload_images/2050891-0a270189a647e11a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
```
CREATE TABLE IF NOT EXISTS test_bit(
bit_test BIT(2) NOT NULL DEFAULT 0 COMMENT '比特测试字段'
)ENGINE=InnoDB DEFAULT CHARACTER SET=utf8 COMMENT '比特类型测试表';
```
![bit_2.png](http://upload-images.jianshu.io/upload_images/2050891-3ee6f808d82ed34c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
```
CREATE TABLE IF NOT EXISTS test_bit(
bit_test BIT(3) NOT NULL DEFAULT 0 COMMENT '比特测试字段'
)ENGINE=InnoDB DEFAULT CHARACTER SET=utf8 COMMENT '比特类型测试表';
```
![bit_3.png](http://upload-images.jianshu.io/upload_images/2050891-8ea0b4e0ac96dd5b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
```
CREATE TABLE IF NOT EXISTS test_bit(
bit_test BIT(4) NOT NULL DEFAULT 0 COMMENT '比特测试字段'
)ENGINE=InnoDB DEFAULT CHARACTER SET=utf8 COMMENT '比特类型测试表';
```
![bit_4.png](http://upload-images.jianshu.io/upload_images/2050891-4226a06d7e87ff42.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![select_bit_4.png](http://upload-images.jianshu.io/upload_images/2050891-0aaf7d2238732d2c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
```
CREATE TABLE IF NOT EXISTS test_bit(
bit_test BIT(64) NOT NULL DEFAULT 0 COMMENT '比特测试字段'
)ENGINE=InnoDB DEFAULT CHARACTER SET=utf8 COMMENT '比特类型测试表';
```
![select_bit_64.png](http://upload-images.jianshu.io/upload_images/2050891-734b96518754828f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- TINYINT[(M)] [UNSIGNED] [ZEROFILL]:占用1个字节的整型数据，有符号的数据范围是-128到127，无符号的数据范围是0到255。通过`M`来指定数字位数，通过`UNSIGNED`来指定是否有符号，通过`ZEROFILL`来指定是否进行零填充。
```
CREATE TABLE IF NOT EXISTS test_int(
tiny_test TINYINT(2) UNSIGNED NOT NULL DEFAULT 0 COMMENT '小整型字段'
)ENGINE=InnoDB DEFAULT CHARACTER SET=utf8 COMMENT '整型数据类型测试表';
```
![unsigned_tinyint.png](http://upload-images.jianshu.io/upload_images/2050891-b005e7c694ab78eb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
```
CREATE TABLE IF NOT EXISTS test_int(
tiny_test TINYINT(2) ZEROFILL NOT NULL DEFAULT 0 COMMENT '小整型字段'
)ENGINE=InnoDB DEFAULT CHARACTER SET=utf8 COMMENT '整型数据类型测试表';
```
![zerofill_tinyint.png](http://upload-images.jianshu.io/upload_images/2050891-2c09c7a696a235f4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
```
CREATE TABLE IF NOT EXISTS test_int(
tiny_test TINYINT(2) NOT NULL DEFAULT 0 COMMENT '极小整型字段'
)ENGINE=InnoDB DEFAULT CHARACTER SET=utf8 COMMENT '整型数据类型测试表';
```

![tinyint.png](http://upload-images.jianshu.io/upload_images/2050891-e0ce4daefa765f9d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- BOOL(BOOLEAN):布尔型和`tinyint(1)`是一样的
```
CREATE TABLE IF NOT EXISTS test_bool(
bool_test BOOL NOT NULL DEFAULT 0 COMMENT '布尔型字段'
)ENGINE=InnoDB DEFAULT CHARACTER SET=utf8 COMMENT '布尔型数据类型测试表';
```

![](//upload-images.jianshu.io/upload_images/2050891-2e6ab70c4f3040e2.png)

![bool_if.png](http://upload-images.jianshu.io/upload_images/2050891-f2f4e84937af41cf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- SMALLINT[(M)] [UNSIGNED] [ZEROFILL]:占用2个字节的整型数据，有符号的数据范围是-32768到32767，无符号的数据范围是0到65535。通过`M`来指定数字位数，通过`UNSIGNED`来指定是否有符号，通过`ZEROFILL`来指定是否进行零填充。
```
alter table test_int add column test_small smallint not null default 0 comment '小整型字段';
```

![](//upload-images.jianshu.io/upload_images/2050891-9f2734de41df283f.png)

![alter_test_int.png](http://upload-images.jianshu.io/upload_images/2050891-c1f4d6e87f22c49a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![modify_tiny_test.png](http://upload-images.jianshu.io/upload_images/2050891-3aa62b31796cbd85.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- MEDIUMINT[(M)] [UNSIGNED] [ZEROFILL]:占用3个字节的整型数据，有符号的数据范围是-8388608到8388607，无符号的数据范围是0到16777215。通过`M`来指定数字位数，通过`UNSIGNED`来指定是否有符号，通过`ZEROFILL`来指定是否进行零填充。
- INT(INTEGER)[(M)] [UNSIGNED] [ZEROFILL]:占用4个字节的整型数据，有符号的数据范围是-2147483648到2147483647，无符号的数据范围是0到4294967296。通过`M`来指定数字位数，通过`UNSIGNED`来指定是否有符号，通过`ZEROFILL`来指定是否进行零填充。
- BIGINT[(M)] [UNSIGNED] [ZEROFILL]:占用8个字节的整型数据，有符号的数据范围是-9223372036854775808到9223372036854775807，无符号的数据范围是0到18446744073709551615。通过`M`来指定数字位数，通过`UNSIGNED`来指定是否有符号，通过`ZEROFILL`来指定是否进行零填充。如果一个字段被设置成`BIGINT UNSIGNED NOT NULL AUTO_INCREMENT UNIQUE`，则该字段被认为是`SERIAL`的。

![serial.png](http://upload-images.jianshu.io/upload_images/2050891-4115200f400bd033.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![bigint.png](http://upload-images.jianshu.io/upload_images/2050891-a9e718b801ca5b51.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![bigint2.png](http://upload-images.jianshu.io/upload_images/2050891-55505d11649624ed.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![drop_column_2.png](http://upload-images.jianshu.io/upload_images/2050891-0cfee9d47c728a66.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
```
create table if not exists test_int(
bigint_test bigint unsigned not null default 0 comment 'bigint test'
)engine=myisam default character set=utf8 comment '整型测试';
```

![create_bigint_table.png](http://upload-images.jianshu.io/upload_images/2050891-9de05c51436581c7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![auto_increment_field.png](http://upload-images.jianshu.io/upload_images/2050891-766b3950246d14da.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![bigint_insert_test.png](http://upload-images.jianshu.io/upload_images/2050891-6281022e36ac4227.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![min_max.png](http://upload-images.jianshu.io/upload_images/2050891-e565c61072c21574.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- DECIMAL[(M[,D])] [UNSIGNED] [ZEROFILL]:总数为`M`，小数位数为`D`的小数，负数的`-`及小数点不算在`M`中，`M`的最大数为65，`D`的最大数为30，`D`的默认值为0，`M`的默认值为10。通过`UNSIGNED`来指定是否有符号，通过`ZEROFILL`来指定是否进行零填充。
```
create table if not exists test_float(
decimal_test decimal(5, 2) not null default 0 comment 'decimal test'
)engine=myisam default character set=utf8 comment '浮点数测试表'; 
```

![create_decimal.png](http://upload-images.jianshu.io/upload_images/2050891-cf8a6b1ff6d71cc9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![insert_decimal.png](http://upload-images.jianshu.io/upload_images/2050891-c15ef497f5448270.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![select_decimal.png](http://upload-images.jianshu.io/upload_images/2050891-6934744d3589a491.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![unsigned_decimal.png](http://upload-images.jianshu.io/upload_images/2050891-2a8877c8b9bcccfc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![insert_unsigned_decimal.png](http://upload-images.jianshu.io/upload_images/2050891-25628c4ad40d3818.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![zerofill_decimal.png](http://upload-images.jianshu.io/upload_images/2050891-11b1445e1ca18136.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- DEC[(M[,D])] [UNSIGNED] [ZEROFILL], NUMERIC[(M[,D])] [UNSIGNED] [ZEROFILL], FIXED[(M[,D])] [UNSIGNED] [ZEROFILL]都和DECIMAL和一样的，FIXED适合与其它数据库管理系统进行交互。
- FLOAT[(M, D)] [UNSIGNED] [ZEROFILL]:单精度浮点数，取值范围是-1.7976931348623157E+308到-2.2250738585072014E-308, 0, 以及2.2250738585072014E-308到1.7976931348623157E+308，这是基于IEEE标准的理论值，实际值可能略小于这个范围，主要取决于硬件配置和操作系统。`M`是数字的总位数，`D`是小数位数，如果`M`和`D`被省略了，数值将会根据硬件的限制来存储。单精度浮点数大概可以精确到小数点后面6位。指定了`unsigned`的字段不能保存负数。使用`FLOAT`可能会带来意想不到的问题，因为在`mysql`中数据的计算是按照双精度来进行。

![create_float.png](http://upload-images.jianshu.io/upload_images/2050891-9572270268825ad2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![insert_float.png](http://upload-images.jianshu.io/upload_images/2050891-0bb7d27eef853db1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![insert_float(5,2).png](http://upload-images.jianshu.io/upload_images/2050891-6f9c5d81137d8580.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![insert_float(5,2)_2.png](http://upload-images.jianshu.io/upload_images/2050891-48af9f228a465b1d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- DOUBLE[(M, D)] [UNSIGNED] [ZEROFILL]:双精度浮点数，取值范围是-1.7976931348623157E+308到-2.2250738585072014E-308, 0, 以及2.2250738585072014E-308到1.7976931348623157E+308，这是基于IEEE标准的理论值，实际值可能略小于这个范围，主要取决于硬件配置和操作系统。`M`是数字的总位数，`D`是小数位数，如果`M`和`D`被省略了，数值将会根据硬件的限制来存储。双精度浮点数大概可以精确到小数点后面15位。指定了`unsigned`的字段不能保存负数。
- DOUBLE PRECISION[(M,D)] [UNSIGNED] [ZEROFILL], REAL[(M,D)] [UNSIGNED] [ZEROFILL]这两种是DOUBLE的同义词，但是如果REAL_AS_FLOAT模式被打开的话，REAL就是和FLOAT是同义的。
- FLOAT(p) [UNSIGNED] [ZEROFILL]:这是一个浮点数，其中`p`表示在比特位上的精度，但是`mysql`仅仅在决定该使用`FLOAT`还是`DOUBLE`来存放结果值的时候使用这个值，如果`p`的范围是0到24，数据类型将是没有`M`和`D`的`FLOAT`。如果`p`的值从25到53，数据的类型将会是没有指定`M`和`D`的`DOUBLE`。字段的范围和之前描述的单精度浮点类型`FLOAT`和双精度浮点类型`DOUBLE`一致。`FLOAT(p)是为了和`ODBC`交互而提供的。
- DATE
在`mysql`中日期格式以`YYYY-MM-DD`形式显示，取值范围为`1000-01-01`到`9999-12-31`，这个类型保存的数据只能是字符串或数字。
```
create table if not exists datetime_test(
test_date date comment 'test date'
)engine=myisam default character set=utf8 comment '日期时间测试表';
```

![datetime_test.png](http://upload-images.jianshu.io/upload_images/2050891-bb5bdf55ef4f9d8f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![insert_date.png](http://upload-images.jianshu.io/upload_images/2050891-f3f38a8ca4b9c4c2.png)

- DATETIME[(fsp)]
`fsp`是可选的，用于表示小于秒的时间，取值范围是`0`到`6`，默认值是`0`。`DATETIME`可以用于表示日期时间，支持的范围从`1000-01-01 00:00:00.000000`到`9999-12-31 23:59:59.999999`。在`mysql`中日期的格式为`YYYY-MM-DD HH:MM:SS[.fraction]`，允许存放的值只能是字符串和数字。
```
alter table datetime_test change test_date test_datetime datetime comment 'datetime test';
```

![create_datetime.png](http://upload-images.jianshu.io/upload_images/2050891-7ea9839f7573970c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![insert_datetime.png](http://upload-images.jianshu.io/upload_images/2050891-6e70a4e4ccccb30a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- TIMESTAMP[(fsp)]
timestamp表示时间戳，范围从`1970-01-01 00:00:01.000000` UTC to `2038-01-19 03:14:07.999999` UTC，UTC是世界标准时间。timestamp存储的是从`1970-01-01 00:00:00` UTC以来的秒数。`fsp`是可选的，用于表示小于秒的时间，取值范围是`0`到`6`，默认值是`0`。
```
alter table datetime_test change test_datetime test_timestamp timestamp comment 'timestamp test';
```

![test_timestamp.png](http://upload-images.jianshu.io/upload_images/2050891-4b4e0b626091b1c4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- TIME[(fsp)]
- YEAR[(4)]
- [NATIONAL] CHAR(M) [CHARACTER SET charset_name] [COLLATE collation_name]
`M`的范围从`0`到`255`
- [NATIONAL] VARCHAR(M) [CHARACTER SET charset_name] [COLLATE collation_name]
`M`的范围从`0`到`65535`
- ENUM('value1','value2',...) [CHARACTER SET charset_name] [COLLATE collation_name]
- TINYBLOB
最大可存储字节数为255
- TINYTEXT [CHARACTER SET charset_name] [COLLATE collation_name]
最大可存储字符数为255
- BLOB[(M)]
最大可存储字节数为65535
- TEXT[(M)] [CHARACTER SET charset_name] [COLLATE collation_name]
最大可存储字符数为65535
- MEDIUMBLOB
最大可存储字节数为16777215(2 ** 24 - 1)
- MEDIUMTEXT [CHARACTER SET charset_name] [COLLATE collation_name]
最大可存储字符数为16777215(2 ** 24 - 1)
- LONGBLOB
最大可存储字节数为4294967295 (2 ** 32 − 1)
- LONGTEXT [CHARACTER SET charset_name] [COLLATE collation_name]
最大可存储字符数为4294967295 (2 ** 32 − 1)