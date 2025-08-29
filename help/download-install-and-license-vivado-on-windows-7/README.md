# Download, Install and License Vivado 2017.4 on Windows 7

This post lists the step-by-step instructions for downloading and installing Vivado 2017.4 on a Windows 7 machine and getting a 30-day evaluation license.

**Download Vivado**

1\. Go to [https://www.xilinx.com/products/design-tools/vivado.html](http://www.xilinx.com/products/design-tools/vivado.html)

and click on **Download Vivado Design Suite - HLX Editions**.

![download_vivado_design_suite_1](download_vivado_design_suite_1.png)

...and click on **Vivado HLx 2017.4: All OS installer Single-File Download**:

![click_vivado_hlx_2017_4_2](click_vivado_hlx_2017_4_2.png)

..and Sign in and click through the export acceptance.

[2. Go to ](http://www.7-zip.org/)http://www.7-zip.org/[ ](http://www.7-zip.org/)

Get 64-bit version: http://www.7-zip.org/a/7z1801-x64.exe

3\. Double click on it and install it.

4\. Right click on the tar.gz and select **Extract to Xilinx\_SDK\_2017.4\_1216\_1.tar**

![extract_to_xilinx_sdk_2017_4_3](extract_to_xilinx_sdk_2017_4_3.png)

5\. Open the resulting directory named **Xilinx\_SDK\_2017.4\_1216\_1.tar** and right click on **Xilinx\_Vivado\_SDK\_2017.4\_1216\_1.tar.** It took my T460 about a minute and and a half to extract the archive.

![extract_7_zip_here_4](extract_7_zip_here_4.png)

6\. Click on xsetup. Then Click Yes to allow Windows to install it.

![allow_windows_to_install_xsetup_5](allow_windows_to_install_xsetup_5.png)

xsetup will launch

![xsetup_launching_6](xsetup_launching_6.png)

7\. Click **Next>**. Check all the **Agree** boxes. Click **Next>**. Select **Vivado HL System Edition**. Click **Next>**.

8\. Ensure the **Software Development Kit (SDK)** and **Engineering Sample Devices** are checked.

![ensure_sdk_and_engineering_sample_devices_checked_7](ensure_sdk_and_engineering_sample_devices_checked_7.png)

9\. Click **Next>**.

10\. Install into **C:\\Xilinx** (the default). Click **Next>** and accept to have the installer create C:\\Xilinx. Note the installation take 43.41 GBs of diskspace.

![install_to_c_xilinx_8](install_to_c_xilinx_8.png)

11\. Now click install on the **Installation Summary** screen.

![installation_summary_screen_9](installation_summary_screen_9.png)

12\. Disconnect any JTAG cables and click okay.

![disconnect_jtag_cables_10](disconnect_jtag_cables_10.png)

13\. Click **Always trust software from "Jungo LTD"** and click **Install**.

![trust_software_from_jungo_ltd_11](trust_software_from_jungo_ltd_11.png)

14\. Click **Always trust software from "Xilinx".** and click **Install**.

![trust_software_from_xilinx_12](trust_software_from_xilinx_12.png)

15\. Click **Always trust software from "Thesycon Software".** and click **Install**.

![trust_software_from_thesycon_software_13](trust_software_from_thesycon_software_13.png)

16\. Ignore the MATLAB warning. Click **Ok** and **Ok** again**.**

![ignore_matlab_warning_14](ignore_matlab_warning_14.png)

If you miss any of these or accidentally select No (like I did when I accidentally clicked No on the Xilinx device software select **Add Design Tools or Devices 2017.4** after installation completes.

![all_vivado_tools_installed_15](all_vivado_tools_installed_15.png)

Select the **Install Cable Drivers (You MUST disconnect all Xilinx Platform Cable USB II cables before proceeding)** checkbox.

![select_install_cable_drivers_16](select_install_cable_drivers_16.png)

The click through to install the one you accidentally missed.

**Licensing**

1\. Click the **Get Vivado or IP Evaluation Licenses** radio button and click **Connect Now**.

![get_vivado_or_ip_evaluation_licenses_17](get_vivado_or_ip_evaluation_licenses_17.png)

2\. Accept the Name and Address Verification (again).

![accept_name_and_address_verification_18](accept_name_and_address_verification_18.png)

3\. Select the **Vivado HLS Evaluation License** and click **Generate Node Locked License**.

![generate_node_locked_license_19](generate_node_locked_license_19.png)

4\. Select your **Disk** (since it likely won't change in 30 days) and Click **Next** and **Next** again.

![select_disk_20](select_disk_20.png)

5\. You'll get something like this text:

![license_message_21](license_message_21.png)

6\. Check your email. The directions for Windows listed in the email appear wrong. Save the license to **C:\\licenses\\Xilinx.lic**. In the License Manager enter C:\\licenses\\Xilinx.lic into XILINXD\_LICENSE\_FILE and click Set.

![save_license_22](save_license_22.png)

7\. Close all Xilinx related programs (except the License Manager from Xilinx - a point missing from the Information Message) and click OK.

![close_all_xilinx_programs_23](close_all_xilinx_programs_23.png)

8\. Now launch Vivado.

![launch_vivado_24](launch_vivado_24.png)

**Notes**

Specific machine specs listed at [link](http://www.zachpfeffer.com/single-post/2017/01/28/New-T460-System-Information).