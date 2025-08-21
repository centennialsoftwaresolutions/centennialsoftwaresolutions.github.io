# Are HDF Files Going Away?

![xilinx_logo_1](xilinx_logo_1.png)

This post looks at statements made in the 2018.1 and 2018.2 versions of the **PetaLinux Tools Reference Guide** that seem to indicate that Xilinx decided against removing HDF files.

**<u><span>Warnings Removed?</span></u>**

The 2018.2 version of the **PetaLinux Tools Reference Guide** contains this:

![revision_history_2](revision_history_2.png)

**<u><span>What does DSA stand for?</span></u>**

From page 20:

**_Note_**_:_ Device Support Archive (DSA) is hardware description format introduced in Vivado. DSA is super set of HDF holding additional configurations that can be changed by XSCT/XSDK.

**<u><span>"Removed DSA warning and recommendations throughout the book"</span></u>**

I compared the 2018.1 and 2018.2 versions of the **PetaLinux Tools Reference Guide**. Here were the differences of substance:

**Note**: In the following differences, 2018.1 is on the left and 2018.2 is on the right.

**[#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1) (page 20,21):**

![warning_removed_1_3](warning_removed_1_3.png)

Highlighted: In **2018.1** it says: **the HDF file will be deprecated in the future releases of Vivado and PetaLinux. Currently, PetaLinux supports both HDF and DSA files**. In **2018.2,** this warning is not present.

**[#2](https://www.centennialsoftwaresolutions.com/blog/hashtags/2) (page 24):**

![warning_removed_2_4](warning_removed_2_4.png)

**[#3](https://www.centennialsoftwaresolutions.com/blog/hashtags/3) (page 127):**

![trademarks_added_5](trademarks_added_5.png)

Highlighted: 2018.1 is missing the line: AMBA, AMBA Designer, Arm, ARM1176JZ-S, CoreSight, Cortex, PrimeCell, Mali, and MPCore are trademarks of Arm Limited in the EU and other countries

**<u><span>Commentary</span></u>**

A Google search for **site:xilinx.com HDF deprecated** turned up no other relevant info, like an announcement from Xilinx.

**<u><span>Call to Action</span></u>**

Do you know what the story is with the DSA vs. HDF? If so, post a comment.

**<u><span>References</span></u>**

-   The 2018.1 \[[link](https://www.xilinx.com/support/documentation/sw_manuals/xilinx2018_1/ug1144-petalinux-tools-reference-guide.pdf)\] and 2018.2 \[[link](https://www.xilinx.com/support/documentation/sw_manuals/xilinx2018_2/ug1144-petalinux-tools-reference-guide.pdf)\] versions of _ug1144-petalinux-tools-refence-guide.pdf_ were compared using [https://draftable.com](https://draftable.com/).
    
-   Xilinx logo found via [https://twitter.com/xilinxinc](https://twitter.com/xilinxinc) at \[[link](https://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]
    

**<u><span>Other Info</span></u>**

**What is a CR update?**

**CR update** is not defined in the document.