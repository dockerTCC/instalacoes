# instalações
Instruções de instalação das aplicações utilizadas

## Install docker e docker compose
curl https://releases.rancher.com/install-docker/24.0.9.sh | sh
apt install docker-compose

## Configurar chave ssh para clonar projetos
ssh-keygen -t rsa -b 4096
cat ~/.ssh/id_rsa.pub (copie a chave ssh)
adicione a chave ssh no SSH keys do github

## Acesso as maquinas
é necessário ter a chave tcc-docker.pem instalada e está no diretório em que está localizada na máquina para ter acesso remoto.
### Docker
ssh -i "tcc-docker.pem" ubuntu@ec2-44-194-218-112.compute-1.amazonaws.com
ip privado 44.194.218.112

### Máquina de vm
ssh -i "tcc-docker.pem" ubuntu@ec2-44-196-178-218.compute-1.amazonaws.com
ip privado: 172.31.62.132

git@github.com:dockerTCC/produto-api.git