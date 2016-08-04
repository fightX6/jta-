# jta-分布式事务

Windows下 出现这个警告  不影响程序运行 
   javax.transaction.xa.XAException: 函数 RECOVER: 失败。状态为: -3。错误:“*** SQLJDBC_XA DTC_ERROR Context: xa_re

    [Atomikos:1] [com.atomikos.recovery.xa.XaResourceRecoveryManager] -  Error while retrieving xids from resource - will retry later...
网上的解决方法是：将驱动里面的sqljdbc_auth.dll文件放入C:\Windows\System32下，重启sqlserver即可   注（我还没有成功过）
