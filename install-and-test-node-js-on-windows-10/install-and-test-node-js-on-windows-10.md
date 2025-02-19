# Install and Test Node.js on Windows 10

![node_js_logo_1](node_js_logo_1.jpg)

## Install and Test Node.js on Windows 10

Quickly install and Test Node.js on Windows 10 using this post. Node.js v20.11.1 (LTS) Windows, x86 is used.

## Download & Install

1\. Open https://nodejs.org/en/download

2\. Select v20.11.1 (LTS), Windows, x86:

![v20_11_1_lts_2](v20_11_1_lts_2.png)

3\. Download [<u><span>node-v20.11.1-x64.msi</span></u>](https://nodejs.org/dist/v20.11.1/node-v20.11.1-x64.msi) (Windows Installer Package) to the **Downloads** folder

4\. Open **Downloads**

![open_downloads_3](open_downloads_3.png)

5\. Right-click and select **Install**

![right_click_install_4](right_click_install_4.png)

6\. On the **Node.js Setup** screen, click **Next**

![node_js_setup_next_5](node_js_setup_next_5.png)

7\. Accept the [License Agreement](https://drive.google.com/file/d/1eadRw2--utEgWFNThkDm77FNNuLVCMtM/view?usp=sharing) and click Next

![node_js_license_agreement_6](node_js_license_agreement_6.png)

8\. Click Next to install Node.js in the default directory **C:\\Program Files\\nodejs\\**

![directory_program_files_7](directory_program_files_7.png)

9\. Click Next to install everything:

![next_install_everything_8](next_install_everything_8.png)

Disk Usage:

![disk_usage_9](disk_usage_9.png)

Everything:

![node_js_runtime_10](node_js_runtime_10.png)

![corepack_manager_11](corepack_manager_11.png)

![npm_package_manager_12](npm_package_manager_12.png)

![online_documentation_shortcuts_13](online_documentation_shortcuts_13.png)

![add_to_path_14](add_to_path_14.png)

![node_js_and_npm_15](node_js_and_npm_15.png)

![npm_modules_16](npm_modules_16.png)

10\. Check the **Automatically install tools...** box and click **Next**

![automatically_install_tools_17](automatically_install_tools_17.png)

11\. Click **Install**

![install_node_js_18](install_node_js_18.png)

12\. After a time, click **Finish**

![finish_node_js_setup_19](finish_node_js_setup_19.png)

13\. To skip this, close the pop-up. To proceed, close other programs, and hit any key

![proceed_hit_any_key_20](proceed_hit_any_key_20.png)

14\. You may see this Chocolatey notification, if so press any key to start the installation

![chocolatey_notification_21](chocolatey_notification_21.png)

The end of the install [<u><span>log</span></u>](https://drive.google.com/file/d/1earyUI9jIZW47Kbn095M4SCsf8V9J7ec/view?usp=sharing)

```
Chocolatey upgraded 19/19 packages.
 See the log for details (C:\ProgramData\chocolatey\logs\chocolatey.log).

Upgraded:
 - chocolatey-compatibility.extension v1.0.0
 - chocolatey-core.extension v1.4.0
 - chocolatey-dotnetfx.extension v1.0.1
 - chocolatey-visualstudio.extension v1.11.1
 - chocolatey-windowsupdate.extension v1.0.5
 - dotnetfx v4.8.0.20220524
 - KB2919355 v1.0.20160915
 - KB2919442 v1.0.20160915
 - KB2999226 v1.0.20181019
 - KB3033929 v1.0.5
 - KB3035131 v1.0.3
 - python v3.12.2
 - python3 v3.12.2
 - python312 v3.12.2
 - vcredist140 v14.38.33135
 - vcredist2015 v14.0.24215.20170201
 - visualstudio2019buildtools v16.11.34
 - visualstudio2019-workload-vctools v1.0.1
 - visualstudio-installer v2.0.3

Packages requiring reboot:
 - vcredist140 (exit code 3010)

The recent package changes indicate a reboot is necessary.
 Please reboot at your earliest convenience.
Type ENTER to exit
```

The referenced C:\\ProgramData\\chocolatey\\logs\\[<u><span>chocolatey.log</span></u>](https://drive.google.com/file/d/1ewxsGI06NhKJBz4CRojKu-5RoK5Z1581/view?usp=sharing)

## Test

1\. Right-click the Windows Icon and select run

![test_22](test_22.png)

2\. Type cmd.exe

![type_cmd_exe_23](type_cmd_exe_23.png)

3\. Type node -v. I see v20.11.1.

![node_v_I_see_v20_11_1_24](node_v_I_see_v20_11_1_24.png)

4\. Type npm -v. I see 10.2.4

![npm_v_I_see_10_2_4_25](npm_v_I_see_10_2_4_25.png)

This post showed how to install and test Node.js on Windows 10 using this post.