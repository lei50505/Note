# Note

* 新建文件夹

```
D:\dev\repos
D:\dev\tools
```

* 安装Typora

```
安装typora-setup.exe
```
* 安装Git

```
安装Git-2.6.3-64-bit.exe
打开Git Bash
ssh-keygen -t rsa -b 4096 -C "183515951@qq.com"
cd .ssh/
cat id_rsa.pub
添加到GitHub

git config --global push.default simple
git config --global user.name "CAOLEI"
git config --global user.email 183515951@qq.com

C:\Users\CAOLEI\AppData\Local\Programs\Git\etc -> 右键Git GUI Here打开文件位置 -> etc/bash.bashrc
alias ga='git add'
alias gaa='git add -A'
alias gb='git branch'
alias gba='git branch -a'
alias gc='git commit'
alias gcm='git commit -m'
alias gcmm='git commit -m "update"'
alias gco='git checkout'
alias gd='git diff'
alias gl='git pull'
alias glog='git log --oneline --decorate --color --graph'
alias gm='git merge'
alias gp='git push'
alias gst='git status'
```

* VS Project添加Git

```
新建WPF项目
解决方案IPGW -> 右键 -> 将解决方案添加到源代码管理 -> Git -> 确定
GitHub新建仓库IPGW
项目目录内 -> 右键 -> Git Bash Here
git add -A
git commit -m "init"
git remote add origin git@github.com:lei50505/IPGW.git
git push -u origin master
```

* 安装JDK

```
安装jdk-8u77-windows-x64.exe
配置环境变量
新建 -> JAVA_HOME -> C:\Program Files\Java\jdk1.8.0_77
PATH前加 -> %JAVA_HOME%\bin
```

* 安装Maven

```
解压apache-maven-3.3.9-bin.zip -> D:\dev\tools
配置环境变量
新建 -> M2_HOME -> D:\dev\tools\apache-maven-3.3.9
PATH前加 -> %M2_HOME%\bin
```

* 安装Tomcat8

```
解压apache-tomcat-8.0.22-windows-x64.zip -> -> D:\dev\tools
```

* 安装Spring Tool Suite 3.6.3

```
解压spring-tool-suite-3.6.3.RELEASE-e4.4.1-win32-x86_64.zip -> D:\Programs
创建快捷方式 -> D:\Programs\sts-bundle\sts-3.6.3.RELEASE\STS.exe

打开STS
Select a workspace
Workspace -> D:\STS
选中Use this as the defult... -> OK

Preferences
Install/Update -> Automatic Update -> 取消Automatically find...
Java -> Installed JREs -> 选择JDK1.8 -> 只有JRE需添加JDK -> 无用的移除 -> Edit...
Default VM arguments -> 填写 -Dmaven.multiModuleProjectDirectory=$M2_HOME
Server -> Runtime Environments -> Add... -> Tomcat v8.0 + Create a new... -> OK -> Tomcat installation directory -> dev/tools/apache-tomcat-8.0.30 -> JRE选择JDK1.8 -> Finish
Maven -> Installations -> Add... -> Installation home -> dev/tools/apache-maven-3.3.9 -> Finish -> 选择新添加 -> Apply
General -> Editors -> Text Editors -> 选中Insert spaces for tabs -> OK
Java -> Code Style -> Formatter -> Edit... -> Tab policy -> 选Spaces only -> Profile name -> 改Spaces only -> OK

布局
左
Package Explorer
下
Console
Servers
Problems
Progress
右
Outline

下Servers -> 删除Pivotal tc Server... -> 选中Delete unused...
双击Tomcat v8.0 -> Open
Server Locations -> 选中Use Tomcat installation...
Deploy path -> webapps
command + S 保存

退出
Confirm Exit -> 选中Always exit without prompt
```

* 安装MySQL

