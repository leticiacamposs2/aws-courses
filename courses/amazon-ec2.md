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

Links:
- [Portal AWS](https://aws.amazon.com/)
- [Preços das instâncias EC2](https://aws.amazon.com/pt/ec2/pricing/on-demand/)
