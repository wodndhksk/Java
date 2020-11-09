```java
package day09.homework;

import java.util.Scanner;

//dates 배열은 다음과 같이 1~12월의 최대 일자가 들어있습니다. 
//==> int[] dates = {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31}; 
//
//1) dates 배열을 활용하여 1/1일부터 사용자에게 입력 받은 월/일 까지 며칠이 소요되는지 출력하세요.
//  단, 사용자에게 해는 따로 입력받지 않기때문에 윤년은 없다고 가정합니다.
//
//	예) 월 : 12   일 : 31  ==> 364일 소요!
//	    월 : 4    일 : 12   ==> 101일
//	원리) 4/12 의 결과를 계산하려면
//	    1 / 1 ~ 1 / 31  => 31 (dates[0]) 
//	    2 / 1 ~ 2 / 28  => 28 (dates[1])
//	    3 / 1 ~ 3 / 31  => 31 (dates[2])
//   	4 / 1 ~ 4 / 12  => 12 (사용자가 입력한 일)
//	 => 31 + 28 + 31 + 12 - 1 = 101일 



//2) 시작월/일과 목표 월/일 을 각각 입력 받고 d-day 계산기를 만드세요.
//단, year는 입력받지 않기때문에 d-day의 최댓값은 364일로 가정합니다.
//예) 시작 : 9/26  목표 : 11/23  ==> 결과 : d-day 58 !!!
//    시작 : 1/1 목표 : 12/31  ==> 결과 : d-day 364 !!!
//    시작 : 12/31 목표 : 1/1  ==> 결과 : d-day 1 !!!
//    시작 : 4/12 목표 : 4/11  ==> 결과 : d-day 364 !!!
//원리)
//	start : 1/1 ~ 시작 월/일까지 며칠이 소요되는지 계산합니다. 
//	end : 1/1 ~ 목표 월/일까지 며칠이 소요되는지 계산합니다. 
//	end-start 를 합니다. 
//	이때 음수가 나온다면 목표일이 시작일보다 앞서있다는 의미입니다. (즉 목표일이 이듬해)
//	이 경우 +365를 하면 됩니다.

public class Test04 {

	
	public static void main(String[] args) {
		
		int[] dates = {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31}; 
		
		int t = 0;
		
		Scanner sc = new Scanner(System.in);
		
		System.out.println("월 : ");
		int month = sc.nextInt();
		
		System.out.println("일 : ");
		int day = sc.nextInt();
		
		
			
			if(month == 1) {
			
				for(int i = 0; i < month-1; i++) {
				
					t += day;
				
				}
			}
			
			for(int i=2; i <dates.length; i++) {
				
				if(month == i) {
					for(int j = 0; j < month-1; j++) {
					
						t += dates[j];
					}
					t +=day-1;
					
				}
			}
			System.out.println(t);
			
			
			int start = 0;
			int end = 0;
			
			System.out.print("시작 월 : ");
			int startMonth = sc.nextInt();
			
			System.out.println("시작 일 : ");
			int startDay = sc.nextInt();
			
			System.out.print("목표 월 : ");
			int endMonth = sc.nextInt();
			
			System.out.println("목표 일 : ");
			int endDay = sc.nextInt();
			
			
			
			if(startMonth == 1) {
				
				for(int i = 0; i < startMonth-1; i++) {
				
					start += startDay;
				
				}
			}
			
			for(int i=2; i <dates.length; i++) {
				
				if(startMonth == i) {
					for(int j = 0; j < startMonth-1; j++) {
					
						start += dates[j];
					}
					start +=startDay-1;
					
				}
			}
			
			
			if(endMonth == 1) {
				
				for(int i = 0; i < endMonth-1; i++) {
				
					end += endDay;
				
				}
			}
			
			for(int i=2; i <dates.length; i++) {
				
				if(endMonth == i) {
					for(int j = 0; j < endMonth-1; j++) {
					
						end += dates[j];
					}
					end += endDay -1;
					
				}
			}
			
			System.out.println("D-day : " + (end - start));
			

	

	}

}
```
