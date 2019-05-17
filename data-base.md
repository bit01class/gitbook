# DATA BASE



### Oracle port번호 변경

```sql
sqlplus '/ as sysdba'
exec dbms_xdb.sethttpport(0);
commit;

```



### mariaDB 설치\(Windows\)

■ [https://downloads.mariadb.org/](https://downloads.mariadb.org/)에서 최신 mariaDB를 다운로드 받는다. 현재 최신 버전은 10.1.11이다. window7 64bit 컴퓨터에 설치할 것이므로 패키징 파일 중에서 [mariadb-10.1.11-winx64.zip](https://downloads.mariadb.org/interstitial/mariadb-10.1.11/winx64-packages/mariadb-10.1.11-winx64.zip/from/http%3A//ftp.kaist.ac.kr/mariadb/)파일을 다운로드 받는다. 파일을 클릭하면  이름과 이메일 등의 정보를 입력하는 창이 나타나는데 입력하면 파일이 다운로드 된다.[![mariaDB window7 zip&#xBC84;&#xC804; &#xC124;&#xCE58; 00](http://blog.iotinfra.net/wp-content/uploads/2016/02/mariaDB-window7-zip%EB%B2%84%EC%A0%84-%EC%84%A4%EC%B9%98-00.png)](http://blog.iotinfra.net/wp-content/uploads/2016/02/mariaDB-window7-zip%EB%B2%84%EC%A0%84-%EC%84%A4%EC%B9%98-00.png)[![mariaDB window7 zip&#xBC84;&#xC804; &#xC124;&#xCE58; 01](http://blog.iotinfra.net/wp-content/uploads/2016/02/mariaDB-window7-zip%EB%B2%84%EC%A0%84-%EC%84%A4%EC%B9%98-01.png)](http://blog.iotinfra.net/wp-content/uploads/2016/02/mariaDB-window7-zip%EB%B2%84%EC%A0%84-%EC%84%A4%EC%B9%98-01.png)

[![mariaDB window7 zip&#xBC84;&#xC804; &#xC124;&#xCE58; 02](http://blog.iotinfra.net/wp-content/uploads/2016/02/mariaDB-window7-zip%EB%B2%84%EC%A0%84-%EC%84%A4%EC%B9%98-02.png)](http://blog.iotinfra.net/wp-content/uploads/2016/02/mariaDB-window7-zip%EB%B2%84%EC%A0%84-%EC%84%A4%EC%B9%98-02.png)

■ 다운로드받은 mariadb-10.1.11-winx64.zip파일의 압축을 풀고 mariadb-10.1.11-winx64 폴더를 mariaDB를 실행하고자 하는 폴더로 이동한다. 지금은 C:\mariaDB\mariadb-10.1.11-winx64 폴더로 이동시켰다. 그리고 DOS창을 열고 bin디렉토리로 가서 mysql\_install\_db 명령어를 실행한다. **DOS 창을 열때 아래와 같이 관리자 권한으로 실행해야 하는데 만약 그렇지 않으면 FATAL ERROR: OpenSCManager failed \(5\) 에러가 발생하고 윈도우 서비스에 mariaDB가 등록되지 않는다.**   
[![mariaDB window7 zip&#xBC84;&#xC804; &#xC124;&#xCE58; 03](http://blog.iotinfra.net/wp-content/uploads/2016/02/mariaDB-window7-zip%EB%B2%84%EC%A0%84-%EC%84%A4%EC%B9%98-03.png)](http://blog.iotinfra.net/wp-content/uploads/2016/02/mariaDB-window7-zip%EB%B2%84%EC%A0%84-%EC%84%A4%EC%B9%98-03.png)

■ 아래와 같이 mysql\_install\_db명령어를 실행하는데, 옵션으로 데이터베이스 파일은 ‘C:\mariaDB\data’폴더에 생성하고 윈도우 서비스명은 ‘mariaDBZip’, 포트는 ‘5306’, 패스워드는 ‘xxxx’으로 정했다.

**&gt;mysql\_install\_db --datadir=C:\mariaDB\data --service=mariaDBZip --port=5306 --password=mysql**

[![mariaDB window7 zip&#xBC84;&#xC804; &#xC124;&#xCE58; 05](http://blog.iotinfra.net/wp-content/uploads/2016/02/mariaDB-window7-zip%EB%B2%84%EC%A0%84-%EC%84%A4%EC%B9%98-05.png)](http://blog.iotinfra.net/wp-content/uploads/2016/02/mariaDB-window7-zip%EB%B2%84%EC%A0%84-%EC%84%A4%EC%B9%98-05.png)

■ mysql\_install\_db 명령어를 실행 후 윈도우 서비스를 열면 서비스명이 mariaDBZip인 서비스가 등록된 것을 확인할 수 있다. 상단 시작 화살표를 클릭해서 mariaDB를 실행한다.  
[![mariaDB window7 zip&#xBC84;&#xC804; &#xC124;&#xCE58; 04](http://blog.iotinfra.net/wp-content/uploads/2016/02/mariaDB-window7-zip%EB%B2%84%EC%A0%84-%EC%84%A4%EC%B9%98-04.png)](http://blog.iotinfra.net/wp-content/uploads/2016/02/mariaDB-window7-zip%EB%B2%84%EC%A0%84-%EC%84%A4%EC%B9%98-04.png)

■ DOS창을 열고 C:\mariaDB\mariadb-10.1.11-winx64\bin&gt;**mysql -u root -p –port=5306**명령어를 실행하고 패스워드를 입력하면 아래와 같이 mariaDB에 접속할 수 있다

[![mariaDB window7 zip&#xBC84;&#xC804; &#xC124;&#xCE58; 06](http://blog.iotinfra.net/wp-content/uploads/2016/02/mariaDB-window7-zip%EB%B2%84%EC%A0%84-%EC%84%A4%EC%B9%98-06.png)](http://blog.iotinfra.net/wp-content/uploads/2016/02/mariaDB-window7-zip%EB%B2%84%EC%A0%84-%EC%84%A4%EC%B9%98-06.png)[![mariaDB window7 zip&#xBC84;&#xC804; &#xC124;&#xCE58; 07](http://blog.iotinfra.net/wp-content/uploads/2016/02/mariaDB-window7-zip%EB%B2%84%EC%A0%84-%EC%84%A4%EC%B9%98-07.png)](http://blog.iotinfra.net/wp-content/uploads/2016/02/mariaDB-window7-zip%EB%B2%84%EC%A0%84-%EC%84%A4%EC%B9%98-07.png)

 **SQLyog 설치하기**

[https://code.google.com/archive/p/sqlyog/wikis/Downloads.wiki](https://code.google.com/archive/p/sqlyog/wikis/Downloads.wiki)



[mirinae.maru](http://blog.iotinfra.net/?author=1)[2016/02/15](http://blog.iotinfra.net/?p=1090)  [0 Comments](http://blog.iotinfra.net/?p=1090#respond)









###  인증\(Authentication\), 권한부여\(Authorization\), 접근제어\(Access Control\)

```text
-- Create the new database
mysql> create database db_example; 
---------------------------------------------
mysql> SHOW VARIABLES LIKE 'skip_name_resolve';
mysql> FLUSH PRIVILEGES;
mysql> SELECT `user`, `host`, `password` FROM `mysql`.`user`;
---------------------------------------------
-- Creates the user
mysql> CREATE USER 'user01'@'%' IDENTIFIED BY 'class01';
-- Gives all the privileges to the new user on the newly created database
-- mysql> grant all on db_example.* to 'springuser'@'%'; 
mysql> GRANT EXECUTE, PROCESS, SELECT, SHOW DATABASES, SHOW VIEW, ALTER, ALTER ROUTINE, CREATE, CREATE ROUTINE, CREATE TABLESPACE, CREATE TEMPORARY TABLES, CREATE VIEW, DELETE, DROP, EVENT, INDEX, INSERT, REFERENCES, TRIGGER, UPDATE, CREATE USER, FILE, LOCK TABLES, RELOAD, REPLICATION CLIENT, REPLICATION SLAVE, SHUTDOWN, SUPER  ON *.* TO 'user02'@'%' WITH GRANT OPTION;
mysql> FLUSH PRIVILEGES;
mysql> SHOW GRANTS FOR 'user01'@'%';

```







### Driver

* com.mysql.jdbc.Driver
* | `jdbc:mysql://[host][,failoverhost...][:port]/[database][?propertyName1][=propertyValue1][&propertyName2][=propertyValue2]...` |
  | :--- |

```text

jdbc:mysql://localhost:3306/lesstif?useUnicode=true&characterEncoding=utf8

-- jdbc:mysql://localhost:3306/lesstif?useUnicode=true&amp;characterEncoding=utf8


```



### MySQL

```sql
-- sequence
idx int primary key auto_increment

-- nextval , currval
insert table tablename(sub,lvl) 
    select 'NOsubject',max(index)+1
    from tablename;
```











### PL/SQL\(Procedural Language/SQL\)

: 오라클에서 제공하는 프로그래밍 언어 : 일반 프로그래밍 언어적인 요소를 다 가지고 있고, 데이터베이스 업무를 처리하기 위한 최적화된 언어

 **\[ 프로시저\(PL\)의 기본 구조 \]** 

* 선언부\(Declare\) : 모든 변수나 상수를 선언하는 부분
* 실행부\(Executable\) : BEGIN ~ END // 실재 로직이 수행되는 부분 

     ex\) 제어문, 반복문, 함수정의 등의 로직을 기술하는 부분...

* 예외처리부\(Exception\) : 실행도중에 에러 발생시 해결하기위한 명령들을 기술하는 부분 \(생략가능\)

   **Declare, begin, exception 키워드들은 ';' 을 붙이지 않는다.**  \*\* 나머지 문장들은 ';'으로 처리하여 영역의 긑을 표시한다.

* 익명 블록\(Anonymous PL/SQL\) : 주로 일회성으로 사용할 경우 많이 사용된다.
* 저장 블록\(Stored PL/SQL\) : 서버에 저장해 놓고 주기적으로 반복해서 사용할 경우 사용된다. \*/ -- EX\)

set SERVEROUTPUT OFF; set SERVEROUTPUT ON; -- dbms\_output.put\_line메서드를 이용해 출력을 가능케해주는 세팅

-- 익명 블럭\(Anonymous PL/SQL\) EX DECLARE --선언부 cnt integer; BEGIN --실행부 cnt := cnt+1; / _할당 '=' 이 아니라 ':='_ / -- null과 연산하면 결과는 null if cnt is null then dbms\_output.put\_line\('결과 : cnt는 NULL입니다.'\); -- 괄호 안 내용을 화면에 출력하는 메서드 end if; END;

/ -- 작성한 프로시저 실행

/\* PL/SQL 문장 안에 SQL 문장이 포함될 수 있는데 이 SQL 문장은 SQL 실행자에 의해 실행된다. PL/SQL 문장은 프로시저 실행자가 처리-&gt;\(PL/SQL엔진\)이 수행한다.

SQL실행자가 SQL문을 실행해 프로시저 실행자에게 넘겨준다.\(돌려준다\) 그러면 그걸 PL/SQL엔진이 처리하게 된다. \*/

DECLARE empNo number\(20\); empName varchar2\(10\); BEGIN select employee\_id, first\_name into empNo, empName -- empNo와 empName에 각 결과 필드값을 넣겠단 의미\(into\) from Employees where employee\_id = 124;

DBMS\_OUTPUT.put\_line\(empNo\|\|' '\|\|empName\); -- 각 변수 값을 화면에 출력 END;

/

### 변수

/\* \[ PL/SQL 변수 \]

* 변수의 생성 규칙 1. 반드시 문자로 시작해야 한다. 2. 문자나, 숫자, 특수문자를 포함할 수 있다. 3. 변수명은 30Byte 이하여야 한다. 4. 예약어\(키워드\)를 사용하면 안된다.
* 변수의 선언은 선언부\(Delcare 블럭\)에서 선언되어야 하고, 값으로 초기화가 가능하다.
* 실행부\(Begin~End\)에서 실행될 경우 값이 할당 된다.
* 서브프로그램의 파라미터로 전달되기도 하며, 서브프로그램의 출력 결과를 저장하기도 한다.
* 선언의 예&gt; emp\_no number\(6,3\) : 숫자를 저장하는 변수로 총 6자리며 소수점 밑 3자리

  emp\_name varchar2\(10\) : 문자를 저장하는 변수로 총 10Byte 저장가능 변수

  emp\_date date : 날자를 저장하는 변수

* 데이터 타입&gt;

  * char : 고정길이 문자 타입, 기본최소값 1, 최대 32,767Byte를 저장 가능
  * varchar2 : 가변길이 문자 타입, 기본값은 없다. 

    ```text
           최대 32,767Byte 저장 가능.
    ```

  * number\(전체자리수,소수점이하 자리수\) : 숫자를 저장 

    ```text
                                   전체자리수 범위는 1~38까지 가능하고,
                                   소수점 자리수 범위는 -84~127까지 가능                                     
    ```

  * binary\_double : 부동 소수점 수를 저장하는 타입, 9Byte 필요
  * date : 날짜 및 시간을 나타내는 타입, 초단위로 저장,

    ```text
       날짜의 범위는 4712B.C ~ 9999 A.D
    ```

  * timestamp : date 타입을 확장, 연도, 월, 일, 시, 분, 초 및 소수로

    ```text
            표시되는 초단위를 저장.
    ```

   **참조 변수**  테이블명.필드명%Type

  empNo employees.employee\_id%TYPE // 현재 employees테이블의 employee\_id의 타입을 그대로 가져오겟다. : employees 테이블의 employee\_id와 동일한 데이터 타입으로 선언한다는 의미.

  emp\_name employees.frst\_name%TYPE : employees 테이블의 first\_name과 동일한 데이터 타입으로 선언

  empRow employees%ROWTYPE : employees 테이블의 모든 컬럼을 한꺼번에 저장하기 위한 변수로 선언 \*/

-- EX\) create table employees1 as select employee\_id, salary, department\_id from employees;

set serveroutput on;

DECLARE empNo employees.employee\_id%TYPE; empSalary employees.salary%TYPE; BEGIN select employee\_id, salary into empNo, empSalary from employees1 where department\_id = 10;

DBMS\_OUTPUT.put\_line\(empNo\|\|' '\|\|empSalary\); END; /

DECLARE emp\_row employees1%ROWTYPE; -- employees1 테이블의 모든 컬럼 타입을 의미함 BEGIN select \* into emp\_row from employees1 where employee\_id = 100;

DBMS\_OUTPUT.put\_line\(emp\_row.employee\_id\|\|' '\|\|emp\_row.salary\|\|' '\|\|emp\_row.department\_id\); END; /

create table row\_test\( no number, name varchar2\(20\), hdate date \);

create table row\_test2 as select \* from row\_test;

insert into row\_test values\(1,'아무개',sysdate\); insert into row\_test values\(2,'홍길동',sysdate\); insert into row\_test values\(3,'고길동',sysdate\);

select \* from row\_test;

commit;

DECLARE c\_rec row\_test%ROWTYPE; BEGIN select \* into c\_rec from row\_test where no = 3;

insert into row\_test2 values c\_rec; END; /

select \* from row\_test2;

### rowType 변수

--\[ rowType 변수 및 복합변수 활용의 예 \] -- : rowType 변수를 활용한 데이터의 변경

DECLARE c\_rec row\_test%ROWTYPE; BEGIN select \* into c\_rec from row\_test where no = 3;

-- 대입연산자는 := 를 사용해야 한다.\(주의!\)  
c\_rec.name := '강길동';

-- row\(행 전체\)를 c\_rec로 바꾸는 방법 update row\_test2 set row = c\_rec where no = 3;

END; /

select \* from row\_test2;

-- 사용자로 부터 두개의 숫자를 입력받아서 합을 구하는 예 -- 치환연산자 & 사용\)

set SERVEROUTPUT ON;

declare no1 number := &no1; -- 사용자로부터 입력을 받아 값을 할당 no2 number := &no2; sumV number; begin sumV := no1 + no2; DBMS\_OUTPUT.put\_line\('첫번째 수'\|\|no1\|\|'두번째 수'\|\|no2\|\|'합'\|\|sumV\); end; /

-- 복합변수 \) -- 직접 복합 타입을 지정할 수도 있다. -- record Type 변수 지정 방법 --1. type 타입명 is record\(\); --2. 식별자 타입명

declare type emp\_rec is record \(emp\_id employees.employee\_id%type, emp\_name employees.first\_name%type, emp\_job employees.job\_id%type \);

```text
rec1 emp_rec; -- 위에서 정의한 타입을 사용해 변수 선언
```

begin select employee\_id, first\_name, job\_id into rec1 from employees where department\_id = 10;

```text
DBMS_OUTPUT.put_line('사번    이름    업무ID');
DBMS_OUTPUT.PUT_LINE(rec1.emp_id||'   '||rec1.emp_name||'   '||rec1.emp_job);
```

end; /

declare type emp\_rec2 is record \( emp\_id employees.employee\_id%type, emp\_name employees.last\_name%type, emp\_email employees.email%type, emp\_salary employees.salary%type \);

rec2 emp\_rec2; -- 사원번호는 사용자로부터 입력받도록 vemp\_id employees.employee\_id%type := '&사번'; begin select employee\_id, last\_name, NVL\(email,'없음'\), salary into rec2 from employees where employee\_id = vemp\_id; -- 사원번호가 사용자로부터 입력받은 것과 같은 정보

DBMS\_OUTPUT.put\_line\('사번:'\|\|rec2.emp\_id\);

DBMS\_OUTPUT.put\_line\('이름:'\|\|rec2.emp\_name\);

DBMS\_OUTPUT.put\_line\('이메일;'\|\|rec2.emp\_email\);

DBMS\_OUTPUT.put\_line\('월급:'\|\|rec2.emp\_salary\); end; /

-- 지금까지 공부한 PL/SQL 부분 연습하기 -- declare -- 1.일반 변수 선언법 no number\(10\); strValue varchar2\(20\); -- 2.기존 테이블의 특정 필드의 타입으로 선언하는 방법 emp\_id employees.employee\_id%TYPE; emp\_name employees.first\_name%TYPE; -- employees테이블의 first\_name 필드와 같은 타입으로 선언 -- 3.특정 기존 테이블과 동일한 복합 타입으로 지정하는 방법 emp\_rec employees%ROWTYPE; dep\_rec departments%ROWTYPE; -- 4.사용자에게 입력을 받아 선언한 변수에 데이터를 넣는 방법 input\_data row\_test.no%TYPE := '&no번호'; -- 5.사용자 지정 복합 타입으로 변수를 선언하는 방법 type myType is record \( my\_no row\_test.no%TYPE, my\_name row\_test.name%type, my\_hdate row\_test.hdate%type \); myDefVal myType; begin select no, name, hdate into myDefVal from row\_test where no = 3;

myDefVal.my\_name := '수정합니다.'; update row\_test set row = myDefVal where no = input\_data; -- 사용자가 입력한 no번호에 해당하는 필드 값을 수정하도록...

end; / select \* from row\_test;

### 배열,컬렉션,바인드변수

/\* \[ Table Type 변수\(=컬렉션\) \] 컬렉션 : 일반 프로그래밍 언어에서 사용하는 배열 타입을 pl/SQL에서는 "컬렉션"이라 한다.

* 종류 1. 연관배열\(associative array or index-by table\) : \(KEY, VALUE\) 쌍으로 저장되는 배열 - 키값을 통해 값에 접근한다.

  ```text
    . key의 데이터 유형 - 숫자 : binary_integer, pls_integer
                              위 두가지 데이터 타입은 number보다
                              작은 저장 영역이 필요, 산술연산의 경우
                              number보다 빠르다.
                      - 문자 : varchar2
    . 값(value) 유형  - 일반 데이터 타입, 레코드 데이터 타입도 값이 될 수 있다.
                        -> 레코드 타입일 경우 여러개의 값을 가질 수 있다.
  ```

  1. varry\(variable array\) 

        : 고정 길이를 가진 배열\(일반 프로그래밍에서 사용하는 배열과 동일\)

        : 인덱스가 "0"부터 시작한다.

     ```text
        ex) 3번째 v[3]
     ```

  2. 중첩테이블\(nested table\)

        : varry와 흡사한 구조의 배열

        : \(배열의 크기를 명시하지 않음\)배열의 최대값이 정해지지 않고 동적으로 자동으로 최대값이 증가됨

* \[ Table Type\(컬렉션\)의 선언 형식 \]
  1. 정의

     TYPE 타입명 IS TABLE OF

     employees.first\_name%type

     INDEX BY BINARY\_INTEGER -- binary integer로 인덱스를 사용한단 의미

  2. 선언\(메모리 공간이 잡히는 부분\)

     식별자 타입명;

     \*/

```sql
set SERVEROUTPUT ON;

declare
  tname varchar2(20);
  
  -- 정의
  TYPE t_emp_name IS TABLE OF
  employees.last_name%type
  INDEX BY BINARY_INTEGER;
  
  -- 선언
  v_name t_emp_name;
begin
  select last_name into tname
  from employees
  where employee_id = 100;
  
  -- 인덱스를 통해 접근
  v_name(0) := tname;
  DBMS_OUTPUT.PUT_LINE(v_name(0));
end;
/

```

```sql
declare
  TYPE tbl_type IS TABLE OF
    employees.last_name%type
  INDEX BY BINARY_INTEGER;
  
  vtbl_type tbl_type;
  a binary_integer := 0; -- 변수 a값을 0으로 초기화
begin
  for emp_name in(select last_name from employees) loop
    a := a+1;
    vtbl_type(a) := emp_name.last_name; 
  end loop;
  
  for i in 1..a loop
    DBMS_OUTPUT.PUT_LINE(vtbl_type(i));
  end loop;
end;
/
```



\[ 바인드 변수\(비 PL/SQL 변수\) \] 

:호스트 환경에서 생성되어 데이터를 저장하기 때문에 호스트 변수라고 한다.

쿼리의 일부분 예를 들어 WHERE 절의 내용만 다른 쿼리를 실행해야 하는 경우가 종종 생길 것이다. 이러한 경우에 거의 비슷한 두번의 쿼리를 실행하는 비효율성을 해소하는 방법이 바로 바인드 변수의 사용이다. 바인드 변수는 입력 내용을 넣고 SQL로부터 출력 내용을 받아내는 방법으로, " 이 부분에 들어갈 정확한 값은 이후에 알려줄테니, 일단 내가 값을 넣었을 때 어떻게 실행할 것인지에 대해서 계획만 세워둬라 "는 명령을 오라클에 내리는 것이다.

select \* into temp from row\_test where no = :bind\_no; 이 부분이 있을 때 :가 붙은 변수가 바인드 변수인대, 실행한 뒤에 바인드 변수에 입력할 값을 넣게 된다. 그에 따라 no = 1, no = 2 등 실행할 때마다 다양한 결과를 낼 수가 있게 된다.

* 키워드 VARIABLE를 이용하며, SQL문이나 PL/SQL블록에서도 사용가능
* PL/SQL블록이 실행된 후에도 액세스가 가능하다.
* print명령을 이용하여 출력가능
* :을 붙여 이용한다.

```sql
set autoprint on; -- print를 하지 않아도 자동으로 출력하도록 세팅하는 부분(default는 false로 되어있음)

declare
  temp row_test%ROWTYPE;
begin
  select * into temp from row_test where no = :bind_no;
  insert into row_test3 values temp;
end;

select * from row_test3;

-- no에 1을 입력시 그에 해당되는 결과가 2를 입력하면 그에 해당하는 결과가 나오게 된다.


begin
  select (salary*12+nvl(commission_pct,0)) into :vsal -- 결과값을 바인드 변수에 넣는다.
  from employees
  where employee_id = 100;
end;
/
-- print를 이용해서 PL/SQL블럭 밖에서도 출력할 수 있다.
print vsal;


create table row_test3 as select * from row_test;
truncate table row_test3;
select * from row_test3;

declare
  type arrRecType IS TABLE OF
  row_test%ROWTYPE
  INDEX BY binary_integer;
  
  TestValue arrRecType;
  a binary_integer := 0;
begin
  for temp_rec in (select * from row_test) loop
    a := a+1;
    TestValue(a) := temp_rec;
  end loop;
  
  for i in 1..a loop
    insert into row_test3 values TestValue(i);
  end loop;
end;
/
select * from row_test3;
```







### 조건문

/\* \[ 제어문 \] : 조건문, 반복문

* 조건문 : if문, case문\(switch문과 유사\)
* 반복문 : basic loop문, while문\(반복횟수를 정하지 않을 경우\) : for문\(반복횟수 지정할 경우\)

  // if문 : if ~ end if EX\) if\(조건\) then 실행명령; elsif\(조건\) then 실행명령; else 실행명령; end if;

  // case문 EX\) case 변수명 when 값1 then 실행명령; when 값2 then 실행명령; ... end; \*/

```sql
set serveroutput on;

-- if문 Ex)
declare
  emp_id employees.employee_id%type;
  emp_name employees.last_name%type;
  emp_dept employees.department_id%type;
  dept_name varchar2(20) := null;
begin
  select employee_id, last_name, department_id
  into emp_id,emp_name,emp_dept
  from employees
  where employee_id = 124;
  
  if(emp_dept = 50) then --if문 시작
    dept_name := 'Shipping';
  end if;
  if(emp_dept = 60) then
    dept_name := 'IT';
  end if;
  if(emp_dept = 70) then 
    dept_name := 'Public Relation';
  end if;
  
  DBMS_OUTPUT.PUT_LINE(emp_id||' '||emp_name||' '||emp_dept||' '||dept_name);
end;
/


declare
  emp_id employees.employee_id%type;
  emp_name employees.last_name%type;
  emp_dept employees.department_id%type;
  dept_name varchar2(20) := null;
begin
  select employee_id, last_name, department_id
  into emp_id,emp_name,emp_dept
  from employees
  where employee_id = 103;
  
  if(emp_dept = 50) then 
      dept_name := 'Shipping';
    elsif(emp_dept = 60) then -- elseif가 아니라 elsif임을 주의...
      dept_name := 'IT';
    elsif(emp_dept = 70) then
      dept_name := 'Public Relation';
    ELSE 
      dept_name := 'Other';
  end if;
  DBMS_OUTPUT.PUT_LINE(emp_id||' '||emp_name||' '||emp_dept||' '||dept_name);
end;
/


declare
  emp_id employees.employee_id%type;
  emp_name employees.last_name%type;
  emp_comm employees.commission_pct%type := null;
begin
  select employee_id, last_name, commission_pct
  into emp_id, emp_name, emp_comm
  from employees
  where employee_id = 130;
  
  if (emp_comm > 0) then
    dbms_output.put_line(emp_id||' 의 보너스는 '||emp_comm);
  else
    DBMS_OUTPUT.PUT_LINE(emp_id||'의 보너스는 없습니다.');
  end if;
end;
/


-- case문 EX)

declare
  emp_id employees.employee_id%type;
  emp_name employees.last_name%type;
  emp_dept employees.department_id%type;
  dept_name varchar2(20) := null;
begin
  select employee_id, last_name, department_id
  into emp_id, emp_name, emp_dept
  from employees
  where employee_id = &empno; --치환변수 이용해 사용자로부터 입력받음
  
  dept_name := case emp_dept
                 when 50 then 'Shipping'
                 when 60 then 'IT'
                 when 70 then 'Public Relation'
                 when 80 then 'Sales'
               end;
  DBMS_OUTPUT.PUT_LINE(dept_name);
end;
/
```





### 반복문

1. basic loop문
2. while문
3. for문

1. basic loop문\(조건을 나중에 검사\) : DO WHILE문과 유사 

-- 형식 

_`loop  
  pl/sql문장;   
  exit when(조건);   
end loop;`_ 

```text
-- 1~10까지 출력하기
declare
  num number := 1;
begin
  loop
    dbms_output.put_line(num);
    num := num + 1;
    exit when (num > 10);
  end loop;
end;
/
```

-- 2. while문\(조건을 먼저 검사\) 

_형식\)_ 

_`while 조건 loop 실행문장; end loop`_ `/ declare num number := 1;  
 begin while (num <= 10) loop DBMS_OUTPUT.PUT_LINE(num);  
 num := num + 1;  
 end loop;`   
__`end;` 

```text
declare
  num number := 10;
begin
  loop
    DBMS_OUTPUT.PUT_LINE(num);
    num := num - 1;
    exit when num = -1;
  end loop;
end;
/

declare
  num number := 10;
begin
  while (num >= 0) loop
    DBMS_OUTPUT.PUT_LINE(num);
    num := num - 1;
  end loop;
end;
/
```

-- 3. FOR문 : 반복횟수를 지정할 수 있다. /   
_형식\) java의 FOR EACH문과 유사! IN뒤에 나온 것이 순차적으로 i에 들어가는 개념 FOR i IN start..end loop 실행문장 end loop;_ / declare

begin FOR i IN 1..10 loop DBMS\_OUTPUT.PUT\_LINE\(i\); end loop; end; /

-- for문 역순 -- reverse를 붙여주자. begin FOR n IN reverse 0..10 loop DBMS\_OUTPUT.PUT\_LINE\(n\); end loop; end; /

/\*사원테이블에서 사원id를 입력받아서 사원이름의 문자길이만큼

```text
#을 찍는 PL/SQL문을 작성해보자.(employees테이블을 이용)
```

\*/ declare emp\_id employees.employee\_id%type := &emp\_no; -- 입력받음 emp\_name employees.last\_name%type; emp\_name\_length number\(20\); v\_char varchar2\(30\); begin select last\_name, length\(last\_name\) into emp\_name, emp\_name\_length from employees where employee\_id = emp\_id;

```text
for i in 1..emp_name_length loop
  v_char := v_char ||'#';
end loop;

DBMS_OUTPUT.PUT_LINE(v_char);
```

end; /

-- continue 보조제어문\(_11g부터 추가된 기능임_\) \] declare tot number := 0; begin for i in 1..10 loop tot := tot + 1; DBMS\_OUTPUT.put\_line\('tot : ' \|\| tot\); continue when i &gt; 5; -- 해당 조건을 만족하면 다음 차수로 바로 가게 된다. -- 아래를 수행하지 않고 다음번 차수로 넘어가게 됨. tot := tot + i; DBMS\_OUTPUT.PUT\_LINE\('tot2 :' \|\| tot\); end loop; end; /

### 커서

1. 암시적 커서
2. 명시적 커서



**암시적 커서의 속성**

* - SQL%ROWCOUNT : 해당 SQL 문에 영향을 받는 행의 수
* - SQL%FOUND : 해당 SQL 영향을 받는 행의 수가 한 개 이상일 경우 TRUE
* - SQL%NOTFOUND : 해당 SQL 문에 영향을 받는 행의 수가 없을 경우 TRUE
* - SQL%ISOPEN : 항상 FALSE, 암시적 커서가 열려 있는지의 여부 검색

```sql
CREATE OR REPLACE PROCEDURE Implicit_Cursor
        (p_empno IN emp.empno%TYPE)

    IS

        v_sal  emp.sal%TYPE;
        v_update_row NUMBER;

    BEGIN

        SELECT sal
        INTO v_sal
        FROM emp
        WHERE empno = p_empno;

        -- 검색된 데이터가 있을경우
        IF  SQL%FOUND THEN     
            DBMS_OUTPUT.PUT_LINE('검색한 데이터가 존재합니다 : '||v_sal);
        END IF;

        UPDATE emp
        SET sal = sal*1.1
        WHERE empno = p_empno;

        -- 수정한 데이터의 카운트를 변수에 저장
        v_update_row := SQL%ROWCOUNT;
        DBMS_OUTPUT.PUT_LINE('급여가 인상된 사원 수 : '|| v_update_row);
        
        EXCEPTION    
           WHEN   NO_DATA_FOUND  THEN  
           DBMS_OUTPUT.PUT_LINE(' 검색한 데이터가 없네요... ');
        
    END;
    /
 
-- DBMS_OUTPUT.PUT_LINE을 출력하기 위해 사용
SQL> SET SERVEROUTPUT ON ;  

-- 프로시저 실행
SQL> EXECUTE Implicit_Cursor(7369);

검색한 데이터가 존재합니다 : 880
급여가 인상된 사원 수 : 1
```



**명시적 커서**

커서의 내용을 미리 정의 해 놓고 사용하는 방법.

```sql
DECLARE
  CURSOR C_LIST IS
    SELECT MY_ID FROM MY_TABLE WHERE 조건;
BEGIN

  FOR I_ID IN C_LIST LOOP
    DBMS_OUTPUT.put_line(I_ID);
  END LOOP;
END;
```

_커서의 내용을 정할 때 select 문제 동적으로 parameter가 넘어가야 할 경우 사용이 불가능 하다. 왜냐하면 BEGIN 전에 정의하기 때문이다._

커서 변수를 미리 만들어 놓고 불러서 사용하는 방법. 

```sql
DECLARE
	I_ID   VARCHAR2(100);		-- 변수 정의				
  C_LIST SYS_REFCURSOR;		-- 커서 정의
BEGIN
  OPEN C_LIST FOR
  SELECT MY_ID   
    FROM MY_TABLE
    WHERE 조건;
  LOOP					-- LOOP 돌기.
      FETCH C_LIST
      INTO  I_ID;			--  하나씩 변수에 넣기.
      EXIT WHEN C_LIST%NOTFOUND;	-- 더이상 없으면 끝내기.
      DBMS_OUTPUT.put_line(I_ID);    --  출력
  END LOOP;
  CLOSE C_LIST;
END;
```

재사용성이 있어서 나름 괜찮음. 커서를 정의 한 뒤 그 때 그 때 커서의 내용을 채우는 방법이다.

### 예외

```text
종류
      1. 컴파일 에러 : PL/SQL 블럭이 파싱(Parsing)될 때 "사용자 오타" 등으로 인해 발생되는 에러.
        (Compile Error)
      2. 런타임 에러(=Exception)
          : PL/SQL 블럭이 실행되는 동안 발생하는 에러로 일반적으로 런타임에러를 "Exception"이라 부른다.
            종류)
              a. 오라클 예외 
                  : 오라클에서 제공되는 예외(Predefined ORACLE Exception과 Non-Predefined ORACLE Exception이 있다.)
                    ㄱ. Predefined ORACLE Exception 
                          : 사전에 정해진 예외
                          종류)
                            - ACCESS_INTO_NULL 
                                : 정의되지 않은 오브젝트 속성에 값을 할당하고자 했을 때 발생하는 예외.                      
                            - CASE_NOT_FOUND 
                                : CASE문의 when절에 해당되는 조건이 없고 else절도 없을 경우 발생
                            - COLLECTION_IS_NULL 
                                : 선언되지 않은 컬렉션(nested table, varray)에 존재하는 메서드
                                                   이외의 메서드를 사용했을 때 발생되는 예외.
                            - CURSOR_ALREADY_OPEN 
                                : 이미 열려진 커서를 열려고 시도 했을 때 발생하는 예외
                            - DUP_VAL_ON_INDEX 
                                : 유일인덱스에 중복값을 입력햇을 때 발생하는 예외.
                            - INVALID_CURSOR 
                                : 잘못된 커서 조작이 샐행될 때 발생되는 예외.
                            - INVALID_NUMBER 
                                : 문자를 숫자로의 변환 시 실패가 될 때 발생하는 예외.
                            - LOGIN_DENIED 
                                : 잘못된 사용자명이나 암호로 로그인시도시 발생하는 예외.
                            - NO_DATA_FOUND 
                                : PL/SQL Select문이 한 건도 리턴하지 못하는 경우 발생하는 예외.
                            - NOT_LOGGED ON 
                                : 접속되지 않은 상태에서 데이터베이스에 대한 요청이 PL/SQL 프로그램으로
                                  실행된 경우 발생되는 예외.
                            - PROGRAM_ERROR 
                                : PL/SQL이 내부적인 문제를 가지고 있는 경우 발생되는 예외.
                            - ROWTYPE_MISMATCH 
                                : 할당문에서 호스트 커서 변수와 PL/SQL 커서 변수의 데이터 형이 불일치할 때 발생되는 예외
                            - STORAGE_ERROR 
                                : PL/SQL이 실행될 때 메모리가 부족하거나 메모리상에 문제가 일어났을 대 발생하는 예외.
                            - SUBSCRIPT_BEYOND_COUNT 
                                : 컬렉션의 요소 갯수보다 더 큰 첨자 값으로 참조한 경우 발생
                            - SUBSCRIPT_OUTSIDE_LIMIT 
                                : 컬렉션의 첨자 한계를 벗어난 참조가 일어났을 때 발생
                            - SYS_INVALID_ROWD 
                                : 문자열을 ROWID로 변환할 때 무효한 문자열의 표현일 경우 발생되는 예외.
                            - TIMEOUT_ON_RESOURCE 
                                : 자원에 대한 대기시간이 초과했을 때 발생하는 예외.
                            - TOO_MANY_ROWS 
                                : PL/SQL select문이 두건이상의 행을 리턴햇을 때 발생되는 예외.
                            - VALUE_ERROR 
                                : 산술,변환,절삭 크기 제약에 에러가 생겼을 때 발생되는 예외.
                            - ZERO_DIVIDE
                                : 0으로 나누려 했을 때 발생하는 예외.
                  
                    ㄴ. Non-predefined ORACLE Exception
                          : 사전에 정해지지 않은 예외
              b. 사용자 정의 예외
                  : 사용자에 의해 정의되는 예외
                    사용자 정의 예외 사용 예)
                      declare (선언부에서)
                      예외명 exception;
                      begin부나 exception부에서 raise문을 이용해서 예외를 발생시킨다.
                      
                      - 예외처리부 형식)
                          -- 예외처리부 : 예외 발생시 어떻게 처리할 것인지에 예외처리 내용이 들어간다.
                        Exception
                          when 예외명 then
                            실행문...
                          when 예외명2 then
                            실행문...
                          when OTHERS then
                            실행문...
```







### 저장프로시저

```text
create procedure 프로시저명
        파라미터1(in,out,in out) 데이터타입, -- default는 in모드
          -- out : 값을 반환하겠다, in : 서브프로그램 내에 값 전달 in out : 서브프로그램 내에도 전달되고, 외부 응용프로그램에도 반환하기도 함
        파라미터2(in,out,in out) 데이터타입
      is
        변수 선언부;
      begin
        프로시저 본문 처리부;
      exception
        예외처리부;
      end;
```

-- 프로시저 정의 create procedure sumProcedure\(numVal in number, resultVal out number\) AS BEGIN resultVal := numVal + 10; END; /

-- 외부에서 변수를 하나 선언 variable numV number; -- 함수를 수행하되 외부에서 선언해논 변수에 값이 저장될 수 있도록 같이 전달해 준다. 이때 외부 선언한 -- 변수를 사용할 때는 : 를 붙여주어야 함 exec sumProcedure\(8, :numV\); print numV; -- 18 출력

### 함수

```text
create (or replace) function 함수명
    파라미터1 파라미터타입,
    파라미터2 파라미터타입,...
    return datatype
    is
    PL/SQL 블럭;
--EX)
create or replace function dept_max_sal
  (dept_id employees.department_id%type)
return number
IS
  max_sal employees.salary%type;
begin
  select max(salary) into max_sal
  from employees
  where department_id = dept_id;
  
  -- number 타입의 max_sal을 리턴시킴
  return max_sal; 
end;
/
  
select dept_max_sal(50) from dual;


create or replace function cnt_number
  (cnt number)
return number
IS
  total_cnt number;
begin
  select count(*) into total_cnt
  from employees
  where department_id = cnt;
  
  return total_cnt;
end;
/

select distinct cnt_number(50) from employees;
-- 부서별 인원수
select distinct department_id, cnt_number(department_id) from employees;

declare

begin
   dbms_output.put_line(cnt_number(50));
end;


create or replace function avg_sal
  (dept_id employees.department_id%type)
return number
IS
  avg_salary number;
begin
  select round(avg(salary),2) into avg_salary
  from employees
  where department_id = dept_id;
  
  return avg_salary;
end;
/

select department_id, avg_sal(department_id) 부서별평균급여
from employees
group by department_id;



create or replace function emp_dept_name
  (emp_id employees.employee_id%type)
return varchar2
IS
  dept_name departments.department_name%type;
BEGIN
  select department_name into dept_name
  from departments
  where department_id = (select department_id from employees 
                         where employee_id = emp_id);
  
  return dept_name;
END;
/

select distinct employee_id, emp_dept_name(employee_id) from employees;
```



### 트리거

: 개발자가 호출해서 사용하는 것이 아니라, 특정 이벤트와 연동해서 그 이벤트, 조건이 발생시 자동적으로 수행하는 동작을 의미한다. \(데이터베이스가 미리 정해 놓은 조건들을 만족하거나, 특정 이벤트가 발생하면 자동적으로 수행되는 동작\(PL/SQL 블럭\)으로 오라클에서 자동적으로 실행되는 PL/SQL 블럭을 의미\)

* \[ 트리거의 유형 \] // 여기선 dml트리거에 대해서만 알아봄
  * insert, update, delete의 결과로 실행되는 ""
* \*\* 트리거는 commit, rollback을 수행할 수 없고, commit,rollback을 수행하는 함수도 사용할 수 없다.
* \[ 트리거 구문 형식 \] 

```text
create (or replace) trigger 트리거이름 
  timming[before | after] event [insert | update | delete] ON 테이블명
begin
  실행명령;
end;
```

트리거 내에서는 new와 old키워드를 통해서 DML작업이 일어난 테이블의 필드값을 가지고 올 수 있는데 :NEW.컬럼명: DML트리거의 수정 또는 삽입문 내에서 사용이 가능하다. -&gt; SQL 반영 후의 컬럼 데이터   
:OLD.컬럼명 : DML트리거의 수정 또는 삭제문 내에서 사용이 가능하다. -&gt; SQL 반영전의 컬럼 데이터 를 의미하게 됩니다.

```sql
EX)
-- 테스트용 테이블 하나 생성
create table sample_dept(
  dept_id number,
  dept_name varchar2(15),
  loc varchar2(10)
);
desc sample_dept;

-- 위의 sample_dept에 데이터가 insert될 때 자동으로 동작하는 트리거를 작성해보자.
create or replace trigger print_msg
-- sample_dept테이블에 insert작업 이후에 실행되도록
after insert ON sample_dept 
BEGIN
  DBMS_OUTPUT.PUT_line('부서가 추가되었습니다.');
END;
/
-- 화면 출력 가능하게 세팅
set serveroutput on;
-- 테이블에 insert작업 발생시킴
insert into sample_dept values(10,'마케팅부','서울');
-- 자동으로 print_msg 트리거가 동작하게됨
--------------------------------------------------------------------------------

-- 물건 관리를 위한 테이블
create table item(
  code char(6) primary key, -- 물품 코드
  name varchar2(15) not null,
  company varchar2(15),
  price number(8),
  cnt number default 0 -- 재고 수량
);

create table warehouse(
  num number(6) primary key, --물품 입고 번호
  code char(6),
  indate date default sysdate, -- 입고 날짜
  incnt number(6),
  inprice number(6),
  totalprice number(8),
  constraint fk_code foreign key(code) references item(code)
);

insert into item(code,name,company,price) values('c0001','선풍기','삼성',100000);
insert into item(code,name,company,price) values('c0002','에어컨','LG',50000);
select * from item;

-- 창고(warehouse)에 상품이 입고될 때마다 상품(item)의 수량이 늘어나도록!(
    --  재고수량이 자동으로 늘어나도록 !! 트리거로 작성해 보자.

-- 재고수량 갱신을 위한 트리거 생성
create or replace trigger cnt_add
after insert on warehouse
for each row -- 각 row마다 반복한다는 의미
  begin
    update item set cnt = cnt + :new.incnt -- new 선언은 insert문,update문에서만 사용가능
    -- new키워드를 통해 warehouse 테이블 데이터에접근할 수 있고, warehouse 테이블에 insert작업이 이루어진 후의
    -- 데이터를 가지고 온다는 의미이다.(new)
    where code = :new.code; 
  end;
/

insert into warehouse(num, code, incnt, inprice, totalprice)
values(1,'c0001',2,100000,200000);
select * from item;
select * from warehouse;

-- 창고에서 물품이 삭제될 때마다 수량을 줄이는 트리거
create or replace trigger cnt_sub
after delete on warehouse
for each row
  begin
    -- delete에서는 new가 아닌 old를 사용해야 함
    -- delete작업이 반영되고 나버리면 데이터가 없기 때문에 반영할 incnt값이 없으니까
    update item set cnt = cnt - :old.incnt
    where code = :old.code;
  end;
/

delete from warehouse where code = 'c0001';
select * from item;
--------------------------------------------------------------------------------

-- **update**
  -- 수식 주의
create or replace trigger cnt_update
after update on warehouse
  for each row
    begin
      -- +- 는 +와 - 작업을 둘 다 해준다는 의미
      --  update item set cnt = cnt +- :old.incnt + :new.incnt -- 기존의 incnt값을 빼주고, 새로운 incnt값을 더해준다는 의미
      -- ex) 기존에 incnt값이 5가 있었으면 기존에 있었던 5를 빼주고 새로 입력된 7로 갱신해주기 위해 7을 더한다는 의미 5-5+7
      -- 기존의 값을 없애고 새 값을 반영해주도록 update를 짜야한다.
    --  where code = :new.code;
      
     -- update item set cnt = cnt - :old.incnt + :new.incnt where code = :new.code;
      update item set cnt = :new.incnt where code = :new.code;
    end;
/

update warehouse set incnt = 11, inprice = 800000 where code = 'c0001';
select * from warehouse;
select * from item;


-- 조건을 이용한 EX)
Create Trigger testTrigger
    after insert or update or delete -- 삽입, 업데이트, 삭제 중 하나 발생 이후에 실행
    on emp -- emp 테이블에 적용
    for each row -- DML작업에 의해 변경된 각각의 튜플(행)에 대해서
    when (:new.sal > :old.sal) -- 새로 변경된 sal이 변경전의 sal보다 큰 튜플에 대해서만
    -- 아래의 작업을 진행하라.
    BEGIN
        if (inserting) then dbms_output.put_line('inserting'); -- 삽입이면 
        elsif (updating) then dbms_output.put_line('updating'); -- 수정이면
        elsif (deleting) then dbms_output.put_line('deleting'); -- 삭제이면
        end if;
    END;
    
    -- 따라서, DML에 의해 변경된 모든 튜플들 중에 when의 조건에 해당하는 튜플(행)들에
    -- ~작업을 하도록 되는 것
```





### 테이블스페이스

```sql
/*
  [ 테이블 스페이스 ]
  : 오라클에서 데이터를 저장할 때 사용하는 논리적 저장공간(하드디스크에서는 실제 여러개의 물리적인
    데이터 파일로 구성될 수 있음)
    -> 오라클 시스템 운영에 필요한 필수 정보를 담고 있음
    
    DB는
      여러개의 테이블 스페이스로 구성되고, 각 테이블 스페이스는 여러개의 세그먼트로 구성된다.
      이때, 세그먼트는 각종 table, trigger, index, package 등 다양한 DB Object들이 될 수 있다.
      
    - 시스템 테이블 스페이스
      : DB설치시 자동으로 기본적으로 가지고 있는 테이블 스페이스로, 
        별도로 테이블 스페이스를 지정하지 않고 테이블, 트리거, 프로시저 등을 생성했다면
        이 시스템 테이블 스페이스에 저장되었던 것!
        EX) Data Dictionary 정보, 프로시저, 트리거, 패키지, 시스템 rollback segment, 사용자 데이터 포함
      
        rollback segment란?
          : rollback시 commit하기 전 상태로 돌리는데 그 돌리기 위한 상태를 저장하고 있는 세그먼트
      
    - Non-System 테이블 스페이스
      : EX) Temporary 세그먼트, application Data 세그먼트, index 세그먼트, 사용자 데이터 세그먼트
       Temporary세그먼트란?
        : order by를 해서 데이터를 가져오기 위해선 임시로 정렬할 데이터를 가지고 있을 공간이 필요하고
          그 곳에서 정렬한 뒤 데이터를 가져오는데 이 공간을 가리킨다.
        
    
    - [ 테이블스페이스의 구성 ]
    - 테이블 스페이스
      - 세그먼트(segment) : table, 트리거 등
          - 익스텐트(extent) : 연속적인 데이터블록으로 구성(오라클 입출력 최소 저장 단위)
          
    - [ 테이블 스페이스 생성 구문 ]
    create tablespace 테이블스페이스명
      datafile '저장될 경로 및 사용할 파일명' // DBF, ora 파일로 저장
      size 저장공간 // 기본 크기 지정
      default storage storage_clause;
    
    테이블스페이스 삭제
      drop tablespace 테이블스페이스이름
      [including contents[and datafiles] //테이블 스페이스에 들어있는 데이터도 지울지
      [cascade constraints] // 연계성 있는 테이블스페이스도 삭제할지

    이렇게 쿼리문으로 만들수도 잇지만 EM이라는 관리도구를 통해 쉽게 UI적으로 할 수 있다.
    
    - 테이블스페이스 생성은 system 계정이어야 한다.
*/
create tablespace test_1
  datafile 'c:\oradata\test_1.dbf'
  size 100M
  default storage (
                    initial 6M --최초 익스텐트 크기
                    next 1M -- 첫번째 익스텐트 다 사용 후 그 다음 익스텐트 크기
                    MINEXTENTS 1 -- 최소 개수
                    MAXEXTENTS 10
                    PCTINCREASE 0 -- next 익스텐트 다음에 ()프로 저장공간을 할당한다.
                  );
-- 저장공간을 10M 늘리도록 수정해 보자.                  
alter tablespace test_1
  add datafile 'c:\oradata\test_2.dbf' size 10M;

create table aaa(
  name varchar2(10)
); -- 그냥 이렇게 하면 시스템 테이블 스페이스에 저장되게 됨

-- test_1 테이블 스페이스에 저장하도록 테이블 aaa2를 생성
create table aaa2(
  name varchar2(10)
)tablespace test_1;

-- 테이블 스페이스를 지움
drop tablespace test_1; -- 오류 발생 내용이 잇기 때문 따라서 including contents 옵션 사용이 필요

drop tablespace test_1
  including contents; -- 테이블 스페이스 내부에 있는 데이터도 같이 삭제한다는 의미임
-- 하고나도 파일은 남아 있음
-- 따라서, 파일까지 지울려면 and datafiles 옵션도 추가해주어야 함


create tablespace test_3
  datafile 'c:\oradata\test_3.dbf'
  size 100M
  default storage (
                    initial 6M --최초 익스텐트 크기
                    next 1M -- 첫번째 익스텐트 다 사용 후 그 다음 익스텐트 크기
                    MINEXTENTS 1 -- 최소 개수
                    MAXEXTENTS 10
                    PCTINCREASE 0 -- next 익스텐트 다음에 ()프로 저장공간을 할당한다.
                  );
drop tablespace test_3
  including contents and datafiles;

/*
  [ 테이블스페이스 관리 ]
  : 처음 생성한 테이블스페이스 크기를 넘어가면 테이블스페이스 저장 용량을 늘려줘야할 것이다.
  이때, 수동으로 하지 않고 저장공간을 자동으로 늘리는 방법에 대해 알아보자.
  
  - 테이블스페이스의 size를 자동으로 조정하는 옵션 ]
  
*/
create tablespace test_3
  datafile 'c:\oradata\test_3.dbf'
  size 10M
  default storage (
                    initial 6M --최초 익스텐트 크기
                    next 1M -- 첫번째 익스텐트 다 사용 후 그 다음 익스텐트 크기
                    MINEXTENTS 1 -- 최소 개수
                    MAXEXTENTS 10
                    PCTINCREASE 0 -- next 익스텐트 다음에 ()프로 저장공간을 할당한다.
                  );
                  
-- 테이블 size를 자동으로 조정하는 방식
alter tablespace test_3
  add datafile 'c:\oradata\test_4.dbf' size 10M
  AUTOEXTEND ON NEXT 10M MAXSIZE 200M; -- 10M초과시 자동으로 10M시 늘리되 최대 200M까지


-- DBA가 수동으로 size를 조정하는 방법
alter database datafile 
  'c:\oradata\test_3.dbf' resize 30M; -- 기존 파일을 30M사이즈로 바꿈


-- [ 테이블스페이스 관련 Dictionary ]  
/*
    .DBA_TABLESPACES : 모든 테이블스페이스의 저장정보 및 상태정보를 갖고 있는 Dictionary
    .DBA_DATA_FILES : 테이블스페이스의 파일정보
    .DBA_FREE_SPACE : 테이블스페이스의 사용공간에 관한 정보
    .DBA_FREE_SPACE_COALESCED : 테이블스페이스가 수용할 수 있는 익스텐트의 정보
*/
select tablespace_name, initial_extent, next_extent, min_extents, max_extents,
       pct_increase, status, contents
from DBA_TABLESPACES;
select * from dba_tablespaces;
select * from dba_data_files;
select * from dba_free_space;
select * from SYS.DBA_FREE_SPACE_COALESCED;

-- extent 수집(coalesced) 명령
--alter tablespace 테이블스페이스명 coalesce;











```





















