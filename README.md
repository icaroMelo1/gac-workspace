# Docker Compose para Ambiente de Testes

Este projeto utiliza Docker Compose para orquestrar um ambiente de testes que inclui um banco de dados MySQL, um backend em NestJS e um serviço de monitoramento de métricas com Prometheus. O objetivo é fornecer um ambiente de desenvolvimento e testes simples e eficiente.

## Estrutura do Projeto

O projeto é composto pelos seguintes serviços:

1. **MySQL**
   - **Imagem:** mysql:8.0
   - **Porta:** 3306
   - **Variáveis de Ambiente:**
     - MYSQL_ROOT_PASSWORD: Senha do usuário root.
     - MYSQL_DATABASE: Nome do banco de dados a ser criado.
   - **Volume:** Persistência dos dados.

2. **Wallet Backend**
   - **Imagem:** Aplicativo Node.js construído a partir do Dockerfile no diretório backend.
   - **Porta:** 3000
   - **Dependências:** Espera o serviço MySQL estar ativo antes de iniciar.
   - **Configuração:** Conexão com o banco de dados usando TypeORM.

3. **Prometheus** (opcional)
   - **Imagem:** prom/prometheus
   - **Porta:** 9090
   - **Configuração:** Leitura de métricas do backend e do MySQL (se o exporter estiver habilitado).

4. **Filebeat** (opcional)
   - **Imagem:** Configuração para coletar logs dos serviços.
   - **Porta:** 5066 (opcional, dependendo da configuração).

## Instalação

Para subir os serviços, certifique-se de ter o Docker e o Docker Compose instalados. Após isso, você pode rodar o seguinte comando na raiz do projeto:

docker-compose up --build

Isso buildará e iniciará todos os serviços definidos no arquivo docker-compose.yml.

## Acesso

- **MySQL:** Acesse o banco de dados na porta 3306.
- **Wallet Backend:** Acesse o backend em http://localhost:3000.
- **Prometheus:** Acesse a interface do Prometheus (se habilitada) em http://localhost:9090.
- **Filebeat:** Acesse a API do Filebeat (se habilitada) em http://localhost:5066.

## Monitoramento de Métricas

As métricas do backend estão disponíveis em http://localhost:3000/metrics. O Prometheus está configurado para coletar essas métricas periodicamente.

## Postman Collection:

Para realizar testes no backend, importe o json da collection no seu postman