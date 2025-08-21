# Install Node.js on Windows 7

This post walks through a Node.js install on Windows 7 and tests that node and npm work. It installs v13.14.0 LTS.

It seems that v13.14.0 LTS is the last installer that works on Window 7. I get this error when I try to install v14.0.0 (node-v14.0.0-x64.msi from \[[<u><span>link</span></u>](https://nodejs.org/download/release/v14.0.0/)\]):

![modejs_error_1](nodejs_error_1.jpg)

This post also includes a link to the License Agreement so people can review it before installing. The install takes about 30 secs and uses 86 MB.

**<u><span>Steps</span></u>**

**1**. Go to [[link](https://nodejs.org/download/release/v13.14.0/)]

**2**. Click node-v13.14.0-x64.msi or click \[[link](https://nodejs.org/download/release/v13.14.0/node-v13.14.0-x64.msi)\]

![select_node_version_2](select_node_version_2.jpg)

**3**. Click to launch the install

![launch_install_3](launch_install_3.jpg)

**4**. Click **Run**

![confirm_run_install_4](confirm_run_install_4.jpg)

**5**. Click **Next**

![nodejs_setup_wizard_5](nodejs_setup_wizard_5.jpg)

**6**. Click the **I accept the terms in the License Agreement** checkbox and click **Next**

**Note**: A PDF of the 25 page **License Agreement** is \[[<u><span>here</span></u>](https://drive.google.com/file/d/1aLdNUrLCFfv2IUZbYVg9_zq-zmvfOSxh/view?usp=sharing)\] a Word doc is \[[<u><span>here</span></u>](https://drive.google.com/file/d/1wc5zXwjB53L7x20k9Hnu1LmBgt-sk4nX/view?usp=sharing)\]

![nodejs_license_agreement_6](nodejs_license_agreement_6.jpg)

**7**. Click **Next**

**Note**: Installs **Node.js** into **C:\\Program Files\\nodejs\\**

![node_js_installation_destination_7](node_js_installation_destination_7.jpg)

**8**. Click **Next** on the Custom Setup

**Note**: I've expanded the submodules in the picture

![custom_setup_8](custom_setup_8.jpg)

**Note 2**: Clicking on Disk Usage shows that all the features require 86 MB

![disk_usage_9](disk_usage_9.jpg)

**9**. Click **Install**

![install_node_js_10](install_node_js_10.jpg)

**10**. You'll see the screen pause, darken, and see this pop up. Click **Yes**.

![user_account_control_confirm_11](user_account_control_confirm_11.jpg)

**11**. Click **Finish**

![completed_setup_wizard_12](completed_setup_wizard_12.jpg)

Congratulations! You've installed node and npm.

**<u><span>Test</span></u>**

1\. (A) Click the **Windows Icon**, (B) type **cmd** and (C) click **cmd.exe**

![cmd_exe_13](cmd_exe_13.jpg)

2\. Type **node -v**. I see **v10.14.2.**

![node_v_14](node_v_14.jpg)

3\. Type **npm -v**. I see **6.4.1**.

![npm_v_15](npm_v_15.jpg)

...and it works!

**<u><span>Reference</span></u>**

Node.js logo from \[[link](https://nodejs.org/static/images/logo.svg)\]