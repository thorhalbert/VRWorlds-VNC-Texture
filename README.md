## Fork from cfloutier/Unity-VNC-Client

# VRWorlds - VNC Client to Texture

The intention is to add a VRWorlds service to be able to connect to a VNC service that ultimately will be tunneled over a GRPC stream.
This is done to maximize security, since it will expose a vnc server on a Kubernetes cluster (running some application -- terminal, visual studio code, even theoretically an RDP client such as remmina or similar to connect to a windows server).

This is one of several services that will be added to the VRWorlds browser, along with keyboards and such.   I'm starting with VNC since we already have the pieces for a remote frame-buffer system (rather than having to do my own, though ultimately this will be necessary).

I will write a shim which connects to the service on the kubernetes pod and rather than exposing the VNC socket, will expose a properly secured GRPC endpoint.  It's much harder to route a non-HTTP port out of kubernetes.   Likely this will not use the existing VNC authentication, though I can probably deal with that since I have access to the whole VNC stack here in this code.  Also will handle autoreconnect.   I will still let the client connect to conventional VNC ports if they're routable via the browser's machine.   The GPRC network is entirely virtual and exposed via a world or entity server.   I wish I did have something more like an RCP or CITRIX type protocol so I could expose separate windows.    I would love to have an actually x11 client in unity or something like https://spice-space.org/.  Maybe someday.

I will be adding virtual VR mouse and keyboard (and physical passthrough).   Sound might also be possible via a separate socket (I don't think that the VNC protocol includes sound).

I am ultimately trying to build a 3d UI environment so I can actually do my work in VR (or in flat 3d -- VRWorlds should also be able to work in FPS style on a regular display), or someday in AR.

My thanks to cfloutier for the original effort.

I started with https://github.com/saccadic/Unity-VNC-Client, but not sure if the projects are related.


 



