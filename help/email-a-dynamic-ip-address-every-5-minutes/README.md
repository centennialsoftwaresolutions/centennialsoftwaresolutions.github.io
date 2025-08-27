# Email a Dynamic IP Address Every 5 Minutes

![clock_image](clock_image.png)

This post describes how to set up a computer to email its IP address every 5 minutes. It is useful if you are working on a remote machine who's ISP changes their IP address daily, hourly, etc...

This method requires that you have sudo on the machine you want to get the IP address of. It also requires:

-   wget
    
-   Creating a Gmail account
    
-   mail
    
-   https://api.myip.com
    
-   ssmtp
    
-   Ubuntu
    
-   awk
    
-   crontab -e
    
-   vi
    

**Note**: When you see <MAC> replace it with a MAC address of the computer you're getting the ipaddress from. When you see <Your Password> replace it with a password you come up with.

**Getting the IP from the Command Line**

```
wget https://api.myip.com --output-document=/dev/stdout --quiet
```

This command:

...will output this to the command line (a.k.a. to stdout) \*:

```
{"ip":"66.249.75.9","country":"United States","cc":"US"}
```

...each field is defined as \*:

"ip": IP address 

"country": IP country location in English language 

"cc": Two-letter country code in [ISO 3166-1 alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) format

\* This info and the service is provided by [https://www.myip.com/api-docs/](http://www.myip.com/api-docs/). 

**Create an Email Just for This**

1\. Create a Google Account at: [https://accounts.google.com/SignUp ](http://accounts.google.com/SignUp) 

-   Set **First** to: IPAddressOf
    
-   Set **Last** to: <A name for the machine you can remember or the MAC Address (without ':')>
    
-   Type ifconfig to get one of the MAC Addresses.
    
-   Set the **username** to: ipaddressof.<MAC>
    
-   Set **password** to: A password just for this account that you don't use.
    
-   **Birthday**: I set it to the creation date-18 years.
    
-   **Gender**: Rather not say
    
-   Mobile phone: leave blank
    
-   Current email: leave blank
    

2\. Log into the account

**Send a Mail from the Command Line**

1\. Install mail:

```
sudo apt-get update
sudo apt-get install ssmtp
```

2\. Open /etc/ssmtp:

```
sudo vi /etc/ssmtp/ssmtp.conf
```

3\. Append the following:

```
root=ipaddressof.<MAC>@gmail.com
mailhub=smtp.gmail.com:465
rewriteDomain=gmail.com
AuthUser=ipaddressof.<MAC>
AuthPass=<Your Password>
FromLineOverride=YES
```

4\. Test

```
echo "Hello, World!" | ssmtp ipaddressof.f0d5bffbe7b7@gmail.com
```

5\. Check your mail

**Connect the Getting the IP Address and Sending the Mail**

Type:

```
wget https://api.myip.com --output-document=/dev/stdout --quiet | awk -F'"' '{print $4}' | ssmtp ipaddressof.f0d5bffbe7b7@gmail.com
```

Note: There's an extra little bit of text between the wget and the sstp. This pulls just the IP address out. Its there because when I tried to send the output directly to Google I got nothing in the body of the mail. I'm not sure why this is. I'm theorizing that if Google receives a mail who's body just contains a single JSON, it filters it out.

**Have the Computer Run this Command Every 5 Min**

1\. Type these into the computer you're having send the IP address and note down the paths. Use these paths in step 2.

```
which wget;
which awk;
which ssmtp;
```

2\. Type:

```
VISUAL="vi" crontab -e
```

```
*/5 * * * * /usr/bin/wget https://api.myip.com --output-document=/dev/stdout --quiet | /usr/bin/awk -F'"' '{print $4}' | /usr/sbin/ssmtp ipaddressof.@gmail.com
```

After all the '#'s type this:

The \*/5 says: run this command every every 5 minutes.

3\. Now wait 5 minutes and you should start to see emails with the machines IP.

**Reference**

Setup ssmtp

-   [https://askubuntu.com/questions/12917/how-to-send-mail-from-the-command-line](http://askubuntu.com/questions/12917/how-to-send-mail-from-the-command-line)
    
-   [https://unix.stackexchange.com/questions/363814/simplest-way-to-send-one-line-mail-out-via-command-line-using-gmail](http://unix.stackexchange.com/questions/363814/simplest-way-to-send-one-line-mail-out-via-command-line-using-gmail)
    

Setup cron

-   [https://vexxhost.com/resources/tutorials/how-to-use-cron-jobs-for-automation-on-ubuntu-14-04/](http://vexxhost.com/resources/tutorials/how-to-use-cron-jobs-for-automation-on-ubuntu-14-04/)
    
-   https://crontab.guru/every-5-minutes
    

Other Materials Used

-   [https://www.freeformatter.com/html-escape.html](http://www.freeformatter.com/html-escape.html)
    
-   [The clock image](http://kinsta.com/wp-content/uploads/2017/02/wordpress-cron-job.png)