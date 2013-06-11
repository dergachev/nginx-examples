# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "precise64"

  config.vm.provision :shell, :inline => <<-EOT
    apt-get update
    apt-get -y install vim curl git nginx
    ln -s /vagrant/nginx-conf/conditional-blocking /etc/nginx/sites-enabled/conditional-blocking
    service nginx restart
  EOT

  # now run some tests
  config.vm.provision :shell, :inline => <<-EOT
    curl localhost:8000/
  EOT
end
