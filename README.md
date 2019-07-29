# Controle-de-velocidade-de-motor-DC-com-PWM-no-Arduino-UNO
Os sistemas embarcados estão cada vez mais presentes no nosso dia-a-dia. Basta olhar ao seu redor: há sistemas embarcados presentes em televisores, monitores, smartwatches, celulares, setup boxes, veículos, iluminação inteligente, etc. Enfim, os sistemas embarcados dominam, mesmo que silenciosamente, a maneira como a tecnologia evolui. Uma das tarefas dos sistemas embarcados é o controle de atuadores, dos quais um dos mais comuns são motores DC (cuja velocidade pode ser controlada com precisão pela grande maioria dos microcontroladores disponíveis no mercado).

# Material necessário

Para reproduzir o projeto você precisará de:

Um Arduino UNO (com cabo USB para programação)

Um Driver Motor Ponte H L298n

Um Motor DC 3-6V com Caixa de Redução e Eixo Duplo

Uma Fonte DC Chaveada 9V 1A Plug P4

Jumpers (macho-fêmea e macho-macho)

# Relação entre velocidade de motor DC e PWM
No caso dos motores DC, a “velocidade de giro” (RPM) pode ser controlada variando-se sua tensão de alimentação. Além disso, o RPM é diretamente proporcional à tensão aplicada. Portanto, variando-se a tensão média de alimentação do motor, varia-se o RPM do mesmo.

Em resumo: o sinal de PWM, devidamente amplificado, pode ser usado para controlar o RPM de um motor DC!

Isso significa que:

Duty cycle de 0%: tensão média igual a 0V, logo o motor fica parado

Duty cycle de 50%: tensão média igual a 50% da tensão de alimentação do motor, logo este girará com RPM igual a metade de sua rotação máxima

Duty cycle de 100%: tensão média igual a tensão de alimentação do motor, logo este girará com RPM igual a sua rotação máxima.

Neste caso, como amplificador para acionar o motor DC, irá ser usado um driver de motor (com ponte H) feito com o circuito integrado L298N. Trata-se de um driver muito versátil e muito utilizado para acionamento de motores DC de 3 – 6V.

# PWM no Arduino
A programação do Arduino (incluindo o Arduino UNO, utilizado neste post) já possui uma função nativa para gerar um sinal PWM em alguns dos pinos (aqueles identificados com um símbolo/identificação ~). Isso torna muito mais fácil o desenvolvimento dos projetos que envolvem PWM, permitindo fácil utilização do mesmo com pouquíssimo custo em termos computacionais (uso de memória Flash, RAM e processamento) e escrita de códigos-fonte mais limpos e curtos. Tal função é chamada de analogWrite(), e recebe dois parâmetros, conforme abaixo:

analogWrite(PINO, VALOR_ANALOGICO);

Onde:

PINO: número do pino do Arduino o qual se deseja que o sinal PWM seja gerado.
Conforme dito anteriormente, somente pinos com símbolo/identificação ~ podem gerar sinais PWM.

VALOR_ANALOGICO: valor (de 0 a 255), proporcional ao Duty Cycle a ser gerado.
Ou seja, para Duty Cycle de 100%, deve-se utilizar valor 255, já para Duty Cycle 20% deve-se utilizar o valor 51 e assim por diante.

# ATENÇÃO:

1) NÃO utilize a alimentação pela USB de programação. Você, obrigatoriamente, deve utilizar a Fonte DC Chaveada 9V/1A. Caso contrário, você corre sérios riscos de danificar o dispositivo que está alimentando o Arduino pela USB de programação (computador, por exemplo).

2) NÃO SE ESQUEÇA de colocar um jumper em ATIVA MA .

