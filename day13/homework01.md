#Pokemon
```java
package day13.quiz;

import java.util.Scanner;

public class Pokemon {
	private String name;
	private int level;
	private int hp;
	private int ap;
	
	void setPokemon(String name, int level , int hp, int ap){
		
		this.name = name;
		this.level = level;
		this.hp = hp;
		this.ap = ap;
		
	}
	
	// 생성자 
	Pokemon(String name, int level) {
		setInfo(name, level);
	}
	Pokemon(String name) {
		this.name = name;
	}
	
	// setInfo()
//	인자값 : 이름, 레벨
//	하는 일 : 인자로 들어온 값들을 멤버변수 name, level 에 모두 저장 
//		체력은 레벨의 1000배
//		공격력은 레벨의 1.5배 (20% 확률로 2배)
//	리턴값 : X
	void setInfo(String name, int level) {
		this.name = name;
		this.level = level;
		reset();
	}
	
	// getInfo()
//	인자값 : X
//	하는 일 : "XXX / Lv. @@ / HP. ####" 형태로 name, level, hp 의 값들을 하나의 문자열로 표현
//	리턴값 : "XXX / Lv. @@ / HP. ####" 형태의 문자열
	String getInfo() {
		return name + 
				" / Lv. " + level + 
				" / HP. " + hp + 
				" / AP. " + ap;
	}
	
	// levelUp()
//	인자값 : X
//	하는 일 : level을 1증가
//	리턴값 : 증가된 level
	int setLevelUp() {
		++level;
		reset();
		return level;
	}
	
	String getLevelUp(){
		return "레벨업! 결과 : " + setLevelUp();
		
	}
	
	// + 추가 메서드 : 레벨 기반으로 hp, ap 리셋
	void reset(){
		this.hp = this.level * 1000;
		this.ap = (int)(this.level * ( Math.random() < 0.8 ? 1.5 : 2));
	}
	
	
	// isAlive()
//	인자값 : X
//	하는 일 : 객체의 생사여부 확인( 체력이 0 이하면 죽음 )
//	리턴값 : 살아있으면 true, 아니면 false
	boolean isAlive() {
		return hp > 0;
	}
	
	// attack()
//	인자값 : 적 포켓몬 객체 (Pokemon형)
//	하는 일 : 상대 포켓몬의 체력을 이 객체의 공격력만큼 감소
//		10% 확률로 치명타 (공격력 X 1.5배)
//	리턴값 : 없음
	void setAttack(Pokemon enemy) {
		enemy.hp -= Math.random() < 0.1 ? ap * 1.5 : ap;
		
	}
    String getAttack(){
		
		return "의 남은 체력 : " + hp;
	}
    
 
	
}


```
#Pokemon main
```java
package day13.quiz;

import java.util.Scanner;

public class PokemonMain {
	public static void main(String[] args) {
		Pokemon p1 = new Pokemon("피카츄");
		Pokemon p2 = new Pokemon("라이츄", 100);
		
		System.out.println(p1.getInfo());
		System.out.println(p2.getInfo());
		
		Scanner sc = new Scanner(System.in);
		System.out.print("이름, 레벨 : ");
		
		String name = sc.next();
		int level = sc.nextInt();
		
		p1.setInfo(name, level);
		
		//p1.name = sc.next();
		//p1.level = sc.nextInt();
		//  ==> p1.hp, p1.ap 도 따로 수정해줘야 함! 
		
		
		System.out.println("수정 후 p1 : " + p1.getInfo());
		
		System.out.println("p1의 "+p1.getLevelUp());//System.out.println("p1의 레벨업! 결과 : " + p1.getLevelUp());
		System.out.println("p2의 "+p2.getLevelUp());//System.out.println("p2의 레벨업! 결과 : " + p2.getLevelUp());
	
		System.out.println("레벨 업 후 p1 : " + p1.getInfo());
		System.out.println("레벨 업 후 p2 : " + p2.getInfo());
		
		p1.setAttack(p2);
		
		System.out.println("p2"+p2.getAttack()); //System.out.println("p1의 공격 후 p2의 남은 체력 : " + p2.getAttack());
		
	}
}

```


#Student
```java
package day13.quiz;

import java.util.Scanner;


//day12 에 했던 
//Pokemon, Student 의 
//모든 필드를 private 으로 바꾸고 
//getter, setter 메서드들을 만들기 
//-> Main 클래스에서 getter, setter 호출 연습

class Student{
	private String name;
	private int kor, eng, math, avg;
	
	void setData(String n, int k, int e, int m ){ ////
		
		name = n;
		kor = k;
		eng = e;
		math = m;
		
					
	}
	
	
	int setMean(int k,int e,int m){
		
		avg = (k+e+m) / 3;
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
	 
	 String getData() {
		 return this.name + "\t국어: " + this.kor + "\t영어: " + this.eng + "\t수학: " +this.math + "\t등급: " + setGrade();
	 }
	
	 //printData() : 객체의 모든 정보(이름, 국, 영, 수, 평균, 등급)를 sysout
	
	 void getprintData() {
		 
		 System.out.println(getData());
	 }
	 
	 
	 void setInput() {
		 
		 	Scanner sc = new Scanner(System.in);
		 	
			int k,e,m,a;
			String n;
			
		 	n = sc.next();
			k = sc.nextInt();
			e = sc.nextInt();
			m = sc.nextInt();
			a = setMean(k,e,m);
			
			setData(n, k, e, m);
	 }
	 
	 void getInput() {
		 
			System.out.println("이름과 국어, 영어, 수학, 점수를 입력하세요 :");		

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
	
	




public class Test01 {

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
		
		//Scanner sc = new Scanner(System.in);
		
		
		 for(int i = 0; i < arr.length; ++i) {
			 	s.getInput();
			 	s.setInput();
			 	
				all[i] = s.getData();
				
			}
		
		
		for(int i = 0; i < arr.length; ++i)
			System.out.println(all[i]);
		
		
	}

}
```
