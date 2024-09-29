## How to create a remote server using DigitalOcean

### Downloading an Arch Linux image and uploading it to DigitalOcean
***

> What is an Arch Linux image?

> Why Arch Linux?

A disk image is a static file (meaning that it does not change) that contains the data and structure of a physical disk drive. An Arch Linux image is a file containing everything that an actual computer disk running the Arch Linux operating system would have.

We will be using Arch Linux because it has extensive documentation. It is intended to be customizable, so you can add whatever you need to it yourself.

#### Downloading an Arch Linux image

To use an Arch Linux image, first we have to download one. To download an Arch Linux image, follow these steps:

1. Go to https://gitlab.archlinux.org/archlinux/arch-boxes/-/packages/
2. Under Package Registry, locate and click the most recent **images** folder
![[arch-linux-download-package-registry.png]]
3. Scroll down to the Assets section
![[arch-linux-download-assets.png]]
4. Locate and click an Arch Linux image for which the filename includes "cloudimg" and the extension name is .qcow2
![[arch-linux-download-image-files.png]]

You will be prompted to download the Arch Linux image

6. Click Save
![[arch-linux-download-save-file.png]]

Congratulations, you have successfully downloaded an Arch Linux image. Now, you can move on to the next section: uploading that image to DigitalOcean.

#### Uploading an Arch Linux image to DigitalOcean

To use our Arch Linux image with DigitalOcean's services, we first have to upload it onto DigitalOcean. To upload the Arch Linux image we downloaded in the previous section, follow these steps:

1. Login to your DigitalOcean account
2. Locate and click **Manage**
![[arch-linux-upload-manage.png]]
3. From the dropdown menu, locate and click **Backups & Snapshots**

This will open the Backups & Snapshots page

4. Click **Custom Images**
![[arch-linux-upload-custom.png]]

This will take you to the Custom Images tab

5. Locate and click **Upload Image**
![[arch-linux-upload-upload.png]]

This will open your file directory

6. Locate and select the Arch Linux image you downloaded previously
![[arch-linux-upload-select.png]]
7. Click **Open**
![[arch-linux-upload-open.png]]

This will cause a pop-up window to appear

8. Click **Choose a Distribution**
9. From the dropdown menu, locate and click Arch Linux
![[arch-linux-upload-distribution-arch.png]]
10. Click the third San Francisco datacenter region

> Note: We are choosing this region because it is the datacenter closest to Vancouver

![[arch-linux-upload-datacenter.png]]

> Note: You will be charged when you upload an image

11. At the bottom of the pop-up window, click Upload Image

This will exit the pop-up window

12. Wait for the image to finish uploading
![[arch-linux-upload-pending.png]]

You should now see information on your image under Custom Images

13. Wait for the status of your image to change from Pending to the date it was uploaded
![[arch-linux-upload-done.png]]

Congratulations, you have successfully uploaded your Arch Linux image to DigitalOcean. Now, you can move on to the next section: creating an SSH key pair and adding it to your DigitalOcean account.

#### References

1. DigitalOcean. (n.d.). _Image_. DigitalOcean. Retrieved September 29, 2024, from https://docs.digitalocean.com/glossary/image/#:~:text=Last%20edited%20on%2011%20Mar,to%20run%20a%20containerization%20platform
2. Cloudflare. (n.d.). _Caching static and dynamic content_. Cloudflare. Retrieved September 29, 2024, from https://www.cloudflare.com/learning/cdn/caching-static-and-dynamic-content/#:~:text=Static%20content%20is%20any%20file,of%20this%20kind%20of%20content
3. Arch Linux. (n.d.). _Arch Linux_. ArchWiki. Retrieved September 29, 2024, from https://wiki.archlinux.org/title/Arch_Linux

### Creating an SSH key pair and adding it to your DigitalOcean account
***

> What are SSH keys?

> Why are we using SSH keys?

SSH stands for the Secure Shell protocol, and it is a way of securely sending data over an unsecured network through the use of public key cryptography. In public key cryptography, you have two keys (a pair): one public and one private. Your private key should only be known to you. **These are known as SSH keys**. 

We will be using SSH keys because they are more secure than using a password.

#### Creating an SSH key pair

To create an SSH key pair, follow these steps:

1.  (For Windows users) Create a .ssh directory in your home directory by creating a new folder called .ssh

This folder will be used to store our ssh keys and config files

![[create-ssh-folder.png]]
2. Run the following command in your terminal
> Note: Replace "your-user-name" with your Windows user name

```
`ssh-keygen -t ed25519 -f C:\Users\your-user-name\.ssh\do-key -C "youremail@email.com"`
```
What these commands mean:
- ssh-keygen = a tool that creates SSH key pairs (you should already have this if you are using a MacOS or Windows device)
- -t = type (the type of encryption used for the key)
- -f = filename (specifying the name of the and its location)
- -C = comment (the comment that will be attached to the key)

