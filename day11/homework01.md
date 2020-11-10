```java
package day11.quiz;

public class FunctionFactory {
	/* strGugudan()
	 *  인자값 : 정수 1개 
	 *  하는 일 : 해당 구구단 1개의 문자열로 만들기 
	 *  리턴값 : 구구단 문자열 ("2 X 1 = 2 \n2 X 2 = 4 \n2 X 3 = 6\n...")
	 */
	
	String strGugudan(int a) {

		return (a+"X 1 = "+a*1+"\n"
				+a+"X 2 = "+a*2+"\n"
				+a+"X 3 = "+a*3+"\n"
				+a+"X 4 = "+a*4+"\n"
				+a+"X 5 = "+a*5+"\n"
				+a+"X 6 = "+a*6+"\n"
				+a+"X 7 = "+a*7+"\n"
				+a+"X 8 = "+a*8+"\n"
				+a+"X 9 = "+a*9);
		
		
	}
		/* getAverage()
		 *  인자값 : 국, 영, 수
		 *  하는 일 : 국, 영, 수 평균 계산
		 *  리턴값 : 평균값
		 */
		void getAverage(int kor, int eng, int math) {
			
			int avg = (kor + eng + math) / 3;
			
			return;	
		}
		
		 /* getRandomPokemon()
		 *  인자값 : X
		 *  하는 일 : "피카츄", "라이츄", "파이리", "꼬부기" 중 1개의 포켓몬을 랜덤으로 뽑기
		 *  		(Math.random() 사용)
		 *  리턴값 : 뽑힌 포켓몬 이름 
		 */
		String getRandomPokemon() {
			
			String array[] = {"피카츄", "라이츄", "파이리", "꼬부기"};
			
			int randomIndex = (int)(Math.random()*array.length);
			
			return array[randomIndex];
			
			
		}
		
		/* getMax()
		 *  인자값 : int형 배열 1개 
		 *  하는 일 : 이 배열의 원소 중 가장 큰 수 찾기
		 *  리턴값 : 가장 큰 수
		 */
		
		int getMax(int arr[]) {
			
			int b=0;
			for(int i = 0; i<arr.length; i++) {
				
				if(b < arr[i])
					b = arr[i];
				
			}
			return b;
		}
		
		
		
		
		
		
		
	
}
```
