# How to Setup SSH to a Target Behind a Host

![OpenSSH_logo](OpenSSH_logo.gif)

This post lists the commands to ssh to a target (\<tgt>) behind a host (<hst>) from Linux (<lnx>). Its written as a reference. Replace <tgt>, <tgt-username>, <tgt-ip>, <hst>, <hst-username>, and <lnx> with your values.

**<u><span>Relevant Versions</span></u>**

```
ssh -V
# OpenSSH_7.4p1 Debian-10+deb9u7, OpenSSL 1.0.2l  25 May 2017
```

**<u><span><a href="https://www.centennialsoftwaresolutions.com/blog/hashtags/1" target="__blank"><span>#1</span></a><span> Gen &lt;hst&gt; Key</span></span></u>**

```
ssh-keygen -t rsa -C "me@mydomain.com"
# Use /home/demo/.ssh/id_rsa_<hst>
# Enter a passphrase
ssh <hst-username>@<hst>
exit 
# Upload your public key with scp
scp ~/.ssh/id_rsa_<hst>.pub <hst-username>@<hst>:~/
```

**<u><span><a href="https://www.centennialsoftwaresolutions.com/blog/hashtags/2" target="__blank"><span>#2</span></a><span> Configure &lt;hst&gt;</span></span></u>**

```
# Log into <hst> 
ssh <hst-username>@<hst>
chmod go-w ~/
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
cd ~/.ssh
cp authorized_keys authorized_keys_backup
cat ~/id_rsa_<hst>.pub >> authorized_keys
exit
```

**<u><span><a href="https://www.centennialsoftwaresolutions.com/blog/hashtags/3" target="__blank"><span>#3</span></a><span> Configure &lt;lnx&gt;</span></span></u>**

```
# On your computer, create:
vi ~/.ssh/config
# With:
Host <hst>
User <hst-username>
Hostname <hst>
ServerAliveInterval 240
ServerAliveCountMax 2
IdentityFile ~/.ssh/id_rsa_<hst>
IdentitiesOnly yes
# Now test:
ssh <hst>
# Enter your passphrase
exit
```

**<u><span><a href="https://www.centennialsoftwaresolutions.com/blog/hashtags/4" target="__blank"><span>#4</span></a><span> Use ssh-agent to store your passphase so you don't need to keep typing it</span></span></u>**

```
# Store your passphrase for this session
eval $(ssh-agent)
ssh-add ~/.ssh/id_rsa_<hst>
# Test
ssh <hst>
exit
```

**<u><span><a href="https://www.centennialsoftwaresolutions.com/blog/hashtags/5" target="__blank"><span>#5</span></a><span> Set up a jump to &lt;tgt&gt; (assumes id_&lt;tgt&gt;, the &lt;tgt&gt;'s private key exists in ~/.ssh/id_&lt;tgt&gt;)</span></span></u>**

```
ssh <hst>
# On <hst>, enumerate targets
# Get the IP of the <tgt>
ifconfig
# <tgt-ip>
# On <hst>, grab the private key for <tgt>, id_<tgt>
# Test ssh to <tgt>
ssh <tgt-username>@<tgt>

# Back on <lnx>, get <tgt>'s private key
scp <hst>:~/.ssh/id_<tgt> ~/.ssh/

# On your <lnx>, edit ~/.ssh/config
vi ~/.ssh/config
# Add:
Host <tgt>
User <tgt-username>
Hostname <tgt-ip>
ProxyCommand ssh <hst> -W %h:%p
ServerAliveInterval 240
ServerAliveCountMax 2
IdentityFile ~/.ssh/id_<tgt>
IdentitiesOnly yes
# Test
ssh <tgt>
```

**<u><span># Note: your full ~/.ssh/config on &lt;lnx&gt; will look like:</span></u>**

```
Host <hst>
User <hst-username>
Hostname <hst>
ServerAliveInterval 240
ServerAliveCountMax 2
IdentityFile ~/.ssh/id_rsa_<hst>
IdentitiesOnly yes

Host <tgt>
User <tgt-username>
Hostname <tgt-ip>
ProxyCommand ssh <hst> -W %h:%p
ServerAliveInterval 240
ServerAliveCountMax 2
IdentityFile ~/.ssh/id_<tgt>
IdentitiesOnly yes
```

**<u><span>References</span></u>**

https://help.ubuntu.com/community/SSH/OpenSSH/Keys