The command we ran will create two text files in your .ssh directory:
- do-key = your private key
- do-key.pub = your public key (the one you will copy to your server)
![[public-and-private-key-in-ssh-folder.png]]

Congratulations, once you see these two files in your .ssh directory, you can move onto the next step: adding your public key to your DigitalOcean account.

#### Adding your public SSH key to your DigitalOcean account

You must connect your public key to your server on your DigitalOcean account for it to allow you to login to the server using your private key. To add your public key onto DigitalOcean, follow these steps:

1. Copy the contents of your do-key.pub file (the file containing your public key) by running one of the following commands depending on your operating system

For Windows users:

> Note: Replace "your-user-name" with your Windows user name

```
Get-Content C:\Users\your-user-name\.ssh\do-key.pub | Set-Clipboard
```

For MacOS users:

``` 
pbcopy < ~/.ssh/do-key.pub
```

For Linux users:

> Note: This command depends on the system you are using

```
wl-copy < ~/.ssh/do-key.pub
```

2. Go to the DigitalOcean website
3. Locate and click **Settings**
4. Under Settings, click the **Security** tab
5. Locate and click Add SSH Key

A pop-up window will appear

6. Under Public Key, paste your public key in the text box
7. Under Key Name, type the name you want to give your key

> Note: Give your key an appropriate name that will distinguish itself from other keys.
> 
> For example: Name your key "school-linux-2420" if you are creating this key on your school computer

8. Click **Add SSH Key**

Congratulations, you have successfully added a public key to your DigitalOcean account. You can now move onto the next section: creating a Droplet that runs Arch Linux and connecting to it using SSH.

#### References

1. Cloudflare. (n.d.). _What is SSH?_. Cloudflare. Retrieved September 29, 2024, from https://www.cloudflare.com/learning/access-management/what-is-ssh/
2. SSH Academy. (n.d.). _SSH keygen_. SSH Academy. Retrieved September 29, 2024, from https://www.ssh.com/academy/ssh/keygen
3. DigitalOcean. (n.d.). _Add SSH keys_. DigitalOcean. Retrieved September 29, 2024, from https://docs.digitalocean.com/products/droplets/how-to/add-ssh-keys/

### Creating a Droplet that runs Arch Linux with automated initial set-up tasks (cloud-init)
***

> What is a Droplet?

A Droplet is a virtual machine (VM) that lives on servers owned by DigitalOcean that uses a Linux-based operating system. For our purposes, we will be running Arch Linux on our Droplet. The server we create will live in this VM.

> What is a cloud-init?

Cloud-init is a package that contains the tools used to initialize (setup) cloud instances, or in our case, servers, automatically. It does this by using YAML-formatted configuration files (files that contain human-readable instructions), the most common of which being cloud-config files. When a server starts, cloud-init will read and execute the instructions written in YAML file(s). 

Instead of creating 100 servers and manually changing each of them to have the same configurations, we can have those 100 servers all have the settings we want them to have right from the beginning by using a cloud-config file. This can save us a lot of time, and it also reduces the chances of human error.


To create an Arch Linux Droplet with automated initial set-up tasks on DigitalOcean, follow these steps:

> Note: You must complete the previous instructions sections for this section to work because we will be using the Arch Linux image and SSH keys we made earlier

1. Log into your DigitalOcean account
2. At the top of the screen, locate and click the **Create** button

A dropdown menu will appear

3. Click **Droplets**

> Note: For steps 4-6, you are choosing options that match with the choices we made when uploading the Arch Linux image. We are trying to choose the location closest to Vancouver.

4. Under Region, choose **San Francisco**
5. Click **San Francisco - Datacenter 1 - SFO1**
![[choose-datacenter.png]]

A dropdown menu will appear

6. Click **San Francisco - Datacenter 1 - SFO3
7. Under Choose an image, click **Custom images**

This will take you to the Custom images tab

8. Click the Arch Linux image you downloaded previously
9. Under Size, select the following options:
	- Droplet Type: Basic
	- CPU options (pick either one): 
		- With Premium Intel selected, $8 per month
		- With Premium AMD selected, $7 per month

> Note: Be careful not to create a Droplet using a CPU option that is out of your budget

10. Under Choose Authentication Method, ensure that the SSH key is selected
11. Under Choose your SSH keys, select the SSH key you created previously
![[choose-ssh-key.png]]

12. Locate and click **Advanced Options**
![[advanced-options.png]]

This will expand the menu

13. Select **Add Initialization scripts (free)**
![[add-initialization scripts.png]]

14. Copy the following code. This is your cloud-config file:
>Note: 
>- Replace "your-user-name" with the name you want to give your user (we are naming ours "fish")
>- Replace "your-public-key" with the contents of the public key you made earlier

>Note: You can find the contents of your public key by going into the terminal and running the following command:
>
> - Replace "your-user-name" with your Windows user name

