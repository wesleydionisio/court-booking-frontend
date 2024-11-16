# Sistema de Agendamento de Quadras - Documentação Frontend

## Índice

* [Descrição do Projeto](#descrição-do-projeto)
* [Funcionalidades Principais](#funcionalidades-principais)
* [Estrutura do Projeto](#estrutura-do-projeto)
* [Fluxo do Usuário](#fluxo-do-usuário)
* [Regras de Negócio](#regras-de-negócio)
* [Próximos Passos](#próximos-passos)
* [Design e Estilo](#design-e-estilo)

## Descrição do Projeto

O frontend será desenvolvido em React com Material-UI para estilização, proporcionando uma interface moderna e responsiva. O objetivo é criar uma experiência de agendamento simples e intuitiva, desde a exibição das quadras até a criação e revisão de reservas.

## Funcionalidades Principais

### 1. Página Inicial

* Exibição de todas as quadras disponíveis em formato de cards
* Cada card deve conter:
  * Nome da quadra
  * Imagem principal da quadra
  * Clique no card redireciona o usuário para a tela de agendamento

### 2. Tela de Agendamento

* **Banner da quadra**:
  * Imagem principal
  * Nome da quadra
* **Conteúdo da reserva**:
  * Calendário para seleção de data
  * Time slots (horários disponíveis):
    * Exibem apenas os horários dentro do funcionamento
    * Horários fora do funcionamento não aparecem
    * Horários já reservados aparecem "congelados"
  * Seleção do esporte:
    * Lista dinâmica dos esportes permitidos
  * Seleção do método de pagamento:
    * Lista dinâmica das opções disponíveis

### 3. Criar Reserva

* Ao clicar em "Criar Reserva":
  * Verificar se o usuário está logado
  * Se não estiver:
    * Redirecionar para tela de login/criar conta
    * Após login, concluir a reserva com dados preenchidos
  * Após a reserva, redirecionar para tela de revisão

### 4. Tela de Revisão da Reserva

* **Exibir dados da reserva**:
  * Nome da quadra
  * Data e horário
  * Esporte selecionado
  * Método de pagamento
* **Opções**:
  * Botão para "Início"
  * Botão para "Cancelar Reserva"

### 5. Autenticação de Usuário

* **Tela de login/criar conta**:
  * Login com e-mail e senha
  * Cadastro de novos usuários
* **Após autenticação**:
  * Manter estado do usuário logado
  * Retornar à etapa de criação da reserva

## Estrutura do Projeto

### 1. Páginas

* `HomePage`: Página inicial com lista de quadras
* `BookingPage`: Tela de agendamento
* `LoginPage`: Tela para login/registro
* `ReviewPage`: Tela de revisão da reserva

### 2. Componentes

#### Globais
* `Header`: Navegação com logo e auth
* `Footer`: Informações gerais

#### Específicos
* `CourtCard`: Cards das quadras
* `Calendar`: Seletor de data
* `TimeSlots`: Horários disponíveis
* `SportsDropdown`: Seleção de esportes
* `PaymentOptions`: Seleção de pagamento

### 3. Estados Globais

* Autenticação do usuário
* Dados da reserva (quadra, data, horário, esporte, pagamento)

### 4. APIs

#### Quadras
```typescript
GET /api/courts
```

#### Horários Agendados
```typescript
GET /api/bookings/:quadraId/reserved-times?data=YYYY-MM-DD
```

#### Criação de Reserva
```typescript
POST /api/bookings
```

#### Autenticação
```typescript
POST /api/auth/login
POST /api/auth/register
```

## Fluxo do Usuário

### Página Inicial
1. Acesso à página inicial
2. Visualização dos cards de quadras
3. Clique em um card → tela de agendamento

### Tela de Agendamento
1. Visualização do banner da quadra
2. Seleção de data no calendário
3. Visualização dos time slots disponíveis
4. Seleção do esporte
5. Seleção da forma de pagamento
6. Clique em "Criar Reserva"

### Autenticação
1. Caso não logado:
   * Redirecionamento para login/registro
   * Retorno automático após autenticação

### Tela de Revisão
1. Exibição dos dados da reserva
2. Opções de confirmação ou cancelamento

## Regras de Negócio

### 1. Horários Disponíveis
* Exibição apenas dentro do horário de funcionamento
* Horários reservados → "congelados"

### 2. Esportes Permitidos
* Seleção limitada aos esportes suportados pela quadra

### 3. Métodos de Pagamento
* Exibição apenas das formas suportadas

### 4. Autenticação
* Reservas exclusivas para usuários autenticados

### 5. Validação do Frontend
* Conformidade com regras da API
* Mensagens de erro amigáveis

## Próximos Passos

### 1. Configuração Inicial
- [ ] Instalar React + Material-UI
- [ ] Configurar react-router-dom
- [ ] Estruturar componentes e páginas

### 2. Integração com API
- [ ] Configurar serviço de consumo
- [ ] Implementar chamadas aos endpoints

### 3. Criação dos Componentes
- [ ] Desenvolver componentes globais
- [ ] Desenvolver componentes específicos
- [ ] Implementar estilização Material-UI

### 4. Gerenciamento de Estado
- [ ] Configurar Context API/Redux
- [ ] Implementar estado de autenticação
- [ ] Implementar estado da reserva

### 5. Teste e Validação
- [ ] Validar funcionalidades
- [ ] Verificar regras de negócio
- [ ] Testar integração com API

## Design e Estilo

O design será baseado em Material-UI, garantindo:
* Layout responsivo (desktop/mobile)
* Componentes interativos
* Estilo consistente com Material Design

---

📝 Para sugestões ou dúvidas, abra uma issue no repositório!