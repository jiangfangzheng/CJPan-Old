# CJPanWebsite
花云云盘

### 截图
![](./[screenshot]/1.jpg)
![](./[screenshot]/2.jpg)

### 使用说明
下载工程，编译打包，生成jar后运行：
java -jar panWebsite.jar --server.port=8080

### 更新日志

#### 2019年07月06日
* 服务Website与处理后台分离，本服务只作为网页前端，服务更名为CJPanWebsite
* 代码重构优化
* 负载均衡

#### 2019年3月29日

* 1. 解决下载安卓手机上的apk在文件名上出现乱码的情况，

> 出现的问题：
> 
> 在火狐浏览器上，中文出现乱码，在谷歌浏览器上，（变成%28，）变成%29
> 
> 出现问题的接口：
> 
> 在controller中的ShareController文件的/downloadApk的接口
> 
> 出现问题原因及解决方法：
> 
> response的编码方式是ISO-8859-1,所以文件名也要以同样的方式解码，解决中文乱码
> 
> 对于%28和%29采用替换的方式

* 2. 解决jpa创建表时默认的字符集的编码方式的问题，（测试中，不知道能否配置成功）

> 出现的问题：
> 
> 为用户注册生成验证码时registerCode，中文的名字不能正确生成验证码
> 
> 出现问题的接口：
> 
> registerCode
> 
> 出现问题的原因及解决办法
> 
> jpa自动生成的表的默认编码方式为latin1，所以在config中配置了一个类MySQL5InnoDBDialectUtf8mb4
> 
> 然后再配置文件中对这个类进行配置
> 
> spring.jpa.database-platform=com.whut.pan.config.MySQL5InnoDBDialectUtf8mb4

#### 2019年3月7日
* server.max-http-header-size=8192

> 在application.properties中添加了这一句，
> 
> 试图解决：
> 
> java.lang.IllegalArgumentException: Invalid character found in method name. 
> 
> HTTP method names must be tokens

#### 2019年3月6日
* 解决一段时间后，springboot部署到服务器后，运行一段时间后处理文件上传的接口报异常
* 在config目录下增加类MultipartConfig
 
#### 2019年2月18日
* 增加下载客户端apk的接口
* 接口名：downloadApk(在ShareController里面)

#### 2018年12月4日
* 动态生成注册码：注册码为6位跟生成密码的代码一致
* 生成注册码只有wsj和zc和517909395@qq.com用户可以操作接口为/registerCode(只有登录了才可以使用)


#### 2018年11月26日
* 根据用户名删除用户 "/alterPassword"
* 更改用户的密码  "/deleteUser", 

#### 2018年11月13日
* 数据库密码加密
* 搜索前端做好
* 上传文件分块断点上传

#### 2018年11月3日
* 搜索只查询当前路径变为查询所有路径（后台）
* 配合安卓接口，download传MD5校验值
* 删除文件中配合安卓接口删除多个文件（以$$分割每个名字）

#### 2018年11月3日
* 复制链接失效问题
* 生成的分享链接中可能出现\r\n替换为了~号
* 密码去掉前后的空格，大小写不区分

#### 2018年3月19日
* 文件夹结构支持
* 文件分享功能
* 修改后台输出Logo
* Bug修复

#### 2018年2月14日
* 新增版本说明、警告文档
* 文件编码后存HDFS，防止特殊字符异常
* 用户退出时清空缓存

#### 2018年2月13日
* HDFS文件下载功能、单独接口
* 限制文件上传大小9999MB

#### 2018年2月12日
* HDFS基本调通
* 待解决：HDFS中不可见字符需编码、HDFS文件提取

#### 2018年2月11日
* 完成上传下载删除重命名功能
* 美化用户界面
* 增加捐助功能
* 修复打包错误

#### 2018年2月10日
* 文件删除、重命名
* HDFS文件系统代码(暂未调试)
* 文件显示修改时间、增加用户名接口

#### 2018年2月10日
* 文件上传功能
* 用户文件列出：文件名、大小、下载地址
* 登录、注册界面美化

#### 2018年2月9日
* 用户注册
* 排除log日志文件
* 界面美化

#### 2018年2月6日
* 花盘动工