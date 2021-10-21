`xfreerdp /v:IP /u:USERNAME /p:'PASSWORD'`
use single quotes for password

Userful xfreerdp flags:

-   `/dynamic-resolution` -- allows us to resize the window, adjusting the resolution of the target in the process
-   `/size:WIDTHxHEIGHT` -- sets a specific size for targets that don't resize automatically with `/dynamic-resolution`
-   `+clipboard` -- enables clipboard support
-   `/drive:LOCAL_DIRECTORY,SHARE_NAME` -- creates a shared drive between the attacking machine and the target. This switch is insanely useful as it allows us to very easily use our toolkit on the remote target, and save any outputs back directly to our own hard drive. In essence, this means that we never actually have to create any files on the target. For example, to share the current directory in a share called `share`, you could use: `/drive:.,share`, with the period (`.`) referring to the current directory

A useful directory to share is the `/usr/share/windows-resources` directory on Kali. This shares most of the Windows tools stockpiled on Kali, including Mimikatz which we will be using next. This would make the full command:  

`xfreerdp /v:IP /u:USERNAME /p:PASSWORD +clipboard /dynamic-resolution /drive:/usr/share/windows-resources,share

