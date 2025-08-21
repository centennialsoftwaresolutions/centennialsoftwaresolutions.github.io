# Fix E_FAIL Virtual Machine **Launch**

![virtualbox_logo_1](virtualbox_logo_1.png)

**<u><span>Short</span></u>**

Right-click Discard Saved State... to fix E\_FAIL (0x80004005) on Version 5.2.12 r122591 (Qt5.6.2).

**<u><span>Step-by-Step</span></u>**

If you see this error:

![e_fail_message_2](e_fail_message_2.png)

Right click on the virtual machine you tried to start:

![right_click_virtual_machine_3](right_click_virtual_machine_3.png)

...and click **Discard Saved State...**

![discard_saved_state_4](discard_saved_state_4.png)

Click **Discard**

![click_discard_5](click_discard_5.png)

Then start the virtual machine.

**<u><span>Text of Error</span></u>**

VirtualBox - Error

Failed to open a session for the virtual machine **machine-name**.

The VM session was closed before any attempt to power it on.

Result Code:

E\_FAIL (0x80004005)

Component:

SessionMachine

Interface:

ISession {7844aa05-b02e-4cdd-a04f-ade4a762e6b7}

**<u><span>References</span></u>**

-   Answer to https://www.virtualbox.org/ticket/6930 by Democritus
    
-   VirtualBox logo from \[[link](https://linux.systeminside.net/como-instalar-y-configurar-virtualbox/)\]