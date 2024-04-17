# vpc-demo

## Cenário VPC: 
Em uma conta isolada da AWS:
- Subir uma VPC /16. 
- Segmentar em 3 subnets privadas, 3 subnets públicas. 
- Sem ACLs de acesso. 

### Testes de validação: 
1. Instância iniciada em subnet pública possui IP público e conexão com a internet validados via ping, dig e traceroute. 
1. Instância iniciada em subnet privada possui apenas ip privado, se comunica com a instância pública via rede privada ( ping + telnet ), essa instância também consegue se comunicar com um banco de dados lançado em outra subnet privada ( ping + telnet ). 
1. Instância RDS ( micro ) iniciada na subnet privada possui somente ip privado e conectividade interna apenas. 
Todas as instâncias precisam de um security group que viabilize os testes de acesso acima.
1. Explicar o racional de porque cada recurso foi lançado em suas respectivas subnets e como funciona a comunicação com a internet a partir de cada 1 dos 2 tipos de subnets ( privadas / públicas ). 

### Perguntas: 
- O que é CIDR ?
- Qual a função das route tables, IGW e NATGW ? 


### Solução

Acesse [aqui](solution.md) a solução proposta.