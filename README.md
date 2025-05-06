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

**Part 2**
- 1: open an additional terminal window and enter cd /root/.set command. After this enter ls -l to view the directory and see the payload.exe file created in part 1 through SET
- 2: Then enter this command "zip /var/www/html/acctupd.zip payload.exe". This command zips the payload.exe into a file located in the roor directory of the Apachezweb server. Zips ensures that the file doesnt contain sub-directories and the zip file essentially sures the file reaches client as many client systems will stip or block aatachments and downloads that are executable.
- 3: Enter service apache2 start and this command will essentially start the pre-installed Apache webserver on kali. Using this terminal start SET agian using setoolkit.
- 4: Enter 1 to select the Socail Engineering Attack menue iteam. Enter 5 to select the Mass Mailer attack (You could instead choose option 1 to tailor a more targetted attack but this requires gathering more OSINT data to create an effective social engineering attack). Enter yes when prompted "start sendmail (yes/no)"
- 5: Enter 1 and select Email Attack Single Email Address and then enter 2 to select One-time use Email Template.
- 6: Now we will configure an email. Enter h to send this email in HTML format and follow the steps below:

Type in the first line of text of the email: Please download, extract, and run the update file from this link:<BR>

Second line of text of the email: <A HREF=http:// target IP address/acctupd.zip>Update</A><BR> and press enter

third line of text of the email: Otherwise, your certs will automatically expire!<BR> and press enter

fourth line of text of the email: Sincerely,<BR>Support Department and press enter 

Type: END in all caps on the Next line of the body: to finish. Then, press ENTER. Then enter the targets emial for the prompt send email to. 

Enter 2 to select own server or open relay. Then enter the spoofed email address you have created for the prompt from address

Enter Support Department as the From name.

-7: Enter y to flag the email as a high priority. Then enter n regarding adding an attachment and finally enter n regarding adding an inline attachment. SET will attempt to send the email to the targeted client victim. If successful, you should see the message:   SET has finished sending the emails Press <return> to continue  and Press ENTER and  you will be returned to the SET Social-Engineering Attacks menu.( Note you must use the virtual keyboard to press enter).
-8: Return to the original terminal used for part 1

**Note**: Normally you will require extra lines of text to make the phishing email appear more legitimate, and this may include a social media section in which fake accounts are created to trick the target and a disclaimer section stating legal repercussions associated with unlawfully distributing and accessing the email. Additionally, hackers frequently utilise minor name misspellings to deceive targets into thinking a message is from a trustworthy source.  In order to fool the receiver into thinking the attack email is from a trustworthy source, attackers frequently fake the From address.

**Part 3**
the target will then open their mail service and see email sent by you in their mail box called Important Account Update. Assume the victim is fooled by the message into thinking this is a legitimate communication they will lick the link and a emial scam alert message will be displayed. They will then lick yes and a Microsoft Edge browser should open, and the file will be downloaded. Once the payload is downloaded and run a reverse shell will be established betwwwn you and the victim system.


### Disclaimer

This project is intended solely for educational and research purposes. The techniques and methodologies described herein are designed to enhance cybersecurity awareness and ethical hacking practices. Under no circumstances should they be used for unauthorised or malicious activities.

Phishing and other forms of deceptive cyber tactics are illegal and punishable under various cybersecurity and criminal laws worldwide. The author of this repository bears no responsibility for any misuse, illegal activity, or consequences arising from the implementation of any information provided here.

By accessing and utilising this repository, you agree to use the content responsibly and within legal boundaries. If you have any doubts about compliance with applicable laws, seek professional legal advice.



