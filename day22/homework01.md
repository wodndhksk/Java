```java
package day22.homework;

import java.util.ArrayList;
import java.util.HashMap;
//import java.util.Iterator;
import java.util.List;
import java.util.Random;
import java.util.Scanner;
import java.util.Set;

//String menu = "1. 단어 추가\n" 
//		+ "2. 단어 검색\n" 
//		+ "3. 모든 단어 보기\n"
//		+ "4. 퀴즈 풀기 \n"
//		+ "0. 종료\n입력 : ";
//

//1 : 영단어, 그의 뜻(한글) 을 입력 받고 단어장(Map)에 저장
//2 : 영단어 입력 받고 그의 뜻을 출력. 없으면 "미등록 단어" 출력  (containsKey("apple")) 
//3 : for문 사용 
//4 : (선택문제) 
//      문제 : 뜻   / 답 : 영단어  
//예) 사과(은)는 영어로? ==> 'home' 입력 ==> 땡!
//문제는 랜덤하게 나와야 함. Map --> List 나 array 로 변경해야 함
class englishQuiz{
	
	private HashMap<String, String> hashMap;
	private String quiz;
	private String answer;
	
	
	englishQuiz(){
		hashMap = new HashMap<>();
	}
	
	
	public void Menu01(String quiz, String answer) {
		this.quiz = quiz;
		this.answer = answer;
		hashMap.put(this.quiz, this.answer);
		
	}//Menu01
	
	public boolean Menu02(String quiz) {
		this.quiz = quiz;
		
		if(hashMap.containsKey(quiz)){
			
			System.out.println(hashMap.get(quiz));
			return true;
		}
		System.out.println("미등록 단어 ");
		
		return false;
		
	}//Menu02
	
	public void Menu03() {
		
//		Iterator<String> ir = hashMap.keySet().iterator();
//		while(ir.hasNext()) {
//			String key = ir.next();		
//			System.out.println(hashMap.get(key));
//			
//		}//key값을 통해 value값 출력 
		
		Set<String> keys = hashMap.keySet();
		for(String key : keys) {
			System.out.println(key);
		}
		
	}//Menu03
	//4 : (선택문제) 
	//  문제 : 뜻   / 답 : 영단어  
	//예) 사과(은)는 영어로? ==> 'home' 입력 ==> 땡!
	//문제는 랜덤하게 나와야 함. Map --> List 나 array 로 변경해야 함
	
	
	public void Menu04() {
		Scanner sc = new Scanner(System.in);
		String answer;
		
		List<String> keyList = new ArrayList<>(hashMap.keySet());
		List<String> valueList = new ArrayList<>(hashMap.values());
		Random random = new Random();
		String randomValue = valueList.get( random.nextInt(valueList.size()) );
		
		this.answer = randomValue;
		
		System.out.println(randomValue+"(은)는 영어로? ");
		answer = sc.next();
		
//		if(randomValue == null) {
//			System.out.println("단어를 추가해 주세요 ");
//		}
//		else if(answer.equals(hashMap.getKey())) {
//			System.out.println("정답! ");
//			
//		}
//		
//		else {
//			System.out.println("땡!");
//			System.out.println(hashMap.keySet());
//		}
//		
		
		
		
	}
	
	public String getQuiz() {
		return quiz;
	}


	public void setQuiz(String quiz) {
		this.quiz = quiz;
	}


	public String getAnswer() {
		return answer;
	}


	public void setAnswer(String answer) {
		this.answer = answer;
	}

	
}
public class Test01 {

	public static void main(String[] args) {
//		String  eng;
//		String kor;
		int num;
		Scanner sc = new Scanner(System.in);
		
		englishQuiz quiz = new englishQuiz();
		
		
		loop : while(true) {
			System.out.println("1. 단어 추가\n"
					+ 		"2. 단어 검색\n" 
					+ 		"3. 모든 단어 보기\n"
					+ 	    "4. 퀴즈 풀기 \n"
					+ 		"0. 종료\n입력 : ");
			
			num = sc.nextInt();
			
			switch (num) {//1 : 영단어, 그의 뜻(한글) 을 입력 받고 단어장(Map)에 저장
			case 1: {
			    System.out.println("영단어, 그의 뜻(한글)을 입력 : ");
				quiz.Menu01(sc.next(), sc.next());
				continue;
			}
			case 2: {//2 : 영단어 입력 받고 그의 뜻을 출력. 없으면 "미등록 단어" 출력  (containsKey("apple")) 
				
				System.out.println("찾을 영어 단어 입력 : ");
				quiz.Menu02(sc.next());
				
				continue;
			}
			case 3: {//3 : 모든 단어 보기 ,for문 사용 
				
				quiz.Menu03();
				continue;
			}
			case 4: {
				//4 : (선택문제) 
				//문제 : 뜻   / 답 : 영단어  
				//예) 사과(은)는 영어로? ==> 'home' 입력 ==> 땡!
				//문제는 랜덤하게 나와야 함. Map --> List 나 array 로 변경해야 함
				quiz.Menu04();
				continue;
				
			}
			case 0: {
				break loop;
			}
			
			
		}
		
		
		
		
		}
		
	}

}

```
