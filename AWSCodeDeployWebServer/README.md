# Lab AWS Code Deploy

## Lab Part 1 - instâncias

- Criar instância EC2
- Conectar instância 
- Atualizar instância 

> sudo yum update -y

- Instalar Apache

> sudo yum install httpd -y

- Configurar serviço Apache

> sudo systemctl start httpd
> sudo systemctl enable httpd

- Instalar CodeDeploy agent (necessário Ruby)

> sudo yum install ruby -y
> wget https://aws-codedeploy-sa-east-1.s3.sa-east-1.amazonaws.com/latest/install

- Tornar arquivo "install" executável

> sudo chmod +x ./install

- Executar o arquivo install

> sudo ./install auto

- Conferir status do agent

> sudo service codedeploy-agent status

- Criar permissões para uso do codeDeployAgent no IAM Roles
    - selecionar AWSCodeDeployRole

- Anexar IAM Role à instância EC2 Code Deploy

## Lab Code Deploy - Parte 2 - Usar instâncias como modelo / AMI Personalizada 

- Parar a instância

> Acoes > Gerenciar Estado da Instância > Interromper

- Criar Imagem

> Selecionar Instância EC2 CodeDeploy criada > Acoes > Imagens > Criar Imagem

- Conferir se AMI criada já está disponível. 

> Images > AMIs > Status

- Se sim, terminar instância EC2 utilizada como modelo

- Atualizar tags da imagem

## Lab CodeDeploy - appspec

## Lab CodeDeploy - AWS CodeSuit

-  CodeDeploy> criar nova aplicação > Plataforma=EC2 / OnPremise > Criar
- Criar IAM Role para uso do code deploy (IAM > Funções > Criar Função > Code Deploy)
- Criar Deployment Group (aqui escolher quais instâncias que vão receber a aplicação)
  - Nome
  - IAM Role
  - Como Implantar > In place
  - Configuração de ambiente = Instancias EC2
  - adicionar tags das instancias criadas anteriormente para uso do codedeploy, feitas a partir da imagem personalizada.
    se nao tiverem sido criadas, criar antes de prosseguir
  - escolher configuração do deploy (one at a time|half at a time | all at once)
  - criar grupo

## Finalizando Lab

- Criar Deployment
  - Escolher o deployment group criado
