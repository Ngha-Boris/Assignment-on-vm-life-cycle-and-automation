# Assignment on VM lifecycle and automation

This repository contains three small tasks demonstrating VM lifecycle operations and basic automation using VMware, Vagrant, and cloud-init with Multipass.

## Tasks overview

- Task 1 — VMware: Create, export, and import a VM
	- Summary: Walks through creating a new virtual machine in VMware Workstation, installing Ubuntu Server, exporting the VM to OVF, and importing the OVF back into VMware to verify the VM boots correctly.
	- See: [task-1/README.md](./task-1/README.md).

- Task 2 — Vagrant: Provision a VM with Vagrant
	- Summary: Shows how to install Vagrant (and VirtualBox as needed), bring up a VM using `vagrant up`, verify services (nginx, git, docker), and how to destroy the VM.
	- See: [task-2/vagrant-project/REAME.md](./task-2/vagrant-project/REAME.md).

- Task 3 — cloud-init + Multipass: Provision one or more VMs using cloud-init
	- Summary: Contains a `cloud-init.yaml` example for use with Multipass to automate provisioning (users, packages, and initial configuration). See the multipass example for details.
	- See: [task-3/cloud-init-multipass/REAME.md](./task-3/cloud-init-multipass/REAME.md)
