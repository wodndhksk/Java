package day09.homework;

public class Test01 {
	

	
	public static void main(String[] args) {
		 //하-1 int형 6칸 짜리 배열을 생성 
		
			int arr[] = new int[6];
		
		 //하-2 : 다음 출력 결과를 예상하세요.
			int[] a = new int[2]; 
			System.out.println(a[0]); // 답 : 0 
			System.out.println(a[1]); // 답 : 0 

			double[] b = new double[2];
			System.out.println(b[0]); // 답 : 0.0 
			System.out.println(b[1]); // 답 : 0.0 

			String[] c = new String[2];
			System.out.println(c[0]); // 답 : null
			System.out.println(c[1]); // 답 : null 


			char[] d = new char[2];
			System.out.println(d[0]); // 답 : ""
			System.out.println(d[1]); // 답 : "" 


			boolean[] e = new boolean[2];
			System.out.println(e[0]); // 답 : false 
			System.out.println(e[1]); // 답 : false

	}

}
