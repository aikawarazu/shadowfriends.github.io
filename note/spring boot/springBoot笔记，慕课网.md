SpringBoot慕课网学习 
===================================  
0、最简单的demo
-----------------------
1、配置
-----------------------
2、controller
-----------------------
3、spring-data-jpa
-----------------------
4、事物控制
-----------------------

### 需要回顾的知识
		maven
		spring注解
		RESTful

0、最简单的demo
-----------------------
##### 0、配置文件pom.xml：
		<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
			xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
		http://maven.apache.org/xsd/maven-4.0.0.xsd">
			<modelVersion>4.0.0</modelVersion>
			<groupId>com.fh</groupId>
			<artifactId>spring-boot-test1</artifactId>
			<version>0.0.1-SNAPSHOT</version>
			<name>springboot练习</name>

			<parent>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-starter-parent</artifactId>
				<version>1.4.3.RELEASE</version>
			</parent>
			<dependencies>
				<dependency>
					<groupId>org.springframework.boot</groupId>
					<artifactId>spring-boot-starter-web</artifactId>
				</dependency>
			</dependencies>
			<build>
				<plugins>
					<plugin>
						<groupId>org.springframework.boot</groupId>
						<artifactId>spring-boot-maven-plugin</artifactId>
					</plugin>
				</plugins>
			</build>
		</project>

##### 启动：SampleController.java
编写一个main方法，实现：
		SpringApplication.run(SampleController.class, args);

##### 编写controller类：
		@Controller
		public class HelloSpringBoot {
			@ResponseBody
			@RequestMapping("/hello")
			String home() {
				return "Hello World!";
			}
		}

##### 运行SampleController.main方法
		运行方式：
		1、直接运行
		2、项目目录下，使用 mvn spring-boot:run
		3、编译：mvn :install， java运行：java -jar spring-boot-test1-0.0.1-SNAPSHOT.jar
	
	
1、配置
-----------------------	
##### 方式一:properties 配置
		在main/resource/下面，application.properties文件中加入配置：
		server.port=8081
		server.context-path=/whataaa
		这样，访问http://localhost:8081/whataaa/hello就可以了。
		
##### 方式二:yml 配置
		创建如下几个配置文件：
> 	application-dev.yml
> 	application-product.yml
> 	application.yml

		application-product、application-product配置文件内容如下：
>>  	server:
>>      port: 8081
>>      context-path: /whataaa
>>  base:
>>      address: 192.168.1.47 
>>      username: hao.fu
>>      password: 123456
>>      content: "${base.address}"
>> 
		application.yml内容如下：
>>  		spring:
>>      profiles:
>>        active: product

		创建配置类，使用注解：ConfigurationProperties，注意prefix属性

		@Component
		@ConfigurationProperties(prefix="# base #")
		public class DataBaseConfig {
			String address; 
			String username;
			String password;
			String content;
			...
		}

#### 配置总结：1、使用yml控制多环境		2、使用ConfigurationProperties配置值

2、controller
------------------------------
##### RestController和GetMapping：
	RestController 相当于 Controller+ResponseBody
	GetMapping 相当于 RequestMapping 中限定method=get