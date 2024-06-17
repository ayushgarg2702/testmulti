- This is test Repo. That I create to test of adding 2 different git hosting platforms.

- - Setting up a seperate Github and Bitbucket account

- Below are the steps for this : 

* Create SSH Keys
* * ssh-keygen -t rsa -C "github email"
* * pbcopy < ~/.ssh/id_rsa_gh.pub

- Create Config file
* vim ~/.ssh/config
#Github (default)
  Host gh
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_rsa_gh

#Bitbucket (secondary)
  Host bb
  HostName bitbucket.org
  User git
  IdentityFile ~/.ssh/id_rsa


- Add SSH Key to SSH Agent
* * eval "$(ssh-agent -s)"
* * ssh-add ~/.ssh/id_rsa_gh

- Secondary (GitHub)
* * git config user.name "Full Name"
* * git config user.email email_address
* * git remote add origin git@bb:username/testbucket.git
* * git push origin master


- Add the identities to SSH:
* * ssh-add ~/.ssh/id_rsa_gh
* * ssh-add ~/.ssh/id_rsa

- Check keys were added:
* * ssh-add -l

- Check that repo recognizes keys:
* * ssh -T gh
* * ssh -T bb


- Test SSH Connection
* * ssh -T git@github.com

- Check and Update Git Remote URL
* * git remote -v
* * git remote set-url origin git@github.com:ayushgarg2702/testmulti.git

- Restart SSH Service (if necessary)
* * sudo systemctl restart ssh