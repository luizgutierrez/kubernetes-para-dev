## Iniciando o lab com o vagrant

1. Na pasta raiz do projeto, digite:
``` bash
vagrant up
```

## Principais comandos vagrant para este lab


``` bash
vagrant up # Criar/Provisionar os recursos no host
vagrant ssh # Para conectar-se as máquinas virtuais.
vagrant provision # Provisionar recurso no host, no caso executará o ansible e fara a instalação do nosso lab
vagrant halt # Para excluir as máquinas virtuais.
vagrant destroy # Para deletar as máquinas virtuais.
```

> Obs.: como nosso lab possui mais de uma máquina será necessário especificar a máquina no caso de conexões ssh ou caso deseje executar outro comando em apenas um host, se a máquina não for especificada o comando será executado para todas as máquinas. Exemplos abaixo:

``` bash 
vagrant up k8s-master
vagrant provision node-1
vagrant ssh node-2
vagrant halt
```
