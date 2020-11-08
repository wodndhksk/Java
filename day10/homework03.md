package day09.homework;

import java.util.Scanner;



//하-5 : 사용자에게 배열의 칸 개수를 입력 받고, 해당 정수의 크기만큼 String형 배열을 생성하고
//입력 : 3  ===> 결과 : [ null, null, null ] 
//입력 : 5  ===> 결과 : [ null, null, null, null, null ]
//
//사용자에게 입력받은 단어들을 순차적으로 배열에 저장하세요. 

public class Test03 {

	public static void main(String[] args) {
		
		Scanner sc = new Scanner(System.in);
		String a;
		
		int num = sc.nextInt();		
		String arr[] = new String[num];
		
		for(int i = 0; i < arr.length; i++) {
			
			System.out.println(arr[i]);
			
			
		}
		
		for(int i=0; i <arr.length; i++) {
			
			System.out.println("["+ i + "] 번째 단어를 입력하세요 :");
			a =sc.next();
			arr[i] = a;
			
			
		}
		
		for(int i = 0; i<arr.length; i++) {
			System.out.println("["+ i + "] 번째 단어 : "+arr[i]);
		}
		
		
		
		
		
		
	}

}
