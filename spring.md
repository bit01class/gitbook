# SPRING



* Spring Core
  * Spring 프레임워크의 근간이 되는요소. IoC\(또는 DI\) 기능을 지원하는 영역을 담당.
  * BeanFactory를 기반으로 Bean 클래스들을 제어할 수 있는 기능을 지원
* Spring Context
  * Spring Core 바로 위에 있으면서 Spring Core에서 지원하는 기능외에 추가적인 기능들과 좀 더 쉬운 개발이 가능하도록 지원
* Spring DAO
  * 지금까지 우리들이 일반적으로 많이 사용해왔던 JDBC 기반하의 DAO개발을 좀 더 쉽고, 일관된 방법으로 개발하는 것이 가능하도록 지원
  * Spring DAO를 이용할 경우 지금까지 개발하던 DAO보다 적은 코드와 쉬운 방법으로 DAO를 개발하는 것이 가능
* Spring ORM
  * Object Relation Mapping 프레임워크인 Hibernate, IBatis, JDO와의 결합을 지원하기 위한 기능 
  * Spring ORM을 이용할 경우 Hibernate, IBatis, JDO 프레임워크와 쉽게 통합하는 것이 가능
* Spring AOP
  * Spring 프레임워크에 Aspect Oriented Programming을 지원하는 기능이다. 이 기능은 AOP Alliance 기반하에서 개발
* Spring Web
  * Web Application 개발에 필요한 Web Application Context와 Multipart Request등의 기능을 지원
* Spring Web MVC
  * Spring 프레임워크에서 독립적으로 Web UI Layer에 Model-View-Controller를 지원하기 위한 기능





### Interceptor

### 

{% code-tabs %}
{% code-tabs-item title="com.bit.interceptor.MyInterceptor.java" %}
```java
public class MyInterceptor extends HandlerInterceptorAdapter { 
    private static final Logger logger = LoggerFactory.getLogger(MyInterceptor.class); 
    // 컨트롤러 실행 전 
    @Override 
    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception { 
        logger.info("preHandle call......"); 
        if (handler instanceof HandlerMethod) { 
            HandlerMethod method = (HandlerMethod) handler; 
            logger.info("handler method name : " + method.getMethod().getName()); 
        } 
        return true; 
    } 
    // 컨트롤러 실행 후, View 페이지가 렌더링 되기전
    @Override 
    public void postHandle(HttpServletRequest request, HttpServletResponse response, Object handler, ModelAndView modelAndView) throws Exception { 
        logger.info("postHandle call......"); 
    } 
    // View 페이지가 렌더링 되고 난 후 
    @Override 
    public void afterCompletion(HttpServletRequest request, HttpServletResponse response, Object handler, Exception ex) throws Exception { 
        logger.info("afterCompletion call......"); 
    } 
    // 비동기 호출시 Servlet 3.0 ~
    @Override 
    public void afterConcurrentHandlingStarted(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception { 
        logger.info("afterConcurrentHandlingStarted call......"); 
    } 
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="/WEB-INF/spring/appServlet/servlet-context.xml" %}
```markup
<interceptors> 
    <interceptor> 
        <!-- 인터셉터가 적용될 URL 입니다. --> 
        <mapping path="/*.do" /> 
        <!-- 인터셉터가 제외될 URL 입니다. --> 
        <exclude-mapping path="/login.do"/> 
        <!-- 적용될 인터셉터를 지정합니다. --> 
        <beans:bean id="myInterceptor" class="com.bit.interceptor.MyInterceptor" /> 
    </interceptor> 
</interceptors>
```
{% endcode-tabs-item %}
{% endcode-tabs %}









### AOP

{% code-tabs %}
{% code-tabs-item title="POM.xml" %}
```markup
...
<!-- user add libs -->
<dependency> 
    <groupId>org.aspectj</groupId> 
    <artifactId>aspectjweaver</artifactId> 
    <version>${org.aspectj-version}</version> 
