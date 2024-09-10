
As plantas de cada carro foram formuladas separadamente, porém cada planta tinha valor referente ao último evento que aconteceu nela tal valor se referia a numeração de qual via o carro estava.Foi utilizado 3 variáveis uma pra cada carro para atribuir o valor citado antes cuja foi explicitado que teriam posições diferentes.Com o acesso a essas variáveis se utilizou dos recursos GUARD e Action.Guard  são condições que devem ser satisfeitas para que uma transição ocorra e Action são as operações que ocorrem quando uma transição é disparada.
Assim em cada plant  o guard que resultaria em um action de atribuir valor 2(ocupação da segunda via pela planta do carro que esta executando a função) esse guard teria que checar se as variáveis referente aos outros 2 carros estavam na posição que ele queria ocupar no exemplo a 2.  
O exemplo de evento em questão é o mais problemático pois ele antecipa um evento não controlado que é a passagem para a via 3 como não se tem controle da passagem da via 2 para 3 o evento que faz a passagem para via 2 (no caso a saída da via 1 para 2) tem que além de observar se a via 2 está ocupada por outro carro também tem que observar a via 3.
Assim foi construído o projeto para executar o comportamento pedido porém nota que não é explicitado a sequência de eventos do supervisor e sim limitado a ocorrência do evento a fim de não ferir as especificações do projeto então para alisar se a existência de um deadlock a necessidade de análise do sistema e uma analise matemática lógica posteriormente.
Com a presença de apenas 1 evento não controlado é fácil prever um deadlock . O deadlock acontecerá quando apenas o único evento possível que não vai ferir e especificação de 1 carro por via sera o evento a qual se colocaria um carro no estado que se tem o inicio de um evento não controlado e além disso existiria um carro já no final do evento não controlado.Trazendo para o projeto seria ter um carro na 1, um na via 3 e ngm na via 2 e o carro da via 1 ser o único carro do qual poderia ir para próxima via sem automaticamente fazer com que fique 2 carros na mesma via. Note que para que a única forma para qual  tal evento descrito ocorra (deadlock) apenas o carro da via 1 poderia se mexer o que implica em que o carro que estava na via 3 não podia se mexer logo tinha um carro na via 4 e se tinha um carrro na via 4 e ele não podia se mexer logo tinha um carro na via 5 e o mesmo tinha que ter um carro na via 6,7,8, e o da 1 já foi dito logo observe que estamos falando de 7 carros então isso comprova que não acontecerá deadlock no exemplo apenas com 3 carros.
Quando saber se existe ou nao deadlock com +- vias/carros/eventos não controlados.
Pode ser feito uma analise numa escala menor inicialmente sem eventos não controlados: exemplo 1: (carro 1, via 1)  não há possibilidade de evento.
exemplo 2: (carro 1, via 2) há possibilidade de evento.
exemplo 3: (carro 2, via 2) não há possibilidade de evento.
exemplo 4: (carro 2, via 3) há possibilidade de evento.
logo podemos denominar que numero _de_vias =>numero_de_vias_ocupadas.
numero_de_vias_ocupadas no exemplo seria o numero de carros +1 .O mais 1 acontece apois um evento de passagem de uma via para outra se faz quando a próxima via está livre então se tem um entendimento que o carro que efetuou o movimento precisava de 2 vias ,uma da qual ele vinha e a próxima livre.
Logo aproveitando o entendimento do +1 podemos analisar quando se tem evento não controlados observe que para que não aconteça deadlock quando o objeto esta preste a executar o evento que o deixaria em um estado onde se tem a possibilidade de um evento não controlado para especificação do projeto é necessario que no fim do evento não controlado  a via final desse evento não esteja ocupada assim o carro que efetuou o movimento precisava de 2+(numero de eventos não controlados) vias, uma da qual ele vinha , a próxima livre e a do final do evento não controlado.
Assim resulta  na expressão: numero_de_vias>=numero_de_carros+numero_eventos_não_controlados+1.
No projeto  numero_de_vias>=3+1+1.
com 5 ou mais vias já era possível fazer especificação do projeto.


