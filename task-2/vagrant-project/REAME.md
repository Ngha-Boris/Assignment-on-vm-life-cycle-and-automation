# Use Vagrant to Provision a VM

### Step 1: Install Vagrant

```bash
# Update package list
sudo apt update

# Install Vagrant
sudo apt install vagrant -y

# Verify installation
vagrant --version
```

### Step 2: Install virtual box

If you don't have virtualbox installed, install in from http://virtualbox.org/wiki/Linux_Downloads make sure the version you are installing aligns with the version of your ubuntu.

### Step 3: Create VM with Vagrant

```bash
cd ~task-2/vagrant-project
vagrant up

# This will:
# 1. Download the Ubuntu box (first time only)
# 2. Create the VM
# 3. Configure networking
# 4. Run provisioning scripts
```
###  Step 4: Verify Vagrant VM

```bash
# Check VM status
vagrant status

# SSH into the VM
vagrant ssh

# Once inside, verify installations:
nginx -v
git --version
docker --version

# Exit SSH
exit

# Test web server from host
curl http://localhost:8888
```

### Destroy the VM(oprional)
```bash
vagrant destroy
```