```
Get-Content C:\Users\your-user-name\.ssh\do-key.pub | Set-Clipboard
```

```
#cloud-config
users:
  - name: your-user-name
    primary_group: your-user-name
    groups: wheel
    shell: /bin/bash
    sudo: ['ALL=(ALL) NOPASSWD:ALL']
    ssh-authorized-keys:
      - your-public-key
packages:
  - ripgrep
  - rsync
  - neovim
  - fd
  - less
  - man-db
  - bash-completion
  - tmux
disable_root: true
```

15. In the text box, paste the contents of the the cloud-config file
![[paste-config-file-contents.png]]

16. Under Hostname, type the name you want to give your host

> Note: Choose a simple, memorable, and school-appropriate name. This is the name that will appear in the terminal when you are connected to your server.
> 
> For example: Name your host "pond"

17. Click **Create Droplet**

You should now see a Droplet in your project folder
![[created-droplet-pond.png]]

18. Copy the IP address listed next to the name of your Droplet (this will be used in the next section)

Congratulations, you have created your first Arch Linux droplet. Now you can move onto the next step: connecting to that Droplet using SSH.

#### References

1. Cloud-Init. (n.d.). _Introduction_. Cloud-Init. Retrieved September 29, 2024, from https://docs.cloud-init.io/en/latest/explanation/introduction.html
2. YAML. (n.d.). _YAML_. YAML. Retrieved September 29, 2024, from https://yaml.org/
3. Arch Linux. (n.d.). _Cloud-init_. ArchWiki. Retrieved September 29, 2024, from https://wiki.archlinux.org/title/Cloud-init
4. DigitalOcean. (n.d.). _How to use cloud-config for your initial server setup_. DigitalOcean. Retrieved September 29, 2024, from https://www.digitalocean.com/community/tutorials/how-to-use-cloud-config-for-your-initial-server-setup
5. DigitalOcean. (n.d.). _Automate setup with cloud-init_. DigitalOcean. Retrieved September 29, 2024, from https://docs.digitalocean.com/products/droplets/how-to/automate-setup-with-cloud-init/

### Connecting to a Droplet using SSH
***

1. Open your terminal
2. Run the following command in your terminal

> Note: 
> - Replace "your-droplets-ip-address" with the IP address of the Droplet you made earlier
> - Replace "your-user-name" with the username that you gave your user in your cloud-config file

```
ssh -i .ssh/do-key your-user-name@your-droplets-ip-address
```

What this command means:
- -i = identity_file. This is the path to the file where your private key is stored
- your-user-name = the username that you put in your cloud-config file

3. Type yes
![[ssh-do-key-fish.png]]

4. Press **Enter**

5. If you want to disconnect from the Droplet, run the following command

```
exit
```

Congratulations, now that you know how to connect to and disconnect from your Droplet using SSH, you can move onto the next section: creating and using an SSH config file to connect to your Droplet.

#### References

1. Red Hat. (n.d.). _What is Linux?_. Red Hat. Retrieved September 29, 2024, from https://www.redhat.com/en/topics/linux/what-is-linux#:~:text=Linux%20was%20designed%20to%20be,rest%20of%20the%20operating%20system

### Creating and using an SSH config file to connect to a Droplet
***

> What is an SSH config file?

An SSH config file is short for a Secure Shell configuration file. We are creating a configuration file to make it so that any different connection options we use for our hosts (servers) are kept organized. If we want to create and connect to more servers, having this configuration file can make the process of connecting to those servers easier.

To create a SSH config file, follow these steps:

1. In the .ssh folder in your home directory, create a new file named `config`

> Note: The config file is just called "config". Do not add a file extension

2. In the config file, paste the following text:

> Note: 
> - Replace "your-user-name" with the username that you gave your user in your cloud-config file
> - Replace "your-droplets-ip-address" with the IP address of your droplet

```
Host your-user-name
  HostName your-droplets-ip-address
  User your-user-name
  PreferredAuthentications publickey
  IdentityFile ~/.ssh/do-key
  StrictHostKeyChecking no
  UserKnownHostsFile /dev/null
```

3. Save the config file
4. Restart the terminal
5. Run the following command to connect to your server

> Note: Replace "your-user-name" with the username that you gave your user in your cloud-config file

```
ssh your-user-name
```

![[ssh-fish.png]]
You should see something similar to this after running the command
fish = the user we named fish in our cloud-config file. Yours may be different
pond = the hostname that we set previously when creating the Droplet. Yours may be different

Congratulations, you have successfully connected to a Droplet using an SSH config file. You have reached the end of the tutorial.

#### References

1. DigitalOcean. (n.d.). _How to configure custom connection options for your SSH client_. DigitalOcean. Retrieved September 29, 2024, from https://www.digitalocean.com/community/tutorials/how-to-configure-custom-connection-options-for-your-ssh-client
