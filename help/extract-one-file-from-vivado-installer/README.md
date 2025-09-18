# Extract One File From the "Vivado Installer"
You may need this if you accidentally delete a file and don't want to re-extract everything.
## Get the path of the file you need:
```bash
tar -tvf FPGAs_AdaptiveSoCs_Unified_SDI_2025.1_0530_0145.tar | grep installLibs.sh
```
### Example Output
```bash
# -rwxr-xr-x xbuild/hd       5721 2025-05-22 00:08 FPGAs_AdaptiveSoCs_Unified_SDI_2025.1_0530_0145/installLibs.sh
```
## Get just that file:
```bash
tar -xf FPGAs_AdaptiveSoCs_Unified_SDI_2025.1_0530_0145.tar FPGAs_AdaptiveSoCs_Unified_SDI_2025.1_0530_0145/installLibs.sh
```
