# Student class

```java
package day15.homework;
//* 부모 클래스 : Student 
//*  1) 필드 : 학생이름, 나이, 학교명
//*  2) 메소드 :
//*   	ㄱ. 생성자 
//*   		- 디폴트 생성자(기본생성자)
//*   		- 학생이름, 나이, 학교명 3개 넣고 생성되도록 
//*   	ㄴ. getters
//*   	ㄷ. setters
class Student {
	private String studentName;
	private int age;
	private String schoolName;
	Student(){
		
	}
	
	Student(String studnetName, int age ,String schoolName){
		this.studentName = studnetName;
		this.age = age;
		this.schoolName = schoolName;
	}
	
	
	public String getStudentName() {
		
		return studentName;
	}
	
	public void setStudentName(String studentName) {
		this.studentName = studentName;
	}
	
	public int getAge() {
		return age;
	}
	
	public void setAge(int age) {
		this.age = age;
	}
	
	public String getSchoolName() {
		return schoolName;
	}
	
	public void setSchoolName(String schoolName) {
		this.schoolName = schoolName;
	}
	
	

}
```

# ElementaryStudent class

```java
package day15.homework;
//자식 클래스1 : ElementaryStudent
//*  1) 추가할 필드 : 국어점수, 영어점수, 학부모 연락처
//*  2) 메소드 : 
//*   	ㄱ. 생성자 
//*   		- 학생이름, 나이, 학교명
//*   		- 학생이름, 나이, 학교명, 학부모 연락처
//*   		- 학생이름, 나이, 학교명, 국어점수, 영어점수
//*		ㄴ. getters
//*		ㄷ. setters

class ElementaryStudent extends Student{
	
	private int kor;
	private int eng;
	private String parentsNum;
	
	ElementaryStudent(String studentName, int age, String schoolName){
		setStudentName(studentName);
		setAge(age);
		setSchoolName(schoolName);
		
	}
	
	ElementaryStudent(String studentName, int age, String schoolName, String parentsNum){
		setStudentName(studentName);
		setAge(age);
		setSchoolName(schoolName);
		this.parentsNum = parentsNum;
		
	}
	
	ElementaryStudent(String studentName, int age, String schoolName, int kor, int eng){
		setStudentName(studentName);
		setAge(age);
		setSchoolName(schoolName);
		this.kor = kor;
		this.eng = eng;
		
	}
	
	
	public int getKor() {
		return kor;
	}
	
	public void setKor(int kor) {
		this.kor = kor;
	}
	
	public int getEng() {
		return eng;
	}
	
	public void setEng(int eng) {
		this.eng = eng;
	}
	
	public String getParentsNum() {
		return parentsNum;
	}
	
	public void setParentsNum(String parentsNum) {
		this.parentsNum = parentsNum;
	}
	
	
}
```

# MiddleSchoolStudent class

```java
package day15.homework;
//* 자식 클래스2 : MiddleSchoolStudent
//*  1) 추가할 필드 : 국어점수, 영어점수, 수학점수, 평균점수		
//*  2) 메소드 : 
//*  	ㄱ. 생성자 
//*  		- 학생이름, 나이, 학교명, 국어점수, 영어점수, 수학점수
//*  		  (평균 자동 계산)
//*  	ㄴ. getters
//*  	ㄷ. setters
class MiddleSchoolStudent extends Student{
	
	private int kor;
	private int eng;
	private int math;
	private double avg;
	
	MiddleSchoolStudent(String studentName, int age , String schoolName,int kor, int eng, int math){
		
		setStudentName(studentName);
		setAge(age);
		setSchoolName(schoolName);
		this.kor = kor;
		this.eng = eng;
		this.math = math;
		this.avg = (this.kor + this.eng + this.math) / 3.0;
		
	}
	
	
	public int getKor() {
		return kor;
	}
	public void setKor(int kor) {
		this.kor = kor;
	}
	public int getEng() {
		return eng;
	}
	public void setEng(int eng) {
		this.eng = eng;
	}
	public int getMath() {
		return math;
	}
	public void setMath(int math) {
		this.math = math;
	}
	public double getAvg() {
		return avg;
	}
	public void setAvg(int avg) {
		this.avg = avg;
	}
	

}
```

# HighSchoolStudent class

