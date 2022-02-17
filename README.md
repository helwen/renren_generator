**项目说明** 
- renren-generator是人人开源项目的代码生成器，可在线生成entity、xml、dao、service、html、js、sql代码，减少70%以上的开发任务
<br> 


**如何交流、反馈、参与贡献？** 
- Git仓库：https://gitee.com/renrenio/renren-generator
- [人人开源](https://www.renren.io)：https://www.renren.io   
- [人人开源社区](https://www.renren.io/community)：https://www.renren.io/community   
- 官方QQ群：324780204、145799952
- 技术讨论、二次开发等咨询、问题和建议，请移步到人人开源社区，我会在第一时间进行解答和回复
- 如需关注项目最新动态，请Watch、Star项目，同时也是对项目最好的支持
- 微信扫码并关注【人人开源】，获得项目最新动态及更新提醒<br>
![输入图片说明](http://cdn.renren.io/47c26201804031918312618.jpg "在这里输入图片标题")
<br> 
<br> 

 **本地部署**
- 通过git下载源码
- 修改application.yml，更新MySQL账号和密码、数据库名称
- Eclipse、IDEA运行RenrenApplication.java，则可启动项目
- 项目访问路径：http://localhost

**演示效果图：**
![输入图片说明](https://images.gitee.com/uploads/images/2018/0731/150920_761d8835_63154.jpeg "aa.jpg")

如果要使用mybatisplus的话，要用3.2以下的版本，否则启动时会报错。
<dependency>
			<groupId>com.baomidou</groupId>
			<artifactId>mybatis-plus-boot-starter</artifactId>
			<version>3.0.1</version>
		</dependency>
		<dependency>
			<groupId>com.baomidou</groupId>
			<artifactId>mybatis-plus-generator</artifactId>
			<version>3.5.0</version>
		</dependency>
		<dependency>
			<groupId>com.baomidou</groupId>
			<artifactId>mybatis-plus-extension</artifactId>
			<version>3.0.1</version>
		</dependency>
		<dependency>
			<groupId>cn.hutool</groupId>
			<artifactId>hutool-all</artifactId>
			<version>4.4.2</version>
		</dependency>
然后在配置文件中加

mybatis.mapper-locations=classpath:mybatis/*.xml   --这个是mybatis用来扫码的,能将mapper接口与mapper.xml联系起来，否则没绑定。
# 下划线格式转换成驼峰格式
mybatis.configuration.map-underscore-to-camel-case=true
mybatis-plus.mapper-locations=classpath:mybatis/*.xml  --这个是mybatis-plus用来扫码的,能将mapper接口与mapper.xml联系起来，否则没绑定。
mybatis-plus.global-config.db-config.id-type=auto
mybatis-plus.global-config.db-config.insertStrategy=NOT_EMPTY
mybatis-plus.global-config.db-config.updateStrategy=NOT_EMPTY
mybatis-plus.configuration.map-underscore-to-camel-case=true
mybatis-plus.configuration.call-setters-on-nulls=true
mybatis-plus.configuration.log-impl=org.apache.ibatis.logging.stdout.StdOutImpl

注意在GenUtils.java类中配置各种模板。getTemplates方法取到哪些模板，要在getFileName方法中取设置各个模板对应的生成文件名。
