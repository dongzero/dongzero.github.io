---
title: "주소록 프로젝트_AddressProject"
categories: Java
tag:
toc: true
---

<span style = "font-size:80%"> comment)
주소록 프로젝트를 한번 진행해 보았다.
문득 튜토리얼 루프에 빠질것같다는 생각이 들었고
클론코딩이든 구글링코딩이든 무언가 스스로 한번 만들어봐야겠다는
생각이 들었다 온전한 나의실력이 아니더라도 분명이 알게되는것도
있을것이고 느낀것도 있을거라 생각하였기 때문이다.<span>

<br>
<br/>

### 사용 모듈리스트
```java
package address2.java;

import java.io.BufferedReader;//입출력 모듈 scanner보다 상대적 빠른 성능을 가지고있다(캐시메모리?)
import java.io.IOException;//입출력 예외처리 모듈
import java.io.InputStreamReader;//입력과 출력을 이어주는 데이터 연결관같은 역할
import java.sql.Connection;//자바와 DB를 연결해주는 모듈
import java.sql.DriverManager;//JDBC 드라이버의 기본적서비스 자바에서 작성한 DB쿼리문을 연동해준다
import java.sql.PreparedStatement;//SQL구문을 실행하는 역할
import java.sql.ResultSet;//DB로 전달되는 명령을 DB에서 처리가되고 값을 돌려주는 역할
import java.sql.SQLException;//DB접근과 다른에러에대한 정보를 제공
import java.sql.Statement;//Connection로 연결한 객체에게 쿼리작업을 실행시켜주는 역할
```  
  <br><br/>
  <br><br/>
  

### DB로그인
```java
class Db{
	private Connection conn;
	public Db() {
		try {
			Class.forName("com.mysql.jdbc.Driver");
			String url="jdbc:mysql://127.0.0.1:3306/project01";
			String user="dong";
			String pass="1230";
			conn=DriverManager.getConnection(url, user, pass);
		} catch (ClassNotFoundException | SQLException e) {
			// TODO 자동 생성된 catch 블록
			e.printStackTrace();
		}
	}
```
<span style = "font-size:70%">
DB라는 class를 생성하였다 DB에 로그인시 에러를 확인하기 위해 try(예외감지)와 catch(예외처리)로 작성하였고, forname로 드라이버로드 설정 그리고 DB의 경로,로그인정보를 제공하여 DB의 접속할수 있도록 하였다.  <span>
<br>
<br/>

### DB데이터 조회
```java
	public void insert(Phone p) {
		String sql="insert into phone values(?,?)";
		try {
			PreparedStatement pmt=conn.prepareStatement(sql);
			pmt.setString(1, p.getName());
			pmt.setString(2, p.getNo());
			pmt.executeUpdate();
			pmt.close();
			
			
		} catch (SQLException e) {
		
			e.printStackTrace();
		}
	}
```
<span style = "font-size:70%">
SQL구문을 실행해주도록 한다 String sql을 폰의 정보를 입력하는 문자열을 만들어준다 PreparedStatement 클래스 객체를 만들고 conn(객체).PreparedStatement(메소드)를 받아와 쿼리구문을 실행할수 있는 환경을 작성하였고, 1번은 getname(이름)2번은(전화번호)를 실행하여 업데이트 되도록 하였다.<span>
<br>
<br/>

### DB쿼리전송
```java
	public void select() {
		try {
			Statement stm=conn.createStatement();
			String sql="select * from phone";
			ResultSet rs=stm.executeQuery(sql);
			while(rs.next()) {
				System.out.println(rs.getString(1)+":"+rs.getString(2));
			}
			rs.close();
			stm.close();
		} catch (SQLException e) {
			// TODO 자동 생성된 catch 블록
			e.printStackTrace();
		}
	}
```
<span style = "font-size:70%">
DB에 SQL문을 보내기위한 createStatement()객체를 생성하고  DB의 select * from phone 라는 쿼리가 생성될수있도록 한다 그정보는 ResultSet객체의 stm.executeQuery문을 통해 생성된 DB정보의 값을 반환받는다 반환된 값은 1이름과 2번호의 정보이다.<span>
}

### JAVA입출력
```java
class Phone{
	private String name;
	private String no;
	BufferedReader in=new BufferedReader(new InputStreamReader(System.in));
	public Phone() throws IOException {
		System.out.println("이름:");
		name=in.readLine();
		System.out.println("전화번호:");
		no=in.readLine();
		
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public String getNo() {
		return no;
	}
	public void setNo(String no) {
		this.no = no;
	}
}
```
<span style = "font-size:70%">
정보를 등록하고 등록한 정보가 출력되는 Phone class를 생성한다 BufferedReader in=new BufferedReader(new InputStreamReader(System.in)); 를 통해 콘솔창에 정보를 입력하고 출력할수 있도록 기반을 만들어주고 이름: 전화번호: 를 콘솔창을 통해 입력하고 readLine을 통해 한줄라인으로 가독성을 높혔다. 위에 생성한 getname,  getno class를 호출하여 참조할수 있도록 하였다.<span>
<br>
<br/>

### 메인화면
```java
public class Ex06 {

	public static void main(String[] args) throws NumberFormatException, IOException {
		BufferedReader in=new BufferedReader(new InputStreamReader(System.in));
		Db db=new Db();
		while(true) {
			System.out.println("1.등록 2.출력 0.종료: ");
			int s=Integer.parseInt(in.readLine());
			if(s==1) {
				db.insert(new Phone());
			}
			if(s==2) {
				db.select();
			}
			if(s==0) {
				break;
			}
			
		}
		System.out.println("프로그램 종료");
	}

}
```
<span style = "font-size:70%">
데이터 메인 화면 1.등록 2.출력 3.종료 번호를입력하여 동작할수 있도록 하였다.
<span>
<br>
<br/>

### 결과화면
```java
1.등록 2.출력 0.종료: 
1
이름:
아무개
전화번호:
222-2222-2323
1.등록 2.출력 0.종료: 
2
노동영:111-1111-1111
홍길동:222-2222-2222
노동영:111111222
아무개:222-2222-2323
1.등록 2.출력 0.종료: 
0
프로그램 종료
```
<br>
<br/>

### DB Table 정보
<span style = "font-size:70%">
(mysql)DB에 생성되어있는 정보  
정상적으로 데이터가 저장되어있는것을 볼 수 있다.
<span>
![addressTable](https://user-images.githubusercontent.com/110845862/195926084-8ce235cd-20bb-4680-aca5-716d061d5acc.PNG)