# Sys1-homework
Hello ,In this repo you will see how the sys1 homework will progress

# **Make sure you install ansible first **
You can do it with those simple line 
 
 ```sh
sudo apt update
```

```sh
sudo apt install ansible
```
&nbsp;
> NOTE: I use debian for those step

# ** Next thing to Create a script that will automate the process  **

This part will explai how the scipt work , how he will configure apaches and where it should be : 

1. Creation of a `.conf` file in `/etc/apache2/sites-available`:
   - The script generates a configuration file in the `/etc/apache2/sites-available` directory. This file contains the necessary settings for each provided domain name and `activate that configuration.`
   - The configuration file ensures that Apache2 handles requests for the specified domain names correctly.

2. Creation of an appropriate directory in `/var/`:
   - The script creates a directory in the `/var/` path, specifically for each provided domain name.
   - These directories serve as the document roots for the respective websites associated with the domain names.

3. Creation of an `index.html` file for each domain name:
   - For each domain name provided, the script generates an `index.html` file within the corresponding directory in `/var/`.
   - The content of each `index.html` file is set to display a welcoming message specifically tailored to the corresponding domain name. For example, the content of `index.html` for the domain `www.example.com` would say "Welcome to www.example.com".

By executing this script, you automate the process of creating the necessary Apache2 configuration files, setting up the appropriate directories for the websites, and generating welcome pages for each domain name.

# ** launch the script :
- Change the `hosts` value in `script.yaml` to the IP address of the server or machine that you want to configure Apache2 on.

- now run the script with those commands : 
    
    ---

  - If you want to run the script on a remote host (not localhost):
    ```sh
    ansible-playbook --private-key=your_private_ssh_key --ask-become-pass --user=your_user script.yaml
    ```
    ---

  - If you want to run the script on a remote host and  use a passphrase for the SSH keys:
    ```sh
    ansible-playbook --private-key=your_private_ssh_key --ask-become-pass --ask-pass --user=your_user script.yaml
    # The --ask-pass option is added
    ```
    ---

  - If you are running the script on your local machine, simply use the command:
    ```sh
    ansible-playbook script.yaml --ask-become-pass


**Note**:

- Replace `your_private_ssh_key` with your private key and `your_user` with your username, which has access to the server using the private key.

