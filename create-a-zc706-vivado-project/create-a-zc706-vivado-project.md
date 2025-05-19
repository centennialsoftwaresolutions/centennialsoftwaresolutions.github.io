# Create a ZC706 Vivado Project

![xilnx_logo_1](xilnx_logo_1.png)

This post lists the steps to create a Vivado project for a ZC706 and to check the version of the ZC706 you're using.

**<u><span>Versions Used</span></u>**

-   Vivado 2018.2
    
-   ZC706 Rev 2.0 Board
    

**<u><span>Steps</span></u>**

Step 1: Create a directory called **c:\\vivprjs**

Step 2: Launch **Vivado 2018.2**

Step 3: Click **Create Project**

Step 4: At the **Create a New Vivado Project** click **Next >**

![create_new_vivado_project_2](create_new_vivado_project_2.png)

Step 5:

A) Use **Project name: vhdl1**

B) Use **Project location: c:/vivadoprjs.**

C) Leave the **Create project subdirectory** check-box **checked**.

D) The wizard page should list: **Project will be created at: C:/vivadoprjs/vhdl1.**

E) Click **Next >**

![project_name_3](project_name_3.png)

Step 6:

A) Leave **RTL Project selected**

B) Leave **Do not specify sources at this time checked**

C) Click **Next >**

![project_type_4](project_type_4.png)

Step 7:

A) Click **Boards**

B) Select [**xilinx.com**](http://xilinx.com/) 

C) Select **Latest**

D) Type **ZC706**

E) Click on the **ZYNQ-7 ZC706 Evaluation Board box** to select the ZYNQ-7 ZC706

F) Click **Next >**

![select_board_5](select_board_5.png)

Note on **Board Rev**:

You should ensure that the Board Rev listed on the board (see \[[<u><span>link</span></u>](https://www.xilinx.com/support/answers/62325.html)\] to answer **How can I determine what Board Revision I am using?**). On the 2.0 version of the ZC706 board the rev number is here:

![check_board_rev_6](check_board_rev_6.png)

You'll notice that we only have **Version 1.4** available. From \[[<u><span>link</span></u>](https://www.xilinx.com/products/boards-and-kits/ek-z7-zc706-g.html#documentation)\] you can download the UCF and XDC files:

![download_board_schematics_7](download_board_schematics_7.png)

In this archive it says in the **readme.txt:**

**"**No XDC or UCF changes from Revision 1.0 through Revision 2.0.**"**

So the fact that it only lists 1.4 is not a problem since the XDC and UCF files are what change when you update the version.

Here are some pictures of the rest of the columns:

![board_columns_8](board_columns_8.png)

![board_columns_9](board_columns_9.png)

![board_columns_10](board_columns_10.png)

Step 8: Click **Finish** on the **New Project Summary** page

![finish_new_project_summary_11](finish_new_project_summary_11.png)

You should see:

![project_finished_12](project_finished_12.png)

**<u><span>Reference</span></u>**

Xilinx logo from https://twitter.com/xilinxinc