</dependency>
...
```
{% endcode-tabs-item %}
{% endcode-tabs %}



#### **AOP 용어**

* target : 부가 기능을 부여할 대상
* advice : target에 제공할 부가 기능을 담은 클래스, Indicate the action to take either before or after the method execution.
* joinpoint : advice가 적용될 수 있는 위치. 예를 들어 method의 실행 단계
* pointcut : advice가 적용될 target을 지정하는 것을 의미, Indicate which method should be intercept, by method name or regular expression pattern.
* Advisor – Group ‘Advice’ and ‘Pointcut’ into a single unit, and pass it to a proxy factory object.



### Common AspectJ annotations :

1. **@Before** – Run before the method execution
2. **@After** – Run after the method returned a result
3. **@AfterReturning** – Run after the method returned a result, intercept the returned result as well.
4. **@AfterThrowing** – Run after the method throws an exception
5. **@Around** – Run around the method execution, combine all three advices above.



### Transaction 

{% tabs %}
{% tab title="방법" %}
클래스, 메서드위에 **@Transactional** 이 추가되면, 이 클래스에 트랜잭션 기능이 적용된 프록시 객체가 생성된다.

이 프록시 객체는 **@Transactional**이 포함된 메소드가 호출 될 경우, **PlatformTransactionManager**를 사용하여 트랜잭션을 시작하고, 정상 여부에 따라 Commit 또는 Rollback 한다.
{% endtab %}

{% tab title="속성" %}
* **원자성\(Atomicity\)**  - 한 트랜잭션 내에서 실행한 작업들은 하나로 간주한다. 즉, 모두 성공 또는 모두 실패.
* **일관성\(Consistency\)** - 트랜잭션은 일관성 있는 데이타베이스 상태를 유지한다. \(data integrity 만족 등.\)
* **격리성\(Isolation\)** - 동시에 실행되는 트랜잭션들이 서로 영향을 미치지 않도록 격리해야한다.
* **지속성\(Durability\)** - 트랜잭션을 성공적으로 마치면 결과가 항상 저장되어야 한다.
{% endtab %}

{% tab title="설정" %}
```markup
<bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
     <property name="dataSource" ref="dataSource" />
