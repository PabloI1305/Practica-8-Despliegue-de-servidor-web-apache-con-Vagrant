Vagrant.configure("2") do |config|
  # Usar la box de Ubuntu 20.04
  config.vm.box = "ubuntu/bionic64"

  # Configurar la memoria y CPU
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "512"
    vb.cpus = 1
  end

  # Configurar la carpeta compartida
  config.vm.synced_folder "./pagina-web", "/var/www/html"

  # Provisionar el servidor web Apache
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y apache2
    echo '<h1>Hola Mundo</h1>' > /var/www/html/index.html
    systemctl enable apache2
    systemctl start apache2
  SHELL
end