```
安装mysql-essential-5.1.68-win32.msi
最后选中Config MySQL ... Now
Detailed Configuration -> Developer Machine -> Multifunctional Database -> Manual Selected Default Character Set/Collation -> utf8 -> Include Bin Directory in Windows PATH -> 取消Launch MySQL Server automatically -> 设置Root密码为password -> 选中Enable root access from...
```

* 安装Navicat

```
安装并注册navicat 10.0.10+注册机+注册码.rar
```

* 安装WebStorm

```
安装WebStorm-10.0.4.exe
激活
User or company Name:
EMBRACE
===== LICENSE KEY=====
24718-12042010
00001h6wzKLpfo3gmjJ8xoTPw5mQvY
YA8vwka9tH!vibaUKS4FIDIkUfy!!f
3C"rQCIRbShpSlDcFT1xmJi5h0yQS6
===== LICENSE END =====
```

* 安装Nginx

```
解压nginx-1.8.1.zip -> ...D:\dev\tools

新建 nginx-start.bat
D:
cd D:\dev\tools\nginx-1.8.1
start nginx.exe

nginx.exe -s stop 退出不保存
nginx.exe -s quit 退出保存
nginx.exe -s reload 重新加载
```

* 新建项目

```
打开 D:\dev\repos
Shift + 右键 -> 在此处打开命令窗口
mvn archetype:generate -DgroupId=cn.rest -DartifactId=my-web -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false -DarchetypeCatalog=local
cd my-web
mvn eclipse:eclipse

STS -> Import -> Existing Maven Projects -> Next
Root Directory -> ...dev/repos/my-web -> Finish

pom.xml
添加properties
<properties>
		<!-- 源文件编码,解决单独设置目标编码warning -->
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
		<!-- 编译jdk版本 -->
		<maven-compiler-plugin.source>1.8</maven-compiler-plugin.source>
		<!-- 目标jdk版本 -->
		<maven-compiler-plugin.target>1.8</maven-compiler-plugin.target>
		<!-- junit版本 -->
		<junit.version>4.12</junit.version>
</properties>

改junit.version
<dependencies>
		<!-- junit单元测试 -->
		<!-- junit-4.12.jar -->
		<!-- hamcrest-core-1.3.jar -->
		<dependency>
			<groupId>junit</groupId>
			<artifactId>junit</artifactId>
			<version>${junit.version}</version>
			<scope>test</scope>
		</dependency>
</dependencies>

添加build
<build>
		<!-- 解决eclipse升级报错 -->
		<pluginManagement>
			<plugins>
				<plugin>
					<groupId>org.apache.maven.plugins</groupId>
					<artifactId>maven-compiler-plugin</artifactId>
					<version>3.3</version>
					<configuration>
						<!-- jdk版本 -->
						<source>${maven-compiler-plugin.source}</source>
						<target>${maven-compiler-plugin.target}</target>
						<!-- 文件编码 -->
						<encoding>${project.build.sourceEncoding}</encoding>
					</configuration>
				</plugin>
			</plugins>
		</pluginManagement>
		<!-- target包名字 -->
		<finalName>my-web</finalName>
</build>

修改target包名字

Ctrl + Shift + F 格式化代码
Ctrl + S 保存
Alt + F5 更新项目

my-web -> Properties -> Java Build Path -> Libraries
jre
maven

Alt + F5 更新项目

New Source Folder -> 
src/main/resources
src/test/resources
各添加a.txt防止空目录不上传

my-web -> Properties -> Java Build Path -> Order and Export
main/java
main/resources
test/java
test/resources
maven
jre

my-web -> Properties -> Java Build Path -> Source
main -> Output folder -> target/classes
test -> Output folder -> target/test-classes

改<packaging>war</packaging>
Ctrl + Shift + F 格式化代码
Ctrl + S 保存
Alt + F5 更新项目

my-web -> Properties
Project Facets -> Dynamic Web Module -> 勾取消 -> Apply -> 勾选中 -> 3.1 -> Further configuration available -> Content directory -> src/main/webapp -> Generate web.xml deployment descriptor
```

