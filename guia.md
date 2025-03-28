Guia: Criação do jogo flap bird com o pygame

1- O primeiro passo vai ser fazer a instalçao da biblioteca do pygame que é quem permite a criação de jogo, agora é so importa a biblioteca, alem dessa nos vamos importa a biblioteca 'os' que permite a integração com os arquivos do no pc por exemplos pasta etc e a 'random' que gera numeros aleatorios.

2- O proximo passo e definir algumas constante que sao variaveis que nao sao modificaveis vai ser sempre essas, no nosso caso e as configuraçoes do jogo, as constantes normalmente sao colocadas em letras maiuscula, nessa nossa configuraçoes alem de definir altura e largura que da nossa tela do jogo nos vamos ter q utilizar imagens que ja foram disponibilizadas do jogo.

Aqui nos teremos que pegar essa imagem pelo pygames e para fazer isso basta da um pygames.imagem.load ,  alem disso nos temos que pegar a imagem e ela esta em uma pasta separada, por isso importamos a biblioteca os pois ela vai permitir pegarmos o caminho da pasta imgs e concatenar com a nossa imagem que queremos. A unica diferença vai ser nas iamgens do passaro pois ela possui 3 imagens para fazer o efeito da asa batendo entao o que vai acontecer é que vamos fazer ela em uma lista de imagens

Se fizemos so isso quando rodarmos o codigo o nassa tela vai ficar bem pequena, entao nos vamos pegar esse codigo que fizemos pra pegar as iamgens e usar um metodo do pygames que escala essas iagem em 2x, pra isso é so usar o pygame.transform.scale2x()

Agora a ultima constante é o fonte_pontos pra fazer a contagem, mas antes dela nos temos que fazer um pygame.font.init(), que o que vai permitir iniciar a contagem, ai dps podemos fazer a constante do ponto


3- O proximo passo nos teremos que criar os objetos do nosso jogo, e cada objeto vai ser uma class python, esse objetos normalmente sao as coisas moveis do jogo, por exemplo o passaro ele vai poder subir e descer, o cano vai esta movimentnado pra esquerda assim como o chao para da a sensação de movimento, e dentro dessa class nos vamos ter os atributos que no caso sao as caracteristica desse objeto como em que eixo ele o passo ta, qual a imagem do passado etc.

E cada classe ira ter os seus metodos associados, como movimento de subir e descer do passaro , o desenho dele, escolher pular ou nao e  etc.

4- Agora para nossa class passaro nos vamos fazer a função de pular, entao nos temos que definir o quanto vai ser o movimento do pulo que vai ser a velocidade que vai ser negativa pq para o eixo y do pygames o sentido crescente dele quando ele é esta positivo e para baixo(ve a aula para entender), o tempo que vai começar no zero pq vamos ter que definir o deslocaento quando ele pular, e a altura em q nosso passaro vai estar, que vai ser o nosso eixo y.

A segunda função  vai ser em relação ao movimento do passaro , entao nos vamos fazer a função mover, dentro dela nos temos q se preucupar em algumas coisas, primeiro nos temos que calcular o deslocamento do passaro para isso nos vamos ter q definir um tempo, e depois usar a forma de deslocamento , para o nosso passaro fazer aquela parabrola de meio arco.

A proxima coisa que tempos que se precupar e restringir esse movimento do passaro , para que ele fica constante e nao ultrapasse uma certa velocidade ou algo do tipo. gora é so fazer o deslocamento do nosso passaro, que é pegar o nosso eixo y e somar o delocamento

A gora a terceira coisa é o angulo do nosso passaro, o que vai ocorrer é que temos que lembrar q quando estamos subindo com o passaro ele a numeração é negativa , entao se o deslovamento for menos que 0 nos vamos verificar se o angulo do nosso passo esta menor que a rotação maxima caso esteja quero q ele fica com a toração maxima. 

alem disso no primeiro if nos vamos verificar se o nosso eixo y e menor que nossa altura + 50 para fazer com que o passaro so saia do angulo maximo quando ele tiver abaixo do eixo y inicial.

Agora caso o angulo tiver abaixo do zero que no caso seria indo parao -90 graus o nosso algura vai ser -= nossa velocidade de rotação

5- Agora nos vamos fazer uma classe que vai nos ajudar muito que vai ser a   função desenhar, ela vai ser como se fosse desenhar o nosso passaro ela que vai se preucupar com onde o passaro vai aparecer, em que rotação o passaro vai estar e etc, pq assim isso vai nos permitir que na nossa classe do passaro vai ter como esse passaro esta desenhado no momento(como ele vai aparecer), pq ai na nossa função principal que vai rodar o jogo nos so iremos utlizar essa classe


6- função desenhar o passaro, o primira coisa que vamos fazer e pegar aquele Constante que fizemos de contagemd e imagem e somar nela, caso a imagem tenha um determinado numero de contagem comparado ao seu tempo de animação ela ira mudar para outra entao nos temos que passar pelas imagens ate ele fazer um bater de asas completo e entao zerar para começar denovo.

