

# 1. Create a VM

1. Open **VMware Workstation 17 Pro** (17.5.2 build-23775571) and click **File > New Virtual Machine...** (Ctrl+N).

   > [!NOTE]
   >
   > Ran this on **Microsoft Windows 11 Pro Version 10.0.26100 Build 26100** (from System Information)

1. On the **Welcome Screen**, leave the **default**: Typical. Click Next >.
2. On the **Guest Operating System Installation** screen, set **Installer disc image file (iso)** to your <u>ubuntu-24.04.3-desktop-amd64.iso</u>. Click Next >.
3. On the **Easy Install Information** screen, set **Full Name** to <u>Demo User</u>, **User name** to <u>demo-user</u>, **Password and Confirm** to <u>(your password)</u>. Click Next >.
4. On the **Name the Virtual Machine** screen, set **Virtual machine name** to <u>Ubuntu_64-bit</u>. Click **Browse...** Click **Make New Folder**. Create <u>sitedev_24.04.3</u>. Click Next >.
5. On the **Specify Disk Capacity** screen, leave defaults: Maximum disk size (GB): <u>20 GB</u>, <u>Split virtual disk into multiple files</u>. Click Next >.
6. On the **Ready to Create Virtual Machine** screen, leave defaults. Click **Finish**.

The VM should start, and the installer should come up. 

------

# 2. Install Ubuntu

1. Click on the disk icon. 
2. Use defaults till the **Create your account** screen. 
3. Set **Your name** to <u>Demo User</u>, **Your computer's name** to <u>demo</u>, Your username to <u>demo-user</u>, a password. Leave other defaults. Click **Next**. 
4. Use defaults for all remaining screens and start the install. 
5. On the **Installation complete** screen, you can do 1 of 2 things: 1) click the **Restart now** button or 2) close the installer, shutdown, remove the ISO from the VM, and restart. You should see a **Welcome to Ubuntu 24.04.3 LTS** screen, click next. Skip Ubuntu Pro. Select **Don't share data** and click **Finish**. 

## Enable VM to Host Shared Folders and Copy/Paste (Optional)

After booting, open a terminal and run:

```
sudo apt-get install open-vm-tools open-vm-tools-desktop
```

Power off and restart.

> [!WARNING]
>
> Running `sudo systemctl restart vmtoolsd.service` instead of rebooting doesn't work reliably for me. 

## Change Screen Resolution (Optional)

After booting, change the screen resolution. Right-click the desktop. Click **Display settings**. Choose a new setting. On **Keep settings** popup, click Ok.

------

# 3. Get git and gh

```
sudo apt-get install git gh
```

## Configure git

```
git config --global user.email "artur.dent@example.com"
git config --global user.name "Arthur Dent"
```

------

# 4. Login to GitHub Via Browser

In Ubuntu, open Firefox and go to [github.com](github.com). Click **Sign in** in the upper right or **Sign up** to create and account.

------

# 5. Login to GitHub Via gh

Run `gh auth login` and use defaults.

## Get other packages (Optional)

### curl and Vim

```
sudo apt-get install curl vim
```

### Typora

> [!NOTE]
>
> From https://typora.io/#linux

```
# add Typora's key

sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://downloads.typora.io/typora.gpg | sudo tee /etc/apt/keyrings/typora.gpg > /dev/null
# add Typora's repository securely
echo "deb [signed-by=/etc/apt/keyrings/typora.gpg] https://downloads.typora.io/linux ./" | sudo tee /etc/apt/sources.list.d/typora.list
sudo apt update
# install typora
sudo apt install typora
```

------

# 6. Install and Configure Development Tools: ruby, jekyll, bundler

> [!NOTE]
>
> Adapted from instructions listed on:
>
> https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyllhttps://jekyllrb.com/docs/installation/ubuntu/

1. Install Ruby and other prerequisites

``` 
sudo apt-get install ruby-full build-essential zlib1g-dev 
```

2.  Set up a gem installation directory for your user account

```
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

3. Install Jekyll and Bundler

```
gem install jekyll bundler
```

   > [!NOTE]
   >
   > The last 3 lines you should see:
   >
   > ```
   > ...
   > Installing ri documentation for bundler-2.7.2
   > Done installing documentation for bundler after 0 seconds
   > 30 gems installed
   > ```
   >

4. Clone site into home dir:

   ```
   cd ~
   git clone https://github.com/centennialsoftwaresolutions/centennialsoftwaresolutions.github.io.git
   cd ~/centennialsoftwaresolutions.github.io
   ```

5.  Check **Gemfile**

   ```
   cd ~/centennialsoftwaresolutions.github.io
   cat Gemfile
   ```

   You should see:

   ```
   source "https://rubygems.org"

   gem "github-pages", group: :jekyll_plugins
   gem "webrick", "~> 1.8"
   gem "jekyll-sitemap"
   ```

6. Keep gems in the project

   ```
   bundle config set path 'vendor/bundle'
   ```

7. Install gems

   ```
   bundle install
   ```

# 7. Run and Test

1. Serve pages:

   ```
   bundle exec jekyll serve
   ```

   You should see:
   
   ```
   Configuration file: /home/demo-user/centennialsoftwaresolutions.github.io/_config.yml
   To use retry middleware with Faraday v2.0+, install `faraday-retry` gem
               Source: /home/demo-user/centennialsoftwaresolutions.github.io
          Destination: /home/demo-user/centennialsoftwaresolutions.github.io/_site
    Incremental build: disabled. Enable with --incremental
         Generating... 
          Jekyll Feed: Generating feed for posts
   ```

2. Then wait a bit. After just over a minute on my machine, I see:

   ```
                       done in 73.598 seconds.
    Auto-regeneration: enabled for '/home/demo-user/centennialsoftwaresolutions.github.io'
       Server address: http://127.0.0.1:4000/
     Server running... press ctrl-c to stop.
   ```

3. Open a browser window to http://127.0.0.1:4000/ and you should see the site. 

   Serve & rerun with each save:
   
   ```
   bundle exec jekyll serve --incremental
   ```

------

# Errors You May See

## `bundle install` error

```
[DEPRECATED] This Gemfile does not include an explicit global source. ...
Could not find gem 'github-pages' in locally installed gems.
```

**Cause:** Your `Gemfile` is missing a global source or the correct gems.

**Fix:** Make sure your `Gemfile` looks like this:

```ruby
source "https://rubygems.org"

gem "github-pages", group: :jekyll_plugins
gem "webrick", "~> 1.8"
```

Then run:

```bash
bundle install
```

## `bundle exec jekyll serve` error

```
Could not find gem 'github-pages' in locally installed gems.
Run `bundle install` to install missing gems.
```

**Cause:** Gems have not been installed yet.

**Fix:** Run:

```bash
cd ~/post/
bundle install
```

...to install everything from your `Gemfile`, then retry:

```bash
bundle exec jekyll serve
```

