```java
package day14.homework;

public class Tourist {
	
	 private String name;
	 static private String destination;
	 private int budget;
	 private int age;
	 
	 
	 void setInfo(String name, int age, int budget ){
		 
		 this.name = name;
		 this.age = age;
		 this.budget = budget;
		 
		 
	 }
	 String getInfo() {
		 
		 return "이름 : " + name + ", 나이 : "  + age; 
	 }
	 
	 void setName(String name) {
		 this.name = name;
		 
	 }
	 
	 String getName() {
		 return name;
	 }
	 
	 void setAge(int age) {
		 this.age = age;
	 }
	 
	 int getAge() {
		 return age;
	 }
	 // destination
	 static void setDestination(String destination) {
		 Tourist.destination = destination;
	 }
	 
	 static String getDestination() {
		 return destination;
	 }
	 
	 //budget
	 void setBudget(int budget) {
		  this.budget = budget;
	 }
	 
	 int getBudget() {
		 
		 return budget;
	 }
	 

}

```
#main
```java
package day14.homework;

import java.util.Scanner;

public class Quiz01 {

	public static void main(String[] args) {
		
		
		//String destination;
		
		Scanner sc = new Scanner(System.in);
		
		
		Tourist t1 = new Tourist();
		Tourist arr[] = new Tourist[5];
		
		for(int i = 0; i<arr.length; i++) { //Exception in thread "main" java.lang.NullPointerException
			arr[i] = new Tourist();
		}
		
		
		
		
// 		메뉴에서 해당 숫자 입력시 나오는 각 결과들 설정 
//				1. 목적지 설정
//		 * 		2. 여행객 추가 
//		 * 		3. 모든 여행객 정보 보기
//		 * 		4. 전체 예산 보기
//		 * 		5. VIP 조회 
//		 * 		0. 종료 
		boolean start = true;
		int b = 0;
		while(start) {
			
			//메뉴 호출과 원하는 숫자 입력하기;
			int btn;
			System.out.println( "1. 목적지 설정 \n2. 여행객 추가 \n3. 모든 여행객 정보 보기 \n4. 전체 예산 보기 \n5. VIP 조회 \n0. 종료 ");
			btn = sc.nextInt();
			
		switch (btn) {
		
		case 1: {
			System.out.println("목적지를 입력하세요. ");
			 Tourist.setDestination(sc.next());
			 System.out.println(Tourist.getDestination());
			
			 break;
		}
		//2. 여행객 추가 
		case 2: {
			
			if(b >= arr.length) {
				System.out.println("회원 정보가 가득 찼습니다!");
				
				break;
			}
			
			System.out.println("이름과 나이, 예산을 입력하세요 : ");	
			
				String name = sc.next(); 
		
				int age = sc.nextInt();
				
				int budget = sc.nextInt();		
				
				arr[b].setName(name);
				arr[b].setAge(age);
				arr[b].setBudget(budget);
				
			//}
				b += 1;
				
			
			break;
		}
		//3. 모든 여행객 정보 보기
		case 3: {
			for(int i = 0; i < arr.length; ++i) {
				System.out.print(arr[i].getInfo());
				
				System.out.println(" , 목적지 : " + Tourist.getDestination());
			}
			break;
		}
		//4. 전체 예산 보기
		case 4: {
			int total = 0;
			for(int i = 0; i< arr.length; ++i) {
				
				int a = arr[i].getBudget() ; 
				total += a;
				
			}
			System.out.println("전체 예산 : " + total);
			System.out.println();
	
			break;
		}
		//5. VIP 조회 
		case 5: {
			int max = 0;
			String info = "";
			for(int i =0; i<arr.length; ++i) {
				
				
				if(max < arr[i].getBudget()) {
					
					max = arr[i].getBudget();
					info = arr[i].getInfo();
				}
				
							
			}
			System.out.println("VIP 정보 ==> " + info  +", 예산 : "+ max);
	
			break;
		}
		//0. 종료 
		case 0 :
			System.out.println("종료되었습니다 .");
			start = false;
			
			break;
		}
		
		
	}//while 
		
		

	}

}
```
