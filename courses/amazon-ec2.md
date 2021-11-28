# Amazon EC2 

As instâncias EC2 são um recurso computacional que a AWS oferece para que nós criemos a infraestrutura das nossas aplicações em outras palavras são as máquinas virtuais hospedadas na AWS.

No AWS Management Console basta realizar a busca por EC2 de Elastic Computer, que é a máquina virtual que será trabalhada.

No menu de Resources é exibido um dashboard com a quantidade de serviços do E2 estão sendo utilizados

![ec2](https://user-images.githubusercontent.com/34458509/143723410-a0db365d-1e75-422f-abf5-eae64c822c9e.png)

Para criar uma nova instância, basta clicar em Resources > Instances > Launch instances

Seleciona a imagem que deseja criar a sua instancia (vulgo vm)

 Dica: Se não tiver nenhuma especificação de infra, pode selecionar o Amazon Linux, é uma máquina gratuita (free tier) e tem uma CPU e 1gb de RAM.

Existe a máquina virtual, questão de processamento, memória e tudo mais. Quem vai processar. E existe o disco. São serviços separados, a cobrança disso é separado. Você tem uma máquina virtual e tem o disco dessa máquina.

No Security Group, a máquina está dentro da AWS. Como é que eu, daqui do escritório, da empresa, de casa, como é que eu acesso é essa máquina? Eu tenho que chegar dentro da infraestrutura da AWS.

Tem um mecanismo de faro, de proteção. O Security Group é como, generalizando, como se fosse o Firewall que você configura. Para que eu possa chegar lá, eu preciso de acesso SSH. Sim, todas as máquinas Linux são gerenciadas via SSH. SSH na porta 22. Ele vai criar um grupo novo para mim. Quem pode fazer acesso a esse SSH? 000, todo mundo. Talvez isso aqui não seja interessante.

Como a parte de autenticação, é feita via SSH, ou seja através de chaves a AWS por default não vai deixar você utilizar usuário e senha para acessar a instância, nesse caso será necessário criar uma chave e guarda em um local seguro, porque se perder a chave perde o acesso a instância criada.

Feito isso, a máquina será PROVISIONADA ou seja, estara em processo de criar a máquina virtual e deixar ela no ar.

## Mapa de regiões da AWS

![image](https://user-images.githubusercontent.com/34458509/143723831-444af5a1-afaa-469a-b33a-5531f4189352.png)

Cada região dessa são data centers e dentro dessas regiões, zonas de disponibilidade.

![image](https://user-images.githubusercontent.com/34458509/143723888-9c9c9900-00a1-4b25-a7be-2d3109108625.png)

Em SP temos 3 zonas de disponibilidades, assim como em Ohio

![image](https://user-images.githubusercontent.com/34458509/143723938-7c748019-223c-4769-88ac-7f41ce57a94a.png)

Outro recurso interessante, é clicar na instance > instance settings > Change termination protection ao ativar essa proteção você evita que a sua instancia seja terminada

## Comunicação entre as máquinas

As máquinas são criadas dentro de uma mesma sub-rede. Como é que fica a comunicação entre elas? Ao pegar o IP da máquina e executar o comando de PING no cmd no caso de falha isso significa que será necessário AUTORIZAR essa comunicação.

Quando você cria uma instância EC2, ela é criada de forma isolada, apesar de ela estar na mesma sub-rede. Para autorizar basta ir no Security Group (instance > action > Networking > Change Security Group) seleciona o acesso group default e assim vou conseguir a comunicação, visto que antes eu permitia a ida mas não a volta, assim eu permito ambas comunicações.

## Acessando a instância

- Selecione a EC2 criada e clique em Connect > SSH Client será exibido os comnados linux para conexão
- Abra o CMD da máquina local e execute o comando na pasta do projeto
- Como parar a instancia? Na AWS clique com o direto na instancia > Stop instance
- Como remover a máquina? Na AWS clique com o direto na instancia > Terminate instance

** O Linux já tem nativo o SSH
** VPC de forma simples é a minha rede dentro da AWS

## Precificação dos Discos

Na AWS o nome dos discos são EBS, como estamos usando uma instância ela tem um disco anexado a ela, por isso é importante saber qual a precificação do disco! Lembrando que: O nível gratuito inclui 30 GB de armazenamento

Com o Amazon Elastic Block Store (EBS), você paga somente pelo que provisiona. O armazenamento de volume para todos os tipos de volumes do EBS é cobrado pela quantidade provisionada em GB por mês até a liberação do armazenamento. Os custos aumentam para os volumes EBS compatíveis com mais operações de entrada/saída por segundo (IOPS) e taxa de transferência superior à performance da linha de base.

É importante saber sobre a precificação do disco também para não cair no erro: Eu tenho uma máquina que está rodando, gastando recurso computacional e dicido parar a máquina. Mesmo que a máquina não esteja mais bilhetando e nem usando algum recurso é errado achar que não terá nenhum gasto mensal, visto que mesmo com máquina parada, existe um disco associado a ela. Está aqui: Elastic Block Store são os discos.

## Customizando a instância

Você pergunta assim: “Será que dá para eu lançar uma máquina EC2 já pré-customizada, ou seja, um template. Como é que eu faço isso?” Quando nós vamos aqui em lançar instância. Além daqueles modelos que eu te mostrei no início, existem já aqui, AWS marketplace, já existem algumas imagens pré-definidas.

Caso queira fazer na mão, ao criar a instância na etapa 3 de configuração na aba Detalhes Avançados > Dados usuário

Basta informar os comandos de instalação que deverá ser executado, nesse caso o ideal é criar um script.sh e depois colar os comandos 

![image](https://user-images.githubusercontent.com/34458509/143726258-cb399a66-ca2e-4eb8-ab98-0b7e7d9d5294.png)
