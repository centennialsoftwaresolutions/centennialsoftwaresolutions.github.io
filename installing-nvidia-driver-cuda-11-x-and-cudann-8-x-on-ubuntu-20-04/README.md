# Installing Nvidia Driver, Cuda 11.x, and CudaNN 8.x on Ubuntu 20.04

## Nvidia Driver

-   Go to Nvidia's [<u><span>driver download website</span></u>](https://www.nvidia.com/Download/index.aspx?lang=en-us) and find a menu that looks like this at the top of the page
    

![Nvidia_driver_downloads_1](Nvidia_driver_downloads_1.png)

-   The first three dropdown boxes just define which GPU you are using. Click through the options to select your GPU
    
-   "Download Type" should always be set to "Production Branch" and "Language" can be set to whatever you prefer
    
-   If using standard Ubuntu 20.04
    
    -   Select "Linux 64-bit" for the "Operating System" dropbox
    
-   If using WSL2
    
    -   Select "Windows 10 64-bit" or "Windows 11" for the "Operating System" dropbox
    
-   Click "Search"
    

![Geforce_game_ready_driver_2](Geforce_game_ready_driver_2.png)

-   Click "Download"
    
-   Open the terminal and run the installer (in the case of WSL2, it will be an exe file)
    

![Terminal_run_installer_3](Terminal_run_installer_3.png)

![Checking_system_compatibility_4](Checking_system_compatibility_4.png)

![Click_NVIDIA_graphics_driver_5](Click_NVIDIA_graphics_driver_5.png)

-   Click on "NVIDIA Graphics Driver", then "AGREE AND CONTINUE "
    

![Choose_express_6](Choose_express_6.png)

-   Choose "Express" then click "NEXT"
    

![Installer_execute_7](Installer_execute_7.png)

-   The installer will then execute
    

![NVIDIA_installer_finish_8](NVIDIA_installer_finish_8.png)

-   Then "CLOSE" the installer
    
-   Restart the terminal and then run the command

```
nvidia-smi
```

![Run_command_nvidia-smi_9](Run_command_nvidia-smi_9.png)

## Cuda

-   Get the new Nvidia keys
    

```
sudo apt-key del 7fa2af80
```

```
wget https://developer.download.nvidia.com/compute/cuda/repos/wsl-ubuntu/x86_64/cuda-wsl-ubuntu.pin
```

```
sudo mv cuda-wsl-ubuntu.pin /etc/apt/preferences.d/cuda-repository-pin-600
```

-   Check [<u><span>this chart</span></u>](https://docs.nvidia.com/deeplearning/cudnn/support-matrix/index.html) to see the latest version of CUDA that is supported by cuDNN
    

![Check_cuda_version_10](Check_cuda_version_10.png)

-   As you can see above, CUDA 11.6 is the latest version to be supported by cuDNN. Click on that number on the webpage to be redirected to the release page
    

![Confirm_cuda_version_11](Confirm_cuda_version_11.png)

-   You should not click any links here - just see that 11.6.2 in this case is the newest version of CUDA 11.6, so we will install that version
    
-   Set the CUDA version number that you would like to download in order of "XX.Y.Z". The example of downloading 11.6.2 is shown below. All the rest of the commands can be copy-pasted directly
    

```
export XX=11
export Y=6
export Z=2
```

-   Download the debian file
    

```
wget https://developer.download.nvidia.com/compute/cuda/${XX}.${Y}.${Z}/
local_installers/cuda-repo-wsl-ubuntu-${XX}-${Y}-local_${XX}.${Y}.${Z}-1_amd64.deb
```

-   Configure the installer to be available to the "apt" system
    

```
sudo dpkg -i cuda-repo-wsl-ubuntu-${XX}-${Y}-local_${XX}.${Y}.${Z}-1_amd64.deb
```

![Configure_installer_12](Configure_installer_12.png)

-   Install cuda
    

```
sudo apt update
sudo apt install cuda=${XX}.${Y}.${Z}-1 -y
```

![Install_cuda_13](Install_cuda_13.png)

-   Add CUDA to your system PATH. Open ~/.bashrc ("gedit ~/.bashrc") and add this line to the bottom of the file
    

```
export PATH=/usr/local/cuda/bin:${PATH}
```

-   Reflect those changes in your current terminal session

```
source ~/.bashrc
```

-   Check that your version of cuda is installed

```
nvcc --version
```

![Check_cuda_version_14](Check_cuda_version_14.png)

## CUDNN

-   Export the CUDA version, which can be found as shown above, using "nvcc --version"

```
export CUDA_VERSION=11.6
```

-   Install the CUDNN driver for ubuntu 20.04

-   Go the the [<u><span>CUDNN home page</span></u>](https://developer.nvidia.com/cudnn)

-   Click on "Download cuDNN"


![Download_cuDNN_15](Download_cuDNN_15.png)

-   Check "I Agree To the Terms..." and then click on "Download cuDNN vW.X.Y for CUDA ...". just choose the latest version
    

![Agree_to_terms_16](Agree_to_terms_16.png)

-   Click on "Local Installer for Ubuntu 20.04 x86\_64"
    

![Click_local_installer_ubuntu_20.04 x86_64_17](Click_local_installer_ubuntu_20.04 x86_64_17.png)

-   Configure the installer to be available to the "apt" system
    

```
sudo dpkg -i cudnn-local-repo-ubuntu2004-*_1.0-1_amd64.deb<span><span>sudo dpkg -i cudnn-local-repo-ubuntu2004-*_1.0-1_amd64.deb</span></span>
```

![Configure_installer_cudnn_18](Configure_installer_cudnn_18.png)

-   sudo apt update
    
-   Install CudaNN
    

```
sudo apt install libcudnn8=*-1+cuda${CUDA_VERSION}
```

```
sudo apt-get install libcudnn8-dev=*-1+cuda${CUDA_VERSION}
```

```
sudo apt-get install libcudnn8-samples=*-1+cuda${CUDA_VERSION}
```

-   Validate the install
    

```
cp /usr/src/cudnn_samples_v8/ $HOME -rfv
cd ~/cudnn_samples_v8/conv_sample
make clean
make -sj
./conv_sample
```

![Validate_install_19](Validate_install_19.png)