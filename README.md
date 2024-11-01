# Creating a Custom ESXi Installer Image

Creating a custom ESXi installer image can help streamline deployments by including drivers, configurations, and custom software in a single bootable image. Here’s a guide on how to create one.

## Requirements

1. **VMware PowerCLI** installed.
2. **ESXi-Customizer-PS** (for PowerCLI) – This PowerShell script helps create custom ESXi images.
3. **VMware vSphere ESXi ISO** – The base ISO image from VMware’s website.
4. **VIB (VMware Installation Bundle) files** – Any drivers or packages you want to include.

## Steps

### 1. Install PowerCLI and ESXi-Customizer-PS
   - Install PowerCLI if it’s not already installed:
     ```powershell
     Install-Module -Name VMware.PowerCLI
     ```
   - [Download the ESXi-Customizer-PS PowerShell script](https://www.v-front.de/p/esxi-customizer-ps.html).

### 2. Download the ESXi ISO
   - Visit the VMware [download page](https://customerconnect.vmware.com/) and download the ESXi ISO file.

### 3. Obtain VIB Files
   - If you need specific drivers or tools, download them as VIB files. Ensure they are compatible with your ESXi version.

### 4. Prepare the Custom ESXi ISO
   - Open PowerShell as Administrator.
   - Import PowerCLI and run the ESXi-Customizer-PS script.
   
   ```powershell
   Import-Module VMware.PowerCLI
   Set-ExecutionPolicy Unrestricted -Scope Process
