Vagrant.configure("2") do |config|

  config.vm.box = "bento/fedora-34"
  config.vm.box_version = "~> 202107.08.0"

  config.vm.provision "shell", inline: <<-SHELL
    yum install -y git nano unzip
    dnf install -y podman butane python3-pip pwgen vim-common
    curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
    unzip awscliv2.zip
    sudo ./aws/install
    cd /vagrant
    git clone https://github.com/forem/selfhost.git
    cd selfhost
    pip3 install -r requirements.txt
    cp inventory/example/setup.yml inventory/forem/setup.yml
    pwgen -1 24|tee ~/.forem_selfhost_ansible_vault_password
    ansible-galaxy collection install -r requirements.yml
  SHELL
end
