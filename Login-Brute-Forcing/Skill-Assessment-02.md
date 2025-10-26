Welcome Hackers, 

Once again, I am back with another blog and this time we are completing what we started 

Lets see what we are dealing with first and what information we have

So far: we know a name --> `satwoosh`

First, since we don't have any other information on the target lets try to get information by service scanning

```
sudo nmap -sS -sV -T4 <ip_address> -Pn -n --disable-arp-ping 
```
![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/Login-Brute-Forcing/assets/skill-assessment2image/2.png)

From This scan we can see the running service.

Though there are lot of services running but what peeked my interest the ssh service

Lets try to connect to this service using ssh utility

But as we try to connect to the target via ssh, we get blown with an input for password. 

And, as we dont' have the password but the username lets try to bruteforce the password

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/Login-Brute-Forcing/assets/skill-assessment2image/3.png)
![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/Login-Brute-Forcing/assets/skill-assessment2image/4.png)

WOOSH!! Found the password

```
satwoosh:password1
```

Quick, lets connect with these credentials to the target via ssh

As, you try to connect to target via ssh and default port it will throw error, so try with the port that given by htb

```
ssh satwoosh@<ipaddresss> -p <portgivenbyhtb>
```

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/Login-Brute-Forcing/assets/skill-assessment2image/5.png)

There, we now in target's system. Let's find the username 

As we hop around try to explore we will come across a file name incident.txt and we look into the contents

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/Login-Brute-Forcing/assets/skill-assessment2image/6.png)


We will a name Thomas Smith. Looks like our user for the ftp. But its a fullname doesn't look like username. 

But maybe we can guess his username. Lets create a custom username wordlist using his fullname using username-anarchy

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/Login-Brute-Forcing/assets/skill-assessment2image/7.png)

After that we will launch the hydra and brute force the password for ftp service

```
hydra -L /home/ThomasSmith.txt -P /home/Common-Credentials/2023-200_most_used_passwords.txt -V 127.0.0.1 ftp -f
```
After the scan we will find the username and password for the ftp. Try loginn 

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/Login-Brute-Forcing/assets/skill-assessment2image/8.png)

After Loggin, Look for the flag.txt file

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/Login-Brute-Forcing/assets/skill-assessment2image/8.1.png)

export the file to local machine and Open it.

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/Login-Brute-Forcing/assets/skill-assessment2image/9.png)

Congratulations Hacker!! Yet another win. 


`See you in the Next module`


