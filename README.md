## How to create a remote server using DigitalOcean

### Adding an Arch Linux image (using the web console)
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
4. Find an Arch Linux image for which the filename includes "cloudimg" and the extension name is .qcow2
![[arch-linux-download-image-files.png]]
5. Click the Arch Linux image you located

You will be prompted to download the Arch Linux image

6. Click Save
![[arch-linux-download-save-file.png]]

Congratulations, you have successfully downloaded an Arch Linux image. Now, you can move on to the next section: uploading that image to DigitalOcean.

#### Uploading the Arch Linux image to DigitalOcean

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


### Adding an SSH key to your 
***

> What are SSH keys?

> Why are we using SSH keys?

SSH stands for the Secure Shell protocol, and it is a way of securely sending data over an unsecured network through the use of public key cryptography. In public key cryptography, you have two keys: one public and one private. Your private key should only be known to you. **These are known as SSH keys**. 

We will be using SSH keys because they are more secure than using a password.

#### How to create an SSH key

text
#### References
1. https://www.cloudflare.com/learning/access-management/what-is-ssh/
2. https://docs.digitalocean.com/products/droplets/how-to/add-ssh-keys/

### Creating a Droplet that runs Arch Linux (using the DigitalOcean web console)
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