## Iniciando o lab com o vagrant

1. Na pasta raiz do projeto, digite:
``` bash
vagrant up
```

## Principais comandos vagrant para este lab


``` bash
vagrant up
vagrant ssh # Para conectar-se as máquinas virtuais.
vagrant provision # as máquinas virtuais 
vagrant halt # Para excluir as máquinas virtuais.
vagrant destroy # Para deletar as máquinas virtuais.
```

> Obs.: como nosso lab possui mais de uma máquina será necessário especificar a máquina no caso de conexões ssh ou caso deseje desligar apenas uma máquina, se a máquina não for especificada o comando será executado para todas as máquinas. Exemplos abaixo:

``` bash 
vagrant up k8s-master
vagrant provision node-1
vagrant ssh node-2
vagrant halt
```