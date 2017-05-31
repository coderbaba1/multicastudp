#MULTICAST CLIENT
import java.io.*;
import java.net.*;

class MulticastClient1
{
final static String Inet_addr = "224.0.0.3";
final static int Port = 8008;
public static void main(String args[])throws UnknownHostException
{
InetAddress address = InetAddress.getByName(Inet_addr);
byte [] buf = new byte[256];
try{
MulticastSocket clientsocket = new MulticastSocket(Port);
clientsocket.joinGroup(address);
while(true)
{
DatagramPacket receivePacket = new DatagramPacket(buf, buf.length);
clientsocket.receive(receivePacket);
String msg = new String(buf, 0, buf.length);
System.out.println("socket receive message" + msg);
Thread.sleep(500);
}
}
catch(Exception e){}
}
}
##MULTICAST SERVER
import java.io.*;
import java.net.*;

class MulticastServer
{
final static String Multicastaddr = "224.0.0.3";
final static int Port = 8008;
public static void main(String args[])throws UnknownHostException
{
InetAddress IPaddress = InetAddress.getByName(Multicastaddr);
try{
	DatagramSocket serversocket = new DatagramSocket();
	int i;
	for(i=0; i<=5; i++)
	{
	String msg = "server send data to client " + i;
	DatagramPacket sendPacket=new DatagramPacket(msg.getBytes(), msg.getBytes().length, IPaddress, Port);
	serversocket.send(sendPacket);
	System.out.println("SERVER SEND PACKET :" + i);
	}
}
catch(Exception e){}
}
}
###MULTICAST CLIENT2
import java.io.*;
import java.net.*;

class MulticastClient2
{
final static String Inet_addr = "224.0.0.3";
final static int Port = 8008;
public static void main(String args[])throws UnknownHostException
{
InetAddress address = InetAddress.getByName(Inet_addr);
byte [] buf = new byte[256];
try{
MulticastSocket clientsocket = new MulticastSocket(Port);
clientsocket.joinGroup(address);
while(true)
{
DatagramPacket receivePacket = new DatagramPacket(buf, buf.length);
clientsocket.receive(receivePacket);
String msg = new String(buf, 0, buf.length);
System.out.println("socket receive message" + msg);
Thread.sleep(1000);
}
}
catch(Exception e){}
}
}
