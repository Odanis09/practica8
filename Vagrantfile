Vagrant.configure("2") do |config|
    # Usa una caja de Ubuntu como base (puedes cambiar la versión si es necesario)
    config.vm.box = "ubuntu/jammy64"
    
    # Configuración de la VM
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"       # RAM de 256 MB
      vb.cpus = 1             # 1 CPU
    end
    
    # Instala Apache
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y apache2
    SHELL
    
    # Sincroniza la carpeta de Apache con una carpeta local
    config.vm.synced_folder "./src", "/var/www/html"
    
    # Configuración de red para acceder a Apache desde el host
    config.vm.network "forwarded_port", guest: 80, host: 8080
  end
  