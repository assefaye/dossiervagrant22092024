Vagrant.configure("2") do |config|
  config.vm.define "server" do |server| 
    # Utiliser l'image de la box Ubuntu 22.04
    server.vm.box = "bento/ubuntu-22.04"
    #Configurer l'adresse IP de la machine virtuelle
    server.vm.network "private_network", ip: "192.168.33.10"
    # Provisionnement pour exécuter le script Docker
    server.vm.provision "shell", path: "docker.sh"
    # Configuration du fournisseur VirtualBox
    server.vm.provider "virtualbox" do |domain|
      domain.gui = false
      domain.name = "server"
      domain.cpus = 1
      domain.memory = 1024
    end
  end

  config.vm.define "client" do |client| 
    # Utiliser l'image de la box Ubuntu 22.04
    client.vm.box = "bento/ubuntu-22.04"
    #Configurer l'adresse IP de la machine virtuelle
    client.vm.network "private_network", ip: "192.168.33.11"
    #Configurer le port redirigé
    client.vm.network "forwarded_port", guest: 80, host: 82
    # Provisionnement pour exécuter le script Nginx
    client.vm.provision "shell", path: "nginx.sh"
    # Configuration du fournisseur VirtualBox
    client.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.name = "client"
      vb.cpus = 1
      vb.memory = 1024
    end
  end 

end