 # Cloud-Init Configuration with Multipass

 ### Step 1: Install Multipass if not installed yet

```bash
# Install Multipass
sudo snap install multipass

# Verify installation
multipass version
```

### Launch VM with Cloud-Init Configuration

```bash
# enter directory
cd ~task-3/cloud-init-multipass

# Launch the VM with cloud-init
multipass launch --name cloudinit-demo --cloud-init cloud-init.yaml

# This will:
# 1. Download Ubuntu cloud image (first time only)
# 2. Create the VM
# 3. Apply cloud-init configuration on first boot
# 4. Install all packages
# 5. Configure all services
```
*Note:* The first boot will take 3-5 minutes as cloud-init installs packages and configures everything.

### Step 2: Monitor Cloud-Init Progress
```bash
# Check VM status
multipass list

# Watch cloud-init progress (in another terminal)
multipass exec cloudinit-demo -- cloud-init status --wait

# Or follow the cloud-init log
multipass exec cloudinit-demo -- sudo tail -f /var/log/cloud-init-output.log
```

### Step 3: Verify Cloud-Init Configuration
```bash
# SSH into the VM
multipass shell cloudinit-demo

# Once inside, verify the configuration:

# 1. Check cloud-init status
cloud-init status

# 2. View cloud-init logs
sudo cat /var/log/cloud-init.log | tail -50

# 3. Check installed packages
nginx -v
docker --version
git --version

# 4. Verify users were created
cat /etc/passwd | grep -E 'clouduser|adminuser'

# 5. Check services are running
sudo systemctl status nginx
sudo systemctl status docker

# 6. Check firewall
sudo ufw status

# 7. Test nginx
curl http://localhost

# 8. Test Docker container
curl http://localhost:8080

# 9. Run the system info script
system-info.sh

# 10. Check README files
cat ~/README.txt

# 11. View MOTD
cat /etc/motd

# Exit the VM
exit
```
### Step 4: Access the Web Server from Host
```bash
# Get the VM's IP address
multipass list

# Or use curl from host
curl http://$(multipass info cloudinit-demo | grep IPv4 | awk '{print $2}')
```

### Step5: View Cloud-Init Configuration Details

```bash
# View the cloud-init configuration that was applied
multipass exec cloudinit-demo -- sudo cat /var/lib/cloud/instance/cloud-config.txt

# View all cloud-init modules that ran
multipass exec cloudinit-demo -- sudo cloud-init analyze show

# View timing information
multipass exec cloudinit-demo -- sudo cloud-init analyze dump
```