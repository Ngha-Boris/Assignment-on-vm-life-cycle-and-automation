# Create, Export, and Import a VM in VMware

## Step 1: Create a New Virtual Machine

### Open VMware Workstation

Launch VMware from your Ubuntu applications menu

### Create New VM

Click "File" → "New Virtual Machine"  
Select "Typical (recommended)" → Click "Next"

### Select Installation Media

Choose "Installer disc image file (iso)"  
Click "Browse" and select an ISO file (I recommend Ubuntu Server 22.04 LTS - download from ubuntu.com if you don't have one)  
Click "Next"

### Configure VM Details

VM Name: Enter a name (e.g., "TestVM")  
Location: Choose where to store VM files (default is fine)  
Click "Next"

### Specify Disk Capacity

Maximum disk size: 20 GB is sufficient  
Select "Store virtual disk as a single file"  
Click "Next"

### Review and Finish

Click "Finish"

---

## Step 2: Install Operating System

### Start the VM

The VM will boot from the ISO  
Follow the Ubuntu installation prompts:

- Language: English  
- Keyboard: Select your layout  
- Installation type: "Ubuntu Server (minimized)"  
- Network: Use DHCP (default)  
- Storage: Use entire disk  
- Profile setup:
  - Your name: testuser  
  - Server name: testvm  
  - Username: testuser  
  - Password: (choose a password)

SSH: Check "Install OpenSSH server"  
Featured snaps: Skip (press Enter)

Wait for installation to complete  
Select "Reboot Now"

### Login to verify

After reboot, login with your credentials  
Run: sudo apt update && sudo apt upgrade -y  
Shutdown the VM: sudo shutdown -h now

---

## Step 3: Export VM to OVF Format

### Export the VM

In VMware, ensure the VM is powered off  
Click "File" → "Export to OVF"  
Or right-click on the VM in library → "Manage" → "Export to OVF"

### Configure Export Settings

Name: TestVM_Export  
Directory: Choose a location (e.g., /home/yourusername/VMExports/)  
Format: Select "OVF" (not OVA, as OVF is more flexible)  
Description: Add optional description  
Click "Export"

### Wait for Export

This creates three files:

- .ovf (XML configuration file)  
- .vmdk (virtual disk file)  
- .mf (manifest file with checksums)

---

## Step 4: Import VM from OVF

### Import the OVF

Click "File" → "Open"  
Navigate to your export directory  
Select the .ovf file  
Click "Open"

### Configure Import

Name: TestVM_Imported (rename to distinguish from original)  
Storage path: Choose location for new VM files  
Click "Import"

### Wait for Import

VMware will convert and import the VM

---

## Step 5: Verify New VM Boots

### Power On Imported VM

Select the imported VM  
Click "Power on this virtual machine"

### Verify Boot

Wait for boot to complete  
Login with the same credentials (testuser/password)  
Verify system is working:

```bash
hostname
ip addr show
df -h
uname -a
