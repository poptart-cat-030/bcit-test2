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

Congratulations, you have successfully uploaded your Arch Linux image to DigitalOcean. Now, you can move on to the next section: ==Insert instruction section name here==

#### References
1. https://docs.digitalocean.com/glossary/image/#:~:text=Last%20edited%20on%2011%20Mar,to%20run%20a%20containerization%20platform
2. https://www.cloudflare.com/learning/cdn/caching-static-and-dynamic-content/#:~:text=Static%20content%20is%20any%20file,of%20this%20kind%20of%20content
3. https://wiki.archlinux.org/title/Arch_Linux


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
2. Run the following command in your terminal, replacing "your-user-name" with your Windows user name
> Note: "ssh-keygen" is a tool that creates SSH key pairs. If you are using a MacOS or Windows device, you should already have this installed. 
```
`ssh-keygen -t ed25519 -f C:\Users\your-user-name\.ssh\do-key -C "youremail@email.com"`
```
What these commands mean:
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

1. Copy the contents of your do-key.pub file (your public key) by running one of the following commands depending on your operating system

For Windows users:
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
3. Locate and click Settings
4. Click the **Security** tab
![[security-tab.png]]
5. Locate and click Add SSH Key

A pop-up window will appear

6. Under Public Key, paste your public key in the text box
7. Under Key Name, type the name you want to give your key

> Note: Give your key an appropriate name that will distinguish itself from other keys

Congratulations, you have successfully added a public key to your DigitalOcean account. You can now move onto the next section: creating a Droplet that runs Arch Linux and connecting to it using SSH.

#### References
1. https://www.cloudflare.com/learning/access-management/what-is-ssh/
2. https://www.ssh.com/academy/ssh/keygen
3. https://docs.digitalocean.com/products/droplets/how-to/add-ssh-keys/

### Creating a Droplet that runs Arch Linux and connecting to it using SSH
***

> What is a Droplet?

A Droplet is a virtual machine (VM) that lives on servers owned by DigitalOcean that uses a Linux-based operating system. For our purposes, we will be running Arch Linux on our Droplet. The server we create will live in this VM.

#### Steps

text

#### References
1. https://www.redhat.com/en/topics/linux/what-is-linux#:~:text=Linux%20was%20designed%20to%20be,rest%20of%20the%20operating%20system.

### Automating initial setup tasks using a cloud-init configuration file
***

> What is cloud-init?

Cloud-init is 


#### Steps

text
- create a new regular user
- install some initial packages
- add a public ssh key to the authorized_keys file in your new users home directory
- disable root access via ssh

#### References
1. https://docs.digitalocean.com/products/droplets/how-to/automate-setup-with-cloud-init/
2. https://wiki.archlinux.org/title/Cloud-init
3. https://docs.cloud-init.io/en/latest/explanation/introduction.html

### Connecting to a Droplet using SSH keys
***
#### Steps

text
```
code block
```

#### References
1. https://docs.digitalocean.com/products/droplets/how-to/connect-with-ssh/