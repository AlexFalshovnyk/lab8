
Vagrant.configure("2") do |config|
  config.vm.box = "matthiasmullie/debian9-arm64"
  config.vm.box_version = "1.0.0"
  config.vm.synced_folder "For_Vagrant", "/home/vagrant/www/default/", type: "rsync"

  config.vm.network "forwarded_port", guest: 80, host: 8888, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", guest: 443, host: 8443, host_ip: "127.0.0.1"
  
  config.vm.provision "shell", inline: <<-SHELL
   apt-get -y update
   apt-get -y upgrade
   apt-get -y install nginx
      
openssl req -x509 -nodes -days 3650 -newkey rsa:2048 -subj "/C=UA/ST=Lviv/L=Lviv/O=EnJay, LLC/CN=enjay" -keyout /etc/ssl/private/localhost.key -out /etc/ssl/certs/localhost.crt


   cp /home/vagrant/www/default/file.html /var/www/html/index.html
   cp /home/vagrant/www/default/default /etc/nginx/sites-available

   

   #chmod 755 /home/vagrant
   service nginx restart

   
   SHELL
end
