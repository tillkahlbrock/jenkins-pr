# -*- mode: ruby -*-
# vi: set ft=ruby :

$script = <<SCRIPT
if `tty -s`; then
   mesg n
fi
wget -q -O - http://pkg.jenkins-ci.org/debian/jenkins-ci.org.key | sudo apt-key add -
sh -c 'echo deb http://pkg.jenkins-ci.org/debian binary/ > /etc/apt/sources.list.d/jenkins.list'
apt-get -y update
apt-get -y install openjdk-7-jre openjdk-7-jdk jenkins
apt-get clean
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "raring64"
  config.vm.provision "shell", inline: $script
  config.vm.network "forwarded_port", guest: 8080, host: 8080
end
