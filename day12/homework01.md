```java
package day12.quiz;

import java.util.Scanner;

/*
 * 클래스 : Student
 *  필드 : 이름, 국, 영, 수, 평균, 등급
 *  메소드 : 
 *    0) 생성자 : 
 *        Student(String name) : name 만 저장 
 *        Student(int k, int e, int m) : name 은 "없음", 국영수는 k, e, m 값을 저장. 평균, 등급도 계산되어 저장
 *        Student(String name, int k, int e, int m) : 이름,국영수는 name, k, e, m 값을 저장. 평균, 등급도 계산되어 저장
 *    1) setData() : 이름, 국, 영, 수를 인자값으로 받아, 해당 필드에 모두 저장
 *    2) setMean() : 객체가 가지고 있는 국, 영, 수를 가지고 평균을 계산하여 평균 필드에 저장
 *    3) setGrade() : 객체가 가지고 있는 평균을 가지고 등급을 저장 
 *       90이상 : A
 *       80이상 ~ 90미만 : B
 *       70이상 ~ 80미만 : C
 *       60이상 ~ 70미만 : D
 *       60미만 : F
 * 	  4) printData() : 객체의 모든 정보(이름, 국, 영, 수, 평균, 등급)를 sysout
 * 
 *  메인 클래스 : Quiz03
 *   4명의 학생 객체를 배열로 선언하고 
 *   반복문을 사용하여 학생들의 이름, 국, 영, 수를 입력 받음
 *   입력이 끝나면 모든 학생의 정보를 출력
 */

class Student{
	String name;
	int kor, eng, math, avg;
	
	void setData(String n, int k, int e, int m){
		
		name = n;
		kor = k;
		eng = e;
		m = math;
					
	}
	int setMean(){
		avg = (kor+eng+math)/3;
		return avg;
	}
	
	 String setGrade(){
		 
		 String a = null;
		if(avg >= 90) {
			a= "A";
		}
		else if(avg >=80) {
			a= "B";
		}
		else if(avg >=70) {
			a= "C";
		}
		else if(avg >=60) {
			a= "D";
		}
		else if(avg < 60){
			a= "F";
		}
		
		return a;
	}
	
	 //printData() : 객체의 모든 정보(이름, 국, 영, 수, 평균, 등급)를 sysout
	
	 String printData() {
		 
		 return (this.name + "\t국어: " + this.kor + "\t영어: " + this.eng + "\t수학: " +this.math + "\t등급: " + setGrade());
		 
	 }
	 
	 
	 
	 
	Student(String name){
		System.out.println(name);
	}
	Student(int k, int e, int m){
		System.out.println(k+" "+e+" "+m);
	}
	Student(String name, int k, int e, int m){
		System.out.println(name+k+e+m);
	}
	
}
	
	




public class Quiz02 {

	public static void main(String[] args) {
		
//		메인 클래스 : Quiz03
//		 *   4명의 학생 객체를 배열로 선언하고 
//		 *   반복문을 사용하여 학생들의 이름, 국, 영, 수를 입력 받음
//		 *   입력이 끝나면 모든 학생의 정보를 출력
		//int k,e,m; String b;
		Student[] arr = new Student[4];
		String[] all = new String[4];
		
		
		Student s = new Student("홍길동 ");
		Student s1 = new Student(10,20,30);
		Student s2 = new Student("피카츄 ", 50, 60 ,70);
		
		Scanner sc = new Scanner(System.in);
		
		for(int i = 0; i < arr.length; ++i) {
			
			System.out.println("이름을 입력하세요 :");
			s.name = sc.next();
			
			
			
			System.out.println("국어 점수 :");
			s.kor = sc.nextInt();
			
			System.out.println("영어 점수 :");
			s.eng = sc.nextInt();
			
			System.out.println("수학 점수 :");
			s.math = sc.nextInt();
			
			s.avg = s.setMean();
			
			System.out.println("학생 정보 ==>" +s.printData()+"\n");
			
			String x  = s.printData();
			all[i] = new String(x);
			
		}
		for(int i = 0; i < arr.length; ++i)
			System.out.println(all[i]);
		
		
	}

}

```


```java
홍길동 
10 20 30
피카츄 506070
이름을 입력하세요 :
aa
국어 점수 :
50
영어 점수 :
50
수학 점수 :
50
학생 정보 ==>aa	국어: 50	영어: 50	수학: 50	등급: F
이름을 입력하세요 :
bb
국어 점수 :
70
영어 점수 :
70
수학 점수 :
70
학생 정보 ==>bb	국어: 70	영어: 70	수학: 70	등급: C
이름을 입력하세요 :
cc
국어 점수 :
80
영어 점수 :
80
수학 점수 :
80
학생 정보 ==>cc	국어: 80	영어: 80	수학: 80	등급: B
이름을 입력하세요 :
d
국어 점수 :
90
영어 점수 :
90
수학 점수 :
90
학생 정보 ==>d	국어: 90	영어: 90	수학: 90	등급: A
aa	국어: 50	영어: 50	수학: 50	등급: F
bb	국어: 70	영어: 70	수학: 70	등급: C
cc	국어: 80	영어: 80	수학: 80	등급: B
d	국어: 90	영어: 90	수학: 90	등급: A
```
