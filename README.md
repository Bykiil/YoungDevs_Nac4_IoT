
# NAC4 - Smart Citty

**Integrantes YoungDevs:** <br>
    **RM85615 -** Estevão Alves Avelino <br>
    **RM85607 -** Beatriz Kül Rezende <br>
    **RM85136 -** Gustavo Henrique Garrido de Melo <br>
    **RM83436 -** Murilo Salvador Bagodi <br>
    **RM85100 -** Glaydson do Nascimento Marques <br>
    **RM85400 -** Pedro Gabriel da Costa Vieira Oliveira <br>

**Turma:**
    2TDSA


## Objetivo / descrição do Projeto

Este é um projeto para a entrega da NAC4, da matéria de Disruptive Architectures IOT e IA. 
O objetivo é desenvolver uma estação meteorológica que capta informações de sensores e envia para um servidor que exibe as informações em um dashboard, um alerta é enviado automaticamente via twitter, caso a velocidade do vento seja maior que 80km/h.
Para desenvolve-lo utilizamos o **SimulIDE** para construir o circuito e rodar o código arduino, o **Node-RED** para criar os fluxos de comunicação (via **MQTT**) entre nosso dispositivo e o **dashboard** (e o **Twitter** quando necessário). 

## Capa do projeto


<img src="/imgProject.png" width="550">


## Como usar 

Para rodar o projeto, será necessário ter os softwares:

**SimulIDE** <br>
**Node-RED**<br>
**Arduino**<br>
**com0com**


No SimulIDE, deve-se importar os arquivos: circ.simu (o circuito, localizado na pasta circuitos) e cod.ino (o cógigo arduino, localizado na pasta codes_arduino), compilar e rodar! =D <br>
No Node-RED, instalar os modules:
* node-red-dashboard
* node-red-node-serialport
* node-red-node-twitter <br>
Após as intalações incluir o arquivo flows.json (localizado na pasta flows_node).<br>

Caso a velocidade do vento chegue a mais de 80km/h, você pode conferir o Tweet na conta do Twitter "@BiaKiil"


## Link de vídeo demonstração


[Link para o video no drive](https://drive.google.com/file/d/1s7XjuKFu1BPCBxm_8LAGAuPEJtnX6oJT/view?usp=sharing)


### Referências 

* [mastering-markdown](https://guides.github.com/features/mastering-markdown/)
* [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
* [projec template by our awesome teacher](https://github.com/arnaldojr/templatenac)
