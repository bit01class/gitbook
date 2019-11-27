# MVC2



### FrontController 패턴

[http://codedragon.tistory.com/4743](http://codedragon.tistory.com/4743?category=196761)

###  

### Command 패턴

\*\*\*\*[**http://codedragon.tistory.com/4744**](http://codedragon.tistory.com/4744)\*\*\*\*









### Maven

* [Getting Started in 5 Minutes](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html)
* [Getting Started in 30 Minutes](https://maven.apache.org/guides/getting-started/index.html)

### Jetty Plugin

```text
    <plugins>
        <plugin>
            <groupId>org.eclipse.jetty</groupId>
            <artifactId>jetty-maven-plugin</artifactId>
            <version>9.4.7.v20170914</version>
            <configuration>
                <webApp>
                    <contextPath>/${build.finalName}</contextPath>
                </webApp>
                <stopKey>CTRL+C</stopKey>
                <stopPort>8999</stopPort>
                <scanIntervalSeconds>10</scanIntervalSeconds>
                <scanTargets>
                    <scanTarget>src/main/webapp/WEB-INF/web.xml</scanTarget>
                </scanTargets>
            </configuration>
        </plugin>
    </plugins>
```





### Servlet Filter



{% code title="MyFilter.java" %}
```java
import javax.servlet.Filter; 
import javax.servlet.FilterChain; 
import javax.servlet.FilterConfig; 
import javax.servlet.ServletException; 
import javax.servlet.ServletRequest; 
import javax.servlet.ServletResponse; 
import javax.servlet.http.HttpServletRequest; 
import javax.servlet.http.HttpServletRequestWrapper; 
import javax.servlet.http.HttpServletResponse; 
import javax.servlet.http.HttpServletResponseWrapper; 
import org.slf4j.Logger; 
import org.slf4j.LoggerFactory; 

public class MyFilter implements Filter { 
    private static final Logger logger = LoggerFactory.getLogger(MyFilter.class); 
    private String encoding; 
    
    @Override 
    public void init(FilterConfig config) throws ServletException { 
     logger.info("init call");
    } 
    /* 필터 실행 부분 */ 
    @Override 
    public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain) throws IOException, ServletException {
     
     logger.info("before doFilter"); 
     chain.doFilter(request, response);
     logger.info("after doFilter"); 
    } 
     /* 컨텍스트가 종료될 때 호출  */ 
    @Override 
    public void destroy() {
     logger.info("destroy call"); 
    }
```
{% endcode %}



{% code title="web.xml" %}
```markup
<filter> 
<filter-name>myFilter</filter-name> 
<filter-class>com.bit.filter.MyFilter</filter-class> 
<init-param> 
<param-name>encoding</param-name> 
<param-value>UTF-8</param-value> 
</init-param> 
</filter> 
<filter-mapping>
    <filter-name>myFilter</filter-name>
    <url-pattern>/*</url-pattern>
    <dispatcher>REQUEST</dispatcher>
</filter-mapping>
<!--
- REQUEST : 클라이언트로부터의 직접 요청시 적용(기본값)
- FORWARD : 포워드 되는 컴포넌트(페이지) 에 적용
- INCLUDE : 인클루드 되는 컴포넌트(페이지) 에 적용
- ERROR : 에러페이지에 적용(isErrorPage="true")
-->
```
{% endcode %}





















