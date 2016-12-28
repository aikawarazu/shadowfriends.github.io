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
##### 在main/resource/下面，application.properties文件中加入配置：
		server.port=8081
		server.context-path=/whataaa
