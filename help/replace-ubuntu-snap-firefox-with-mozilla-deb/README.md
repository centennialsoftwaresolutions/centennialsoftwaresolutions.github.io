replace-ubuntu-snap-firefox-with-mozilla-deb

Get non-snap Firefox: 

Remove SNAP:

```
sudo snap remove firefox
```

Import the Mozilla repo:

```
# Create the keyring directory if it doesn't exist
sudo install -d -m 0755 /etc/apt/keyrings

# Import the Mozilla signing key
wget -q https://packages.mozilla.org/apt/repo-signing-key.gpg -O- | sudo tee /etc/apt/keyrings/packages.mozilla.org.asc > /dev/null

# Add the Mozilla repository to your sources
echo "deb [signed-by=/etc/apt/keyrings/packages.mozilla.org.asc] https://packages.mozilla.org/apt mozilla main" | sudo tee -a /etc/apt/sources.list.d/mozilla.list > /dev/null
```

Get actual Firefox:

```
echo '
Package: *
Pin: origin packages.mozilla.org
Pin-Priority: 1000
' | sudo tee /etc/apt/preferences.d/mozilla
```

Check:

```
user@demo:~/Desktop$ cat /etc/apt/preferences.d/mozilla

Package: *
Pin: origin packages.mozilla.org
Pin-Priority: 1000
```

Get Firefox:

```
sudo apt update && sudo apt install firefox
```

Check:

```
apt-cache policy firefox
```

Example output:

```
Processing triggers for gnome-menus (3.36.0-1.1ubuntu3) ...
orin@demo:~/Desktop$ apt-cache policy firefox
firefox:
  Installed: 155.0.1~build1
  Candidate: 155.0.1~build1
  Version table:
     1:1snap1-0ubuntu5 500
        500 http://ports.ubuntu.com/ubuntu-ports noble/main arm64 Packages
 *** 155.0.1~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main arm64 Packages
        100 /var/lib/dpkg/status
     155.0~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main arm64 Packages
     154.0.1~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main arm64 Packages
     154.0~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main arm64 Packages
     153.0.4~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main arm64 Packages

```
Output says 155.0.1~build1 the native `.deb` package is installed and Mozilla's repo has higher priority (1000) than Ubuntu (500).

