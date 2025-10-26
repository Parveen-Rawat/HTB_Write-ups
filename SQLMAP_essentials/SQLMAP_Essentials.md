Hello Hacker! 

Let's complete this skill-assessment and get that flag.

First things first, let boot up our machine and get the ip.

Upon visiting the ip in browser we come across a page looking like this:

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/SQLMAP_essentials/assets/1.png)

Looks like simple web application for shopping. Let's fire up Burp-Suite to really see what is going on under the hood.

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/SQLMAP_essentials/assets/2.png)

Switch the intercept proxy on. Start going crazy with the web application request. click on anything and everything that can send a potential request to the back-end server

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/SQLMAP_essentials/assets/3.png)

Upon a several tries we will finally come across a request `/action.php` which looks like sending a POST request to the backend to retrieve the product via id. On top of that id syntax appears to be in javascript language. 

Keep that in mind. `Hacker!` It might come in handy.

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/SQLMAP_essentials/assets/4.png)

Lets import that request as a file and name it whatever you like. `Just make sure to remember it.`

Fire up the sqlmap and before starting blasting the commands like a rifle. Lets take down the target with sniper shoots

Take and use some flags and see the output to conduct our research upon it and counter the WAF with a KO punch

Lets start with the command:

```
sqlmap -r <filename>.txt --batch --dump
```

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/SQLMAP_essentials/assets/5.png)

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/SQLMAP_essentials/assets/6.png)

Upon analysing the results and error, we can notice that `<` is getting filtered by back-end server probably a WAF deed. Lets try to evade or bypass it using the tamper switch

```
sqlmap -r <filename>.txt --batch --dump --tamper=between
```

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/SQLMAP_essentials/assets/7.png)

Now we now what database and in what table the flag is in. Lets retrieve it.

```
sqlmap -r <filename>.txt --batch --dump -D production -T final_flag --tamper=between
```

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/SQLMAP_essentials/assets/8.png)

WOOOSH!!! Crack the code and dump the load 

`Great work hacker!!`

See in next module.

