# STRUTS2

## Action result

* SUCCESS\("success"\) : Action이 설동적으로 실행
* NONE\("none"\) : Action은 성공이지만 화면을 보여줄 필요가 없는 경우
* ERROR\("error"\) : Action 실행 중 에러 발생
* INPUT\("input"\) : 입력값에 문제가 있어 입력화면으로 되돌림
* LOGIN\("login"\) : 로그인을 하지 않아 Action 실행 불가. 로그인 화면으로 돌아간다.

## struts.properties

```text
struts.devMode=false
struts.locale=en_US
struts.i18n.encoding=UTF-8 
struts.url.http.port=8080 
struts.action.extension=do,bit
```

## Intercept

```text
class MyIntercept extends com.opensymphony.xwork2.interceptor.PrepareInterceptor {

    @Override
    public String intercept(ActionInvocation invocation) throws Exception {
        System.out.println("MyIntercept 실행 전");
        String result = invocation.invoke();
        System.out.println("MyIntercept 실행 후");
        return result;
    }
}
```

```text
<interceptor-ref name="timer"/>
<interceptor-ref name="logger"/>

<interceptor-ref name="params"/>

<interceptor-ref name="validation"/>
    - 만약 액션이 Validateable을 구현했다면 액션의 validate() 메서드를 호출한다.
    - 만약 액션이 ValidationAware를 구현했다면 액션의 hasError() 메서드를 호출한다.
<interceptor-ref name="workflow"/>

<interceptor-ref name="prepare"/> : 액션의 실행 이전에 다른 로직을 삽입하고 싶을 때 유용. 
액션은 Preparable을 구현해야 하고 인터셉터는 액션을 실행하기 이전에 prepare() 메서드를 호출 한다


<interceptor-ref name="servletConfig"/> : Struts2의 액션은 Servlet API를 사용하지 않는다. 하지만 HttpServletRequest, HttpServletResponse는 자주 사용되는 Servlet API 들이다. 따라서 액션에서 이런 Servlet API를 사용할 필요가 있는 경우 이 인터셉터에서 액션으로 Servlet API를 넘겨 준다. 단, 넘겨받는 액션은 ServletRequestAware나 ServletResponseAware같은 인터페이스를 구현
```

