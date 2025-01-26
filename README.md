# Websitehosting
Website hosting with Linode Ubuntu image running Apache2

Hello everyone. I have created this document for educational purposes. This is a simple procedure for
Hosting your own website. There is also some info in here regarding configuring an SSL certificate. 
I will also be including a detailed text file with information on editing config files to allow a 
maintenance.html page to default and load automatically using the "ReWriteRule" when disabling your default index.html
for updates or editing and updating purposes of your website.

1. Create an account on Linode.com and proceed to setup the below Ubuntu server.
![Linode Ubuntu](https://github.com/user-attachments/assets/af481ade-2210-4825-b774-406ff41e7046)

2. Login to your Linode box using ssh Yourusername@yourip

3. run apt update && upgrade -y
Note the -y will auto answer yes to any prompts

4. run sudo reboot after updates complete.
  as a side note the Lish Console will show you real time when the box is rebooting.
![linoderebootLish](https://github.com/user-attachments/assets/3b9983e9-afd9-4f65-8ba8-6d6666357eaa)

5. In your domain host A records the below changes must be applied. Update the IP address to the IP of your Linode server.
In my case I used godaddy but you should be able to make these changes on whatever domain company you used.
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

14. reboot (Note this will reload the kernal)

15. install apache. sudo apt install apache2 apache2-doc apache2-utils

16. check if apache running.  systemctl status apache2
![APacheStatus](https://github.com/user-attachments/assets/6195ccf0-a0d7-4b8f-a636-4ea0f3860e78)

17. Open browser and go to your linode box's IP

18. Disable default site. we will disable the defaultsite as the configuration is not adequate or configured properly.
    we will create our own site and setup the directories.
    sudo a2dissite 000-default.conf

19. Activate new config. sudo systemctl reload apache2

20. firewall configuration.  we will make some changes to the firewall.

sudo ufw applist.  This will list available applications for the firewall.
![showfirewallapplist](https://github.com/user-attachments/assets/2d89e322-3ae5-48ab-aaec-200c48c9a07a)

21. We will now configure and enable and update the firewall rules

sudo ufw allow 'Apache full'

sudo allow OpenSSH

sudo ufw enable

sudo ufw status

![UFWallowApacheFull](https://github.com/user-attachments/assets/7ea2fd35-2fdf-4c17-a089-1b284ac34fdc)

22. We will now create the directories for the website
    cd /var/www/html

    sudo mkdir "websitename.com"

    cd "websitename.com"

    sudo mkdir "public_html"

    sudo mkdir "log"

    sudo mkdir "backups"

22. cd /etc/apache2
    go to "sites-available" directory

    (we will make a new .conf file)
    sudo nano "websitename.com.conf"

    You need to paste the information in this file into your new config file.

    the file is available to copy and paste in the Maintenance_ConfigFile_Changes.txt file provided.
    ![newConfigfile](https://github.com/user-attachments/assets/04a3e944-adbe-4309-91fc-da4d49709ec3)

23. Enable the site with following command

    sudo a2ensite "websitename.com"

![enablingsiteaftera2ensite](https://github.com/user-attachments/assets/31747445-e4a1-4b4b-9050-ccae9a412c03)

    




 

