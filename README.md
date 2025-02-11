
### Desafio Java Spring Ambev


# Projeto: Gestão de Pedidos

Este projeto exemplifica uma aplicação para gestão de pedidos desenvolvida com Spring Boot, Kafka e PostgreSQL. A aplicação oferece funcionalidades para criar, listar, atualizar e excluir pedidos por meio de uma API REST.

## Funcionalidades

- **Criar Pedido**: Endpoint para a criação de novos pedidos.
- **Listar Pedidos:** Endpoint para listar todos os pedidos.
- **Atualizar Pedido:** Endpoint para atualizar pedidos existentes. 
- **Deletar Pedido:** Endpoint para excluir um pedido.

## Tecnologias Utilizadas

- **Spring Boot:** Framework utilizado para a construção da aplicação.
- **Kafka:** Sistema de mensageria empregado para monitoramento e reprocessamento de requisições
- **PostgreSQL:** Banco de dados utilizado para armazenar os pedidos.
- **Docker:**  Ferramenta para containerização da aplicação e seus serviços.

## Estrutura do Projeto (Baseada em DDD)

###  **Domain**
- **Entidades:** Representam objetos de domínio que possuem uma identidade distinta.
    - `Order`: Representa um pedido com atributos como ID, nome e descrição.
- **Exceções:** Tratamento de exceções específicas do domínio.
    - `PedidoNotFoundException`: Exceção lançada quando um pedido não é encontrado.
- **Repositórios:** Interfaces que definem os métodos de acesso ao banco de dados.
    - `OrderRepository`: Interface para operações de CRUD relacionadas aos pedidos.

###  **Application**
- **Serviços de Aplicação:** Contêm a lógica de negócio e coordenação entre diferentes partes do sistema.
    - `IOrderService`: Interface que define métodos de operações de negócio relacionados aos pedidos.
    - `OrderServiceImpl`: Implementação de `IOrderService` que contém a lógica de negócio dos pedidos.

### **Infrastructure**

- **Configurações:** Arquivos de configuração e setup do projeto.
    - `KafkaProducerServiceConfig`: Configuração do Kafka para produção de mensagens.
    - `OpenApiConfig`: Configuração do Swagger para documentação da API.
    - `SecurityConfig`: Configurações de segurança da aplicação.

### **Web**
- **Controladores:** Classes responsáveis por expor os endpoints da aplicação.
    - `OrderController`: Define os endpoints para criar, listar, atualizar e deletar pedidos.
- **Documentação:** Classes responsáveis pela documentação da API.
    - `OrderDocumentation`: Define a documentação dos endpoints da `OrderController`.

## Configuração e Execução

### Pré-requisitos

- Docker e Docker Compose instalados.

### Passos para Execução

1. **Clone o Repositório:**

   ```bash
   git clone https://github.com/GabrielVogado/java-ambev.git
   cd java-ambev
   ```

2. **Construa e Inicie os Contêineres:**

   ```bash
   docker-compose up --build
   ```

   Isso iniciará os seguintes serviços:
    - **db:** Servidor PostgreSQL.
    - **zookeeper:** Necessário para o Kafka.
    - **kafka:** Servidor Kafka.
    - **app:** Aplicação Spring Boot.
    - **kafdrop:** Interface web para monitorar o Kafka.

3. **Verifique os Logs:**

   Você pode verificar os logs de qualquer serviço utilizando o comando:

   ```bash
   docker logs nome-do-servico
   ```

   Por exemplo, para verificar os logs do `app`:

   ```bash
   docker logs app
   ```

### Endpoints Disponíveis

A aplicação expõe os seguintes endpoints através do contêiner `app`:

- **Criar Pedido:**
    - **URL:** `http://localhost:8080/orders`
    - **Método:** `POST`
    - **Descrição:** Cria um novo pedido.

- **Listar Pedidos:**
    - **URL:** `http://localhost:8080/orders`
    - **Método:** `GET`
    - **Descrição:** Lista todos os pedidos.

- **Atualizar Pedido:**
    - **URL:** `http://localhost:8080/orders/{id}`
    - **Método:** `PUT`
    - **Descrição:** Atualiza um pedido existente pelo ID.

- **Deletar Pedido:**
    - **URL:** `http://localhost:8080/orders/{id}`
    - **Método:** `DELETE`
    - **Descrição:** Deleta um pedido existente pelo ID.

### Monitoramento do Kafka

A interface web Kafdrop está disponível para monitorar os tópicos do Kafka:

- **URL:** `http://localhost:8085`

## Testes via Postman
Para testar as requisições via Postman, utilize as collections disponíveis na pasta collections localizada na raiz do projeto.

### Importe a Collection para o Postman:

```bash
Abra o Postman.
```

```bash
Clique em Import e selecione os arquivos da pasta collections.
```
```bash
Execute as Requisições:
```

```bash
Utilize os endpoints fornecidos para testar a criação, listagem, atualização e deleção de pedidos.
```

## Conclusão

Este desenvolvimento foi estruturado de forma simples, com foco exclusivo no processamento de pedidos. No entanto, uma solução completa incluiria tabelas e funcionalidades adicionais, como:

Dados do cliente.
Informações de endereço.
Controle de estoque.
Integrações com sistemas externos.
Esses elementos seriam essenciais para atender às necessidades de um sistema robusto e escalável.



