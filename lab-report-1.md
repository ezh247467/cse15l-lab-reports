# Lab Report 1

## 1. Installing VSCode
![Image](Screenshots/InstallVSC.png)
* ### First start off by going to the [Visual Studio Code Website](https://code.visualstudio.com/).
* ### Then, as you can see from the image above, press the Download button. (It should automatically give you the download button for the Operating System you are using)
* ### Once the download is complete, go ahead and open the file to install the VSCode application.
* ### Once the installation is complete, you can now freely open the VSCode application. You should see something similar to the image below.
![Image](Screenshots/Installed-VSCode.png)

---

## 2. Remotely Connecting to SSH
*Disclaimer: I have only done the rest of this lab on MacOS, so I will only be going over the steps for MacOS.*

* ### As a student of UCSD, you will first need to go [here](https://sdacs.ucsd.edu/~icc/index.php) to find your course-specific account for CSE15L. 
* ### Once you have found out your course-specific account, open a terminal in VSCode and type in ```ssh cs15lsp22zz@ieng6.ucsd.edu``` where the ```zz``` will be subsituted with the letters of your course-specific account.
* ### Since it will most likely be your first time logging into this account, you will likely be shown some messages about the authencity of your host and an RSA key. Do not worry too much about these messages.
* ### If you are asked something along the lines of *Are you sure you want to continue connecting?*, simply type **yes**.
* ### After answering the question with yes, you will be prompted to put in your password, which should be the password you used to get your course-specific account. A successful login with your password will look something to similar to the image below.
![Image](Screenshots/ssh-connection.png)
