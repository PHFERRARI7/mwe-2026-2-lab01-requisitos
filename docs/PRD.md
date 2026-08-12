### Visão do Produto & Problema de Negócio

**Problema:** Como os operadores logísticos da LogiTech não têm atualizações precisas sobre a posição dos veículos em um momento específico, tornam-se eficientes na tomada de decisões e possuem um alto índice de faltas. 

**Visão:** Propor uma solução que permita aos motoristas, agentes logísticos, e todos os atores do ambiente LogiTech, acompanhar a localização real dos veículos por meio de tecnologias IoT, APIs de comunicação com veículos (TCV) e soluções de telemetria.

**Público-Alvo:** 
- **Operadores Logísticos:** Gerentes, Coordenadores de Transporte.
- **Agentes Logísticos:** Operadores de manutenção, mecânicos, inspetores.
- **Motoristas:** Pilotos da frota, motociclistas.

### Casos de Uso (Use Cases)

#### UC01 - Verificar Carga em Caminhão
**Ator:** Motorista  
**Pré-condição:** 
- Caminhão está no estacionamento.
- A carga deve estar na área do caminhão a ser aberta para visualização.

**Fluxo Principal:**
1. O motorista abre o cinto de segurança e posiciona-se em frente ao veículo.
2. Ele pressiona um botão específico que liga uma câmera fixada no interior do veículo à rotação das imagens da carga.
3. A imagem é transmitida por uma API de comunicação com veículos (TCV) para o backend, onde é processada e transmitida para os clientes da LogiTech.

**Critérios de Aceite:**
- O motorista deve ver a localização preciso da carga em tempo real.
- Se a imagem não for visível ou se houver algum problema com as câmeras, o motorista deverá ter uma notificação imediata para recarregar.

#### UC02 - Verificar Caminhoes na Matriz
**Ator:** Gerente de Operações  
**Pré-condição:** 
- A matriz deve estar no estado inicial onde todas as informações dos caminhões e cargas estão disponíveis.

**Fluxo Principal:**
1. O gerente abriu o módulo da Matriz de Caminhões.
2. Cada linha do relatório é atualizada com a localização, capacidade e outros dados relevantes do veículo.
3. Os motoristas podem ver suas posições em tempo real na matriz.

**Critérios de Aceite:**
- O gerente deve ter uma visão completa e precisas das operações dos caminhões que estão na matriz.
- Se não encontrar a carga em alguma linha da matriz, ele receberá um aviso imediato para buscar o veículo ou confirmar sua localização.

### Requisitos Não-Funcionais (RNFs) & SLAs

#### RNF1 - Desempenho
- **Resolução Atual:** P95 < 4 segundos.
- **Resolução Esperada:** A média de resolução da telemetria para todas as cargas em operação deve ser menor que 600 ms.

#### SLA2 - Segurança
- **OAuth2:** Autenticação via OAuth2, mantendo a privacidade dos dados.
- **RBAC (Role-Based Access Control):** Gerenciamento eficaz de acesso de acordo com as funções necessárias.
- **Oidc (OpenID Connect):** Framework seguro para autenticação de usuários.

#### SLA3 - Escalabilidade
- A solução deve ser capaz de suportar até 1.000 caminhões em operação simultânea, mantendo a latência dos serviços abaixo de 200 ms.
  
#### SLA4 - Conteinerização 
- As soluções de telemetria devem estar disponíveis na nuvem através das redes Docker/Kubernetes e ser escalável sem alterar o código.

### Conclusão

Esta solução proposta, baseada no padrão PRD, é aprimorada para adaptar-se à realidade do transporte logístico da LogiTech. Com base nessa análise, será possível otimizar os processos de atendimento ao cliente, aumentar a eficiência operacional e mitigar riscos associados a eventuais perda de cargas na distribuição.
