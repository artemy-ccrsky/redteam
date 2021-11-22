# Nmap Recon
Getting more details ```--reason```, ```-v```, ```-vv```
Debugging details: ```-d```, ```-dd```

Port Scan Type 	Example Command
TCP Null Scan 	```sudo nmap -sN 10.10.141.92```
TCP FIN Scan 	```sudo nmap -sF 10.10.141.92```
TCP Xmas Scan 	```sudo nmap -sX 10.10.141.92```
TCP Maimon Scan 	````sudo nmap -sM 10.10.141.92```
TCP ACK Scan 	```sudo nmap -sA 10.10.141.92```
TCP Window Scan 	```sudo nmap -sW 10.10.141.92```
Custom TCP Scan 	```sudo nmap --scanflags URGACKPSHRSTSYNFIN 10.10.141.92```
Spoofed Source IP 	```sudo nmap -S SPOOFED_IP 10.10.141.92```
Spoofed MAC Address 	```--spoof-mac SPOOFED_MAC```
Decoy Scan 	```nmap -D DECOY_IP,ME 10.10.141.92```
Idle (Zombie) ```Scan 	sudo nmap -sI ZOMBIE_IP 10.10.141.92```
Fragment IP data into 8 bytes 	```-f```
Fragment IP data into 16 bytes 	```-ff```

## Spoofing and Decoys:
```nmap -S SPOOFED_IP MACHINE_IP```

In brief, scanning with a spoofed IP address is three steps:

    1. Attacker sends a packet with a spoofed source IP address to the target machine.
    2. Target machine replies to the spoofed IP address as the destination.
    3. Attacker captures the replies to figure out open ports.

You can launch a decoy scan by specifying a specific or random IP address after -D. For example, ```nmap -D 10.10.0.1,10.10.0.2,ME 10.10.27.241``` will make the scan of 10.10.27.241 appear as coming from the IP addresses 10.10.0.1, 10.10.0.2, and then ME to indicate that your IP address should appear in the third order. Another example command would be 

Wi-fi:
```nmap --spoof-mac```

## Fragmented packets:
Nmap provides the option ```-f``` to fragment packets. Once chosen, the IP data will be divided into 8 bytes or less. Adding another -f (-f -f or -ff) will split the data into 16 byte-fragments instead of 8. You can change the default value by using the --mtu; however, you should always choose a multiple of 8.

On the other hand, if you prefer to increase the size of your packets to make them look innocuous, you can use the option ```--data-length NUM```, where num specifies the number of bytes you want to append to your packets

## Idle/Zombie scan:

```nmap -sI ZOMBIE_IP 10.10.27.241```
