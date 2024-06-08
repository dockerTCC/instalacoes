Aplicacao de produto necessita de 2 outros serviços postgres e nginx
simular teste de estresse 
caso vm: criar 3 vm(s) para postgres, nginx e api de produto. subir os serviços separadamentes
caso docker: Criar uma só vm e subir os mesmos serviços em containers, os recursos computacionais serão os mesmos da somatória

exemplo 
## vm-infra-total: 4 vcpu e 6 ram e 24 disk-ssd

 - vm postgres: 2 vcpu, 2 ram e 8 disk-ssd
 - vm nginx: 1 vcpu, 2 ram e 8 disk-ssd
 - vm api produto: 1 vcpu, 2 ram e 8 disk-ssd

## docker-infra-total: 2 vcpu, 3 ram e 12 disk-ssd 
 - vm docker: 2 vcpu e 3 ram e 12 disk-ssd

## Objetivo
Mostrar que com metade dos recursos o docker consegue ter resultados mais efeicientes.


### Metodologia

#### Objetivo
O objetivo deste estudo é demonstrar que, utilizando metade dos recursos computacionais, o Docker pode proporcionar resultados mais eficientes em comparação com máquinas virtuais (VMs). Para isso, será realizada uma simulação de carga com 100.000 usuários na aplicação de produto, avaliando o desempenho tanto no ambiente VM quanto no ambiente Docker.

#### Ambiente de Teste

1. **Configuração das VMs:**
   - **VM PostgreSQL:**
     - vCPUs: 2
     - RAM: 4 GB
     - Disco SSD: 16 GB
   - **VM Nginx:**
     - vCPUs: 1
     - RAM: 2 GB
     - Disco SSD: 8 GB
   - **VM API Produto:**
     - vCPUs: 1
     - RAM: 2 GB
     - Disco SSD: 8 GB

2. **Configuração do Docker:**
   - **Infraestrutura Total:**
     - vCPUs: 2
     - RAM: 4 GB
     - Disco SSD: 12 GB
   - **VM Docker:**
     - vCPUs: 2
     - RAM: 3 GB
     - Disco SSD: 12 GB

#### Etapas da Metodologia

1. **Preparação do Ambiente:**
   - **VMs:**
     - Configuração e instalação do PostgreSQL, Nginx, e a API de Produto em suas respectivas VMs.
   - **Docker:**
     - Configuração de uma VM dedicada para o Docker.
     - Criação de contêineres para PostgreSQL, Nginx e a API de Produto dentro desta VM.

2. **Desenvolvimento do Teste de Carga:**
   - Utilização de ferramentas como Apache JMete para simular 50 usuários fazendo 1000 interações cada, totalizando 50.000 requisições a aplicação de produto e realizando um cadastro no banco de dados.
   - Configuração de cenários de teste idênticos para ambas as infraestruturas (VMs e Docker) para garantir a comparabilidade dos resultados.

3. **Execução dos Testes de Desempenho:**
   - **Para VMs:**
     - Iniciar os serviços (PostgreSQL, Nginx, e API de Produto).
     - Executar o teste de carga e coletar métricas de desempenho (tempo de resposta, utilização de CPU, memória e disco, taxa de erros).
   - **Para Docker:**
     - Iniciar os contêineres correspondentes.
     - Executar o teste de carga e coletar as mesmas métricas de desempenho.

4. **Coleta e Análise de Dados:**
   - Comparação dos tempos de resposta médios, utilização de recursos e taxa de erros entre as duas infraestruturas.
   - Avaliação da eficiência do Docker em termos de uso de recursos computacionais em comparação com as VMs.

5. **Resultados Esperados:**
   - Demonstrar que, com metade dos recursos, o Docker consegue suportar a carga de 50.000 requisições com melhor desempenho ou, pelo menos, desempenho equivalente ao ambiente de VMs.
   - Evidenciar a eficiência do Docker em termos de gerenciamento de recursos.

#### Descrição das Ferramentas

- **Apache JMeter:** Ferramenta de teste de carga para medir o desempenho e comportamento de aplicações web sob diversas condições de carga.
- **htop:** Utilitário de monitoramento para visualizar em tempo real a utilização de recursos (CPU, RAM, etc.) nos servidores.
- **Docker:** Plataforma de contêinerização que permite empacotar e rodar aplicações em contêineres isolados.
- **VMWare/VirtualBox:** Plataformas de virtualização usadas para criar e gerenciar as VMs utilizadas no teste.

#### Conclusão

Ao final deste estudo, espera-se comprovar que o Docker é uma solução mais eficiente em termos de utilização de recursos computacionais, proporcionando desempenho igual ou superior ao das VMs com a metade dos recursos. Este resultado poderá fornecer insights valiosos para organizações que buscam otimizar suas infraestruturas e reduzir custos operacionais.