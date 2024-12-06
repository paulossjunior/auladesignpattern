# Padrões de Projeto (Design Patterns)

## 📚 Introdução
Padrões de Projeto são soluções elegantes e reutilizáveis para problemas comuns no desenvolvimento de software. Eles ajudam a criar sistemas mais flexíveis, modulares e de fácil manutenção.

## 🏗️ Padrões Arquiteturais

São [padrões](designpatterns-structural.md) que definem a estrutura fundamental de uma aplicação de software:

### 1. MVC (Model-View-Controller)
- **Model**: Gerencia os dados e a lógica de negócios
- **View**: Apresenta os dados ao usuário
- **Controller**: Gerencia a comunicação entre Model e View
- **Vantagens**:
  - Separação clara de responsabilidades
  - Facilita manutenção e teste
  - Permite desenvolvimento paralelo

### 2. MVP (Model-View-Presenter)
- **Model**: Gerencia dados e regras de negócio
- **View**: Interface do usuário passiva
- **Presenter**: Mediador entre Model e View
- **Vantagens**:
  - View mais simples que no MVC
  - Melhor testabilidade
  - Maior separação entre View e lógica

### 3. MVVM (Model-View-ViewModel)
- **Model**: Dados e regras de negócio
- **View**: Interface do usuário
- **ViewModel**: Conversor de dados do Model para View
- **Vantagens**:
  - Binding de dados bidirecional
  - Ótimo para interfaces reativas
  - Popular em frameworks modernos

### 4. Layered Architecture (Arquitetura em Camadas)
- **Presentation Layer**: Interface do usuário
- **Business Layer**: Lógica de negócios
- **Data Layer**: Acesso a dados
- **Vantagens**:
  - Separação clara de responsabilidades
  - Facilita manutenção
  - Permite escalabilidade

### 5. Microservices Architecture
- Serviços pequenos e independentes
- Cada serviço com sua própria base de dados
- Comunicação via APIs
- **Vantagens**:
  - Alta escalabilidade
  - Deployment independente
  - Tecnologias flexíveis

### 6. Clean Architecture
- Camadas concêntricas de responsabilidade
- Dependências apontam para dentro
- Regras de negócio no centro
- **Vantagens**:
  - Independência de frameworks
  - Testabilidade
  - Independência de UI



## 🏗️ Padrões Estruturais (Structural Patterns)

Os padrões estruturais lidam com a composição de classes e objetos para formar estruturas maiores.

### Principais Padrões:

1. **Adapter (Adaptador)**
   - Converte a interface de uma classe em outra interface esperada pelo cliente
   - Permite que classes incompatíveis trabalhem juntas

2. **Bridge (Ponte)**
   - Separa uma abstração de sua implementação
   - Permite que ambas variem independentemente

3. **Composite (Composto)**
   - Compõe objetos em estruturas de árvore
   - Permite que clientes tratem objetos individuais e composições uniformemente

4. **Decorator (Decorador)**
   - Adiciona responsabilidades adicionais a objetos dinamicamente
   - Fornece uma alternativa flexível à herança

5. **Facade (Fachada)**
   - Fornece uma interface unificada para um conjunto de interfaces
   - Simplifica o uso de subsistemas complexos

6. **Flyweight (Peso Leve)**
   - Compartilha eficientemente objetos que são usados em grande quantidade
   - Reduz o uso de memória

7. **Proxy**
   - Fornece um substituto ou placeholder para outro objeto
   - Controla o acesso ao objeto original

## 🏭 Padrões de Projeto Criacionais (Creational Patterns)

Os [padrões criacionais]((designpatterns-creational.md) lidam com mecanismos de criação de objetos.

### Principais Padrões:

1. **Factory Method (Método Fábrica)**
   - Define uma interface para criar objetos
   - Permite que subclasses decidam quais classes instanciar

2. **Abstract Factory (Fábrica Abstrata)**
   - Fornece uma interface para criar famílias de objetos relacionados
   - Garante que os objetos criados sejam compatíveis entre si

3. **Builder (Construtor)**
   - Separa a construção de um objeto complexo de sua representação
   - Permite o mesmo processo de construção criar diferentes representações

4. **Prototype (Protótipo)**
   - Cria novos objetos clonando um protótipo
   - Evita o custo de criar novos objetos usando o operador new

5. **Singleton**
   - Garante que uma classe tenha apenas uma instância
   - Fornece um ponto global de acesso a essa instância

## 🎭 Padrões de Projeto Comportamentais (Behavioral Patterns)

Os (padrões comportamentais)[designpatterns-behavioural.md] lidam com a comunicação entre objetos, como os objetos interagem e distribuem responsabilidades.

### Principais Padrões:

1. **Chain of Responsibility (Cadeia de Responsabilidade)**
   - Passa uma solicitação ao longo de uma cadeia de handlers
   - Cada handler decide processar ou passar adiante

2. **Command (Comando)**
   - Encapsula uma solicitação como um objeto
   - Permite parametrizar clientes com diferentes solicitações

3. **Iterator (Iterador)**
   - Fornece uma maneira de acessar elementos sequencialmente
   - Não expõe a representação subjacente

4. **Mediator (Mediador)**
   - Define um objeto que encapsula como outros objetos interagem
   - Promove acoplamento fraco

5. **Observer (Observador)**
   - Define uma dependência um-para-muitos entre objetos
   - Quando um objeto muda de estado, todos seus dependentes são notificados

6. **State (Estado)**
   - Permite que um objeto altere seu comportamento quando seu estado interno muda
   - O objeto parecerá ter mudado sua classe

7. **Strategy (Estratégia)**
   - Define uma família de algoritmos
   - Torna os algoritmos intercambiáveis e independentes dos clientes

8. **Template Method (Método Modelo)**
   - Define o esqueleto de um algoritmo em uma operação
   - Permite que subclasses redefinam certos passos

## 🛠️ Como Utilizar
- Identifique o problema que precisa resolver
- Compare com os padrões disponíveis
- Escolha o padrão mais adequado
- Implemente seguindo as diretrizes do padrão escolhido

## 📈 Benefícios
1. Reutilização de código
2. Código mais organizado e manutenível
3. Comunicação mais eficiente entre desenvolvedores
4. Soluções comprovadas para problemas comuns

## ⚠️ Considerações
- Não force o uso de padrões quando não necessário
- Considere o contexto e as necessidades específicas do projeto
- Balance a complexidade adicional com os benefícios obtidos

## 📚 Recursos Adicionais
- "Design Patterns: Elements of Reusable Object-Oriented Software" (Gang of Four)
- "Head First Design Patterns"
- Repositórios de exemplos práticos no GitHub
