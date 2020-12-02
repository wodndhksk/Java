```java
package day27.quiz;

import java.io.FileWriter;
import java.io.IOException;
import java.text.SimpleDateFormat;
import java.util.Calendar;
import java.util.Scanner;

import javax.swing.JOptionPane;

//* Quiz03
//* -> 사용자에게 exit를 입력 받을 때까지 모든 문자열을 jop으로 입력 받고 
//* 		exit를 입력하면 YYYMMDD_HHmmss.txt 형식으로 log 파일을 생성하여 
//* 		사용자가 입력한 모든 문자열 저장 
//*/
public class Quiz03 {

	public static void main(String[] args) {
		SimpleDateFormat date = new SimpleDateFormat();
		
		Calendar time = Calendar.getInstance();
		String today_time = date.format(time.getTime());
		
		Scanner sc = new Scanner(System.in);
		
		FileWriter writer = null;
		
		
		try {
		
				writer = new FileWriter(today_time+".txt");
				
				while(true) {
					String str = JOptionPane.showInputDialog("문자열 입력 : " );
					writer.append(str);
					if(str.contains("exit")) {
						break;
					}
				}
				
				
			} catch (IOException e) {
					
				e.printStackTrace();
			}
			finally {
				
				try {
					
					if(null != writer)
						writer.close();
					
				} catch (IOException e) {
			
					e.printStackTrace();
				}
			}
		
				
			
	
		
		
		

	}

}

```
