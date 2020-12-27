```java
package chat.Sign;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;

public class MemberDAO {

	private static final String URL = "jdbc:mysql://127.0.0.1/testdb?useUnicode=true&characterEncoding=utf8";
	private static final String ID = "testdba";
	private static final String PASSWORD = "test1234";
	
	private Connection connection;
	private PreparedStatement preparedStatement;
	private ResultSet resultSet;
	
	MemberDAO() throws SQLException{
		connection = DriverManager.getConnection(URL, ID, PASSWORD);
		preparedStatement = connection.prepareStatement("SELECT * FROM member");
		resultSet = preparedStatement.executeQuery();
		System.out.println("연결됨");
		
		
		String sql = "INSERT INTO member(id, pwd, name, eamil) VALUES(?,?,?,?)";
		preparedStatement = connection.prepareStatement(sql);
	}
	public static void main(String[] args) {
	
		try {
			new MemberDAO();
		} catch (SQLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
	}

}

```
