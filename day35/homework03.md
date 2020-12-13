```java
package day35.homework;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.util.Scanner;


public class homework01 {
	
	Scanner sc = new Scanner(System.in);
	Connection connection = null;
	PreparedStatement preparedStatement=null;
	
	String name;
	int level;
	int ap;
	int hp;

	homework01() {
		
		String url = "jdbc:mysql://127.0.0.1/testdb"; 
		String id = "testdba";
		String password = "test1234";
		String sql = "INSERT INTO pokemon(name, level, ap, hp) VALUES(?, ?, ?, ?)";	

		Connection connection = null;
		PreparedStatement preparedStatement = null;
		
		try {
			Class.forName("com.mysql.jdbc.Driver");
			connection = DriverManager.getConnection(url, id, password);
			preparedStatement = connection.prepareStatement(sql);

			System.out.println("새 포켓몬 이름 , 레벨 입력 :");
			name = sc.next();
			level = sc.nextInt();	
			ap = (int) (level * 0.5);
			hp = level * 100;
			
			
			preparedStatement.setString(1, name);
			preparedStatement.setInt(2, level);
			preparedStatement.setInt(3, hp);
			preparedStatement.setInt(4, ap);
			preparedStatement.executeUpdate();
			System.out.println("저장!");
			
			
			

		}catch (Exception e) {
			e.printStackTrace();
		} finally {
			try {
				
				if(preparedStatement != null)
					preparedStatement.close();
				if(connection != null)
					connection.close();
				
			} catch(Exception e) {
				e.printStackTrace();
			}
		}
		
		
		
	}
	
	
	public static void main(String[] args) {
		
			new homework01();
			
	
	
	}

}
```
