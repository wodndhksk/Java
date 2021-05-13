```java
package day19.homework;

import java.util.Scanner;

class User {
	
	interface Whitelist{
		// 유효한 서버 이름과 도메인을 따로 상수로 선언하면 유지보수가 편하다.  
		String[] VALID_MAIL_SERVER_NAMES = 
			{ "naver", "gmail", "hanmail", "nate"};
		
		String[] VALID_MAIL_SUFFIXES = 
			{"com", "co.kr", "net", "org" };
		String PASSWORD_REGEX = "^(?=.*[0-9])(?=.*[a-z])(?=.*[A-Z])(?=.*[@#$%^&+=])(?=\\S+$).{4,20}$";
		
		/*
		 * ^ # start-of-string 
		 * (?=.*[0-9]) # a digit must occur at least once
		 * (?=.*[a-z]) # a lower case letter must occur at least once 
		 * (?=.*[A-Z]) # an upper case letter must occur at least once 
		 * (?=.*[@#$%^&+=]) # a special character must occur at least once 
		 * (?=\S+$) # no whitespace allowed in the entire string 
		 * .{4,20} # anything, at least eight and less or equal to 20 places though 
		 * $ # end-of-string
		 */
	}
	
	
	private String id; // get
	private String email; // set, get
	private String password; // set, (get 대신 hiddenPassword) 
	
	public boolean setEmail(String email) {
		
		// null comparison
		if(null == email) {
			return false;
		}
		
		
		// email 양 공백 제거
		email = email.trim();
		
		
		// @ 를 포함하여야 한다.
		if(!email.contains("@")) {
			System.out.println("@를 포함하셔야 합니다.");
			return false;
		}
		
		// trim이 되었고 @가 있는 이메일은  
		//  아이디가 없을 경우 무조건 맨 앞글자가 "@"일 것이다.
		if(email.indexOf("@") == 0) {
			throw new NumberFormatException("아이디를 포함하셔야합니다."); ///////// 요부분
		}
		
		// com, co.kr, net 중 하나로 끝나야 한다
		String suffix = null;
		for(String s : Whitelist.VALID_MAIL_SUFFIXES) {
			if(email.endsWith(s)) {
				suffix = s;
				break;
			}
		}
		if(null == suffix) {
			return false;  //////// 이런 부분 
		}
		
		// 메일서버(naver, gmail, hanmail 등) 이름을 포함해야 한다.
		boolean check = false;
		for(String server : Whitelist.VALID_MAIL_SERVER_NAMES) {
			if(email.endsWith("@" + server + "." + suffix)) {
				check = true;
				break;
			}
		}
		if(!check) {   
			return false;
		}
		this.email = email;
		setId();
		return true;
	}
	public boolean setPassword(String password) {
		if (!password.matches(Whitelist.PASSWORD_REGEX)) {
			System.out.println("특수기호, 숫자, 대소문자가 최소 1개씩을 포함하셔야 합니다.");
			return false;
		}
		if(password.length() < 4 || password.length() > 20) {
			return false;
		}
		this.password = password;
		return true;
	}
	public boolean confirmPassword(String password) {
		if(null == this.password) {
			//return false;
			throw new NullPointerException();
		}
		return this.password.equals(password);
	}
	
	private void setId() {
		if(null == email) 
			//return;
			throw new NullPointerException();
		// issell@naver.com 
		// 방법1 : split("@") ==> [ 'issell' , 'naver.com' ]
		// 방법2 : substring(0, indexOf("@"))
		
		// 방법1 
		// id = email.split("@")[0];
		
		// 방법2
		id = email.substring(0, email.indexOf("@"));
	}
	
	public String hiddenPassword() {
		if(null == password) {  // pika1234 
			return null;
		}
		String temp = password.substring(0,2); // pi
		for(int i = 0; i < password.length()-2; ++i) { // "*" 를 총 6번 붙임
			temp += "*";
		}
		return temp; // pi******
	}
	
	@Override
	public String toString() {
		return "User [id=" + id + 
				", email=" + email + 
				", password=" + hiddenPassword() + "]";
	}
}
public class day24 {
	public static void main(String[] args) {
		User user = new User();
		Scanner sc = new Scanner(System.in); 
		
		// 이메일 입력 loop 
		while(true) {
			try {
				System.out.print("이메일 : ");
				String email = sc.next();
				if(!user.setEmail(email)) {
					System.out.println("잘못된 이메일 형식입니다.");
					continue;
				}
				break;
			} catch(NumberFormatException e) { ///////////// 요 부분!
				System.out.println(e.getMessage()); 
				e.printStackTrace();
			}
			
		}
		while(true) {
			try {
				System.out.print("비밀번호 : ");
				String password = sc.next();
				if(!user.setPassword(password)) {
					System.out.println("잘못된 비밀번호 형식입니다.");
					continue;
				}
			}catch(NullPointerException e){
				
				System.out.println(e.getMessage());
				e.printStackTrace();
				
			}
			System.out.print("한 번 더 : ");
			String temp = sc.next();
			if(!user.confirmPassword(temp)) {
				System.out.println("두 비밀번호가 일치하지 않습니다.");
				continue;
			}
			break;
		}
		System.out.println(user);
	}
}








```
