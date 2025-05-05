# Social-Engineering-Using-SET
### Context
Phishing is a type of social engineering attack in which the attacker poses as a trustworthy source in an attempt to trick the victim into disclosing private information.  Originally involving email-based messages, the idea of phishing as a social engineering approach has expanded to cover any kind of communication channel. In this lab we are using Social Engineering Toolkit (SET) which is a set of tools that can be used to carry out a variety of social engineering attacks including a phishing campaign, credential harvesting, malware creation, and much more.

In this lab SET will be used to create an exploit payload that will initiate a reverse shell from the victim back to the Kali VM. This is also the SET instance that will be the listener to receive the inbound connection from the victim.
 
### Lab Workflow
<u>**Part 1**</u>
- 1: Open setoolkit in the terminal window of Kali linux. The SET functionality can be found under Social Engineering Attacks menue option 1. Then we want to create a payload and listener using option 4.

**Note**: Using SET to develop social engineering attacks, particularly ones that incorporate a reverse shell technique, presents an unanticipated complexity.  The listener can be launched as part of the payload construction option.  However, SET is trapped into waiting for a connection if the listener is launched.  You must recreate the payload in order to launch the listener if you develop the payload but fail to launch it after sending the email to the victim (either as an attachment or via a web server host).  Therefore, you must utilise two instances of SET in order to avoid this dilemma.One will be used to create the payload and launch the listener, and the second will be used to craft and send the phishing email with the payload access link.

- 2: Enter option 2 to select Windows Reverse_TCP Meterpreter. You will then be prompte to enter your target Ip address to set up listener IP adress to the Kali VM IP address. Enter the port number for the listener. The payload will then be generated , and a file will be created and saved as /root/.set/payload.exe
- 3: After a few secounds you will se the following prompt: " Do you want to start the payload and listener now ? (yes/no)" and Enter yes. SET will automatically launch the MFSconcole and start the listening session. You must leave the terminal open and allow it to remain at this following prompt "msf6 exploit (multi/handler)>" .

- **Part 2**
- 1: open an additional terminal window and enter cd /root/.set command. After this enter ls -l to view the directory and see the payload.exe file created in part 1 through SET
- 2: Then enter this command "zip /var/www/html/acctupd.zip payload.exe". This command zips the payload.exe into a file located in the roor directory of the Apachezweb server. Zips ensures that the file doesnt contain sub-directories and the zip file essentially sures the file reaches client as many client systems will stip or block aatachments and downloads that are executable.
- 3: Enter service apache2 start and this command will essentially start the pre-installed Apache webserver on kali. Using this terminal start SET agian using setoolkit.
- 4: Enter 1 to select the Socail Engineering Attack menue iteam. Enter 5 to select the Mass Mailer attack (You could instead choose option 1 to tailor a more targetted attack but this requires gathering more OSINT data to create an effective social engineering attack). Enter yes when prompted "start sendmail (yes/no)"
- 5: Enter 1 and select Email Attack Single Email Address and then enter 2 to select One-time use Email Template.
- 6: Now we will configure an email. Enter h to send this email in HTML format.


work in progress.....
  
