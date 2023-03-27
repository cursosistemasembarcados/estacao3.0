# Estão Meteorológica - 2o semestre de 2022
## Alunos
Alessandro Vinicius da Silva e Lima 

Misael Fernandes Soares 

Túlio Moreira Costa 

- [A estação](#a-estação)
- [Hardware e esquemas elétricos](#hardware-e-esquemas-elétricos)
  


# A estação
## Introdução
Atualmente, com as mudanças climáticas, tornou-se muito importante estudar e capturar dados do clima, para detectar precipitações de chuvas, temperaturas e qualidade do ar, entre outros fatores, de tal forma que seja possível predizer os
fenômenos meteorológicos.
Pensando nesses fatores, foi agregada no curso de Sistemas Embarcados a construção de uma Estação Meteorológica, iniciada com a primeira turma de sistemas embarcados, com o intuito de criar uma estação de baixo custo e consumo energético.
A partir desse projeto inicial, foi solicitada a continuação pela segunda turma, onde a proposta é fazer a reengenharia da estação, avançando em melhorias de hardware e software, a fim de prosseguir rumo a um produto final.
Após o estudo do funcionamento foi decidido fazer a estação de forma modular, tal qual pode-se montar ou não alguns sensores, tornando o produto com preço variável e com possibilidade de acrescentar ou retirar os sensores somente alterando a programação do ESP32, que vai funcionar como um cérebro gerenciando os módulos através do uso de comunicação I2C (Inter-Integrated Circuit), que utiliza apenas dois cabos, um de Clock e outro de dados para envio e recebimento de informação. Com isso será mantido a leitura dos elementos que já compunham o trabalho anterior (Temperatura, Pressão Barométrica, Umidade, Velocidade do vento, Direção do vento, Precipitação Pluviométrica e Luminosidade) e adicionados novos componentes como Pressão Absoluta com informação de altitude através do módulo MPL3115A2 e qualidade do ar com o módulo CCS811, os quais serão explicados no decorrer do projeto.

# Hardware e esquemas elétricos
## Sensor MPL3115A2
O MPL3115A2 é um sensor de pressão absoluta, compacto do tipo piezo resistivo, o qual possui uma interface digital através do modulo de comunicação I²C. Sua variação abrange de 20kPa até 110kPa, cobrindo todas as elevações existentes na Terra. Ele possui internamente um medidor de temperatura. Os dados dele são alimentados por um ADC de alta resolução para prover compensação total e saídas digitalizadas para pressão em Pascal e temperatura em graus celsius. A saída compensada da pressão, pode ser convertida em altitude em escala métrica.

##Sensor AHT25
O AHT25 é um sensor de temperatura e umidade, equipado com um chip dedicado ASIC com um novo design. Ele é um semicondutor do tipo MEMS, com um sensor de umidade capacitivo e um sensor de temperatura padrão, e sua performance alcançou um nível avançado na indústria. Essa nova geração melhorada de sensores de temperatura e umidade AHT25 tem uma performance mais estável em ambientes pesados e consegue manter uma boa acuracidade em uma larga escala de medida. Devido a miniaturização e melhoria do sensor seu desempenho de custo tornou-se maior.

##Sensor BH1750
BH1750 é um sensor de luz ambiente digital com interface I²C. Esse sensor é o mais apropriado para obter a luz ambiente para o ajuste do LCD e luz de fundo do teclado de um celular. É possível detectar uma larga escala em alta resolução entre 1 e 65535 luxes.

## Anemômetro
O dispositivo de medição da velocidade do vento é um sistema composto por três sensores ópticos, digitais, que, por sua vez, cada um é integrado por um par, formado por um Diodo Emissor de Luz (LED) infravermelho e um receptor, que se trata de um fototransistor NPN, cuja base é sensibilizada e passa a conduzir corrente mediante recebimento de luz infravermelha. A saída do receptor, conectada ao coletor do transistor, entra em nível lógico alto quando o feixe de luz infravermelha é cortado e nível lógico baixo quando a base é ativada e a corrente passa a fluir entre o coletor e o emissor.

## Sensor LM393
A série LM393 são comparadores de tensão de precisão independentes duplos capaz de operação de alimentação simples ou dividida. usados como sensores de precipitação pluviométrica.. Esses dispositivos são projetados para permitirem um modo comum de alcance ao nível do solo com operação de alimentação única. Especificações de tensão de compensação de entrada tão baixas quanto 2,0 mV tornam este dispositivo uma excelente seleção para muitas aplicações em automóveis de consumo e eletrônicos industriais.

## Sensor CCS811
O módulo sensor CCS811 é um medidor de concentração de gás que pode detectar uma ampla gama de compostos orgânicos voláteis (VOCs) e CO2 e destina-se ao monitoramento da qualidade do ar interno. Possui um microcontrolador (MCU), que inclui um conversor analógico-digital (ADC) e uma interface I2C. Quando conectado ao microcontrolador, ele retornará uma leitura de Composto Orgânico Volátil Total (TVOC) e uma leitura de dióxido de carbono equivalente (eCO2) sobre o protocolo de comunicação I2C. Há também um termistor integrado que pode ser usado para calcular a temperatura ambiente local aproximada.

## Sensor TCRT5000
O RoTW (Rose of The Wind) AKA Rosa dos Ventos, é um sensor construído especialmente para a estação meteorológica. Ele consiste no uso de 8 sensores refletivos modelo TCRT5000, os quais são posicionados de acordo com a rosa dos ventos, sendo possível identificar todas as posições conhecidas.
Utilizando o sensor TCRT5000 somado ao comparador LM339 com 4 canais de comparação, pode ser ajustado a reflexão para objetos de cores diferentes, no caso está sendo usado um disco preto com uma faixa branca que faz a reflexão,onde sai o sinal de comparação no LM339, que emite um sinal alto identificando a posição, o qual está a direção da seta. Esse sinal é lido pelo microcontrolador em uso.

##Sensor LM339
O dispositivo LM339 consiste em quatro comparadores de tensão independentes, que são projetados para operar a partir de uma única fonte de alimentação em uma ampla faixa de voltagens. A operação a partir de duas fontes de alimentação também é possível, desde que a diferença entre as duas alimentações seja de 2 V a 36 V, e VCC de pelo menos 1,5 V mais positivo do que a tensão de modo comum de entrada. O dreno de corrente é independente da tensão de alimentação.
