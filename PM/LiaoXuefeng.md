Maven是Java项目管理和构建工具，用于定义项目结构，项目依赖，并使用统一方式进行自动化构建。
# Maven介绍
构建Java项目，Maven之前的时代：

一、确定项目需要引入哪些依赖的包

二、确定项目目录结构

三、配置环境

四、用命令行工具进行编译

Maven的项目结构：

pom.xml:项目描述文件；

groupId类似于Java包名，artifactId类似于Java类名
```
<dependency>
    <groupId>commons-logging</groupId>
    <artifactId>commons-logging</artifactId>
    <version>1.2</version>
</dependency>
```
使用dependency声明一个依赖后，Maven就会自动下载依赖包，并放到classpath中。

src/main/java：Java源代码；src/main/resources:资源文件；src/test/java:测试源代码；src/test/resources:测试资源；target:编译，打包生成的文件。
# 依赖管理
Maven定义的依赖关系：compile,test,runtime,provided

|scope|说明|示例|
|----|----|----|
|compile|编译时需要用到该jar包（默认）|commons-logging|
|test|编译Test时需要用到该jar包|junit|
|runtime|编译时不需要，但运行时需要用到|mysql|
|provided|编译时需要用到，但运行时由JDK或某个服务器提供|servlet-api|

用户主目录的.m2目录是Maven的包缓存目录
# 标准化构建流程
自动化实现compile,package,发布

lifecycle,phase,goal

lifecycle由phase构成，以default lifecycle为例
```
validate
initialize
generate-sources
process-sources
generate-resources
process-resources
compile
process-classes
generate-test-sources
process-test-sources
generate-test-resources
process-test-resources
test-compile
process-test-classes
test
prepare-package
package
pre-integration-test
integration-test
post-integration-test
verify
install
deploy
```
运行mvn package,就会执行default生命周期，直到package

lifecycle clean
```
pre-clean
clean （注意这个clean不是lifecycle而是phase）
post-clean
```
mvn command 后面是phase

多个phase

mvn clean:清理所有生成的class和jar；

mvn clean comile:先清理，然后执行到compile;

mvn clean test;

mvn clean package;

phase和goal
|执行的phase|对应执行的goal|
|----|----|
|compile|compiler:compile|
|test|compiler:testCompile;<br>surefile:test|

总结：lifecycle类似于package;phase类似于class,goal类似于method;
# 使用插件
# 模块管理
# 使用mvnw