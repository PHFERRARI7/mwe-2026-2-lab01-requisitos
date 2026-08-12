### Sistema de Design Document (SDD)

**Bounded Contexts:**
- **C1:** Web Enterprise System (wES) - Representa o ambiente empresarial onde as transações ocorrerão.
  - Linguagem Ubiqua:
    - `HTTP Request` -> HTTP POST, GET, PATCH, DELETE
    - `HTTP Response` -> JSON

**Camadas de Transporte:**
- **A1:** A camada do protocolo HTTP (TCP)
  - Justificativa: TCP é necessário para garantir a transmissão segura e confiável dos dados entre os usuários, sistemas operacionais e aplicativos web da empresa. Além disso, ele fornecerá uma comunicação robusta que pode lidar com possíveis falhas.
- **B1:** A camada de protocolo HTTP (UDP)
  - Justificativa: UDP é adequado para transmissões onde a latência e o desempenho são mais importantes do que a segurança. Em um ambiente empresarial, a precisão e precisão de dados são mais importante.

**Fluxos de Dados:**
- **UC01:** Login (POST)
  - Fluido Principal:
    1. Os usuários enviaram uma requisição POST com os dados necessários (login e senha).
    2. O wES recebe a requisição, verifica o login.
    3. Se os dados forem válidos, envia um token de autenticação para o usuário.
- **UC02:** Consulta de Produtos (GET)
  - Fluido Principal:
    1. O wES recebe uma solicitação GET com a descrição do produto.
    2. O wES busca os dados no banco de dados e retorna um JSON com as informações solicitadas.
- **UC03:** Reserva de Vagas (POST)
  - Fluido Principal:
    1. O usuário faz login na plataforma.
    2. Ele seleciona uma vaga para se inscrever.
    3. Os dados da inscrição são enviados para a API do back-end.

**Requisitos Não-Funcionais:**
- **Desempenho (RPS, tempo de resposta p95/p99):** RPS = 100 req/s e tempo médio de resposta menor que 1 segundo.
- **Segurança (OAuth2, RBAC, OIDC):** OAuth2 para autenticação; RBAC para revisar as permissões dos usuários; OIDC para autenticação multi-tópicos.

**Escala de Escalabilidade:**
- A wES pode ser escalada através da implementação de microservices. Cada serviço será responsável por um determinado aspecto do sistema, permitindo que sejam criadas múltiplas instâncias e as capacidades serão distribuídas para otimizar o desempenho.
  
**Docker/Kubernetes:**
- A wES implementará uma infraestrutura de containerização utilizando Docker e Kubernetes para garantir a disponibilidade dos serviços da aplicação. A implementação desses frameworks também fornecerá um ambiente escalável, onde as instâncias das imagens seriam replicadas em múltiplas contêineres e podres que poderiam ser acessados remotamente por qualquer usuário na empresa.

**Conclusion:**
A wES é uma plataforma que permite a realização de transações eficientes entre os usuários da empresa, garantindo a segurança dos dados dos clientes. A implementação de microservices e a infraestrutura de containerização Kubernetes/Kubernetes permitem que a wES seja escalável, resiliente, e otimizada para operar em ambientes empresariais com alta demanda.
