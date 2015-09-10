Redis Session Manager for Apache Tomcat
=======================================

Overview
--------

鉴于Redis在3.0升级以后采用服务器集群，对于客户端那个分发已经不在适用

* 在原有的开源代码中进行修改
* 采用Redis3.0的服务器集群
* 需要的jar包：tomcat-catalina7.0.37、commons-pools2.2及新版的jedis3.0，因为在开源中暂时性很难找到，所以将它放入本地项目lib库
* 到时候将生成后的tomcat-redis-session-manager.jar及对应的commons-pools2.2、jedis3.0放入对应tomcat的lib库中
* 该项目支持tomcat8，只要将对应pom.xml或build.gradle中替换成8就行了
* 修改tomcat/conf/context.xml

Usage
-----

Add the following into your Tomcat context.xml (or the context block of the server.xml if applicable.)

    <Valve className="com.orangefunction.tomcat.redissessions.RedisSessionHandlerValve" />
    <Manager className="com.orangefunction.tomcat.redissessions.RedisSessionManager"
             ipAndPort="192.168.5.175:7110,192.168.5.175:7111,192.168.5.175:7112,192.168.5.175:7113,192.168.5.175:7114,192.168.5.175:7115" <!-- optional: defaults to "localhost" -->
             database="0" <!-- optional: defaults to "0" -->
             maxInactiveInterval="60" />
