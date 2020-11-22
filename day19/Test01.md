```java
package day19.basic;


	public class Test02 {
		public static void main(String[] args) {
			String email = "issell@naver.com";
			
			// char	charAt(int index) : index 번 문자를 return 
			char ch1 = email.charAt(3);// e
			System.out.println(ch1);
			
			
			// String concat(String str) : 이 문자열 + str 
			String str2 = email.concat("AAA");
					//    email + "AAA"
			System.out.println(str2); // issell@naver.comAAA
			
			
			// boolean	contains(CharSequence s) : s 가 이 문자열에 있니?
			boolean res3 = email.contains("naver");
			System.out.println(res3); // true 
					
			
			// boolean	endsWith(String suffix)  : suffix 로 끝나니?
			// boolean	startsWith(String prefix) : prefix 로 시작하니
			System.out.println(email.endsWith(".com")); // true
			System.out.println(email.endsWith(".co.kr")); // false
			
			// boolean	equalsIgnoreCase(String anotherString) : 대소문자 안가리는 equals
			
			byte[] arr = "ABC".getBytes();
			for(byte a : arr) {
				System.out.println(a);
			}
			
			arr = "가나다".getBytes();
			for(byte a : arr) {
				System.out.println(a);
			}
			
			
			// int	indexOf(String str) 
			// int	indexOf(String str, int fromIndex)
			// int	lastIndexOf(String str) 
			// int	lastIndexOf(String str, int fromIndex)
			String s = "ABC!DEF!JAVA!JAVA!"; 
			System.out.println(s.indexOf("!")); // 3
			System.out.println(s.indexOf("!", 10)); // 12
			
			System.out.println(s.lastIndexOf("!")); // 17
			System.out.println(s.lastIndexOf("!", 10)); // 7
			
			System.out.println(s.indexOf("@")); // -1
			System.out.println(s.indexOf("JAVA")); // 8
			
			// boolean isEmpty() ==> "" 이니? 
			System.out.println(s.isEmpty()); // false
			s = "";
			System.out.println(s.isEmpty()); // true
			//s = null;
			System.out.println(s.isEmpty()); // NullPointerException
			
			String result = String.join(",", "java", "C++", "python");
			System.out.println(result); // java,C++,python
			
			String[] sArr = {"java", "C++", "python"};
			result = String.join(",", sArr);
			System.out.println(result); // java,C++,python
			
			
			// int length() : 문자 개수
			// ** 배열명.length	 => 변수
			//    문자열.length()  => 메서드 
			System.out.println(email.length());
			
			// String	replace(CharSequence old, CharSequence new)
			//          ==> old를 new로 대체한 새 문자열 return
			result = result.replace(",", ""); 
			System.out.println(result); // javaC++python
			
			// String	replaceAll(String regex, String replacement)
			result = email.replaceAll("@|[.]", " ");
			System.out.println(result);
			
			String tel = "010-1111-2222";
			result = tel.replaceAll("[0-9]", "*");
			System.out.println(result); // ***-****-****
			
			String[] b = "JAVA,Python!Hello,C~".split(",|!|~");
			for(String ss : b) {
				System.out.println(ss);
			}
			/*
			for문 결과 : 
			JAVA
			Python
			Hello
			C
			 */
			
			String c = "ABCDEFG";
			System.out.println(c.substring(4)); // EFG
			System.out.println(c.substring(2,6)); // CDEF  //6번째는 표현안됨 2<= <6
			
			char[] chs = c.toCharArray();
			for(char c1 : chs) {
				System.out.println(c1);
			}
			
			
			// String toLowerCase()
			// String toUpperCase()
			System.out.println("AcdhAewBDF".toLowerCase()); // acdhaewbdf
			System.out.println("AcdhAewBDF".toUpperCase()); // ACDHAEWBDF
			
			//중요@@@@@@@@@@@  // String trim() : 양 공백 삭제
			System.out.println("         abc def      asd  ".trim());
			// 결과 : abc def      asd
			
			// static String valueOf(다들어감)
			// 인자값을 String형으로 변환 
			String a1 = 1 + ""; // "1"
			String a2 = String.valueOf(1); // "1"
			
			
			
			
		}
	}





```java
