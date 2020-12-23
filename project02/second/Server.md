```java
package chat;

import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.DataInputStream;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.io.PrintWriter;
import java.net.ServerSocket;
import java.net.Socket;
import java.nio.charset.StandardCharsets;
import java.util.ArrayList;

class Thread1 extends Thread {
    Socket socket;

    private ArrayList<Socket> sockets;
    private BufferedReader br;
    
    Thread1(Socket socket, ArrayList<Socket> sockets) throws IOException {
        this.socket = socket;
        this.sockets = sockets;
        br = new BufferedReader(new InputStreamReader(socket.getInputStream()));
    }


    @Override
    public void run() {
        try {
            String input;
            while ((input = br.readLine()) != null) {
                System.out.println("Client: " + input);
                for (Socket eachSocket: sockets) {
                	if(eachSocket.equals(this.socket))
                		continue;
                    PrintWriter pw = new PrintWriter(
                            new OutputStreamWriter(eachSocket.getOutputStream()), true);
                    pw.println(input);
                }
            }

        } catch (IOException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();

        } finally {
            try {
                if (br != null)
                    br.close();
                if (socket.isClosed()) {
                    sockets.remove(socket);
                }
            } catch (Exception e) {
                // TODO Auto-generated catch block
                e.printStackTrace();
            }
        }
    }
}
	

public class Server {
    private ServerSocket serverSocket;
    private ArrayList<Socket> sockets = new ArrayList<>();
    private Socket socket;

    public Server() {
        try {
            serverSocket = new ServerSocket(50000);
            while(true) {
                socket = serverSocket.accept();
                sockets.add(socket);

                System.out.println("소켓과 연결됨!"+ socket.getInetAddress().getHostAddress());

                Thread1 thread1 = new Thread1(socket, sockets);
                thread1.start();
            }
            
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    public static void main(String[] args) {
        new Server();
    }
}

```
