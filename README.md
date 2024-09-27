## How to create a remote server using DigitalOcean

### Creating SSH keys

> What are SSH keys?
> Why are we using SSH keys?

SSH stands for the Secure Shell protocol, and it is a way of securely sending data over an unsecured network through the use of public key cryptography. In public key cryptography, you have two keys: one public and one private. Your private key should only be known to you. **These are known as SSH keys**. 

We will be using SSH keys because they are more secure than using a password.

#### How to create an SSH key

text
#### References
https://www.cloudflare.com/learning/access-management/what-is-ssh/
https://docs.digitalocean.com/products/droplets/how-to/add-ssh-keys/

### Adding an Arch Linux image (using the web console)

> What is an Arch Linux image?
> Why Arch Linux?

A disk image is a static file (meaning that it does not change) that contains the data and structure of a physical disk drive. Arch Linux is a Linux distribution, an operating system that uses the Linux kernel. An Arch Linux image is a file containing everything that an actual computer disk running the Arch Linux operating system would have.

We will be using Arch Linux because it is minimal and has extensive documentation. It is intended to be customizable, so you can add whatever you need to it yourself.

#### Steps

text
[Download a Arch Linux image](https://gitlab.archlinux.org/archlinux/arch-boxes/-/packages/)

#### References
https://docs.digitalocean.com/glossary/image/#:~:text=Last%20edited%20on%2011%20Mar,to%20run%20a%20containerization%20platform.
https://www.cloudflare.com/learning/cdn/caching-static-and-dynamic-content/#:~:text=Static%20content%20is%20any%20file,of%20this%20kind%20of%20content
https://wiki.archlinux.org/title/Arch_Linux


### Creating a Droplet that runs Arch Linux (using the DigitalOcean web console)

> What is a Droplet?

A Droplet is a virtual machine (VM) that lives on servers owned by DigitalOcean that uses a Linux-based operating system. For our purposes, we will be running Arch Linux on our Droplet. The server we create will live in this VM.

#### Steps

text

#### References
https://www.redhat.com/en/topics/linux/what-is-linux#:~:text=Linux%20was%20designed%20to%20be,rest%20of%20the%20operating%20system.

### Automating initial setup tasks using a cloud-init configuration file

> What is cloud-init?

Cloud-init is 


#### Steps

text
- create a new regular user
- install some initial packages
- add a public ssh key to the authorized_keys file in your new users home directory
- disable root access via ssh

#### References
https://docs.digitalocean.com/products/droplets/how-to/automate-setup-with-cloud-init/
https://wiki.archlinux.org/title/Cloud-init
https://docs.cloud-init.io/en/latest/explanation/introduction.html

### Connecting to a Droplet using SSH keys

#### Steps

text
```
code block
```

#### References
https://docs.digitalocean.com/products/droplets/how-to/connect-with-ssh/