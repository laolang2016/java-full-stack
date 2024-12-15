# oracle 安装和卸载

## 参考

[Oracle11g服务详细介绍及哪些服务是必须开启的？](https://blog.csdn.net/daniel_fei/article/details/56678843)

[18、oracle11g与19c的区别](https://www.cnblogs.com/lgxdev/p/17877610.html)

## 11g 服务介绍以及哪些需要开启

> 摘抄自: [Oracle11g服务详细介绍及哪些服务是必须开启的？](https://blog.csdn.net/daniel_fei/article/details/56678843)

![](/java/java-full-stack/assets/images/oracle/a02_install_and_uninstall/001.png)


<table>
    <tr>
        <td>服务名</td>
        <td>介绍</td>
    </tr>
    <tr>
        <td>Oracle ORCL VSS Writer Service</td>
        <td>Oracle卷映射拷贝写入服务，VSS（Volume Shadow Copy Service）能够让存储基础设备（比如磁盘，阵列等）创建高保真的时间点映像，即映射拷贝（shadow copy）。它可以在多卷或者单个卷上创建映射拷贝，同时不会影响到系统的系统能。（非必须启动）</td>
    </tr>
    <tr>
        <td>OracleDBConsolexx（xx表示实例名称）</td>
        <td>Oracle数据库控制台服务，orcl是Oracle的实例标识，默认的实例为orcl。在运行Enterprise Manager（企业管理器OEM）的时候，需要启动这个服务。（非必须启动）</td>
    </tr>
    <tr>
        <td>OracleJobSchedulerORCL</td>
        <td>Oracle作业调度（定时器）服务，ORCL是Oracle实例标识。（非必须启动）</td>
    </tr>
    <tr>
        <td>OracleMTSRecoveryService</td>
        <td>服务端控制。该服务允许数据库充当一个微软事务服务器MTS、COM/COM+对象和分布式环境下的事务的资源管理器。（非必须启动）</td>
    </tr>
    <tr>
        <td>OracleOraDb11g_home1ClrAgent</td>
        <td>Oracle数据库.NET扩展服务的一部分。（非必须启动）</td>
    </tr>
    <tr>
        <td>OracleOraDb11g_home1TNSListener</td>
        <td>
监听器服务，服务只有在数据库需要远程访问的时候才需要。（非必须启动，下面会有详细详解）。

（监听器服务，服务只有在数据库需要远程访问时才需要（无论是通过另外一台主机还是在本地通过 SQL*Net 网络协议都属于远程访问），不用这个服务就可以访问本地数据库，它的缺省启动类型为自动。服务进程为TNSLSNR.EXE，参数文件Listener.ora，日志文件listener.log，控制台LSNRCTL.EXE，默认端口1521、1526。）
        </td>
    </tr>
    <tr>
        <td>OracleServicexx（xx表示实例名称）</td>
        <td>
数据库服务(数据库实例)，是Oracle核心服务该服务，是数据库启动的基础， 只有该服务启动，Oracle数据库才能正常启动。(必须启动)

（数据库服务，这个服务会自动地启动和停止数据库。如果安装了一个数据库，它的缺省启动类型为自动。服务进程为ORACLE.EXE，参数文件initSID.ora，日志文件SIDALRT.log，控制台SVRMGRL.EXE、SQLPLUS.EXE。）
        </td>
    </tr>
</table>


对新手来说，要是只用Oracle自带的sql*plus的话，只要启动`OracleServiceORCL`即可，要是使用PL/SQL Developer等第三方工具的话，`OracleOraDb11g_home1TNSListener`服务也要开启。OracleDBConsoleorcl是进入基于web的EM必须开启的，其余服务很少用。注：ORCL是数据库实例名，默认的数据库是ORCL，你可以创建其他的，即OracleService+数据库名。






