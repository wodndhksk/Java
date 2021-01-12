### Html
```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Sign-up</title>
 <!-- 합쳐지고 최소화된 최신 CSS -->
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.2/css/bootstrap.min.css">
    <!-- 부가적인 테마 -->
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.2/css/bootstrap-theme.min.css">
    <!-- 합쳐지고 최소화된 최신 자바스크립트 -->
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.2/js/bootstrap.min.js"></script>
</head>
<body>
	<!-- 회원가입 <form>을 하나 만들고 
		action : /ch02-servlet/Test03
		method : post
		
		아이디-text, 
		비밀번호 2번- password,
		이메일- <input> text + <select> naver.com / nate.com / gmail.com / hanmail.net 
		운영진에게 한마디-<textarea>
		 
		 Test03 서블릿
		 인자로 들어온 파라미터를 모두 받아 sysout 으로 출력
		 두 비밀번호가 같으면 "회원 가입 완료!"
		 다르면 "비밀번호가 일치하지 않습니다."
		 
	-->
	<form action="Test03" method="post">
	   <div class="container">
        <div class="row">
            <div class="form-group">
                <label for="id" class="control-label col-xs-2">ID</label>
                <div class="col-xs-10">
                    <input class="form-control" type="text" name="id" placeholder="email을 입력해주세요."/>
                </div>
            </div>

            <div class="form-group">
                <label for="password" class="control-label col-xs-2">Password</label>
                <div class="col-xs-10">
                    <input class="form-control" type="password" name="password" placeholder="password을 입력해주세요."/>
                </div>
            </div>

            <div class="form-group">
                <label for="password2" class="control-label col-xs-2">Password 확인</label>
                <div class="col-xs-10">
                    <input class="form-control" type="password" name="password2" placeholder="password를 한번더 입력해주세요."/>
                </div>
            </div>

            <div class="form-group">
                <label for="email" class="control-label col-xs-2">Email</label>
                <div class="col-xs-5">
                    <input class="form-control " type="text" name="emailText" placeholder="Email 을 입력해주세요."/>
                </div>

                <div class="col-xs-5">
                    <select name="email">
                        <option value="naver">naver.com</option>
                        <option value="nate">nate.com</option>
                        <option value="gmail">gmail.com</option>
                        <option value="hanmail">hanmail.net</option>
                    </select>
                </div>
            </div>

            <div class="form-group">
                <label for="textarea" class="control-label col-xs-12"> 운영진에게 한마디</label>
                <textarea class="control-textarea col-xs-12"></textarea>
            </div>

        </div>
    </div>
<div class="container">
    <button type="submit" class="btn btn-primary">Submit</button>
</div>

</form>	
</body>
</html>
```
### Servlet
```java
package com.megait;

import java.io.IOException;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/Test03")
public class Test03 extends HttpServlet{
	@Override
	protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
		String id = req.getParameter("id");
		String password = req.getParameter("password");
		String password2 = req.getParameter("password2");
		String emailText = req.getParameter("emailText");
		String email = req.getParameter("email");
		String textarea = req.getParameter("textarea");
		
		System.out.println("id : " + id);
		System.out.println("password : " + password);
		System.out.println("password2 : " + password2);
		System.out.println("email : " + emailText +"@"+ email);
		System.out.println("textarea : " + textarea);
		
	}
	
}

```
