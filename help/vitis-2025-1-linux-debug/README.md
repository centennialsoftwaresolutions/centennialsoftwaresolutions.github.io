# Launch Vitis 2025.1 with Debugging

Run to launch Vitis with full Electron and Xilinx debugging:

```
# Create/Enter Workspace
mkdir -p ~/zcu102_petalinux/ws/
cd ~/zcu102_petalinux/ws

# Add XILINX_VITIS to env
source /home/demo/amd/v20251/2025.1/Vitis/settings64.sh 

# Launch Vitis in debug mode and tee the output to a file and the console.
set -x && \
sed 's/> \/dev\/null 2>&1 &//' "${XILINX_VITIS}/bin/vitis" > "${XILINX_VITIS}/bin/vitis-debug" && \
chmod +x "${XILINX_VITIS}/bin/vitis-debug" && \
RDI_VERBOSE=True ELECTRON_ENABLE_LOGGING=1 ELECTRON_DEBUG=1 \
vitis-debug -w . 2>&1 | tee vitis-debug.log
```

