encrypted-backup
================
- scripts for backing up selected files and directories to a remote encrypted subdirectory
- the password for the encrypted remote directory is stored locally on the computer you're backing up
- your files will be backed up to a subdirectory named after the current date and time, with the latest version always available in "current"
- even though it looks like all backups have a full copy of every file, only one new files are actually copied. The rest are hard linked
- you can delete any backup from any date - the rest of the backups will still be intact

Setting up
----------
- copy server files to the home directory of the user you want to use for backup on your remote server
- copy client files to the home directory, or anywhere else, on the computer you want to back up. Make sure you include the hidden config file .encrypted-backup-config
- generate a strong password, for example here: https://passwordsgenerator.net/ -- and copy it
- on the server, run ```~/set-up-new-encrypted-directory name-of-your-backup```
  - the name-of-your-nackup could be the name of your computer, your name, or a name indicating what you're backing up here
  - first press enter
  - then, twice, paste the password and press enter
- on the client, run ```~/encrypted-backup name-of-your-nackup```
  - follow the instruction in the config file that is opened, making sure you paste the same password as you used on the server.
  - write down this password somewhere. If you lose it, it could take billions of years to brute force attack your encrypted directory, so if your password's gone, your filees are too!

Running
-------
Assuming your backup is called "my-backup", on the client machine, run 

```sh
~/encrypted-backup my-backup
```

or add it to your crontab.
You can also mount and unmount the encrypted directory while on the remote server, but you wil then have to provide the password manually:
```sh
~/mount-encrypted-folder my-backup
~/unmount-encrypted-folder my-backup
```

If in doubt, you can run any of the commands without parameters for instructions on what to do:

On the remote server:
```sh
~/set-up-new-encrypted-directory
~/mount-encrypted-folder
~/unmount-encrypted-folder
```

On your local machine:
```sh
~/encrypted-backup
```
