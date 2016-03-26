
#tomcat7中使用Redis 实现Tomcat集群Session同步
源码：
https://github.com/jcoleman/tomcat-redis-session-manager

1. 将以下jar包拷贝到tomcat/lib下
commons-pool2-2.2.jar
jedis-2.5.2.jar
commons-logging-1.1.3.jar
tomcat-redis-session-manage-tomcat7.jar

2.  修改conf/context.xml
添加
<Valve className="com.orangefunction.tomcat.redissessions.RedisSessionHandlerValve" />        
    <Manager className="com.orangefunction.tomcat.redissessions.RedisSessionManager" 
	    host="localhost" //redis HOST
		port="6379"  //redis 端口
		database="0" 
		maxInactiveInterval="1800"/>




Add the following into your Tomcat context.xml (or the context block of the server.xml if applicable.)

<Valve className="com.orangefunction.tomcat.redissessions.RedisSessionHandlerValve" />
<Manager className="com.orangefunction.tomcat.redissessions.RedisSessionManager"
         host="localhost" <!-- optional: defaults to "localhost" -->
         port="6379" <!-- optional: defaults to "6379" -->
         database="0" <!-- optional: defaults to "0" -->
         maxInactiveInterval="60" <!-- optional: defaults to "60" (in seconds) -->
         sessionPersistPolicies="PERSIST_POLICY_1,PERSIST_POLICY_2,.." <!-- optional -->
         sentinelMaster="SentinelMasterName" <!-- optional -->
         sentinels="sentinel-host-1:port,sentinel-host-2:port,.." <!-- optional --> />