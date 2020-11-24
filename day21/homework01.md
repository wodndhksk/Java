```java
package day21.homework;

import java.text.DecimalFormat;
import java.util.ArrayList;
import java.util.Scanner;

//< 국가 관리 프로그램 >
//0. Nation 클래스 
//	필드 : 국가명(nation)  수도명(capital)  인구수(population) ==> 모두 private 
//	메서드 : 	
//		Nation() 
//		Nation(국가, 수도)
//		Nation(국가, 수도, 인구수)
//		getter, setter 
//		toString() 오버라이드 
//
//1. ArrayList 객체 생성 (Nation 객체들을 저장할 창고 객체) 
//
//	
//2. 메뉴 띄우기
//	1) 국가 추가   ==> 국가명, 수도명, 인구수 입력 받아 Nation 객체 생성 후 ArrayList에 add()
//	2) 모든 국가 보기	==> 현재 등록된 국가들을 모두 출력 (for문과 Nation.toString() 활용)
//	3) 국가 검색 	==> 국가명을 입력 받고, 해당 국가가 있으면 수도, 인구수 출력
//			    없으면 "미등록 국가"
//		            인구수는 ',' 추가 ( 예) 100,000,000 명 ) 
//	0) 종료 
//
class Nation{
	private String nation;
	private String capital;
	private long population;
	Nation(){
		
	}
	Nation(String nation, String capital){
		this.nation = nation;
		this.capital = capital;
	}
	Nation(String nation, String capital, long population){
		this.nation = nation;
		this.capital = capital;
		this.population = population;
	}
	public String getNation() {
		return nation;
	}
	public void setNation(String nation) {
		this.nation = nation;
	}
	public String getCapital() {
		return capital;
	}
	public void setCapital(String capital) {
		this.capital = capital;
	}
	public Long getPopulation() {
		return population;
	}
	public void setPopulation(long population) {
		this.population = population;
	}
	
	@Override
	public String toString() {
		
		return nation + " ";
	}
	
	
	
}

public class Test01 {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		Nation na = new Nation();
		ArrayList<String> list = new ArrayList<String>();
		
		//2. 메뉴 띄우기
//		1) 국가 추가   ==> 국가명, 수도명, 인구수 입력 받아 Nation 객체 생성 후 ArrayList에 add()
//		2) 모든 국가 보기	==> 현재 등록된 국가들을 모두 출력 (for문과 Nation.toString() 활용)
//		3) 국가 검색 	==> 국가명을 입력 받고, 해당 국가가 있으면 수도, 인구수 출력
//				    없으면 "미등록 국가"
//			            인구수는 ',' 추가 ( 예) 100,000,000 명 ) 
//		0) 종료 
	//
		
		String nation;
		
		while(true) {
			
		
			System.out.println("1. 국가 추가 \n2. 모든 국가 보기 \n3. 국가 검색 \n0. 종료 ");
		
			int num = sc.nextInt();
		
		
			switch (num) {
			case 1: { //1) 국가 추가   ==> 국가명, 수도명, 인구수 입력 받아 Nation 객체 생성 후 ArrayList에 add()
				System.out.println("국가명, 수도명 ,인구수 입력 : ");
				na.setNation(sc.next());
				na.setCapital(sc.next());
				na.setPopulation(sc.nextLong());
			//	Nation na1 = new Nation(sc.next(),sc.next(),sc.next());
				
				list.add(na.getNation());
				
				continue;
			}
			case 2: { // 2) 모든 국가 보기	==> 현재 등록된 국가들을 모두 출력 
			
				if(list.size()>0) {
					for(int i=0; i<list.size(); i++) {
					
						//System.out.println(na.toString());
						System.out.println(list.get(i));
					}
				}
				else {
					System.out.println("국가를 먼저 추가해 주십시오. ");
				}
				
				
				continue;
			}
			case 3: { //3) 국가 검색 	==> 국가명을 입력 받고, 해당 국가가 있으면 수도, 인구수 출력
//			    없으면 "미등록 국가"
//	            인구수는 ',' 추가 ( 예) 100,000,000 명 ) 
				
				nation = sc.next();
				DecimalFormat df = new DecimalFormat("#,###.");
				String fPopulation = df.format(na.getPopulation());
				
				
				if(list.isEmpty()){
					System.out.println("국가를 먼저 추가해 주십시오. ");
				}
				
				for(int i = 0; i<list.size(); i++) {
					
					if(nation.equals(list.get(i))) {
						System.out.println(nation + "의 수도 : " + na.getCapital()+", 인구수 : " + fPopulation);
						
					}
					if(!nation.equals(list.get(i))) {
						System.out.println("미등록 국가 ");
						
					}
					
				
				}//for
				continue;
				
			}
			case 0: {
				break;
	
			}
		

			}//switch
		
		
		break;
		
		}//while
		
		
		
	
		
	}

}
```
