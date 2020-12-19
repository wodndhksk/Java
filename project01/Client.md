```java

package chatting;

import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.io.IOException;
import java.net.Socket;
import java.util.Scanner;

public class Client_s {

	Client_s() throws Exception{
		
		Socket socket = new Socket("127.0.0.1", 50000);
		System.out.println("접속 완료");
		
		 new read_C(socket).start();
         new write_C(socket).start();
		
		
	}
	
	class read_C extends Thread {
	    Socket socket;

	    public read_C(Socket socket) {
	        this.socket = socket;
	    }

	    @Override
	    public void run() {
	        DataInputStream dis = null;
	        try {
	            dis = new DataInputStream(socket.getInputStream());
	            while (true) {
	                
	                // POINT) server가 write 하면 동작한다
	                // readUTF는 상대가 입력하지 않으면 계속 대기한다(스캐너처럼)
	                // while이 쓸데없이 계속 돌지 않는 이유다
	                String msg = dis.readUTF();
	                    System.out.println();
	                    System.out.println("상대방 msg : " + msg);
	                if (msg.equals("exit"))
	                    break;
	            }
	        } catch (Exception e) {
	            e.printStackTrace();
	        } finally {
	            try {
	                dis.close();
	            } catch (IOException e) {
	                e.printStackTrace();
	            }
	        }
	    }

	}
	
	class write_C extends Thread {
	    Socket socket;

	    public write_C(Socket socket) {
	        this.socket = socket;
	    }

	    @Override
	    public void run() {
	        DataOutputStream dos = null;
	        Scanner sc = new Scanner(System.in);
	        try {
	            dos = new DataOutputStream(socket.getOutputStream());

	            while (true) {
	                System.out.print("할 말 : ");
	                String msg = sc.nextLine();

	                dos.writeUTF(msg);

	                if (msg.equals("exit"))
	                    break;
	            }
	        } catch (Exception e) {
	            e.printStackTrace();
	        } finally {
	            try {
	                dos.close();
	            } catch (IOException e) {
	                e.printStackTrace();
	            }
	        }

	    }

	}
	
	public static void main(String[] args) {
		
		try {
			new Client_s();
			
		} catch (Exception e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		
		

	}

}

```