* 上传

```
打开 D:\dev\repos\my-web
右键 -> git bash
git init
Alt + F5 更新项目
my-web -> Team -> Share Project -> Git -> Next
Alt + F5 更新项目
git add -A
git commit -m "init"
GitHub创建my-web
git remote add origin git@github.com:lei50505/my-web.git
git push -u origin master
```

* 整合SpringMVC

```
pom.xml
		<!-- spring版本 -->
		<spring.version>4.2.3.RELEASE</spring.version>
		
		<!-- spring-webmvc -->
		<!-- spring-webmvc-4.2.3.RELEASE.jar -->
		<!-- spring-beans-4.2.3.RELEASE.jar -->
		<!-- spring-context-4.2.3.RELEASE.jar -->
		<!-- spring-aop-4.2.3.RELEASE.jar -->
		<!-- aopalliance-1.0.jar -->
		<!-- spring-core-4.2.3.RELEASE.jar -->
		<!-- commons-logging-1.2.jar -->
		<!-- spring-expression-4.2.3.RELEASE.jar -->
		<!-- spring-web-4.2.3.RELEASE.jar -->
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-webmvc</artifactId>
			<version>${spring.version}</version>
		</dependency>
		
		<!-- jackson版本 -->
		<jackson.version>2.6.3</jackson.version>
		
		<!-- jackson-databind -->
        <!-- jackson-databind-2.6.3.jar -->
        <!-- jackson-annotations-2.6.0.jar -->
        <!-- jackson-core-2.6.3.jar -->
        <dependency>
            <groupId>com.fasterxml.jackson.core</groupId>
            <artifactId>jackson-databind</artifactId>
            <version>${jackson.version}</version>
        </dependency>
        
Ctrl + Shift + F 格式化代码
Ctrl + S 保存
Alt + F5 更新项目

src/main/resources -> New -> Bean Configuration File
applicationContext.xml

<!-- DispatcherServlet -->

	web.xml
	<servlet>
		<servlet-name>SpringMVC</servlet-name>
		<servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
		<init-param>
			<param-name>contextConfigLocation</param-name>
			<param-value>classpath:applicationContext.xml</param-value>
		</init-param>
		<load-on-startup>1</load-on-startup>
	</servlet>

<servlet-mapping>
	<servlet-name>SpringMVC</servlet-name>
	<url-pattern>*.do</url-pattern>
</servlet-mapping>

<!-- component-scan -->

applicationContext.xml -> Namespaces -> 选中context
<context:component-scan base-package="cn.rest"></context:component-scan>
@Reposirory
@Servicce
@Controller
@Autowired / @Qualifier("loginServiceImpl")
@Resource(name="")

<!-- annotation-driven -->

applicationContext.xml -> Namespaces -> 选中mvc
<mvc:annotation-driven></mvc:annotation-driven>
@RequestMapping("/login")

<!-- 可访问SpringMVC -->

cn.rest -> 新建包controller
controller包下新建类GreetingController

@RestController 
public class GreetingController {
    
    @RequestMapping(value="/hello.do",method=RequestMethod.GET)
    public ResponseEntity<Map<String, Object>> hello(){
        Map<String, Object> map = new HashMap<String, Object>();
        map.put("message", "Hello");
        return new ResponseEntity<Map<String, Object>>(map,HttpStatus.OK);
    }
}

<!-- 添加log4j -->

		pom.xml
		<!-- log4j版本 -->
		<log4j.version>1.2.17</log4j.version>
		
		<!-- log4j -->
		<!-- log4j-1.2.17.jar -->
		<dependency>
			<groupId>log4j</groupId>
			<artifactId>log4j</artifactId>
			<version>${log4j.version}</version>
		</dependency>
		
main/resources -> 新建log4j.properties
#--------console-----------
log4j.rootLogger=info,myconsole
log4j.appender.myconsole=org.apache.log4j.ConsoleAppender
log4j.appender.myconsole.layout=org.apache.log4j.SimpleLayout
#--------HTML-----------
#log4j.rootLogger=error,myfile
#log4j.appender.myfile=org.apache.log4j.FileAppender
#log4j.appender.myfile.File=D\:\\error.html
#log4j.appender.myfile.layout=org.apache.log4j.HTMLLayout
#--------txt,log-----------
#log4j.rootLogger=error,myfile
#log4j.appender.myfile=org.apache.log4j.FileAppender
#log4j.appender.myfile.File=D\:\\error.log
#log4j.appender.myfile.layout=org.apache.log4j.PatternLayout

<!-- aspectj-autoproxy -->
		
		pom.xml
		<!-- aspectjweaver版本 -->
		<aspectjweaver.version>1.8.7</aspectjweaver.version>

		<!-- aspectjweaver -->
		<!-- aspectjweaver-1.8.7.jar -->
		<dependency>
			<groupId>org.aspectj</groupId>
			<artifactId>aspectjweaver</artifactId>
			<version>${aspectjweaver.version}</version>
		</dependency>
		
		提供@Aspect @Around
		
		<!-- servlet-api版本 -->
		<servlet-api.version>2.5</servlet-api.version>
		
		<!-- servlet-api -->
		<!-- servlet-api-2.5.jar -->
		<dependency>
			<groupId>javax.servlet</groupId>
			<artifactId>servlet-api</artifactId>
			<version>${servlet-api.version}</version>
		</dependency>
		
		提供HttpServletRequest

<aop:aspectj-autoproxy proxy-target-class="true"></aop:aspectj-autoproxy>

cn.rest -> 新建包aspect
aspect包下新建类ExceptionLogger

@Component
@Aspect
public class ExceptionLogger {
    @Around("within(cn.rest..*)")
    public Object log(ProceedingJoinPoint p) throws Throwable {
        Object result = null;
        try {
            result = p.proceed(); //调用目标组件
        } catch (Throwable e) {
            //e.printStackTrace();
            //log4j
            Logger logger = Logger.getLogger(this.getClass());
            ServletRequestAttributes sr = (ServletRequestAttributes) RequestContextHolder.getRequestAttributes();
            HttpServletRequest request = sr.getRequest();
            String ip = request.getRemoteHost();
            String now = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss").format(new Date());
            String className = p.getTarget().getClass().getName();
            String methodName = p.getSignature().getName();
            logger.error("IP[" + ip + "],");
            logger.error("在[" + now + "],");
            logger.error("调用[" + className + "." + methodName + "]时,发生如下异常:");
            logger.error("    ["+e.toString()+"]");
            StackTraceElement[] elems = e.getStackTrace();
            for(StackTraceElement elem : elems) {
                logger.error("    " + elem.toString());
            }
            throw e;
        }
        return result;
    }
}

controller包下新建类BaseController
@ControllerAdvice
public class BaseController {
    @ExceptionHandler(value=Throwable.class)
    public ResponseEntity<Map<String, Object>> handleThrowable(Throwable e){
        Map<String, Object> map = new HashMap<String, Object>();
        map.put("message", e.getLocalizedMessage());
        return new ResponseEntity<Map<String, Object>>(map,HttpStatus.INTERNAL_SERVER_ERROR);
    }
}

<!-- properties -->

cn.rest -> 新建包util
util包下新建类ConfigUtils
public class ConfigUtils extends PropertyPlaceholderConfigurer {

    private static final Map<String, Object> propertiesMap = new HashMap<String, Object>();

    @Override
    protected void processProperties(
            ConfigurableListableBeanFactory beanFactoryToProcess,
            Properties props) throws BeansException {
        super.processProperties(beanFactoryToProcess, props);
        for (Object key : props.keySet()) {
            String keyStr = key.toString().trim();
            propertiesMap.put(keyStr, props.getProperty(keyStr).trim());
        }
    }

    public static String getString(String key) {
        return propertiesMap.get(key).toString();
    }

    public static Integer getInt(String key) {
        return Integer.valueOf(propertiesMap.get(key).toString());
    }

    public static Long getLong(String key) {
        return Long.valueOf(propertiesMap.get(key).toString());
    }
}

main/resources -> db.properties
db.driver=com.mysql.jdbc.Driver
db.url=jdbc:mysql://127.0.0.1:3306/webapp
db.user=root
db.password=password

	<!-- 加载配置文件 -->
	<!-- util:properties方式,类中@Value("#{jdbc[driver]}") -->
	<!-- <util:properties id="jdbc" location="classpath:db.properties"></util:properties> -->
	<!-- PropertyPlaceholderConfigurer方式,这里使用其扩展,以便其在源代码中使用,类中ConfigUtils.getString("db.driver") -->
	<bean class="cn.rest.util.ConfigUtils">
		<property name="locations">
			<list>
				<value>classpath:db.properties</value>
			</list>
		</property>
		<property name="fileEncoding" value="UTF-8" />
		<property name="ignoreResourceNotFound" value="false" />
	</bean>
```

