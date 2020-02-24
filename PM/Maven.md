所有代码，都是项目+配置。

Maven是Java的包管理工具，类似于python的pip,node.js的npm.用它可以方便的导入Java第三方库（Spring,Struts,JUnit）和插件（Tomcat）
我在电脑上已经配置好了，IDEA开发。
# Maven的配置过程
https://www.cnblogs.com/stars-one/p/10958796.html 安装和配置
# Maven+IDEA开发
https://www.cnblogs.com/getupmorning/p/7249014.html 一个简单的示例

Maven项目的配置文件就是pom.xml,用来定义Maven项目的有关数据，引入列库依赖。IDEA可以开发Maven项目，通过xml配置外部库，然后就可以使用Java第三方库，类似于pip，这是我目前的感受。

Maven坐标：GroupId,ArtifactId,Version。GroupId一般是公司名或者公司网址。ArtifactId可以理解为项目名，如果是组件，则通过-来分隔。Version默认为1.0-SNAPSHOT,表示未上线。

引入依赖：类库一般是通过pom.xml进行引入的，IDEA会自动引入对应内容

pom.xml是非常有Java特色的东西。

IDEA+Maven经典bug:https://www.jianshu.com/p/8ff4652fabd0 一定可以解决error:java:不支持发行版本5