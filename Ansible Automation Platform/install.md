# Ansible Automation Platform Containerized 2.5.13

This document provides a step-by-step guide to install **Ansible Automation Platform Containerized 2.5.13** on **Red Hat Enterprise Linux 9.6**.

---

## Tech Specs

- Operating System: Red Hat Enterprise Linux 9.6  
- Memory: 6 GiB  
- CPU: 4 cores  
- Bundle: ansible-automation-platform-containerized-setup-bundle-2.5-13-aarch64

---

## Pre-requisites

Set the hostname:
```
hostnamectl set-hostname ansible.local
```

Register the system:
```
subscription-manager register
```

Install necessary packages:
```
sudo dnf install -y ansible-core wget git-core rsync vim
```

---

## Download the Setup Bundle

Download the Ansible Automation Platform containerized bundle for your architecture:

https://access.redhat.com/downloads/content/480/ver=2.5/rhel---9/2.5/x86_64/product-software

Ensure the file name is:
```
ansible-automation-platform-containerized-setup-bundle-2.5-13-aarch64
```

---

## Unpack the Bundle

After downloading, extract the contents and configure the bundle directory. For example:

```
bundle_dir=/home/appuser/Downloads/ansible-automation-platform-setup-bundle-2.5-13-aarch64/bundle
```

Make sure this path reflects the actual location on your machine.

---

## Inventory File

Use the provided `inventory-growth` file for the installation. You can find it in the repository here:  
🔗 [inventory-growth.txt](https://github.com/mmintah00/labs/blob/main/Ansible%20Automation%20Platform/inventory-growth.txt)

You may need to edit it according to your environment. Most importantly, update the `bundle_dir` value inside the inventory file to match the path used above.

---

## Set Ansible Collections Path

Export the collections path as follows:

```
export ANSIBLE_COLLECTIONS_PATH=/home/appuser/Downloads/ansible-automation-platform-containerized-setup-bundle-2.5-13-aarch64/collections/
```

---

## Run the Installer

Run the playbook using the inventory file:

```
ansible-playbook -i inventory-growth ansible.containerized_installer.install
```

---

## forgotten EDA admin password

execute the command below

```
podman secret  ls
```

```
podman secret inspect --showsecret eda_admin_password | jq -r .[].SecretData
```

---

## Notes

- Ensure the machine meets the hardware requirements.
- Adjust firewall and SELinux settings as needed.
- Double-check the inventory file paths and credentials.
- Internet access may be required for pulling containers unless preloaded.

---

## Resources

- Ansible Automation Platform Documentation: https://docs.ansible.com/
- Red Hat Customer Portal: https://access.redhat.com
