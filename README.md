# ETL - Agencias da Previdência Social 

Tutorial para a avaliação U3 da disciplina de Sistemas de Apoio à Decisão, lecionada pelo Prof. Msc. Gilton José Ferreira da Silva. 

**Passo 1** 

Acessar o endereço: http://dados.gov.br/dataset para escolha do dataset para ser tratado. 

![Passo 1](https://i.imgur.com/xUwwrN2.png) 
Neste caso, foi escolhido o dataset de Agências da Previdência Social, que são as responsáveis pela inscrição do contribuinte, para fins de recolhimento, bem como pelo reconhecimento inicial, manutenção e revisão de direitos ao recebimento de benefícios previdenciários e ampliação do controle social.
Para extração dos dados é necessário clicar em "Explorar", e em seguida na opção "Ir para o Recurso", onde será iniciado o download do arquivo *.csv*.  

**Passo 2** 

Abrir o software para realização do ETL. Neste caso, foi utilizado o *Pentaho Data Integration*, que está disponível em: https://sourceforge.net/projects/pentaho/files/Data%20Integration/.

![Passo 2](https://i.imgur.com/3f0B4Jn.png)

**Passo 3** 
Clicar em "Transformations", com isso será aberto um espaço onde deverá ser colocado o arquivo a ser transformado. 

![Passo 3](https://i.imgur.com/6AsfrCl.png) 
**Clicar em CSV File Input**
![Passo 3](https://i.imgur.com/bmEx3DF.png)
**Clicar em "Get Fields"**
![Passo 3](https://i.imgur.com/cLXIlEV.png)
A partir deste passo é necessário realizar o tratamento dos dados. Neste dataset, a maioria dos dados já apresentam um padrão definido. Porém decidi mudar alguns tipos de dados, para melhor corresponder com a realidade.

![Passo 3](https://i.imgur.com/1qctyUF.png)
Compl. Endereço e Ramal estavam com tipo Boolean, e foi feita a mudança para o tipo String, CEP estava como tipo Inteiro, mas decidi mudar para o tipo String.  

**Passo 4** 
Agora será iniciada a operação de Transformação. 

![Passo 4](https://i.imgur.com/IUkkFsy.png)
Escolhi a operação String Operations, selecionei, e fiz a ligação entre Entrada_INSS e ela, para que no fim ocorra a transformação. Para configuração da transformação, é necessário clicar duas vezes na operação de transformação selecionada, e em seguida em "Get Fields". 

![Passo 4](https://i.imgur.com/T8pIeJe.png)
Para fins didáticos, o campo "Descricao situação Unidade" terá todas as letras maiúsculas, e o campo "Descição categ." passará a ter todos os campos minúsculos. 

**Passo 5** 
Em seguida, setaremos os arquivos de saída. Para isso, devemos clicar em *Output*, e em seguida no tipo de saída que queremos. Para essa atividade, as saídas definidas são: *JSON, XLS, TXT e XML*. 
![Passo 5](https://i.imgur.com/8XoKPzW.png) 
Para cada saída, digitei o nome do passo, e configurei o nome do arquivo de saída. Conforme exemplo acima. 

![Passo 5](https://i.imgur.com/ij7LTvk.png)
Agora, é hora de fazer a ligação entre o arquivo transformado, e as suas saídas. 

**Passo 6** 
Hora de Executar a transformação. Após carregar a entrada, passar pelo tratamento e ligar as saídas, basta clicar no botão semelhante a um "Play", para executar a transformação. 
![Passo 6](https://i.imgur.com/aihRlZs.png)

Ao executar, percebi que não deu certo a exportação para o .xls, por conta de valores nulos.
![Passo 6](https://i.imgur.com/NxO6RC0.png)

Então tive que utilizar uma outra transformação para que os valores nulos possam ser setados como uma string Vazia. 
![Passo 6](https://i.imgur.com/udCM7RA.png)
