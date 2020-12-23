```java
package chat;

import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.io.PrintWriter;
import java.net.Socket;
import java.net.UnknownHostException;
import java.nio.charset.StandardCharsets;
import java.util.Scanner;

class ClientReadThread extends Thread{
	Socket socket;
	private BufferedReader br;
	
	ClientReadThread(Socket socket) throws IOException{
		this.socket = socket;
		br = new BufferedReader(new InputStreamReader(socket.getInputStream()));
	}
	@Override
	public void run() {
		try {

			String input;
			while(true) {
				input = br.readLine(); 
				System.out.println("Server: " + input);
			}
			
		} catch (IOException e) {
			e.printStackTrace();
		}		
	}
}

class ClientWriteThread extends Thread{
	Socket socket;
	PrintWriter bw;
	
	public ClientWriteThread(Socket socket) throws IOException{	
		this.socket = socket;
		bw = new PrintWriter(new OutputStreamWriter(socket.getOutputStream(), "UTF8"), true);	
	}
	@Override
	public void run() {
		String input;
		Scanner sc = new Scanner(System.in);
		
		try {
			while(true) {
			input = sc.nextLine();
//			System.out.println("나>> "+input);
			bw.println(input);
			bw.flush();
			}
		} catch (Exception e) {
			e.printStackTrace();
		}
	}
}

public class Client {

	public static void main(String[] args) {

		try {
			Socket socket = new Socket("127.0.0.1",50000);	
			
			//new Client(socket);
			ClientReadThread thread = new ClientReadThread(socket);
			thread.start();
			
			ClientWriteThread thread2 = new ClientWriteThread(socket);
			thread2.start();
			
		} catch (Exception e) {

			e.printStackTrace();
		}

	}

}

```
