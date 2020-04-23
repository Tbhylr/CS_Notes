# Adnroid Studio —— gradle故障解决

> `Gradle sync failed: Cause: unable to find valid certification path to requested target`
>
> <img src="MDpic/image-20200424021216080.png" alt="image-20200424021216080" style="zoom: 67%;" />

## gradle包的更换

- 去https://services.gradle.org/distributions/下载对应的all.zip

<img src="MDpic/image-20200424021637633.png" alt="image-20200424021637633" style="zoom:50%;" />

- 覆盖zip文件

<img src="MDpic/image-20200424022458779.png" alt="image-20200424022458779" style="zoom: 67%;" />

## build.gradle设置

外层build.gradle内两个repositories设置：

```grovy
maven{url'http://maven.google.com' }
maven{url'http://jcenter.bintray.com'}
maven{url'http://maven.aliyun.com/nexus/content/groups/public/' }
maven{url'http://maven.oschina.net/content/groups/public/'}
google()
jcenter()
```

<img src="MDpic/image-20200424014201477.png" alt="image-20200424014201477" style="zoom:67%;" />

## Project模板设置

<img src="MDpic/image-20200424015613462.png" alt="image-20200424015613462" style="zoom: 67%;" />

<img src="MDpic/image-20200424015805011.png" alt="image-20200424015805011" style="zoom: 67%;" />

## 软件设置

![image-20200424020757395](MDpic/image-20200424020757395.png)

<img src="MDpic/image-20200424020818243.png" alt="image-20200424020818243" style="zoom: 67%;" />

<img src="MDpic/image-20200424021537212.png" alt="image-20200424021537212" style="zoom:50%;" />

## JAVA_HOME设置

系统环境变量的JAVA_HOME设为AndroidStudio安装路径下的jre路径

- <img src="MDpic/image-20200413133615023.png" alt="image-20200413133615023" style="zoom:50%;" />

## 证书手动导入

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
