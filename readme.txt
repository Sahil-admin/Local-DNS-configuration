# Local-DNS-configuration
Local-DNS-configuration_steps

While configuring DNS basically you need to make changes in 3 files along with that create 2 more files.

------------Server Side Configuration--------------
Step 1:
Install bind packages which are the DNS packages.
  yum install bind* -y
Use this command to install them.
{if not configured yum check-out my other repo which explains how to setup yum}

Step 2:
As it is a local dns server make changes to your ethernet files which can be named as "ifcfg-enp0s3" or similar to this.
You can find tis file here /etc/sysconfig/network-scripts
If you want to keep your machine connected to internet make sure you either add one more ip-address to your ehternet or attach a new ethernet-adapter.

Step 3: (use the resolve.conf for refrence)
Edit the "resolve.conf" file according to the file provided here.
Use the ip-address similar to your ip-address as configured in the Step 2.

Step 4: (Use the named.conf file  )
Edit the "named.conf" file according to the file provided here.

Step 5: (Use the named.rpc1912.conf file for refrence)
Edit the "named.rpc1912.conf" according to the file provided here.

Step 6: (Use the forward.zone and reverse.zone for refrence)
Make two files in /var/named as "forward.zone" and "reverse.zone" .
This two files will contain the ip-addresses of the server as well as other machines whose ip need to be added in the dns so that they can be accessed by others,
connected to the network.

Step 7:
Add the named service to firewall, use the below commands to do so,
  firewall-cmd --permanent --add-port=53/tcp
  firewall-cmd --permanent --add-port=53/udp
  firewall-cmd --reload

-------------Client Side Configuration---------------
Step 1:
This step is similar to step 3 which is to be done on client machine.
