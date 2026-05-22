# VLANS
In this lab, I am going to be creating virtual local area networks

**So we have a network with seven different PCs. PCs 1-2 are in vlan 10 and connected to switch one. PCs 3-4 are in vlan 30 and connected to switch one. PC 5 is in vlan 20 and connected to switch two. PCs 6-7 are in vlan 10 and connected to switch two. Switch one is connected to switch two and switch two in connected to router one** 

Initially, we can see tha PC 7 in vlan 10 connected to switch two is unable to ping PC 3 in vlan 30 connected to switch one:

<img width="531" height="176" alt="image" src="https://github.com/user-attachments/assets/a31ccbb6-517b-4ce2-b20f-77a4e7b6206c" />

So, in order to resolve this, we will make some cofigurations to ensure that the different PCs are able to communicate with each other.

Firstly, we are going to ensure that the switch ports connected to each PC is in the correct vlan and the switchport mode is access.  We also have to ensure that all three vlans exist on both switches:

<img width="522" height="230" alt="image" src="https://github.com/user-attachments/assets/db3121d2-7110-48a3-beef-39e616f70fa3" />

<img width="528" height="227" alt="image" src="https://github.com/user-attachments/assets/81709046-1461-4421-9c60-f302755f5111" />

Next, we have to ensure that the connection between switch one and switch two is configured as a trunk and allows the vlans to pass through:

<img width="758" height="207" alt="image" src="https://github.com/user-attachments/assets/939d4478-be86-4815-80d1-2b3db763ea62" />

<img width="516" height="120" alt="image" src="https://github.com/user-attachments/assets/c4a6218c-958c-49ec-9091-a5a439ece482" />

Now, we have to ensure that the connection between switch two and router one has been configured as **router-on-a-stick** by ensuring that the interface on router one connected to switch two is divided into sub-interfaces and not in a shutdown state:

<img width="817" height="447" alt="image" src="https://github.com/user-attachments/assets/2221eb9a-4ab7-4656-98e8-9012c4c2615f" />


We also have to ensure that the interface on switch two that is connected to router one is configured as a trunk and the created vlans are allowed:

<img width="777" height="222" alt="image" src="https://github.com/user-attachments/assets/d6761e7b-db6c-4f3a-8fa8-320564abf647" />


Lastly, we have to ensure that the sub-interfaces on router one are configured with the default gateway of the respective vlans we want to assign them to:

<img width="517" height="162" alt="image" src="https://github.com/user-attachments/assets/de80eec5-1994-46d9-9dc7-d6583c608439" />

Now, I am able to ping PC3 in vlan 30 through PC7 in vlan 10:

<img width="492" height="210" alt="image" src="https://github.com/user-attachments/assets/f6d03ce4-5282-4416-8c4a-df401c8f58c3" />

