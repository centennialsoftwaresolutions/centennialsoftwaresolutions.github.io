# AMD Unified Installer for FPGAs & Adaptive SoCs: Windows Self-Extracting Web Installer “Stuck”?

If you’re running the **AMD Unified Installer** on Windows and it looks like it has frozen, it may **not actually be stuck**.

The installer is busy copying and verifying **thousands of small files**. On slower storage (like many USB drives) or when antivirus software scans every file operation, progress can appear to grind to a halt, because updates to the UI are very slow.

If you leave it running, it should eventually finish. Using a faster drive or pointing `TMP`/`TEMP` to a speedier location can also help. See [USB Drive AMD/Xilinx Tools 30-Min Web Install](../install-vivado-on-usb-drive).

## Observations

- The installer performs about the same on **Windows** as it does on **Linux** when using a VHD.
- It’s encouraging to see that **AMD is evolving the installer**. A few changes could make the experience even smoother:
  - **Show file copy progress** - An output window with filenames or a counter would help users distinguish between “hung” and “just slow.”
  - **Improve cancellation** - Currently, canceling doesn’t stop the installer right away; it continues copying files. If the copy process honored a stop signal before each new operation, cancellation would feel responsive.
  - **Set `TMP` and `TEMP` automatically** - Giving users an option to redirect temp files to a faster drive would avoid recommending that they disable antivirus protection, which is both risky and inconvenient.
  - **Skip re-downloads** — If files are already present, the installer should reuse them instead of fetching them again, saving time and bandwidth.

These improvements could reduce “stuck installer” support requests and free up time for AMD and its users to focus on more complex challenges.



