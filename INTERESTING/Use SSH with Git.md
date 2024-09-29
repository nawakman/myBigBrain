[[INTERESTING]]

SSH(secure shell) is a secure communication protocol relying on a set of two keys, a public key that will be on your github and a private one that you only can use to identify

-create and add your public ssh key to github
-In Git, run shh agent with ``eval `ssh-agent` ``
-add your private ssh key with `ssh-add "C:\Users\username\.ssh\yourprivateSSHKey"`
NOTE: public key have `.pub` extension, private key does not
-add all modified files `git add -A`
-prepare a commit `git commit -m"aTextDescribingYourModifications"`
-send it to the remote repository `git push origin master`