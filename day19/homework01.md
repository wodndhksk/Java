#1
```java
package day19.homework;

import java.util.Scanner;

//1. 사용자가 -1을 입력할 때까지 문자열을 입력 받고
//    1) 입력된 문자열 중 소문자 'a'의 개수를 출력하세요.
//    2) 비출력문자(공백,엔터 등)을 제외한 문자의 총 개수를 출력하세요.
//    3) 단어의 개수를 출력하세요.
public class Test02 {

	public static void main(String[] args) {
		String s;
		
		int count = 0;
		int count2 = 0;
		Scanner sc= new Scanner(System.in);
		
		while(true) {
			System.out.println("문자열 입력 : ");
			s = sc.nextLine();
			
			for(int i = 0; i<s.length(); i++) {
				if((s.trim().charAt(i) == 97)) // a 아스키
					count++;
			
				
			}
			
			
			
			System.out.println(count);		// 'a' 갯수 
			System.out.println((s.replaceAll("\\s+","")).length()); //공백등을 제외한 문자 총 갯수 
			
//			while(true) {
//				s = sc.nextLine();
//				if(s.length() == 0) {
//					break;
//				}
//			
//			}
			System.out.println(s.split(" ").length); // 단어의 갯수 
			break;
		}
	

	}

}

```
#2
```java
package day19.homework;
//2. 회원가입과정은 다음과 같습니다.
//1) 이메일을 입력 받는다.
//2) 비밀번호를 2번 입력받는다.
//
//이때 다음 조건에 충족하면 저장, 그렇지 않으면 해당 항목을 재입력 받으세요
//	1) 이메일 조건
//	- @ 를 포함하여야 한다.
//	- com, co.kr, net 중 하나로 끝나야 한다
//	- 메일서버(naver, gmail, hanmail 등) 이름을 포함해야 한다.
//	- 아이디가 있어야 한다.
//	- 양쪽 공백 제거한다.
//	
//2) 비밀번호 조건
//	- 4자 이상 20자 이하여야 한다.
//	- (선택사항) 특수기호, 숫자, 대소문자가 최소 1개씩 모두 있어야 한다. (String 클래스의 matches()사용)
//	- 두 비밀번호가 동일해야 한다.
//
////이메일은 맞고 비밀번호 틀릴시 비밀번호만 재입력 (WHILE문 2개 사용)
//
//모두 정상적인 입력을 받았다면 사용자의 id, 패스워드, 이메일을 출력하세요.
//1) id 는 이메일의 @ 앞 부분을 추출합니다.
//2) 비밀번호는 앞 두 글자만 출력하고 나머지는 '*'로 대체합니다.
//	예) pika1234 ==> pi******
//3) 이메일은 모두 출력합니다.
import java.util.Scanner;

//class Person{
//	String email;
//	String password1,password2;
//	
//}

public class Test01 {

	public static void main(String[] args) {
		String email;
		String password1,password2;
		
		
		Scanner sc = new Scanner(System.in);
	
		while(true) {
			
			System.out.println("이메일을 입력하세요 : ");
			email = sc.next().trim();
			
			if(email.contains("@") && (email.endsWith(".com") || email.endsWith(".co.kr") || email.endsWith(".net"))
					&&(email.contains("naver") || email.contains("gmail") || email.contains("hanmail"))  ) {
				
				
			}
			else {
				System.out.print("다시 ");
				continue;
			}	
			//2) 비밀번호 조건
//			- 4자 이상 20자 이하여야 한다.
//			- (선택사항) 특수기호, 숫자, 대소문자가 최소 1개씩 모두 있어야 한다. (String 클래스의 matches()사용) //아스키 코드값 사용..?
//			- 두 비밀번호가 동일해야 한다.
			
			while(true) {
				System.out.println(" 비밀번호를 입력하세요 : ");
				password1 = sc.next().trim();
				
				System.out.println(" 비밀번호를 다시 한번 입력하세요 : ");
				password2 = sc.next().trim();
			
				if(password1.equals(password2)) {
					
				
				}
				else {
					System.out.println("비밀번호가 일치하지 않습니다! ");
					continue;
				}
				
				if(password1.length()>=4 && password1.length()<=20) {
					
				}
				else {
					System.out.println("비밀번호는 4자이상 20자 이상 가능합니다. ");
					continue;
				}
				
				//if(password1.matches())
				
				
				//모두 정상적인 입력을 받았다면 사용자의 id, 패스워드, 이메일을 출력하세요.
				//1) id 는 이메일의 @ 앞 부분을 추출합니다.
				//2) 비밀번호는 앞 두 글자만 출력하고 나머지는 '*'로 대체합니다.
//					예) pika1234 ==> pi******
				//3) 이메일은 모두 출력합니다.
				System.out.println(email.substring(0,email.indexOf("@")));
				
				String answer = password1.substring(0,2);
				for (int i = 0; i < password1.substring(2).length(); i++)
					answer += "*";
				
				System.out.println(answer);
				System.out.println(email);
	
				break;
				
				
			}//while(1)
		
			break;
		}//while(2)
		
			
		
		
		
	}

}


```
