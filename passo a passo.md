<h1 align="center">Networking-Immersion-Day</h1>

### Pré requisitos ###

Uma conta AWS que possa criar IAM roles e editar permissões, a conta free tier da AWS já oferece os recursos necessários.

### Multi-VPC Account Architecture ###

Amazon Virtual Private Cloud (Amazon VPC) permite provisionar uma seção logicamente isolada da Nuvem AWS onde você pode iniciar recursos da AWS em uma rede virtual que você define. Você tem controle total sobre seu ambiente de rede virtual, incluindo a seleção de seu próprio intervalo de endereços IP, criação de sub-redes e configuração de tabelas de rotas e gateways de rede. Você pode usar IPv4 e IPv6 em sua VPC para acesso fácil e seguro a recursos e aplicativos.

As zonas de disponibilidade (AZ) são vários locais isolados em cada região. Uma VPC abrange todas as AZs na região.

Um gateway da Internet (Interet Gateway) é um componente de VPC dimensionado horizontalmente, redundante e altamente disponível que permite a comunicação entre instâncias em sua VPC e a Internet. Portanto, não impõe riscos de disponibilidade ou restrições de largura de banda em seu tráfego de rede.

Neste laboratório, criaremos três VPCs com gateways da Internet e instâncias do EC2 - uma por VPC. Observaremos que, por padrão, as instâncias do EC2 em diferentes VPCs não podem se comunicar entre si usando endereços IP privados.

<img src="https://user-images.githubusercontent.com/53286067/194913551-188e3435-32bf-4744-856e-1ddb4627e1b2.png" 
     width="800" 
     height="400" />
     
### 1 - Crie VPCs, Subnets e instâncias EC2 ###

Vamos criar 3 VPCs, com suas subnets privadas. Cada VPC terá subnets em 2 zonas de disponibilidade na região. Vamos fazer o Deploy 

<img src="https://user-images.githubusercontent.com/53286067/194914625-159a3678-9926-4d20-9e08-459819b5047c.png" 
     width="800" 
     height="400" />

### 1.1 - Crie VPCs ###

Procure pelo serviço de VPC no campo de busca do console da AWS

![image](https://user-images.githubusercontent.com/53286067/194922019-c265c8fe-fc0b-4d90-8f2b-769ceb2774d2.png)

Navegue até "Your VPCs" e clique em "Create VPC"

![image](https://user-images.githubusercontent.com/53286067/194922215-74a41188-b72e-4448-8684-0e48fe96a3c0.png)

- Crie o "VPC A", especificando 10.0.0.0/16 como bloco CIDR IPv4.
- Não habilite o IPv6.
- Selecione tenancy "Default".
- Aceite as tags propostas

![image](https://user-images.githubusercontent.com/53286067/194922788-f023f9f2-ca3a-4718-9a00-fe7cbb5b8a39.png)

Faça o mesmo para criar o "VPC B" e o "VPC C" (fique atento a tabela acima com os detalhes).

Após completar os passos, você deve ter 3 VPCs e o default

![image](https://user-images.githubusercontent.com/53286067/194923393-e654bd0a-1ff0-4744-ad95-33b4e38adab1.png)
