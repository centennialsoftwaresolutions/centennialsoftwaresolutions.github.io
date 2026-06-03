# Dell Mobile Precision 7750 

- Boot Menu: `F12` 
- System Setup: `F2`
- [Service Manual](precision-7550-7750-external-display-connection-guide_en-us.pdf)

# Diagnostics

## Does the System Board work (M-BIST)?

- Press and hold `M` and `power` to run. On **system board failure**, the **battery status LED** is solid **amber**. It's not on if the board passes. 

## Is the LCD powered by the system board (L-BIST)?

- Runs automatically during POST. On **no power to LCD (the screen)**, the **battery status LED** flashes **amber** twice (**2**) and **white** eight (**8**) times. 

## Does the display panel work (LCD-BIST)?

- Press and hold `M` and `power,` then release `M` and `power` when POST starts. The display should cycle through colors and reboot. Look for graphical anomalies. 

## System diagnostic lights

- **Battery-status light**: power and battery-charge status. Blinks amber and white, along with beeps for failures.
- **Solid white** when the power adapter is connected and the battery > 5%.
- **Amber** when running on battery, and the battery < 5%.   
- **Off** when the power adapter is connected, the battery is fully charged, the battery is> 5%, or the computer is in **sleep**, **hibernation**, or **off**.  	

## System diagnostic light codes

### Example

A **diagnostic light code** of **[2,3]** means the power and battery-status light blinks **amber** twice (**2**), then pauses, then blinks **white** three times (**3**), then pauses, in a **loop** until the **computer is turned off**. 

| Diagnostic light codes | Problem description                                  | Recommended Solution                                         |
| ---------------------- | ---------------------------------------------------- | ------------------------------------------------------------ |
| **1,1**                | TPM Detection Failure                                | Replace System Board                                         |
| **1,2**                | Unrecoverable SPI Flash Failure                      | Replace System Board                                         |
| **1, 5**               | EC unable to program i-Fuse                          | Replace System Board                                         |
| **1, 6**               | Generic catch-all for ungraceful EC code flow errors | Disconnect all power source (AC, battery, coin cell) and drain flea power by pressing & holding down power button |
| **2,1**                | CPU failure                                          | Run the Intel CPU diagnostics tools. If problem persists, replace the system board |
| **2,2**                | Motherboard covers BIOS corruption or ROM error      | Flash latest BIOS version. If problem persists, replace the system board |
| **2,3**                | No Memory/RAM detected                               | Confirm that the memory module is installed properly. If problem persists, replace the memory module |
| **2,4**                | Memory/RAM Failure                                   | Reset the memory module. If problem persists, replace the memory module |
| **2,5**                | Invalid memory installed                             | Reset the memory module. If problem persists, replace the memory module |
| **2,6**                | Motherboard/Chipset Error                            | Flash latest BIOS version. If problem persists, replace the system board |
| **2,7**                | LCD failure - SBIOS message                          | Flash latest BIOS version. If problem persists, replace the LCD module |
| **2,8**                | LCD failure - EC detection of power rail failure     | Replace the system board                                     |
| **3,1**                | CMOS battery failure                                 | Reset the CMOS battery connection. If problem persists, replace the RTC battery |
| **3,2**                | PCI of Video card/chip failure                       | Replace the system board                                     |
| **3,3**                | BIOS Recovery Image not found                        | Flash latest BIOS version. If problem persists, replace the system board |
| **3,4**                | Recovery Image found but invalid                     | Flash latest BIOS version. If problem persists, replace the system board |
| **3,5**                | EC ran into power sequencing failure                 | Replace the system board                                     |
| **3,6**                | Flash corruption detected by SBIOS                   | Replace the system board                                     |
| **3,7**                | Timeout waiting on ME to reply to HECI message       | Replace the system board                                     |

Info from [link](https://www.dell.com/support/manuals/en-us/precision-17-7750-laptop/precision7750_sm/system-diagnostic-lights?guid=guid-41650b44-1ac7-4d87-b9a1-f9fecd0f1b7c&lang=en-us). 

