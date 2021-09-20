## JDBC란

>
>
>Java Database Connectivity
>
>자바에서 DB프로그래밍을 하기위해 사용되는 API  
>
>자바 언어로 다양한 종류의 관계형 데이터베이스에 접속하고 SQL문을 수행하여 처리하고자 할 때 사용되는 표준 SQL 인터페이스 API



*JDBC 프로그래밍 코딩 흐름* 

1. JDBC  드라이버 로드 
2. DB 연결
3. DB에 데이터를 읽거나 쓰기 ( SQL 문)
4. DB연결 종료



***JDBC 드라이버*** >   통신을 담당하는 자바 클래스 

로딩 코드 :  Class.forName("jdbc 드라이버 이름 ")   _ 알맞는 JDBC드라이버 필요

: com.mysql.jdbc.Driver > mysql  



*** jDBC URL***  >  DBMS와의 연결을 위한 식별 값 

구성 : jdbc:[DBMS]:데이터베이스식별자 

"jdbc:mysql://HOST[:PORT]/DBNAME[?param= ]";  > mysql



---

# 일반적인 코드 구성 

``` 
import java.sql.*;
```

``` 
Class.forName("com.mysql.jdbc.Driver");    >> 드라이버 로드 
```

``` 
String url = "jdbc:mysql://HOST[:PORT]/DBNAME[?param= ]";  
Connection conn = DriverManager.getConnection(url,id,pw); >> Connection 객체 생성  
```

``` 
Statment stmt = conn.createStatement(); >> sql문을 서버에 전송 및 실행 
```

```
ResultSet rs = stmt.executeQuery  >> resultset 객체를 통해서 전달 받고 데이터 값을 가지고 옴 
```

```
stmt.executeUpdate(sql); > insert, update , delete  반환값 타입은 int형 
```

``` 
rs.close();
stmt.close();         >> 연결 해제
conn.close();
```









