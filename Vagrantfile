
Vagrant.configure("2") do |config|

  config.vm.box = "centos/7"
  config.vm.synced_folder "files", "/home/vagrant/www/default/", type: "rsync"


  config.vm.network "forwarded_port", guest: 80, host: 8888, host_ip: "127.0.0.1"
  

 
  config.vm.provision "shell", inline: <<-SHELL

  yum install -y epel-release
  yum install -y nginx
  systemctl -l enable nginx
   -l start nginx

  cp www/default/nginx.conf /etc/nginx/
  chmod 755 /home/vagrant
  chcon -Rt httpd_sys_content_t www/default
  systemctl restart nginx

   SHELL
end
