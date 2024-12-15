# mysql 基本使用

## 管理类

### 查看所有的表

第一种
```sql
show tables;
```

```
mysql> show tables;
+------------------+
| Tables_in_ry_vue |
+------------------+
| gen_table        |
| gen_table_column |
| sys_config       |
| sys_dept         |
| sys_dict_data    |
| sys_dict_type    |
| sys_job          |
| sys_job_log      |
| sys_logininfor   |
| sys_menu         |
| sys_notice       |
| sys_oper_log     |
| sys_post         |
| sys_role         |
| sys_role_dept    |
| sys_role_menu    |
| sys_user         |
| sys_user_post    |
| sys_user_role    |
+------------------+
19 rows in set (0.00 sec)

mysql>
```

第二种

```sql
select table_name,table_comment from information_schema.tables where table_schema = 'ry_vue';
```

```
mysql> select table_name,table_comment from information_schema.tables where table_schema = 'ry_vue';
+------------------+-----------------------------+
| table_name       | table_comment               |
+------------------+-----------------------------+
| gen_table        | 代码生成业务表              |
| gen_table_column | 代码生成业务表字段          |
| sys_config       | 参数配置表                  |
| sys_dept         | 部门表                      |
| sys_dict_data    | 字典数据表                  |
| sys_dict_type    | 字典类型表                  |
| sys_job          | 定时任务调度表              |
| sys_job_log      | 定时任务调度日志表          |
| sys_logininfor   | 系统访问记录                |
| sys_menu         | 菜单权限表                  |
| sys_notice       | 通知公告表                  |
| sys_oper_log     | 操作日志记录                |
| sys_post         | 岗位信息表                  |
| sys_role         | 角色信息表                  |
| sys_role_dept    | 角色和部门关联表            |
| sys_role_menu    | 角色和菜单关联表            |
| sys_user         | 用户信息表                  |
| sys_user_post    | 用户与岗位关联表            |
| sys_user_role    | 用户和角色关联表            |
+------------------+-----------------------------+
19 rows in set (0.00 sec)

mysql>
```

### 查看表的所有字段

第一种

```sql
show full columns from sys_menu;
```

```
mysql> show full columns from sys_menu;
+-------------+--------------+--------------------+------+-----+---------+----------------+---------------------------------+-------------------------------------------+
| Field       | Type         | Collation          | Null | Key | Default | Extra          | Privileges                      | Comment                                   |
+-------------+--------------+--------------------+------+-----+---------+----------------+---------------------------------+-------------------------------------------+
| menu_id     | bigint(20)   | NULL               | NO   | PRI | NULL    | auto_increment | select,insert,update,references | 菜单ID                                    |
| menu_name   | varchar(50)  | utf8mb4_general_ci | NO   |     | NULL    |                | select,insert,update,references | 菜单名称                                  |
| parent_id   | bigint(20)   | NULL               | YES  |     | 0       |                | select,insert,update,references | 父菜单ID                                  |
| order_num   | int(4)       | NULL               | YES  |     | 0       |                | select,insert,update,references | 显示顺序                                  |
| path        | varchar(200) | utf8mb4_general_ci | YES  |     |         |                | select,insert,update,references | 路由地址                                  |
| component   | varchar(255) | utf8mb4_general_ci | YES  |     | NULL    |                | select,insert,update,references | 组件路径                                  |
| query       | varchar(255) | utf8mb4_general_ci | YES  |     | NULL    |                | select,insert,update,references | 路由参数                                  |
| route_name  | varchar(50)  | utf8mb4_general_ci | YES  |     |         |                | select,insert,update,references | 路由名称                                  |
| is_frame    | int(1)       | NULL               | YES  |     | 1       |                | select,insert,update,references | 是否为外链（0是 1否）                     |
| is_cache    | int(1)       | NULL               | YES  |     | 0       |                | select,insert,update,references | 是否缓存（0缓存 1不缓存）                 |
| menu_type   | char(1)      | utf8mb4_general_ci | YES  |     |         |                | select,insert,update,references | 菜单类型（M目录 C菜单 F按钮）             |
| visible     | char(1)      | utf8mb4_general_ci | YES  |     | 0       |                | select,insert,update,references | 菜单状态（0显示 1隐藏）                   |
| status      | char(1)      | utf8mb4_general_ci | YES  |     | 0       |                | select,insert,update,references | 菜单状态（0正常 1停用）                   |
| perms       | varchar(100) | utf8mb4_general_ci | YES  |     | NULL    |                | select,insert,update,references | 权限标识                                  |
| icon        | varchar(100) | utf8mb4_general_ci | YES  |     | #       |                | select,insert,update,references | 菜单图标                                  |
| create_by   | varchar(64)  | utf8mb4_general_ci | YES  |     |         |                | select,insert,update,references | 创建者                                    |
| create_time | datetime     | NULL               | YES  |     | NULL    |                | select,insert,update,references | 创建时间                                  |
| update_by   | varchar(64)  | utf8mb4_general_ci | YES  |     |         |                | select,insert,update,references | 更新者                                    |
| update_time | datetime     | NULL               | YES  |     | NULL    |                | select,insert,update,references | 更新时间                                  |
| remark      | varchar(500) | utf8mb4_general_ci | YES  |     |         |                | select,insert,update,references | 备注                                      |
+-------------+--------------+--------------------+------+-----+---------+----------------+---------------------------------+-------------------------------------------+
20 rows in set (0.00 sec)

mysql>
```

第二种
```sql
select column_name from information_schema.columns where table_schema = 'ry_vue' and table_name = 'sys_menu';
```

```
mysql> select column_name from information_schema.columns where table_schema = 'ry_vue' and table_name = 'sys_menu';
+-------------+
| column_name |
+-------------+
| menu_id     |
| menu_name   |
| parent_id   |
| order_num   |
| path        |
| component   |
| query       |
| route_name  |
| is_frame    |
| is_cache    |
| menu_type   |
| visible     |
| status      |
| perms       |
| icon        |
| create_by   |
| create_time |
| update_by   |
| update_time |
| remark      |
+-------------+
20 rows in set (0.00 sec)

mysql>
```