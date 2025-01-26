# Websitehosting
Website hosting with Linode Ubuntu image running Apache2

Hello everyone. I have created this how to for educational purposes. This is a simple how to for
Hosting your own website.  There is also some info in here regarding configuring an SSL certificate. 
I have also included detailed information on editing config files for both http and https in order to
default to a maintenance page which will load when disabling your default index page.

1. Create an account on Linode.com and proceed to setup the below Ubuntu server.
![Linode Ubuntu](https://github.com/user-attachments/assets/af481ade-2210-4825-b774-406ff41e7046)

2. Login to your Linode box using ssh Yourusername@yourip

3. run apt update && upgrade -y
Note the -y will auto answer yes to any prompts

4. run sudo reboot after updates complete.
  as a side note the Lish Console will show you real time when the box is rebooting.
![linoderebootLish](https://github.com/user-attachments/assets/3b9983e9-afd9-4f65-8ba8-6d6666357eaa)

5. In you domain host A records the below changes must be applied. Update the IP address to the IP of your Linode server.
![GodaddyHost records](https://github.com/user-attachments/assets/b402ef49-0256-4626-b8ce-268554e7f633)

6. Log back into your Linode box via ssh.  ssh username@ipaddress

7. cd /Etc

8. edit the hosts file.  nano hosts  (Enter IP address 127.0.1.1 and your domain name) ctrl O to write. ctrl x to exit
![hostsfile](https://github.com/user-attachments/assets/f3a68670-3ee8-400b-8010-cc3c256c7e5f)

9. in the same directory edit the hostname file and add your domain name. nano hostname ctrl O to write. ctrl x to exit
![hostnamefile](https://github.com/user-attachments/assets/d2eff3c9-dd6d-46f5-8a3a-285e369fdeb8)

10. We will now create a user and add the user to the sudo group. Adduser "yourusername" sudo (Do not use quotes)

11. Switch to the new user. su "username"

12. Disable root access via ssh.

sudo nano /etc/ssh/sshd_config
scroll down and remove "yes" from "Permit root login" Type "No"  (write the file ctrl O ctrl x)
![SShd_config](https://github.com/user-attachments/assets/4ad0f460-8d6d-40e2-b7b2-6f0a3f05f979)

13. Restart Daemon. sudo systemctl restart sshd

(NOTE)  IF SERVICE NOT FOUND USE sudo systemctl -l --type service --all | grep ssh
this will show all the services running labeled ssh
![sudosystemctlrestartsSSHD](https://github.com/user-attachments/assets/ccda5621-f19b-4a92-b85d-3fbe71697d0a)



15. 

16. 

17. 

18. 

19.

20.

21.



 

