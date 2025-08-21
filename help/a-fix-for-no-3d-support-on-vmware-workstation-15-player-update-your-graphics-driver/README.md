# A fix for "No 3D support" on VMWare Workstation 15 Player: update your graphics driver

![vmware_workstation_logo](vmware_workstation_logo.png)

This post presents a fix for "No 3D support" on VMWare Workstation 15 Player: update your graphics driver. It also shows some additional details on what I did to debug this issue.

**<u><span>Tested On</span></u>**

This fix was tested on a Dell Precision 3800.

**<u><span>The Fix</span></u>**

Update your graphics driver.

**<u><span>Detail</span></u>**

I saw the following error in my vmware.log at "C:\\Users\\zpfeffer\\Documents\\Virtual Machines\\ubuntu-16.04.5-desktop-amd64-8gb\_ram-100gb\_disk-4\_core\\vmware.log" on my machine:

**2019-09-29T11:13:34.464-04:00| mks| I125: MKS-RenderMain: Failed to start the renderer DX11Renderer**

I ran **Device Manager** and saw that the generic Microsoft driver was used for the **Display adapter**.

I went to Dell's website and ran **Support Assist** on the Dell. **Support Assist** identified that the graphics driver was out of date. I downloaded and installed it.

I reran VMWare Workstation 15 Player and did not see the No 3D support error. I also looked at vmware.log and did not see the DX11Renderer error.

**<u><span>Reference</span></u>**

From [https://communities.vmware.com](https://communities.vmware.com/): Solved: WS15 disables 3D acceleration @ [[link](https://communities.vmware.com/thread/597620)]

From  [https://en.wikipedia.org](https://en.wikipedia.org/wiki/VMware_Workstation_Player): VMWare Workstation Player Icon @ [[link](https://en.wikipedia.org/wiki/VMware_Workstation_Player)]