# Xilinx 2016.4 WebPACK Vivado and SDK Install on Windows 7 SP1

![xilinx_logo_1](xilinx_logo_1.png)

This post shows a WebPACK install of the 2016.4 release of Vivado and the SDK. It also lists the features and devices supported in WebPACK.

**<u><span>Notes</span></u>**

The steps use the 50.44 MB Web Installer which will download 5.38 GB during the install. The install requires an additional 26.86 GB of space.

To find space you can (A) click on C:\\ and (B) type size:gigantic to see if anything can be archived or removed:

![find_gigantic_file_sizes_2](find_gigantic_file_sizes_2.png)

**<u><span>Steps</span></u>**

1\. Vivado 2016.4 is available in the archives @ \[[<u><span>link</span></u>](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/vivado-design-tools/archive.html)\]. SDK is included with Vivado.

2\. (A) Click **Archive** and (B) click **2016.4**

![xilinx_archive_2016.4_3](xilinx_archive_2016.4_3.png)

3. Scroll down and click [[Vivado HLx 2016.4: WebPACK and Editions - Windows Self Extracting Web Installer](https://www.xilinx.com/member/forms/download/xef.html?filename=Xilinx_Vivado_SDK_2016.4_0124_1_Win64.exe)] then login to download.

![webpack_and_editions_4](webpack_and_editions_4.png)

4\. Double-click **Xilinx\_Vivado\_SDK\_2016.4\_0124\_1\_Win64.exe** and click through the acceptance.

Note: At the **Welcome** screen you can click **Preferences** to select a **proxy** or the **\# of cores to use to download and install**

![installer_preferences_5](installer_preferences_5.png)

![preferance_proxy_settings_6](preferance_proxy_settings_6.png)

![preference_cores_cpu_settings_7](preference_cores_cpu_settings_7.png)

5\. Click through the screens to login and agree to terms. At the **Select Edition to Install** screen select **Vivado HL WebPACK** and click **Next**

![vivado_hl_webpack_8](vivado_hl_webpack_8.png)

The features of each edition are (from \[[<u><span>link</span></u>](https://www.xilinx.com/products/design-tools/vivado/vivado-webpack.html)\]):

![edition_features_9](edition_features_9.png)

The devices that are supported in the WebPACK are (from \[[<u><span>link</span></u>](https://www.xilinx.com/products/design-tools/vivado/vivado-webpack.html#architecture)\]):

![webpack_supported_devices_10](webpack_supported_devices_10.png)

6\. At the Vivado HL WebPACK screen ensure you (A) click the Software Development Kit (SDK) check box before (B) clicking **Next**:

![ensure_sdk_checked_11](ensure_sdk_checked_11.png)

If you don't have enough space to install you'll see a the installation directory text as red:

![not_enough_disk_space_12](not_enough_disk_space_12.png)

Note 2: if you're installing for all users make sure you click **All users**! I have not found a way to fix this after the fact with an existing install. I have had to uninstall and reinstall the release.

![check_all_users_13](check_all_users_13.png)

7\. If you have enough room (see note above about **All users** if you need to install for All users). Click **Next**

![next_install_14](next_install_14.png)

8\. Click **Install** on the **Installation Summary** screen:

![installation_summary_15](installation_summary_15.png)

8\. At the **Vivado License Manager 2016.4** page, you can simply click the \[x\] to close the License Manager. Everything will still work.

![close_license_manager_16](close_license_manager_16.png)

9\. Click Yes

![confirm_exit_17](confirm_exit_17.png)

You should see:

![installation_completed_successfully_18](installation_completed_successfully_18.png)

Click **OK**.