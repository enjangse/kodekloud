kke_lab_linux-passwordless-ssh

The system admins team of xFusionCorp Industries has set up some scripts on jump host that run on regular intervals and perform operations on all app servers in Stratos Datacenter. To make these scripts work properly we need to make sure thor user on jump host has password-less SSH access to all app servers through their respective sudo users. Based on the requirements, perform the following:


Set up a password-less authentication from user thor on jump host to all app servers through their respective sudo users.


ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDBlKF7wRHLVOlMWJBQ60blEHChL2m0oN9d3C0OeiCY0HqYrFE/oes+vs/tCvsov2TFcdDCFrwhCLEv5BnucnvDKeiz+rXJD/t40oDZh4/M917xWVmGsXTE19/OTTyCOkWEOL7HmCSa1mAlh4LhB09YJDact4EbyRO7rFy+AQS7G7HSUshd4RxSNgRcGZyYlu2ieH2s/Kstv5Fk6fV6RiSjjAjnejk3iYa7/zFMXa3bA1RiwbxceBTrl632Eyx+b0FOOZn3G9xlvEdYnLfCeS/1WPLp33VNaptNonBlNxC/4RxXbyOBHHziUEzv3jTk7bIF5sHY3Uz9WkmlfeVXRuct thor@jump_host.stratos.xfusioncorp.com
]For #All
🔥Learn Ethical Hacking, Python, Web Development and more with these 9 FREE courses!🔥
Links to register are below👇🏾

▪️ Ethical Hacking https://lnkd.in/d7P92f7
▪️ Python Hacking https://lnkd.in/dUwmUpm
▪️ Python 3 Course https://lnkd.in/d5c48mP
▪️ Front-End Web Dev https://lnkd.in/ds8F9sT
▪️ Full-Stack JavaScript https://lnkd.in/dAjddRe
▪️ Linux for Absolute Beginners https://lnkd.in/dJGF-YH
▪️ Python https://lnkd.in/dKh9855
▪️ Coding Browser Extensions https://lnkd.in/dUbDMDH
▪️ Complete Ethical Hacking https://lnkd.in/dsHzGAm




thor@jump_host /$ ssh-keygen -t rsa
Generating public/private rsa key pair.Enter file in which to save the key (/home/thor/.ssh/id_rsa):
Created directory '/home/thor/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/thor/.ssh/id_rsa.
Your public key has been saved in /home/thor/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:nwqn5IPxfza9CzOFPKJ5aupQRe31u8G1ncid489aBaM thor@jump_host.stratos.xfusioncorp.com
The key's randomart image is:
+---[RSA 2048]----+
|      ..         |
|     .  . .      |
|      .. . .  o  |
|     .  .. ....o |
|    .   S +.Eooo+|
|   ..  o o ++o.=o||  .  += o *. o. o|
|   ..o+* .++o  + |
|   .oo+ooo .oo..+|
+----[SHA256]-----+



n/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now itis to install the new keys
thor@172.16.238.11's password:

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh 'thor@172.16.238.11'"
and check to make sure that only the key(s) you wanted were added.



thor@jump_host /$ ssh thor@172.16.238.12
Last login: Sun Jan  3 15:56:59 2021
[thor@stapp03 ~]$ sudo su
[root@stapp03 thor]# exit
exit
[thor@stapp03 ~]$ exit
logout
Connection to 172.16.238.12 closed.
