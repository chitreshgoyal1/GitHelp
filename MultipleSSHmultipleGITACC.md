Multiple ssh Multiple Git Account
=======

See existing keys:

	ls -al ~/.ssh/

If default id_rsa exist, you need to rename it:

	> mv ~/.ssh/id_rsa ~/.ssh/id_rsa_work
	> mv ~/.ssh/id_rsa.pub ~/.ssh/id_rsa_work.pub

Create one more ssh key:

	> cd ~/.ssh
	> ssh-keygen -t rsa -C "your_email@youremail.com"
	  Enter file in which to save the key (/home/chitresh/.ssh/id_rsa): personal
	  Enter passphrase (empty for no passphrase):      (leave blank just hit enter)
	  Enter same passphrase again:                     (leave blank just hit enter)

Now your key is created as:

	personal
	personal.pub

Now we need to add ssh key:
	
	> ssh-add ~/.ssh/id_rsa_work
	> ssh-add ~/.ssh/personal

Delete cached keys:

	ssh-add -D

Check cached keys:

	ssh-add -l

Configration for multiple account and multiple keys:

	> touch config
	> subl -a config  (open config in editor: in my case sublime)

Add following in Config:

	#My work station account
	Host github.com-id_rsa_work
		HostName github.com
		User git
		IdentityFile ~/.ssh/id_rsa_work

	#My personal account
	Host github.com-personal
		HostName github.com
		User git
		IdentityFile ~/.ssh/personal



Clone your repo and Cheers
