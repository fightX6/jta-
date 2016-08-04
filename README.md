# jta-分布式事务
分布式事务指的是允许多个独立的事务资源（transactionalresources）参与一个全局的事务中。事务资源通常是关系型数据库系统， 也可以是其它类型的资源。

JTA(Java Transaction API) 为 J2EE 平台提供了分布式事务服务。 而普通的JDBC 事务的 事务的范围仅局限于一个数据库连接。一个 JDBC 事务不能跨越多个数据库。

一般 Oracle, Sybase, DB2, SQL Server等大型数据库才支持XA, 支持分布事务。mysql对分布式事务支持的不好。mysql只有Innodb存储引擎支持XA事务，通过XA事务可以支持分布式事务的实现。
在使用分布式事务时候，InnoDB存储引擎的事务隔离级别必须设置成serialiable。

分布式事务使用两段式提交（two-phase commit）的方式。在第一个阶段，所有参与全局事务的节点都开始准备，告诉事务管理器它们准备好提交了。第二个阶段，事务管理器告诉资源管理器执行rollback或者commit，如果任何一个节点显示不能commit，那么所有的节点就得全部rollback。

Windows下 出现这个警告  不影响程序运行 
   javax.transaction.xa.XAException: 函数 RECOVER: 失败。状态为: -3。错误:“*** SQLJDBC_XA DTC_ERROR Context: xa_re

    [Atomikos:1] [com.atomikos.recovery.xa.XaResourceRecoveryManager] -  Error while retrieving xids from resource - will retry later...
网上的解决方法是：将驱动里面的sqljdbc_auth.dll文件放入C:\Windows\System32下，重启sqlserver即可   注（我还没有成功过）
