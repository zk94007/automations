SSH + AppleScript for Switching User in Mac OS
=============

This is a AppleScript for swithcing user in Mac OS remotely with SSH and AppleScript. To run this AppleScript you need to copy main.scpt and wrapper.scpt to /var/tmp in remote Mac OS server with SSH.

Preparation
-----------

```
$ pscp main.scpt [user@]host:/var/tmp
$ pscp wrapper.scpt [user@]host:/var/tmp
```

Please note that you need to log in as admin account through VNC Client and create a new **user** which you want to switch, and set a **password**. After that you have to login with the **user** and setup iCloud with VNC Client before switch user with SSH and AppleScript.


Switch to a new user
-----------

```ssh
$ cd /var/tmp
$ osascript main.scpt <username> <password> <admin-username> <admin-password>
```

Log out the origin user 
-----

You should log out the origin user after switched to another user.

```ssh
$ sudo launchctl bootout user/$(id -u <username>)
```
