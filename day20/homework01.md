# D-day 
```java
package day20.homework;

import java.util.Calendar;
import java.util.Scanner;

// 1. 디데이 계산기를 만드세요.
// 시작년월일 입력 --> 목표 년월일 입력 ---> D-Day XX!!! 


public class Test01 {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		//int year, month, day;
		
		Calendar startDay = Calendar.getInstance(); // 현재 지금 이 순간!// 싱글톤 
		Calendar  endDay = Calendar.getInstance();
		

		System.out.println("시작 년도 ,달 , 일 입력 : ");
		startDay.set(sc.nextInt(), sc.nextInt(), sc.nextInt());
		
		System.out.println("d-day 년도 ,달 , 일 입력 : ");
		endDay.set(sc.nextInt(), sc.nextInt(), sc.nextInt());
		
		long total_StartDay = startDay.getTimeInMillis()/(24*60*60*1000);
		long total_EndDay = endDay.getTimeInMillis()/(24*60*60*1000);
		
		
//		System.out.println(startDay.getTimeInMillis()/(24*60*60*1000));
//		System.out.println(endDay.getTimeInMillis()/(24*60*60*1000));
		System.out.println("D-day 까지 "+(total_EndDay - total_StartDay)+"일 남았습니다. ");
			

	}
}


```
# Calendar
```java
package day20.homework;

import java.util.Calendar;
import java.util.Scanner;

//	2. 년, 월을 입력 받고 해당 월을 달력형태로 출력하세요. (토요일마다 줄바꿈이 일어나도록)
//
//	2020 10
//	일	월	화	수	목	금	토
//					1	2	3
//	4	5	6	7	8	9	10
//	11	12	13	14	15	16	17
//	18	19	20	21	22	23	24
//	25	26	27	28	29	30	31 
public class Test02 {

	public static void main(String[] args) {
		
		Scanner sc = new Scanner(System.in);
		Calendar cal = Calendar.getInstance();
		
		System.out.println("년도 입력 :");
		int year = sc.nextInt();
		
		System.out.println("달 입력 :");
		int month = sc.nextInt();
		
		cal.set(Calendar.YEAR, year);
		cal.set(Calendar.MONTH, month); //Calendar.MONTH 는 '0' 이 1월 (0~11)
		
		cal.set(year, month-1, 1); //year/ month 는 0 이 1월이기 때문에 -1 /date
		
		int dayOfWeek = cal.get(Calendar.DAY_OF_WEEK); // 1 -> 일 , 2 -> 월, 3 -> 화, 4 -> 수, 5 -> 목, 6 -> 금, 7 -> 토 
		int lastDay = cal.getActualMaximum(Calendar.DATE);
		
		System.out.println(year + "  " + month);
//		System.out.println(Calendar.YEAR);
//		System.out.println(Calendar.MONTH);
		
		System.out.println("일  월  화 수  목 금  토");
		
		for(int i = 1; i <= lastDay; i++) {
			
			if(i == 1) {
				
				for(int j=1; j <dayOfWeek; j++)
					System.out.print("   ");
				
			}
			
			if(i < 10) {
				System.out.print("0");
			}
			
			System.out.print(i+" ");
			
			if(dayOfWeek % 7 == 0 ) {
				System.out.println("");
			}
			dayOfWeek++;
		}
	
		
	}

}

```
