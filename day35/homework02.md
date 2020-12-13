
# 2. 사용자에게 조회할 포켓몬의 이름을 입력 받고 해당 포켓몬의 정보를 DB에 조회한 뒤 출력 없으면 '미등록 포켓몬'
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
