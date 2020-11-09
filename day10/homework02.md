```java
package day09.homework;

import java.util.Scanner;

//사용자에게 배열의 칸 개수를 입력 받고, 해당 정수의 크기만큼 정수형 배열을 생성하세요.
//입력 : 3  ===> 결과 : [ 0, 0, 0 ] 
//입력 : 5  ===> 결과 : [ 0, 0, 0, 0, 0 ] 


//하-4 : (3)번에서 생성된 배열에 다음 기능을 추가하세요.
//	ㄱ. 0 ~ n-1 까지의 숫자를 배열에 순서대로 저장하세요.
//		입력 : 3  ===> 결과 : [0, 1, 2]
//		입력 : 5  ===> 결과 : [0, 1, 2, 3, 4]

public class Test02 {
	
	public static void main(String[] args) {
		int num;
		
		
		Scanner sc = new Scanner(System.in);
		
		System.out.println("칸 개수를 입력 : ");
		num = sc.nextInt();
		
		int arr[] = new int[num];
		
		
		for(int i = 0; i < arr.length; ++i)
			System.out.println("[" + i + "] 째 배열" + arr[i]);
		
		
		int b;
		
		for(int i = 0; i< arr.length; ++i) {
			
			System.out.println("["+i+"] 번째 배열 입력 : ");
			b = sc.nextInt();
			arr[i] = b;
		}
		
		for(int i = 0; i<arr.length; i++)
			System.out.println("[" + i + "] 째 배열 : " + arr[i]);
	
	
		
		
		
		
		
	
	}	
 
}
```
