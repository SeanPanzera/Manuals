## To set up the VNC Server...
1. [Login to the remote machine.](#Login-via-SSH.)
2. [Bridge the required ports locally.](#You-must-them-bridge-the-gap.)
3. [Check and start the `vncserver`.](#Then-turn-the-TV-on.)
4. [Use a VNC viewer.](#Then-start-the-viewer.)

<br>

## 1. Login via SSH.
Login to the remote computer to view using `ssh`.
```
ssh sean@panzera.casa
```

You may have to specify a port by appending the `-p` flag.
```
ssh sean@panzera.pro -p 44
```
<br>

## 2. You must then bridge the gap.
On your local computer, bridge the ports required by `vncserver` using `ssh`.
```
ssh -L 59000:localhost:5901 -C -N -l sean panzera.casa
```

In the previous command, the `-L` flag denotes the beginning of the port mapping syntax. Here, we're binding `local-port:host:remote-port`
<br>
> The `-C` flag says to compress all data.
<br>
> The `-N` flag specifies that this input is *not* a remote command.
<br>
> The `-l` flag specifies the username on the remote host.

<br>

## 3. Then turn the TV on.
To see the display on the remote computer from our local environment, we need to access its *X window system*. To accomplish this, we'll use a program on our local machine called `vncserver`; a wrapper to launch an X window system server for Virtual Network Control. 
<br><br>
First, see if there's any `vncserver` screens already running with:
```
vncserver -list
```
You can kill any old or idle screens using: 
```
vncserver -kill :*
```
This will remove **all** screens. You can also enter a process ID instead of `*` to specify the screen you'd like to kill.

<br>

## Then start the viewer.
Assuming we're operating remotely on a Microsoft Windows installation, we can use a program like *TightVNCViewer* to view our desktop environment. It will also bind our peripherals, allowing us to locally operate the remote computer in all familiar aspects.

```
⊞ + tight (return)
```
You will then be prompted to enter a username and password. I'm not sure where those are defined, but I'd like to document it.