* 整合MyBatis

```
运行MySQL
创建数据库和表
CREATE DATABASE `web` DEFAULT CHARSET utf8 COLLATE utf8_general_ci;
USE `web`;
CREATE TABLE `user` (
  `id` int(11) unsigned NOT NULL AUTO_INCREMENT,
  `name` varchar(16) NOT NULL DEFAULT '' COMMENT '姓名',
  `sex` tinyint(1) NOT NULL COMMENT '性别',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8;

更改db.properties属性
db.driver=com.mysql.jdbc.Driver
db.url=jdbc:mysql://127.0.0.1:3306/web?useUnicode=true&characterEncoding=utf8
db.user=root
db.password=password

<!-- BasicDataSource dbcp连接池 -->
		
		pom.xml
		<!-- mysql-connector-java版本 -->
		<mysql-connector-java.version>5.1.37</mysql-connector-java.version>
		
		<!-- mysql-connector-java -->
		<!-- mysql-connector-java-5.1.37.jar -->
		<dependency>
			<groupId>mysql</groupId>
			<artifactId>mysql-connector-java</artifactId>
			<version>${mysql-connector-java.version}</version>
		</dependency>
		
		<!-- commons-dbcp版本 -->
		<commons-dbcp.version>1.4</commons-dbcp.version>
		
		<!-- commons-dbcp -->
		<!-- commons-dbcp-1.4.jar -->
		<!-- commons-pool-1.5.4.jar -->
		<dependency>
			<groupId>commons-dbcp</groupId>
			<artifactId>commons-dbcp</artifactId>
			<version>${commons-dbcp.version}</version>
		</dependency>
		
	<bean id="ds" class="org.apache.commons.dbcp.BasicDataSource">
		<property name="driverClassName" value="${db.driver}"></property>
		<property name="url" value="${db.url}"></property>
		<property name="username" value="${db.user}"></property>
		<property name="password" value="${db.password}"></property>
	</bean>
	
<!-- SqlSessionFactoryBean -->

cn.rest -> 新建包entity
entity包下新建类User
实现序列化接口
无参构造函数
有参构造函数多个
getter和setter方法
重写equals和hashCode
重写toString

public class User implements Serializable {

    private static final long serialVersionUID = 1L;
    private Integer id;
    private String name;
    private Integer sex;
    public User() {
        super();
    }
    
    public User(String name, Integer sex) {
        super();
        this.name = name;
        this.sex = sex;
    }

    public User(Integer id, String name, Integer sex) {
        super();
        this.id = id;
        this.name = name;
        this.sex = sex;
    }
    public Integer getId() {
        return id;
    }
    public void setId(Integer id) {
        this.id = id;
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public Integer getSex() {
        return sex;
    }
    public void setSex(Integer sex) {
        this.sex = sex;
    }
    @Override
    public String toString() {
        return "User [id=" + id + ", name=" + name + ", sex=" + sex + "]";
    }
    @Override
    public int hashCode() {
        final int prime = 31;
        int result = 1;
        result = prime * result + ((id == null) ? 0 : id.hashCode());
        return result;
    }
    @Override
    public boolean equals(Object obj) {
        if (this == obj)
            return true;
        if (obj == null)
            return false;
        if (getClass() != obj.getClass())
            return false;
        User other = (User) obj;
        if (id == null) {
            if (other.id != null)
                return false;
        } else if (!id.equals(other.id))
            return false;
        return true;
    }
}

cn.rest -> 新建包dao
dao包下新建接口UserDao
public interface UserDao {
    public void insert(User user);
}

main/resources/mapper下新建UserMapper.xml
<?xml version="1.0" encoding="UTF-8" ?>  
<!DOCTYPE mapper PUBLIC "-//ibatis.apache.org//DTD Mapper 3.0//EN"      
 "http://ibatis.apache.org/dtd/ibatis-3-mapper.dtd">
<mapper namespace="cn.rest.dao.UserDao">
	<insert id="insert" parameterType="cn.rest.entity.User" useGeneratedKeys="true" keyProperty="id">
        insert into `user`(`name`,`sex`) values(
          #{name,jdbcType=VARCHAR},
          #{sex,jdbcType=INTEGER}
        )
    </insert>
</mapper>

<!-- MyBatis插入对象时，自动在对象内补全主键
对于支持自动生成主键的数据库(如SQL Server)，可以采用以下方式 
<insert id="xxx" parameterType="yyy" useGeneratedKeys="true" keyProperty="id">
.... 
</insert>  
对于不支持自动生成主键(如Oracle)，可以采用以下方式 
<insert id="xxx" parameterType="yyy">   
    <selectKey keyProperty="id" resultType="long" order="BEFORE"> 
        select my_seq.nextval from dual  
    </selectKey>   .... 
</insert> 
-->

		pom.xml
		<!-- mybatis-spring版本 -->
		<mybatis-spring.version>1.2.3</mybatis-spring.version>
		
		<!-- mybatis-spring -->
		<!-- mybatis-spring-1.2.3.jar -->
		<dependency>
			<groupId>org.mybatis</groupId>
			<artifactId>mybatis-spring</artifactId>
			<version>${mybatis-spring.version}</version>
		</dependency>

	<bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
		<property name="dataSource" ref="ds"></property>
		<property name="mapperLocations" value="classpath:mapper/*.xml"></property>
	</bean>

<!-- MapperScannerConfigurer -->
		
		pom.xml
		<!-- mybatis版本 -->
		<mybatis.version>3.3.0</mybatis.version>
		
		<!-- mybatis -->
		<!-- mybatis-3.3.0.jar -->
		<dependency>
			<groupId>org.mybatis</groupId>
			<artifactId>mybatis</artifactId>
			<version>${mybatis.version}</version>
		</dependency>

	<bean class="org.mybatis.spring.mapper.MapperScannerConfigurer">
		<property name="basePackage" value="cn.rest.dao"></property>
		<!-- 可以用注解的方式查找dao -->
		<!-- <property name="annotationClass" value="cn.springmvc.annotation.MyBatisRepository"></property> -->
		<property name="sqlSessionFactoryBeanName" value="sqlSessionFactory"></property>
	</bean>
	
<!-- transactionManager -->

		pom.xml
		<!-- spring-jdbc -->
		<!-- spring-jdbc-4.2.3.RELEASE.jar -->
		<!-- spring-tx-4.2.3.RELEASE.jar -->
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-jdbc</artifactId>
			<version>${spring.version}</version>
		</dependency>
	
	<bean id="transactionManager"
		class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
		<property name="dataSource" ref="ds"></property>
	</bean>
	
	<!-- 注解声明事务 -->
	<!-- <tx:annotation-driven proxy-target-class="true" -->
	<!-- transaction-manager="transactionManager" /> -->
	<!-- 配置事务 -->
	<tx:advice id="txAdvice" transaction-manager="transactionManager">
		<tx:attributes>
			<tx:method name="get*" propagation="NOT_SUPPORTED" />
			<tx:method name="find*" propagation="NOT_SUPPORTED" />
			<tx:method name="add*" propagation="REQUIRED" />
			<tx:method name="*" read-only="true" />
		</tx:attributes>
	</tx:advice>
	<aop:config expose-proxy="true">
		<aop:pointcut expression="within(cn.rest.service..*)"
			id="txPointcut" />
		<aop:advisor pointcut-ref="txPointcut" advice-ref="txAdvice" />
	</aop:config>
	
cn.rest -> 新建包service
service包下新建接口UserService
public interface UserService {
    public void add(User user);
}

cn.rest -> 新建包service.impl
service.impl包下新建类UserServiceImpl实现接口UserService
@Service
public class UserServiceImpl implements UserService {
    
    @Autowired
    private UserDao userDao;

    @Override
    public void add(User user) {
        userDao.insert(user);
    }
}

GreetingController.class
@Autowired
    private UserService userService;
```

