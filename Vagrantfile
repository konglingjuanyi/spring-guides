# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.network "forwarded_port", guest: 6379, host: 6379
  config.vm.network "forwarded_port", guest: 5672, host: 5672
  config.vm.network "forwarded_port", guest: 27017, host: 27017

  config.vm.provision "shell", inline: <<-SHELL
      apt-get update > /dev/null

      apt-get -y install redis-server
      sed -i 's/^bind/#\ bind/' /etc/redis/redis.conf
      service redis-server restart

      apt-get -y install rabbitmq-server

      apt-get -y install mongodb
      sed -i 's/^bind_ip/#bind_ip/' /etc/mongodb.conf
      service mongodb restart
  SHELL
end
