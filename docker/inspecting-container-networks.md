# WIP

I've been on a real self-hosting kick lately and wanted to get a better understanding of how container networking works under the hood. 

When you spin up a container, Docker creates a virtual ethernet adapter (a veth, for short). A veth is the software version of a physical ethernet cable. 

When using the default `bridge` network driver, one end of the "cable" is connected to the container. 
The other end of the cable is connected to the bridge adapter. All containers connected to the same bridge adapter
can communicate with each other via this bridge.

You can list existing bridge adapters using the `bridge` utility[^1] from the iproute2 package:

```
bridge vlan list
```

[^1]: A lot of places on the internet still reference the [deprecated](https://man.archlinux.org/man/brctl.8#NOTES) `brctl` tool

Resources
* https://wiki.archlinux.org/title/Network_bridge
* https://learn-docker.it-sziget.hu/en/latest/pages/advanced/kernel-namespaces-network.html#:~:text=The%20%E2%80%9Cnsenter%E2%80%9D%20(namespace%20enter,has%20the%20process%20ID%20%24pid%20.&text=We%20have%20to%20get%20the,process%20running%20inside%20a%20container.
