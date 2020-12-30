Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
end

$script = <<-'SCRIPTUNIT'

yum install -y epel-release mc nano
yum install -y pam_script
useradd test_user_no_wk
echo "test_user_no_wk:12345" | chpasswd
systemctl restart sshd
useradd test_user
groupadd admin
usermod -a -G admin test_user
echo "test_user:1234567" | chpasswd
sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config
sed -i "2i auth  required  pam_script.so"  /etc/pam.d/sshd
cat <<'EOT' > /etc/pam_script
#!/bin/bash
if [[ `grep $PAM_USER /etc/group | grep 'admin'` ]]
then
exit 0
fi
if [[ `date +%u` > 5 ]]
then
exit 1
fi
EOT
chmod +x /etc/pam_script
systemctl restart sshd

SCRIPTUNIT



Vagrant.configure("2") do |config|
  config.vm.provision "shell", inline: $script
end