Agora se o passaro estiver caindo nos queremos que ele nao bata asa entao temos que fzer ele para de bater asas e ficar em uma imagem fixa

Por ultimo nos temos que fazer o desenho da imagem , onde primeiro nos temos que fazer  a nossa iamgem rotacionada , que no nosso caso vai ser a imagem do passaro que ta no momento e o angulo que ta moment.

Entao pro proximo passo nos vamos precisar do centro dessa imagem, entao vamos pegar essa posição do centro da imagem, nos precisamos disso pq o proximo passo vai se basicamento o retangulo de onde vamos desenhar a nossa imagem, agora para desenhar voce precisa dar um .blit passando a iamgem que quer ser desenhanda e a posição topleft do local da de onde vai aparecer a imagem

7-aqui nos vamos fazer a função get_mask ela vai servir para quebrar nossa imagem do passo que tem uma hit box de um retangulo, e fragmenta ela em diversos pixels, para verificar se em cada pixels ouve realemente a colisao do passaro com o cano, o pygames ja tem isso pronto entao é uma função bem pequena.


8- Agora nos vamos fazer a class cano, entao a primeira coisa a ser feita e crias as configuraçoes padroes que so as constantes como a distancia, velocidade etc. Entao depois de crias as contantes nos vamos fazer um def init que vai possuis as caracteristicas bases iguais fizemos com o nosso passaro. 

Dentro dessa def init ela vai ter uma função que vamos ter que criar abaixo, ela vai estar dentro desse init porque quando rodar nosso codigo,o init puxa automaticamente essa função que vai servir para  dar a altura no qual os canos vao estar posicionado, nossa altura nos vamos definir atraves de um numero aleatorio mais ele sera restringido 

Agora nos vamos fazer a função que vai ser responsavel por mover o cano, que é bem simples basta pegar o x que determina o movimento e diminuir a velocidade. 

Tambem teremos que fazer a função que desenha nossos canos, que basicamente so fazer um blit lembrando que essa tela tambem recebe a tela como parametro da função.

A nossa ultima função vai ser a de colisao que nos temos que verificar a colisao do passaro e dos canos entao pra isso essa função vai ter q recerber o passaro, e vamos fazer a msm coisa que fizemos la no passaro, pegar a mask das imagem so que dessa vez dos 2 canos.
ainda nessa função nos vamos precisar saber a distancia entre essas imagens entao temos que pegar o eixo x e y e subitrailas para saber essa distancia.

 agora basta verificar se tem alguma colisão entre essas imagens e para isso ja possui um metodo ja pronto, que é o overlap , esse metodo ele nos retorna um verdadeiro ou falso, verdadeiro se as imagens se tocaram e falso para nao, entao temos que verificar se ouve essa colisão

9- Agora vamos para o metodo do chao que vai ser o mais simples, entao como todos os outras classes, nos vamos definir os parametros fixos que sao as constantes, dentro dessa contante noss vamos precisa pegar a largura do chao porque vamos precisar ter 2 chao, paraquando um tiver se movimentando aparecer outro logo em seguida. 

10- agora nos vamos fazer é a função que vai desenhar o nosso jogo por completo, pra isso nos vamos usar aquelas funçoes que fizemos dentro de cada class que e da desenhar nossos obejtos, depois de desenhar todos os objetos nos temos que atualizar nossa tela, danto um .display.update()

OBS: aqui nesse função o passaro vai esta no plural pq esse vai ser um jogo que vamos trabalhar em outro modulo com inteligencia artificial entao ai nospoderemos ter mais de um passaro na tela nesse modulo por isso vai esta em plural e dentro de um for ok.


11- Agora vamos pra função principal que é a que vai ser responsavel por executar nosso jogo, nessa função nos vamos ter que criar nossos objetos que va vir la das nossas classes, os numero passados para cada x, y foi a base de teste e alem disso nos temos que passar criar nossa tela com o pygames, definir os pontos e criar o nosso relogio para atualizar a tela , o relogio ja possui um metodo para lidar com isso.

Agora nos temos que rodar o jogo, um jogo e basicamento um loop infinito que fica rodando e fazendo os metodos, funçoes etc ate que aonteça algo, no nosso caso nos vamos utilizar uma variavel = true para fazer esse while.

dentro desse looping nos vamos primeiro refinir o tempo de alualização que vai ser 30 frames por segundo que vaivir la do relogio.

depois nos vamos definir a interação do jogador com o nosso game, onde o py game ja tem isso, que é o pygame.event , que faz com que se eu apertei algum botao ele entende isso como um evento e ai vamos verificar se ouve algum evento.

Agora é so colcoar as coisas para se moverem, com algumas peculiaridades com o cano, porque temos a colisao do cano com o passaro e tambem verificar se o passaro ja passou pelo primeiro cano para poder criar o proximo 

