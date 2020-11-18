# interface 

```java
package day17.quiz;

public interface Transportation {
	
	int getCharge(int age, int km);

}

class Bus implements Transportation{

	@Override
	public int getCharge(int age, int km) {
		int price = 1000;
		
		
		if(age >= 20) {
			price += (km/10)*100;
		}
		else if(age <20) {
			price *= 0.8;
			
		}
		
		return price;
	}
}
	
class Taxi implements Transportation{

	@Override
	public int getCharge(int age, int km) {
		int price = 4000;
		
		if(km <= 10) {
			return price;
		}
		else if (km > 10) {
			price += (km -10) * 100;
			
		}
		
		return price;
		
	}
	
	
}

class Subway implements Transportation{

	@Override
	public int getCharge(int age, int km) {
		int price=0;
		
		if(age <20) {
			price = 720;
			price +=(km/10)*50;
		}
		else if(age >20) {
			price = 1250;
			price +=(km/10)*100;
		}
						
		return price;
	}
	
}

class Train implements Transportation{

	@Override
	public int getCharge(int age, int km) {
		int price = 1500;
		
		if(age <20) {
			price /= 0.5;
		}
		
		price += (km/30) * 1000;
		
		return price;
	}
	
	
}


	


```
#main

```java
package day17.quiz;

import java.util.Scanner;

public class Quiz01 {

	public static void main(String[] args) {
		int tp;
		int age,km;
		Scanner sc = new Scanner(System.in);
		
		
		System.out.println("1.버스, 2.전철, 3.택시, 4.기차 중 택 1 ");
		tp = sc.nextInt();
		
		System.out.println("나이 입력 : ");
		age = sc.nextInt();
		
		System.out.println("km 입력 : ");
		km = sc.nextInt();
		
		//Transportation 으로 객체 선언 
		Bus bus = new Bus();
		Taxi taxi = new Taxi();
		Subway subway = new Subway();
		Train  train = new Train();
		
		
		switch (tp) {
		
		case 1: {
			
			System.out.println("요금 : " + bus.getCharge(age, km));
			
		}
		case 2: {
			
			System.out.println("요금 : " + taxi.getCharge(age, km));
		}
		case 3: {
			
			System.out.println("요금 : " + subway.getCharge(age, km));
	
		}
		case 4: {
	
			System.out.println("요금 : " + train.getCharge(age, km));
		}
		

		}
		
		

	}

}

```
