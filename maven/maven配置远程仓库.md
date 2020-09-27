#### maven 配置指南
打开 maven 的配置文件（ windows 机器一般在 maven 安装目录的 conf/settings.xml ），在<mirrors></mirrors>标签中添加 mirror 子节点:
```
<mirror>
  <id>aliyunmaven</id>
  <mirrorOf>*</mirrorOf>
  <name>阿里云公共仓库</name>
  <url>https://maven.aliyun.com/repository/public</url>
</mirror>
```

link: https://maven.aliyun.com/mvn/guide