## Adding your SSH Key to your Github account

#### So you don't have to log into github all the time when you are pushing/pulling your code

****

<br/>

For Windows:

1. ##### Open up Git Bash

2. ##### Enter in the following 

   ###### To Generate SSH Key

   ```
   ssh-keygen -t rsa -C "yourEmailName@yourEmail.com"
   ```

   > *Generating public/private rsa key pair*
   >
   > *Enter file in which to save the key (/c/Users/UserMe/.ssh/id_rsa):*
   >

   Just Enter to save the keygen file in this directory

   > *Created directory '/c/Users/UserMe/.ssh'.*
   >
   > *Enter passphrase (empty for no passphrase):*
   >

   Enter a simple passphrase eg. 1234 - for security purposes

   > *Your identification has been saved in /c/Users/UserMe/.ssh/id_rsa.*
   >
   > *Your public key has been saved in /c/Users/UserMe/.ssh/id_rsa.pub.*
   >
   > *The key fingerprint is:*
   > *SHA256:sdsPCneeqsdasdasdOEeeeXjSo yourEmailName@yourEmail.com*
   > *The key's randomart image is:*
   >
   > +---[RSA 3073]----+
   >
   > |               .s            |
   >
   > |                       ...    |
   >
   > |    .   ...                   |
   >
   > |   . .r..d   .              |
   >
   > |  . .  .f +           +    |
   >
   > |   . e .          == +   |
   >
   > |o- = ...          o *   |
   >
   > | .+X. . .             +   |
   >
   > |..+ ...o+                 |
   >
   > +----[SHA256]-----+
   >
   > 

   <br/>

   ###### Letting our computer know that we want to use this SSH Key that we generated above:  

   ###### To Start the SSH Agent

   ```
   eval $(ssh-agent -s)
   ```

   > *Agent pid 669 (or anything else)*
   >
   >   

   ###### Adding this SSH Key

   ```
   ssh-add ~/.ssh/id_rsa     
   (this is the default location. if you saved somewhere else, specify your saved file location)
   ```

   > *Enter passphrase for /c/Users/UserMe/.ssh/id_rsa:*

   ###### Enter the passphrase you have chosen earlier on

   > Identity added: /c/Users/UserMe/.ssh/id_rsa (yourEmailName@yourEmail.com)  
   >
   
<br/>

   ###### Copy the Public SSH Key

   option 1:  Manually go to /c/Users/UserMe/.ssh/id_rsa.pub and Copy this key

   option 2: Copy directly from git bash

   ```
   clip < ~/.ssh/id_rsa.pub
   ```

   (this will copy the public ssh key in your clipboard)  

   <br/>

3. ##### Go to Github to save this SSH Key

   Settings > SSH and GPG Keys

   ###### Add 'New SSH Key'

   Paste your clipboard into the Key field

   Give a title - that describes the computer the SSH key is associated with 

   eg. Daryll-Dell-Laptop

   (Easy for you to identify later on as you work on more devices later on)

   <br/>

   <br/>

   ### VOILA YOUR ARE DONE

   <br/>

   <br/>
   
   <br/>
   
<br/>
   
###### Note if this is your first git set up:
   
You will be prompted to set up your account's default identity
   
   ```
   git config --global user.email "yourEmailName@yourEmail.com"
   git config --global user.name "yourName"
   ```
   
   <br/>
   
   <br/>
   
   







