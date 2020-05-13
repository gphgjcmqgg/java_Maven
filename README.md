# java_Maven

Maven
官网：http://maven.apache.org/

## Apache Maven 概述

Maven 是一个项目管理和整合工具。Maven 为开发者提供了一套完整的构建生命周期框架。开发团队几乎不用花多少时间就能够自动完成工程的基础构建配置，因为 Maven 使用了一个标准的目录结构和一个默认的构建生命周期。
maven是一个基于java平台的自动化构建工具
make-ant-maven-gradle

## Maven 能够帮助开发者完成以下工作：

1. 构建
2. 文档生成
3. 报告
4. 依赖
5. SCMs
6. 发布
7. 分发
8. 邮件列表

## Maven的作用

1. 管理jar包
2. 将项目拆分成若干个模块

## Maven 主要用处一：相同的项目结构

1. 有一个pom.xml 用于维护当前项目都用了哪些jar包
2. 所有的java代码都放在 src/main/java 下面
3. 所有的测试代码都放在src/test/java 下面

## Maven 主要用处二：统一维护jar包

maven风格的项目，首先把所有的jar包都放在"仓库“ 里，然后哪个项目需要用到这个jar包，只需要给出jar包的名称和版本号就行了。 这样jar包就实现了共享

## Maven解压后需要配置环境变量

配置完Path环境变量后，执行mvn -v看配置是否成功

## Maven仓库

仓库默认位置
~\.m2\repository

打开maven安装目录，D:\software\apache-maven-3.6.3\conf\settings.xml    --52行指定了仓库的位置

你还可以在运行时指定本地仓库位置：
mvn clean install -Dmaven.repo.local=d:\yourpath

使用阿里云下载路径
<mirror>
  <id>nexus-aliyun</id>  
  <mirrorOf>*,!jeecg,!jeecg-snapshots</mirrorOf>  
  <name>Nexus aliyun</name>  
  <url>http://maven.aliyun.com/nexus/content/groups/public</url>  
</mirror>

修改本地仓库
<localRepository>d:/maven/repository</localRepository>

中央仓库资源：
http://mvnrepository.com/
https://search.maven.org/

当构建一个Maven项目时，首先检查pom.xml文件以确定依赖包的下载位置，执行顺序如下：
1、从本地资源库中查找并获得依赖包，如果没有，执行第2步。
2、从Maven默认中央仓库中查找并获得依赖包（http://repo1.maven.org/maven2/），如果没有，执行第3步。
3、如果在pom.xml中定义了自定义的远程仓库，那么也会在这里的仓库中进行查找并获得依赖包，如果都没有找到，那么Maven就会抛出异常。

## 创建maven项目

mvn archetype:generate -DgroupId=com.how2java -DartifactId=j2se -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false

archetype:generate 表示创建个项目
-DgroupId 项目包名: com.how2java
-DartifactId 项目名称: j2se
-DarchetypeArtifactId 项目类型: maven-archetype-quickstart
-DinteractiveMode:false 表示前面参数都给了，就不用一个一个地输入了


方法一：

输入命令 mvn archetype:generate，按回车，根据提示输入参数，如果是第一次使用，需要下载插件，稍等几分钟即可。
切换目录，输入指令

方法二： 

在命令中指定参数
mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=myapp -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false



## maven 运行package命令

注： 运行这个命令之前要先把当前路径切换到项目路径来

mvn package
package做了编译，测试，打包，最后生成了一个j2se-1.0-SNAPSHOT.jar包，里面放了APP这个类

## 执行Jar

java -cp target/j2se-1.0-SNAPSHOT.jar com.how2java.App

## Jetty运行Web项目


