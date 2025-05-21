#Ansible Automation platform containerized 2.5.13

Tech Specs
Redhat 9.6
Memory 6 GiB
CPU 4 cores

ansible-automation-platform-containerized-setup-bundle-2.5-13-aarch64


Pre-requisites
#set hostname
hostnamectl set-hostname ansible.local

#Register using subscription manager
subscription-manager register

#install pre-requisites
sudo dnf install -y ansible-core wget git-core rsync vim


#download the Ansible Automation platform containerized bundle
https://access.redhat.com/downloads/content/480/ver=2.5/rhel---9/2.5/x86_64/product-software

#unpack and add the inventory growth file attached
ensure you modify the bundle_dir in my case
bundle_dir=/home/appuser/Downloads/ansible-automation-platform-setup-bundle-2.5-12-aarch64/bundle

Refer to inventory growth file for installation