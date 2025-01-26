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

   
. In you domain host records the below changes must be applied.  
![GodaddyHost records](https://github.com/user-attachments/assets/b402ef49-0256-4626-b8ce-268554e7f633)

