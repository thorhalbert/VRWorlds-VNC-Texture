## Fork from cfloutier/Unity-VNC-Client

# VRWorlds - VNC Client to Texture

The intention is to add a VRWorlds service to be able to connect to a VNC service that ultimately will be tunneled over a GRPC stream.
This is done to maximize security, since it will expose a vnc server on a Kubernetes cluster (running some application -- terminal, visual studio code, even theoretically an RDP client such as remmina or similar to connect to a windows server).

This is one of several services that will be added to the VRWorlds browser, along with keyboards and such.   I'm starting with VNC since we already have the pieces for a remote frame-buffer system (rather than having to do my own, though ultimately this will be necessary).

I will write a shim which connects to the service on the kubernetes pod and rather than exposing the VNC socket, will expose a properly secured GRPC endpoint.   Likely this will not use the existing VNC authentication, though I can probably deal with that since I have access to the whole VNC stack here in this code.   I will still set the client connect to convention VNC ports if they're routable via the browser.   The GPRC network is entirely virtual and exposed via a world or entity server.

My thanks to cfloutier for this effort.

I started with https://github.com/saccadic/Unity-VNC-Client, but not sure if the projects are related.


 



