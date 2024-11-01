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
   ```

### 5. Run the ESXi-Customizer-PS Script
   - Navigate to the ESXi-Customizer-PS directory and execute the script with custom options:

   ```powershell
   .\ESXi-Customizer-PS.ps1 -izip C:\Path\to\ESXi.zip -pkgDir C:\Path\to\VIBs -outDir C:\Path\to\output
   ```

-   **Parameters**:
    -   `-izip`: The path to the downloaded ESXi ZIP file.
    -   `-pkgDir`: The directory containing VIB files for custom drivers or applications.
    -   `-outDir`: The output directory where the custom ISO will be saved.

### 6. Verify the ISO

-   The script generates an ISO in the specified output directory. Boot a virtual machine or physical server with it to verify it works as expected.

### 7. Additional Options (Optional)

-   **Add Acceptance Level**: If needed, specify an acceptance level for VIBs with `-vibAcceptanceLevel`.
-   **Add Configuration**: Use kickstart scripts to automate additional setup.

Example
-------

Here's an example command to create an image that includes specific VIBs and sets an output path:

   ```powershell
   `.\ESXi-Customizer-PS.ps1 -izip C:\Install\VMware-ESXi-7.0.0.zip -pkgDir C:\Install\VIBs -outDir C:\CustomESXi`
   ```
