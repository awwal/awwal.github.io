---
published: true
---

## VSTS Git SSH Issue


For unknown reason, after a recent change in VSTS ssh url, my SSH key was rejected by the MS Server.After confirming that my uploaded keys fingerprint matches. I started digging.

For anyone with the same problems. My hunch is that the MS git servers rejects the configured SSH key if it is not the first presented. This will happen if you have multiple keys. 

First you can try 

```
ssh-agent bash -c 'ssh-add /home/xxx/.ssh/me; git clone ssh://myrepo@vs-ssh.visualstudio.com:22/DefaultCollection/xxx/_ssh/xxx'
<<<<<<< Updated upstream:_posts/2017-12-30-vsts-git-ssh-issue.markdown
```

This will execute the git command (clone in this case) in an isolated env using only the specified key. If this works, you can then edit your .ssh/config file and alias the vs-ssh.visualstudio.com and specify the configured key. See example below
=======
This will execute the git command (clone in this case) in an isolated env using only the specified key. If this works, you can then edit your .ssh/config file and alias the vs-ssh.visualstudio.com and specgify the configured key. See example below
>>>>>>> Stashed changes:_posts/2017-12-30-vsts_git_ssh_issue.markdown

```
Host msgit 
HostName vs-ssh.visualstudio.com 
IdentityFile ~/.ssh/me
IdentitiesOnly yes
```

Hence forth you always change vs-sssh.visualstudio.com to msgit





