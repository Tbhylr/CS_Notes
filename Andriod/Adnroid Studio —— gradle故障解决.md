# Adnroid Studio —— gradle故障解决

## 证书无效：<u>Cause: unable to find valid certification path to requested target</u>

- 外层build.gradle内两个repositories设置：

  ```grovy
  mavenCentral()
  maven { url 'http://maven.google.com' }
  maven { url 'http://jcenter.bintray.com'}
  maven {
      url 'http://maven.aliyun.com/nexus/content/groups/public/'
  }
  ```

- 注意将系统环境变量的JAVA_HOME设为AndroidStudio安装路径下的jre路径

  - ![image-20200413133615023](MDpic/image-20200413133615023.png)

- 网页下载证书到本地创建的.cer文件：https://maven.aliyun.com/mvn/view

  <img src="MDpic/image-20200413133628261.png" alt="image-20200413133628261" style="zoom: 67%;" />

- 管理员身份打开CMD向JAVA导入证书：
  - 执行 keytool -import -file server222.cer -keystore "%JAVA_HOME%\jre\lib\security\cacerts" -alias server 
  - -file 后面是刚导出来的 server.cer 文件路径
  - -alias server 表示别名是 server
  - JAVA默认密钥为：changeit
  - 确认信任此证书
  -  出现下面提示，表示正常导入到 %JAVA_HOME% 里面

![image-20200413133650709](MDpic/image-20200413133650709.png)![image-20200413133701822](MDpic/image-20200413133701822.png)
