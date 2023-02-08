# 数据库

以下是基于 Mysql 数据库的开发流程示例

## 配置

| 数据库参数 | 值                  |
| ---------- | ------------------- |
| 地址       | 192.168.71.146:3306 |
| 用户       | root                |
| 密码       | root                |
| 数据库     | thea                |

那么需要在 DemoSQLConfig，改为自己数据库对应的连配置

```java
	static {
		DEFAULT_DATABASE = DATABASE_MYSQL;  // TODO 默认数据库类型，改成你自己的
		DEFAULT_SCHEMA = "sys";  // TODO 默认数据库名/模式，改成你自己的，默认情况是 MySQL: sys, PostgreSQL: public, SQL Server: dbo, Oracle: 

		// 表名和数据库不一致的，需要配置映射关系。只使用 APIJSONORM 时才需要；
		// 如果用了 apijson-framework 且调用了 APIJSONApplication.init 则不需要
		// (间接调用 DemoVerifier.init 方法读取数据库 Access 表来替代手动输入配置)。
		// 但如果 Access 这张表的对外表名与数据库实际表名不一致，仍然需要这里注册。例如
		//		TABLE_KEY_MAP.put(Access.class.getSimpleName(), "access");

		//表名映射，隐藏真实表名，对安全要求很高的表可以这么做
		TABLE_KEY_MAP.put("User", "apijson_user");
		TABLE_KEY_MAP.put("Privacy", "apijson_privacy");
	}

	@Override
	public String getDBVersion() {
		return "5.7.22";  // "8.0.11";  // TODO 改成你自己的 MySQL 或 PostgreSQL 数据库版本号  // MYSQL 8 和 7 使用的 JDBC 配置不一样
	}
	
	@Override
	public String getDBUri() {
		return "jdbc:mysql://localhost:3306?serverTimezone=GMT%2B8&useUnicode=true&characterEncoding=UTF-8"; // TODO 改成你自己的，TiDB 可以当成 MySQL 使用，默认端口为 4000
	}
	
	@Override
	public String getDBAccount() {
		return "root";  // TODO 改成你自己的
	}
	
	@Override
	public String getDBPassword() {
		return "apijson";  // TODO 改成你自己的，TiDB 可以当成 MySQL 使用， 默认密码为空字符串 ""
	}
```

## 导入表

在 [APIJSON-Demo-Master](https://github.com/APIJSON/APIJSON-Demo)/MySQL 目录下有一批 SQL 脚本，他们看起来是这样的：

![use1](../.vuepress/public/assets/use1.png)

其中 APIJSON 5.4 及以下必须导入 Function, Request, Access；APIJSON 6.x 必须导入 Function, Request, Access, Script。

导入完成之后。我们可以把项目跑起来看下，以刚刚配置的项目，项目是否能够连上数据库。其中也有一些初始化数据，可以方便我们测试。
