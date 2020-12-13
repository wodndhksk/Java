### 포켓몬의 이름,레벨 입력, DB에 저장
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

### 이름을 입력받고 해당 정보를 DB에 조회한 뒤 출력, 없으면 '미등록'
```java
package day35.homework;

import java.sql.Connection;
import java.sql.Date;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.util.Scanner;


public class homework2 {
	
	private static final String URL = "jdbc:mysql://127.0.0.1/testdb?useUnicode=true&characterEncoding=utf8";
	private static final String ID = "testdba";
	private static final String PASSWORD = "test1234";
	
	private Connection connection;
	private PreparedStatement preparedStatement;
	private ResultSet resultSet;
	Scanner sc;
	
	public homework2() throws SQLException {
		connection = DriverManager.getConnection(URL, ID, PASSWORD);
		preparedStatement = connection.prepareStatement("SELECT * FROM pokemon ");
		resultSet = preparedStatement.executeQuery();
		sc = new Scanner(System.in);
		
		System.out.println("찾으려는 포켓몬 이름 :");
		String pokemonName = sc.next();
		
		int no ,level;
		String name;
		
		
		while(resultSet.next()) {
		
		no = resultSet.getInt("no");
		name = resultSet.getString("name");
		level = resultSet.getInt("level");
		
		if(!name.equals(pokemonName)) {
			
			if(resultSet.next() != false)
				continue;
			else {
				System.out.println("미등록 포켓몬");
			}

		}
		else if(pokemonName.equals(name)) {
			
			System.out.println(no + ". " + name + "/LV." + level /*+ "[" + regdate + "]"*/);
			break;
		}
		
			
			//int level = resultSet.getInt(3);
			// java.sql.Date regdate = resultSet.getDate(6);
			//String regdate = resultSet.getString(6);
			
		}//while
		
			
	}
	
	public static void main(String[] args) {
		try {
			new homework2();
		} catch(Exception e) {e.printStackTrace();}
		
		
	}
}
```
