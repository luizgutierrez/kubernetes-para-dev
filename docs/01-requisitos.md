## Pré-requisitos
* [VirtualBox](https://www.virtualbox.org/wiki/Download_Old_Builds_6_0) - 6.0.10
* [Vagrant](https://releases.hashicorp.com/vagrant/) - 2.2.5


## Instalando Virtual box

> Obs.: Vamos instalar as versões do sistemas que utilizei para criar o tutorial

O VirtualBox 6.0 não está disponível no repositório oficial de pacotes do Linux. Mas podemos facilmente adicionar o repositório de pacotes do virtualBox e instalar o VirtualBox 6.0 a partir daí. 

1. Para adicionar o repositório oficial de pacotes do VirtualBox:
``` bash
echo "deb https://download.virtualbox.org/virtualbox/debian $(lsb_release -cs) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list
``` 
2. Adicionando a chave pública PGP do VirtualBox:
``` bash
wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
``` 

3. Atualize o cache do repositório de pacotes APT:
``` bash
sudo apt update
```

4. Agora, instale o VirtualBox:
``` bash
sudo apt install virtualbox-6.0 -y
```

5. Para verificar a instalação:
``` bash
virtualbox --help
```

6. O resultado do comando deve ser algo como isso
``` bash
Oracle VM VirtualBox VM Selector v6.0.10
(C) 2005-2019 Oracle Corporation
All rights reserved.

No special options.

If you are looking for --startvm and related options, you need to use VirtualBoxVM.
```

## Instalando Vagrant 

1. O Vagrant 2.2.5 não está disponível no repositório oficial de pacotes do Linux. Mas podemos instalar facilmente a versão necessária realizando o download do pacote.
``` bash
sudo wget https://releases.hashicorp.com/vagrant/2.2.5/vagrant_2.2.5_x86_64.deb
```

2. Em seguida, você pode instalar o pacote usando o seguinte comando:
``` bash
sudo dpkg –i vagrant_2.2.2_x86_64.deb
```

3. Para verificar a instalação:
``` bash
vagrant version
```

4. O sistema deve exibir a versão atual do Vagrant instalada no seu sistema
``` bash
Installed Version: 2.2.5
Latest Version: 2.2.5
 
You're running an up-to-date version of Vagrant!
```
