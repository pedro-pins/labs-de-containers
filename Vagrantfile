# Vagrantfile 

Vagrant.configure("2") do |config|

    # Configuração da box
    config.vm.box = "ubuntu/focal64"
  
    # Rede privada com IP fixo
    config.vm.network "private_network", ip: "192.168.56.11"
  
    # Provisionamento via shell
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update -y
      sudo apt-get upgrade -y
      sudo apt-get install -y nmap apt-transport-https ca-certificates curl software-properties-common
  
      # Adiciona o repositório do Docker
      curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
      sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
      sudo apt-get update -y
      sudo apt-get install -y docker-ce docker-ce-cli containerd.io
  
      # Configura e inicia o Portainer
      sudo docker volume create portainer_data
      sudo docker run -d -p 8000:8000 -p 9443:9443 -p 9000:9000 --name=portainer --restart=always \
        -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
      # Teste de instalação do Nmap
      nmap --version || true
    SHELL
  end
  