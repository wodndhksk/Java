```java
package day23.homework;

import java.util.HashMap;
import java.util.Scanner;
import java.util.TreeMap;

//step 1. 다음 학생들의 정보를 Map 에 저장하세요. (TreeMap<Integer,HashMap<String,Object>>)
//key 는 학번(Integer)입니다.
//
//주의) Student 클래스를 사용하지 않고 학생 정보도 Map을 사용합니다. 
//{
//	101 : {"name":"홍길동", "average":88, "grade":"B", "contact":"010-2222-1231"},
//	102 : {"name":"김길동", "average":92, "grade":"A", "contact":"010-2231-1256"},
//	103 : {"name":"김장미", "average":47, "grade":"F", "contact":"010-2512-7754"},
//	...
//}
//학번          이름      평균      등급      연락처
//101         홍길동      88       B        010-2222-1231
//102         김길동      92       A        010-2231-1256
//103         김장미      47       F        010-2512-7754
//201         장아름      85       B        010-9966-3512
//202         최영수      74       C        010-1111-3864


public class Test02 {
	
	public static HashMap<String, Object> makeHashMapStudentInfo(String name, int average, String grade, String contact) {
		HashMap<String ,Object> hashmap = new HashMap<>();
		hashmap.put("name", "홍길동");
		hashmap.put("average", 88);
		hashmap.put("grade","B");
		hashmap.put("contact","010-2222-1231");
		
		return hashmap;
	}

	public static void main(String[] args) {
	
		TreeMap<Integer, HashMap<String, Object>> treemap;
		
		HashMap<String, Object> hashmap1 = new HashMap<>();
		HashMap<String, Object> hashmap2 = new HashMap<>();
		HashMap<String, Object> hashmap3 = new HashMap<>();
		

		int firstGrade = 101;
		int secondGrade = 201;
		int thirdGrade = 301;
		int fourthGrade = 401;

		
//		101 : {"name":"홍길동", "average":88, "grade":"B", "contact":"010-2222-1231"},
//		102 : {"name":"김길동", "average":92, "grade":"A", "contact":"010-2231-1256"},
//		103 : {"name":"김장미", "average":47, "grade":"F", "contact":"010-2512-7754"},

		treemap = new TreeMap<>();
		treemap.put(firstGrade++, makeHashMapStudentInfo("홍길동", 88, "B", "010-222-1231" ));
		treemap.put(firstGrade++, makeHashMapStudentInfo("김길동", 92, "A", "010-2231-1256" ));
		treemap.put(firstGrade++, makeHashMapStudentInfo("김장미", 47, "F", "010-2512-7754" ));
		
			
		Scanner sc = new Scanner(System.in);
		
		int kor, eng, math, grade;
		int avg;
		String tel , name;
		String testscore = "";
		
		HashMap<String, Object> hashmap4 = new HashMap<>();
		
			for(int i = 0; i <3; i++) {
				
				System.out.println("이름, 국,영,수,학년,전화번호 입력 : ");
				name = sc.next();
				kor = sc.nextInt();
				eng = sc.nextInt();
				math = sc.nextInt();
				grade = sc.nextInt();
				tel = sc.next();    
				
				avg = (kor+eng+math)/3;
				
				if(avg >= 90) {
					testscore = "A";
				}
				else if(avg >=80) {
					testscore = "B";
				}
				else if(avg >=70) {
					testscore = "C";
				}
				else if(avg >= 60){
					testscore = "D";
				}
				else if(avg <60) {
					testscore = "F";
				}
				
				
				
				
				
				if(grade ==4) {
					treemap.put(fourthGrade++,  makeHashMapStudentInfo(name, avg, testscore, tel ));		
				}
				else if(grade ==3) {
					treemap.put(thirdGrade++, makeHashMapStudentInfo(name, avg, testscore, tel ));		
				}
				else if(grade ==2) {
					treemap.put(secondGrade++, makeHashMapStudentInfo(name, avg, testscore, tel ));		
				}
				else if(grade ==1) {
					treemap.put(firstGrade++, makeHashMapStudentInfo(name, avg, testscore, tel ));		
				}
			
			}
			System.out.println(treemap);
		

	}

	

}
```