*  SecurityFilter

```
filter包下新建类SecurityFilter
@Component
public class SecurityFilter implements Filter {
    
    private Logger log = Logger.getLogger(this.getClass());

    @Override
    public void destroy() {
    }

    @Override
    public void doFilter(ServletRequest req, ServletResponse res,
            FilterChain chain) throws IOException, ServletException {
        HttpServletRequest request = (HttpServletRequest) req;
        HttpServletResponse response = (HttpServletResponse) res;
        //解决跨域问题
        response.setHeader("Access-Control-Allow-Origin", "*");
        log.info("SecurityFilter过滤前 " );
        if ("1".equals(request.getParameter("id"))) {
            response.setContentType("application/json");
            response.setStatus(HttpStatus.INTERNAL_SERVER_ERROR.value());
            PrintWriter writer = response.getWriter();
            writer.write("{\"message\":\"error\"}");
            writer.flush();
            writer.close();
            return;
        }
        chain.doFilter(request, response);
        log.info("SecurityFilter过滤后 ");
        
    }

    @Override
    public void init(FilterConfig arg0) throws ServletException {
    }

}

	web.xml
	<filter>
		<filter-name>Encoding</filter-name>
		<filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
		<init-param>
			<param-name>encoding</param-name>
			<param-value>UTF-8</param-value>
		</init-param>
		<init-param>
			<param-name>forceEncoding</param-name>
			<param-value>true</param-value>
		</init-param>
	</filter>
	<filter>
		<filter-name>securityFilter</filter-name>
		<filter-class>org.springframework.web.filter.DelegatingFilterProxy</filter-class>
		<init-param>
			<param-name>targetFilterLifecycle</param-name>
			<param-value>true</param-value>
		</init-param>
	</filter>
	<filter-mapping>
		<filter-name>Encoding</filter-name>
		<url-pattern>/*</url-pattern>
	</filter-mapping>
	<filter-mapping>
		<filter-name>securityFilter</filter-name>
		<url-pattern>*.do</url-pattern>
	</filter-mapping>
```

* 安装Redis

```
解压 Redis-x64-2.8.2400.zip -> dev/tools

环境变量
REDIS_HOME D:\dev\tools\Redis-x64-2.8.2400
PATH %REDIS_HOME%;...

编辑 redis.windows.conf
port 63790
requirepass caolei123

新建 redis-server-start.bat
redis-server D:\dev\tools\Redis-x64-2.8.2400\redis.windows.conf

新建 redis-cli-loclahost.bat
redis-cli -h localhost -p 63790 -a caolei123

新建 redis-cli-bandwagonhost.bat
redis-cli -h 144.168.63.86 -p 63790 -a caolei123
```

