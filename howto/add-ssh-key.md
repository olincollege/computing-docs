# How to add an SSH key to your account on a remote server

If you have remote access to a server over SSH, you can log into your user
account on that server. You may be used to logging in with a username and
password, but you can instead log in with a username and SSH key (a file that
lives on your machine).

If possible, we recommend logging in with a username and SSH key for two
reasons:

1. It provides greater security against unauthorized people logging into your
   account.
2. It is more convenient that typing in a password every time you access the
   server.

In this guide, we will walk through the process of adding an SSH key to your
account on a remote server.

## Terminology

In this guide, **remote** indicates something related to the server that you
have remote access to. For example, that server itself is called the **remote
machine**, and your user account on that server is called your **remote
account**.

On the other hand, **local** indicates something related to the device that you
are accessing the remote server _from_. Your local account may have a different
username and/or password than your remote account.

Your local machine may have multiple **local operating systems (OSes)** or
programs running on it. For example, your local machine might run both Windows
and Linux. If you are using WSL on Windows, you should consider Windows and WSL
to be two different OSes.

If you don't know whether you have multiple OSes on your local machine, you
should assume that the OS you are currently using (e.g., Windows, macOS, Linux)
is your one and only local OS.

## Prerequisites

Before you do the steps in this guide, you should:

- Have access to your remote account credentials (i.e., your remote username and
  password, or your remote username and another SSH key that you can access on
  your local machine).
- Be using the local machine, OS, and/or program that you want to log in _from_.
  In most cases, this program is a terminal (e.g., PowerShell or Microsoft
  Terminal on Windows, Terminal or iTerm2 on macOS).
- Have an SSH key pair on your local OS that you will use to log into the remote
  machine.
- Check that you can access the remote machine by logging in. You may not be
  able to do this if you do not have an Internet connection or if the remote
  machine has restrictions on where it can be accessed from.

## Steps

For the purpose of this guide, we will use `thomas` as the username and
`server.example.com` as the URL of the remote machine. You should replace this
with your own username and remote URL.

Run the following command from your local program:

```
ssh-copy-id thomas@server.example.com
```

### Completing the process with a password

In some cases, you may be asked to enter your password. (If you are not asked,
see "Completing the process with another SSH key" below.) The output will look
something like this:

```
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/thomas/.ssh/id_ed25519.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
thomas@server.example.com's password:
```

If you see this, type the password for your remote account and press
Enter/Return. You may not see anything as you are typing.

If your password is correct, you will then see something like this:

```
Number of key(s) added:        1

Now try logging into the machine, with:   "ssh 'thomas@server.example.com'"
and check to make sure that only the key(s) you wanted were added.
```

Then, finish with "Check completion" below.

### Completing the process without a password

In other cases, you may not need a password during this process. In that case,
your output will skip asking for your password and show this instead:

```
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/thomas/.ssh/id_ed25519.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys

Number of key(s) added:        1

Now try logging into the machine, with:   "ssh 'thomas@server.example.com'"
and check to make sure that only the key(s) you wanted were added.
```

Then, finish with "Check completion" below.

### Check completion

To check that this process completed successfully, run the following command:

```
ssh thomas@server.example.com
```

If all has gone well, you should successfully log into the remote machine
without the need for a password.
