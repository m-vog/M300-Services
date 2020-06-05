# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.define "web" do |web|
    web.vm.box = "centos/8"
    web.vm.hostname = "cent8-web01"
    web.vm.network "public_network", ip: "192.168.1.10"
      web.vm.network "forwarded_port", guest: 80, host:8080, auto_correct:true
      web.vm.provider "virtualbox" do |vb|
        vb.memory = "1024"
        vb.gui = false
      end
      #web.vm.synced_folder ".", "/var/www/html"
      web.vm.provision "shell", inline: <<-SHELL
            dnf install -y httpd mariadb-server
            systemctl enable httpd
            systemctl enable mariadb
            systemctl start httpd
            systemctl start mariadb
            systemctl status httpd
SHELL
        end
end