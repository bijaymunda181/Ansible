## 🧩 Step-by-Step: Install Ansible on CentOS
## 🥇 Step 1: Update your system
sudo yum update -y

## 🥈 Step 2: Enable the EPEL repository

Ansible is available in the EPEL (Extra Packages for Enterprise Linux) repo.

sudo yum install epel-release -y

## 🥉 Step 3: Install Ansible
sudo yum install ansible -y

## 🧾 Step 4: Verify installation
ansible --version


You should see output similar to:

ansible [core 2.9.27]
  python version = 3.x.x
