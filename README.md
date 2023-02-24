<div align="center">
<h1>RSYNC</h1>
</div>

## About

I been using rsync for sometime and is one of my favorite tools.

## What is rsync

Rsync is a fast and versatile file copying tool.

## What you can do with Rsync?

In can copy files locally, or from our computer to a server usning ssh.

Is widely used for backups and mirroring.

## Flags

This is a list of the most use flags.

**-a**: Archive mode

**-h**: Human readable

**-v**: Verbose

**-P**: Partial progress

## Examples And Explanations

This is a pretty basic example.

This example is going be executed locally..

```bash
cd Documents
mkdir CopyHere
touch myspecialfile.txt
```

In our Documents folder we created a directory call CopyHere, then we create a txt file called myspecialfile.txt, using rsync we are going to copy myspecialfile.txt into the MoveHere directory.

```bash
rsync -ahvP myspecialfile.txt CopyHere/
```

Simple no?

As you can see using the flags **-vh** we can display some information about the files beeing copy.

But what about the flags **-aP** ?, the flag -a sync the contents recursively this is usefull when we need to sync a directory with many files on it, now the flag -P, this option is useful for syncing large files, if for any reason our sync gets interupted running the command again will continue with the data that was left.

**Using SSH**

If you have a server and you look for transfering a directory into the server you can do it too.

Imagine that we have a raspberrypi and we want to send all the videos store in theOffice directory into our raspberrypi.

```bash
rsync -ahvP ~/Videos/theOffice/ pi@ip_of_the_raspberry_here:/home/raspberrypi/Videos
```

This is very easy to read firts we call rsync with the flags -a for archive, -h human readable, -v for verbose and for last -P in case that our sync gets
interupted, then we give the locations of the videos, follow by a space we add pi this is the username in our server, then we continue with the ip of the server follow by colon ":" , for last /home/raspberrypi/Videos here is where the videos are going to be send.

**Using SSH Config File**

If you have a config file for your ssh the command will look very similar.

```bash
rsync -ahvP ~/Videos/theOffice/ raspberrypi:/home/raspberrypi/Videos
```

Once we run the last command rsync will look into our ssh config and use the Host raspberrypi configuration.
