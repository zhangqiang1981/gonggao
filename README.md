## 目录结构
解压后生成以下两个子目录

* xuexi-service，包含各中间件的使用示例代码，代码在src/main/java目录下的cn.xuexi-inc.gonggao包中。
* xuexi-start，包含启动类`cn.xuexi-inc.gonggao.Application`。中间件使用示例的单元测试代码在`src/test/java`目录下的`cn.xuexi-inc.gonggao`包中。日志配置文件为`src/main/resources`目录下的logback-spring.xml。使用springmvc的代码在`src/main/java`目录下的`cn.xuexi-inc.gonggao`包中，velocity模板在`/src/main/resources/templates`目录中。

## 使用方式
### 在开发工具中执行
将工程导入eclipse或者idea后，直接执行包含main方法的类`cn.xuexi-inc.gonggao.Application`。

### 使用fat jar的方式
这也是pandora boot应用发布的方式。首先执行下列命令打包
   
```sh
mvn package
```

如果选择了auto-config，可在命令后加

```sh 
-Dautoconfig.userProperties={fullPath}/bootstrap-start/antx.properties
```

通过-D参数指定antx.properties的位置，否则会进入autoconfig的交互模式

然后进入`xuexi-start/target`目录，执行fat jar

```sh
java -Dpandora.location=${sar} -jar xuexi-start-1.0.0-SNAPSHOT.jar
```

其中${sar}为sar包的路径

### 通过mvn命令直接启动
第一次调用前先要执行

```sh
mvn install
```

如果maven工程的Artifact，group id，version等都未变化，只需执行一次即可。

然后直接通过命令执行start子工程

```sh
mvn -pl xuexi-start pandora-boot:run
```

以上两个命令，如果选择了auto-config，可在命令后加

```sh 
-Dautoconfig.userProperties={fullPath}/bootstrap-start/antx.properties
```

通过-D参数指定antx.properties的位置，否则会进入autoconfig的交互模式properties的位置