```java
package day15.homework;
//자식 클래스3 : HighSchoolStudent
//*  1) 추가할 필드 : 국어점수, 영어점수, 수학점수, 평균점수, 내신등급	
//*  2) 메소드 : 
//*  	ㄱ. 생성자 
//*  		- 학생이름, 나이, 학교명, 국어점수, 영어점수, 수학점수
//*  		  (평균 자동 계산)
//*  	ㄴ. getters
//*  	ㄷ. setters
public class HighSchoolStudent extends Student {

	private int kor;
	private int eng;
	private int math;
	private double avg;
	private int schoolGrade;
	
	HighSchoolStudent(String studentName, int age, String schoolName, int kor, int eng, int math){
		
		setStudentName(studentName);
		setAge(age);
		setSchoolName(schoolName);
		this.kor = kor;
		this.eng = eng;
		this.math = math;
		this.avg = (this.kor + this.eng + this.eng) / 3.0;
		
		
	}
	
	public int getKor() {
		return kor;
	}
	public void setKor(int kor) {
		this.kor = kor;
	}
	public int getEng() {
		return eng;
	}
	public void setEng(int eng) {
		this.eng = eng;
	}
	public int getMath() {
		return math;
	}
	public void setMath(int math) {
		this.math = math;
	}
	public double getAvg() {
		return avg;
	}
	public void setAvg(double avg) {
		this.avg = avg;
	}
	public int getSchoolGrade() {
		return schoolGrade;
	}
	public void setSchoolGrade(int schoolGrade) {
		this.schoolGrade = schoolGrade;
	}
	
}
```

# main

```java
package day15.homework;

import java.util.Scanner;


//* 메인 클래스 : Quiz02
//*  - 이름과 나이를 입력 받음
//*  - 나이에 따른 객체 생성 (예. 13 -> new ElementaryStudent())
//*  - 각 객체의 필드를 입력 받아서 저장 
//*    예. 중학생이면
//*    	  학교명, 국어점수, 영어점수, 수학점수 입력 받음
//*  - 결과 출력
//*/
public class Quiz02 {

	public static void main(String[] args) {

		String studentName, schoolName;		
		int age, kor,eng,math;
		double avg;
		
		Scanner sc = new Scanner(System.in);
		
		
		System.out.println("이름과 나이를 입력 : ");
		studentName = sc.next();
		age = sc.nextInt();
		
		if(age >=8 && age<=13) {
			System.out.println("학교 이름 입력 : ");
			schoolName = sc.next();
			
			System.out.println("국어 , 영어 점수 입력 : ");
			kor = sc.nextInt();
			eng = sc.nextInt();
			
			ElementaryStudent e = new ElementaryStudent(studentName, age, schoolName, kor, eng);
			System.out.println("학생 이름 : " + e.getStudentName() + ", " +
					"나이 : "+e.getAge() +", "+ 
					"학교 이름 : "+e.getSchoolName() + "초등학교 , "+
					"국어 점수 : "+e.getKor() + "점 , "+
					"영어 점수 : "+e.getEng()+ "점 , ");
					
			
		}
		else if(age >= 14 && age <=16 ) {
			
			
			
			System.out.println("학교 이름 입력 : ");
			schoolName = sc.next();
			
			
			System.out.println("국어, 수학 , 영어 점수 입력 : ");
			kor =sc.nextInt();
			eng = sc.nextInt();
			math =sc.nextInt();
			
			MiddleSchoolStudent m = new MiddleSchoolStudent(studentName, age, schoolName ,kor, eng, math);
		
			
			System.out.println("학생 이름 : " + m.getStudentName() + ", " +
			"나이 : "+m.getAge() +", "+ 
			"학교 이름 : "+m.getSchoolName() + "중학교 , "+
			"국어 점수 : "+m.getKor() + "점 , "+
			"영어 점수 : "+m.getEng()+ "점 , "+
			"수학 점수 : "+m.getMath()+ "점 , "+
			"평균 : "+ m.getAvg()+"점 ");
			
		}
		else if(age >= 17 && age <=19) {
			
			System.out.println("학교 이름 입력 : ");
			schoolName = sc.next();
			
			
			System.out.println("국어, 수학 , 영어 점수 입력 : ");
			kor =sc.nextInt();
			eng = sc.nextInt();
			math =sc.nextInt();
			
			HighSchoolStudent h = new HighSchoolStudent(studentName, age,  schoolName,  kor,  eng,  math);
			
			System.out.println("학생 이름 : " + h.getStudentName() + ", " +
					"나이 : "+h.getAge() +", "+ 
					"학교 이름 : "+h.getSchoolName() + "고등학교 , "+
					"국어 점수 : "+h.getKor() + "점 , "+
					"영어 점수 : "+h.getEng()+ "점 , "+
					"수학 점수 : "+h.getMath()+ "점 , "+
					"평균 : "+ h.getAvg()+"점 ");
		}
		else
			System.out.println(studentName + "님은 초, 중, 고 학생 나이가 아닙니다!");
			

	}

}
```
