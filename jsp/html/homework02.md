### html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>설문 조사</title>
    <!-- 합쳐지고 최소화된 최신 CSS -->
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.2/css/bootstrap.min.css">
    <!-- 부가적인 테마 -->
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.2/css/bootstrap-theme.min.css">
    <!-- 합쳐지고 최소화된 최신 자바스크립트 -->
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.2/js/bootstrap.min.js"></script>
</head>
<body>

<div class="text-center">
<h3>혈액형 선택</h3>
<input type="radio" name="blood" value="A">A형
<input type="radio" name="blood" value="B">B형
<input type="radio" name="blood" value="AB">AB형
<input type="radio" name="blood" value="O">O형
<hr>

<h3>통신사 선택</h3>
<input type="radio" name="telecom" value="LG">LG-Uplus
<input type="radio" name="telecom" value="SKT">SKT
<input type="radio" name="telecom" value="KT">KT
<input type="radio" name="telecom" value="etc">기타
<hr>

<h3>희망 과목 선택</h3>
<input type="checkbox" name="subject" value="C++">C++
<input type="checkbox" name="subject" value="Pyton">Python
<input type="checkbox" name="subject" value="JAVA">Java
<input type="checkbox" name="subject" value="etc">기타
<hr>

<h4>Submit</h4>
<input type="submit" class="btn btn-primary" name="result" value="아주 좋음">
<input type="submit" class="btn btn-success" name="result" value="좋음">
<input type="submit" class="btn btn-default" name="result" value="보통">
<input type="submit" class="btn btn-warning" name="result" value="별로">
<input type="submit" class="btn btn-danger" name="result" value="아주 별로">

</div>
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

@WebServlet("/Quiz01")
public class Quiz01 extends HttpServlet{
	@Override
	protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
		String blood = req.getParameter("blood");
		String telecom = req.getParameter("telecom");
		String[] subject = req.getParameterValues("subject");
		String result = req.getParameter("result");
		
		
		System.out.println("blood : " + blood);
		System.out.println("telecom : " + telecom);
		for(int i=0; i<subject.length; i++)
			System.out.println("subject : " + subject[i]);
		System.out.println("result : " + result);
	}

}

```