</bean>
<tx:annotation-driven transaction-manager="transactionManager" proxy-target-class="true" />
```



```java
@EnableTransactionManagement
public class AppConfig {
    ...
    @Bean
    public PlatformTransactionManager transactionManager() throws URISyntaxException, GeneralSecurityException, ParseException, IOException {
        return new DataSourceTransactionManager(dataSource());
    }

```
{% endtab %}
{% endtabs %}







### SECURITY



**스프링에서 제공하는 기본 권한\(Authority\)**

| AUTHORITI | DESCRIPTION |
| :--- | :--- |
| ROLE\_ANONYMOUS | 모든 사용자 |
| IS\_AUTHENTICATED\_ANONYMOUSLY | 익명 사용자 |
| IS\_AUTHENTICATED\_FULLY | 인증된 사용자 |
| IS\_AUTHENTICATED\_REMEMBERED | REMEMBERED 사용자 |
| ROLE\_RESTRICTED | 제한된 사용자 |
| ROLE\_USER | 일반 사용자 |
| ROLE\_ADMIN | 관리자 |

\[[권한관리](http://www.egovframe.go.kr/wiki/doku.php?id=egovframework:%EA%B6%8C%ED%95%9C%EA%B4%80%EB%A6%AC)\]



#### 필터설정

{% code-tabs %}
{% code-tabs-item title="web.xml" %}
```markup
<context-param>
	<param-name>contextConfigLocation</param-name>
	<param-value>
	/WEB-INF/spring/root-context.xml
	classpath:/applicationContext.xml
	</param-value>
</context-param>

...

<filter>
	<filter-name>springSecurityFilterChain</filter-name>
	<filter-class>org.springframework.web.filter.DelegatingFilterProxy</filter-class>
	<init-param>
		<param-name>targetBeanName</param-name>
		<param-value>springSecurityFilterChain</param-value>
	</init-param>
</filter>
<filter-mapping>
	<filter-name>springSecurityFilterChain</filter-name>
	<url-pattern>/*</url-pattern>
</filter-mapping>
```
{% endcode-tabs-item %}
{% endcode-tabs %}



{% code-tabs %}
{% code-tabs-item title="root-context.xml" %}
```markup
<!-- 권한없음 : implements AccessDeniedHandler -->
<bean id="accessDeniedHandler" class="com.bit.secure01.MyAccessDeniedHandler"></bean>

<security:http auto-config="true">
	<security:intercept-url pattern="/" access="IS_AUTHENTICATED_ANONYMOUSLY"/>
	<security:intercept-url pattern="/login" access="IS_AUTHENTICATED_ANONYMOUSLY"/>
	<security:intercept-url pattern="/user" access="ROLE_USER"/>
	<security:intercept-url pattern="/admin" access="ROLE_ADMIN"/>
	<!-- 권한없음 -->
	<security:access-denied-handler  ref="accessDeniedHandler"/>
	<!-- 사용자정의 로그인 페이지 -->
	<security:form-login login-page="/login"/>
	<!-- 사용자정의 로그아웃 주소, 세션 갱신 여부 -->
	<security:logout logout-url="/logout" invalidate-session="false"/>
</security:http>

<security:authentication-manager>
	<security:authentication-provider>
		<security:user-service>
			<security:user name="test01" password="1234" authorities="ROLE_USER"/>
			<security:user name="admin" password="1234" authorities="ROLE_ADMIN,ROLE_USER"/>
		</security:user-service>
	</security:authentication-provider>
</security:authentication-manager>
```
{% endcode-tabs-item %}
{% endcode-tabs %}



Default path

* login : j\_spring\_security\_login
* logout : j\_spring\_security\_logout

{% code-tabs %}
{% code-tabs-item title="login.jsp" %}
```markup
<form name='f' action='/secure01/j_spring_security_check' method='POST'>
    id:<input type="text" name='j_username' /><br/>
    pw:<input type='password' name='j_password' /><br/>
    <button>로그인</button>
</form>

<!-- link : 로그인/로그아웃 -->
<c:if test="${pageContext.request.userPrincipal eq null }">
    <a href="${pageContext.request.contextPath }/j_spring_security_login">[login]</a>
</c:if>

<c:if test="${pageContext.request.userPrincipal ne null}">
    <a href="${pageContext.request.contextPath }/j_spring_security_logout">[logout]</a>
</c:if>
```
{% endcode-tabs-item %}
{% endcode-tabs %}





### @PathVariable의 확장자포함

```java
// /down/img.jpg
@RequestMapping("/down/{filename:.+}")
```



### ViewResolver - extends AbstractView

{% code-tabs %}
{% code-tabs-item title="DownView.java" %}
```java
@Component("downView")
public class DownView extends AbstractView{

	@Override
	protected void renderMergedOutputModel(Map<String, Object> model
			, HttpServletRequest req, HttpServletResponse res)
			throws Exception {
		String fileName=(String) model.get("fileName");
	
		RandomAccessFile randomFile = new RandomAccessFile(new File("C:\\upload", fileName), "r");
		long movieSize = randomFile.length(); 
		res.setContentType("image/*");
//		res.setContentType("video/*");
//		res.setContentType("video/mp4");
		res.setHeader("Content-Range", "bytes "+movieSize);
        res.setHeader("Accept-Ranges", "bytes");
        OutputStream out = res.getOutputStream();
        randomFile.seek(0);
        int bufferSize = 8*1024;
        byte[] buf = new byte[bufferSize];
        int s=0;
        try{
	        while((s=randomFile.read(buf)) > 0){
	            out.write(buf, 0, s);
			}
        }finally {
			out.close();
		}
        
	}

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="Controller.java" %}
```java
    @Resource(name="downView")
    private View downView;
    
public ModelAndView down(String filename){    
    ModelAndView mav=new ModelAndView();
		mav.setView(downView);
		mav.addObject("fileName", filename);
		return mav;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}











