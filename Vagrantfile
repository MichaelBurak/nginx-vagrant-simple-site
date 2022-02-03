# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.33.10"

  config.vm.provision "file", source: "./simple-site", destination: "/tmp/"

  # Provisioning with a shell script. 
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y nginx
    
    # Adds /var/www/simple-site/html.index.html with Hello World
    mkdir -p /var/www/simple-site/html
    touch /var/www/simple-site/html/index.html
    echo '<h1>Hello World</h1>' >> /var/www/simple-site/html/index.html

    # Copies over the file provisioner provisioned simple-site file and makes it 
    # available and enabed, restarts nginx to catch it with ufw open on port 81
    cp /tmp/simple-site /etc/nginx/sites-available/
    ufw allow 81 
    sudo ln -s /etc/nginx/sites-available/simple-site /etc/nginx/sites-enabled/
    service nginx restart
  SHELL
end
