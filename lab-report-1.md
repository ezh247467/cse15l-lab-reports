# Lab Report 1

## 1. Installing VSCode
![](Screenshots/InstallVSC.png)
* ### First start off by going to the [Visual Studio Code Website](https://code.visualstudio.com/).
* ### Then, as you can see from the image above, press the Download button. (It should automatically give you the download button for the Operating System you are using)
* ### Once the download is complete, go ahead and open the file to install the VSCode application.
* ### Once the installation is complete, you can now freely open the VSCode application. You should see something similar to the image below.
![](Screenshots/Installed-VSCode.png)

---
## 2. Remotely Connecting to SSH
*Disclaimer: I have only done the rest of this lab on MacOS, so I will only be going over the steps for MacOS.*

* ### As a student of UCSD, you will first need to go [here](https://sdacs.ucsd.edu/~icc/index.php) to find your course-specific account for CSE15L. 
* ### Once you have found out your course-specific account, open a terminal in VSCode and type in ```$ ssh cs15lsp22zz@ieng6.ucsd.edu``` where the ```zz``` will be subsituted with the letters of your course-specific account.
* ### Since it will most likely be your first time logging into this account, you will likely be shown some messages about the authencity of your host and an RSA key. Do not worry too much about these messages.
* ### If you are asked something along the lines of *Are you sure you want to continue connecting?*, simply type **yes**.
* ### After answering the question with yes, you will be prompted to put in your password, which should be the password you used to get your course-specific account. A successful login with your password will look something to similar to the image below.
![](Screenshots/ssh-connection.png)

---
## 3. Trying Some Commands
### Now that you have successfully logged on to the remote server, you can try using some Unix commands on both the server and your personal machine. Here are some examples of the commands you can try below.
* cd
* ls
* ls -a
* ls -lat
* touch helloworld.txt
* mkdir CSE-15L
* mv helloworld.txt ~/CSE-15L

*Note: To log out of your ssh, you can either press Ctrl + D, or type logout*.

---
## 4. Moving Files Over SSH Using SCP
### The scp command, also known as Secure Copy, allows you to securely copy files from one Unix/Linux **system** to another Unix/Linux **server**.
* ### From your personal machine, let's first create a java file to copy over, which we will call ```WhereAmI.java```. While you do not need to have java installed on your computer for what we are about to do, it would be great to have it for the file we will be creating.
* ### Now copy the following code and try compiling and running it using ```javac``` and ```java``` (if you have java installed):

```
class WhereAmI {
    public static void main(String[] args) {
        System.out.println(System.getProperty("os.name"));
        System.out.println(System.getProperty("user.name"));
        System.out.println(System.getProperty("user.home"));
        System.out.println(System.getProperty("user.dir"));
    }
}
```
* ### Now that we have created the file that we will be copying over, we will now use the scp command to copy it over to our remote server's home directory. Type in ```$ scp WhereAmI.java cs15lsp22zz@ieng6.ucsd.edu:~/```
*Note: You will once again be prompted for a password since you are copying the file to your remote server*
* ### Now try logging back into your remote server and check if the correct file is there.
![Image](Screenshots/check-copy.png)
* ### Now try running ```javac``` and ```java``` for the ```WhereAmI.java``` file (java should be installed on the *server*, so you should be able to run it).
![](Screenshots/runGetProp.png)
* ### As you can see, the getProperty functions we used for the Java file shows us the properties of the machine that is being used. When using the terminal on your client, you are given the properties of your personal machine. When running the terminal through ssh to your remote server, you are given the properties of the server in the CSE labs.

---
## 5. Setting an SSH Key 
### Having to type in a password every time you want to access your remote server can be very frustrating, however we can bypass this little issue using an ssh key.
* ### We first need to generate our key by using the ```$ ssh-keygen``` comand. Once you do, you will be asked to choose where you want to save your key files in, which you can just store in the default directory that the terminal provides. For the passphrase, we will not use a passphrase so you can just press enter. You should end up with something similar to the image below.
![](Screenshots/ssh-keygen.png)
* ### Now that your key files have been created, you should find the files under the ```~/.ssh``` directory. You should notice that you have an ```id_rsa.pub``` file, which will be the one we will copy over to your remote server.
* ### Before we start using a ```scp``` command to copy the file over, we first need to log onto our remote server and create a ```.ssh``` directory there. We can do this by using the command: ```$ mkdir .ssh```.
* ### Once you have made the directory, log out of the remote server and copy the ```id_rsa.pub``` file into ```authorized_keys``` folder in the ```.ssh``` directory that you made. Please check the image below for any clarification needed.
![](Screenshots/copy-id_rsa.png)
*Note: While it is true that you did not create an authorized_keys directory, you should be able to copy the id_rsa.pub file into that directory. If you get an error saying that the authorized_keys directory does not exist, log back in to the remote server and create the directory in the .ssh directory yourself and try again.*
* ### Now you should be able to ```ssh``` or ```scp``` without having to input your password each time!

---
## 6. Optimizing Remote Running
### Now that we've made our ssh keys, we are already making our remote running much more efficient. We can do the ```scp``` activity from Part 4 one more time and do it much faster. However, that's not all! There are two other shortcuts that we can learn in this lab.
* ### Firstly, we can write our ssh commands from our personal machine by using quotations to directly run the command in the remote server. An example would be: ```$ ssh cs15lsp22zz@ieng6.ucsd.edu "ls"```.
* ### The second shortcut we can do is having multiple commands on the same line by separating them using semicolons. An example would be: ```$ cp WhereAmI.java OtherMain.java; javac OtherMain.java; java OtherMain.java```.
![](Screenshots/optimized-ssh.png)
### In the image above, I used both shortcuts to show how they can be used.