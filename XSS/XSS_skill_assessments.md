Hello Hackers!!

Today we are doing XSS-Skill-Assessment 

Let's fire up our machine and visit the page But first lets go through the steps that are given to us and keep that in mind while proceeding.
![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/XSS/assets/00.png)

After visiting the website, we will see Welcomme to security blog text and a search bar. 

![alt-text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/XSS/assets/00-0.png)

Lets try to expoilt this search. See what we can do with this input field.

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/XSS/assets/02.png)

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/XSS/assets/03.png)

Upon trying several times with different payloads we got nothing.
![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/XSS/assets/04.png)

Seems like WAF is doing its working + The code is doing input validation and sanitization before injecting the user input in code. Lets try to find another way

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/XSS/assets/05.png)

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/XSS/assets/06.png)

Upon doing some hoping from one hyperlink to another we come across this blog comment section for user to post review. We can use this to exploit the web application and possibly it can be a stored XSS vulnerablility
![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/XSS/assets/07.png)

Lets start a test to see how it handeled the data

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/XSS/assets/08.png)

Aha we can see that the request has to accepted or reviewed by admin. Means we have no idea how the input gonna be handled. But that's doesn't mean we can't exploit it.

Let's do this.

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/XSS/assets/09.png)

Let's write a simple XSS payload that will send a GET request to my ip. On top of that we gonna start a php server to recieve the request and also to handled the data sent to us by our payload 

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/XSS/assets/10.png)

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/XSS/assets/11.png)

Nice, we got the GEt request from URL parameter now we can craft a specific paylaod that will send a GET request to our server. The GET request will call a resource that will execute another payload will infiltrate the back-end server and send the cookies of anyone visit the website.

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/XSS/assets/12.png)

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/XSS/assets/13.png)

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/XSS/assets/14.png)

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/XSS/assets/15.png)

Nice, we got them guys!! Good work

![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/XSS/assets/16.png)

There, the final flag. 
![alt text](https://github.com/Parveen-Rawat/HTB_Write-ups/blob/main/XSS/assets/final.png)

Good Work Today Hacker!!

See in next module

            - Sh2d0w

