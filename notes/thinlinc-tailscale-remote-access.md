# thinlinc with tailscale #
### **remote access to my home machine with Thinlinc through Tailscale from external network...**

- I am trying to gain remote access from my laptop to my home machine via Thinlinc through Tailscale.
It works fine on local network. But when I move to an external network,
I can’t access my home machine using Thinlinc. SSH works fine and I have accessed my machine via SSH just fine

___

- Note that ThinLinc connections are a two-step process.
First the client establishes a connection to the ssh address you state in the connection form.
But once connected, the ThinLinc server replies with the address where the client should actually connect to.
In a simple setup this is the address the ThinLinc server itself thinks it has.
So it is important to make them match up.
___
> #*/vsmagent/master_hostname*# >

==This parameter specifies the hostname of the master machine==

i.e. the machine that runs the VSM server.
In a HA setup, this should be the hostname of the IP address
that is on the machine that is currently the active node,
to ensure that services on the agents that need to access
the VSM Server always connects to the machine that is up and running.


1. open the terminal (master machine) and go from root to directory *conf.d*

##
    cd //opt/thinlinc/etc/conf.d

2. edit file: *vsmagent.hconf*

##
    sudo nano vsmagent.hconf


3. - edit "master_hostname" with ip adress (master machine) from tailscale *

   - edit "allowed_clients" with ip adress (client machine) from tailscale **

   - edit "agent_hostname" with ip adress (master machine) from tailscale ***


> #The host that runs the VSM server (master machine)#
>
> <mark>master_hostname=*</mark>


> #Only allow connections from the VSM servers in this space-separated list.
> localhost, hostname, IP and master_hostname are always allowed. NOTE: Do not
> change this parameter unless you know what you are doing.#
>
> <mark>allowed_clients=**</mark>


> #Public hostname; the hostname that clients are redirected to. If not
> defined, the agent will use the computer's IP address.#
>
> <mark>agent_hostname=***</mark>

4. restart service vsmagent

##
    systemctl restart vsmagent
___


* https://www.cendio.com/resources/docs/tag/config_vsmserver.html#std-server-config-folder-vsmserver

- https://www.cendio.com/resources/docs/tag/man/tl-config.1.html
- https://community.thinlinc.com/t/thinlinc-and-tailscale/644/2

+ https://www.cendio.com/thinlinc/docs/install/simple-nat/
___

last update thinlinc.md - 2025-05-03
