# MarketMenu - MVP (Lista de Compras)

Este repositório contém o projeto **MarketMenu**, um aplicativo para gerenciamento de listas de compras de supermercado. O foco inicial do MVP é permitir que o usuário crie, edite e acompanhe suas listas de compras, com arquitetura orientada a domínios e já preparada para expansão futura.

---

## Visão Geral da Arquitetura

O projeto segue princípios de **Domain-Oriented Microservice Architecture (DOMA)**, com separação entre domínios e uso de BFF (Backend For Frontend) por domínio para facilitar evolução e desacoplamento entre frontends e microserviços.

### Domínios (Domains)

- **User Domain**  
  Gestão de usuários, autenticação e perfis.

- **Product Domain**  
  Gestão de produtos disponíveis para adicionar às listas de compras.

- **ShoppingList Domain**  
  Gestão de listas de compras e itens dessas listas.

### Microserviços

Cada domínio possui um microserviço dedicado:

- `UserService`
- `ProductService`
- `ShoppingListService`

Cada microserviço possui seu próprio banco de dados.

### BFFs (Backend For Frontend)

Cada domínio possui um BFF próprio, responsável por expor endpoints adequados para as necessidades do frontend e orquestrar chamadas aos microserviços:

- `UserBFF`
- `ProductBFF`
- `ShoppingListBFF`

### Kubernetes

No Kubernetes, cada microserviço e BFF é um deployment e service separado. Um Ingress Controller é utilizado para rotear as requisições externas aos BFFs correspondentes.

```
[Ingress]
   |
   |---> [user-bff]         ---> [user-service]         ---> [user-db]
   |---> [product-bff]      ---> [product-service]      ---> [product-db]
   |---> [shoppinglist-bff] ---> [shoppinglist-service] ---> [shoppinglist-db]
```

---

## Convenções

- **Nomenclatura:** Todos os domínios, entidades e projetos utilizam nomes em inglês.
- **Padrões de código:** Utilizar as convenções do .NET.
- **Separação de responsabilidades:** Cada domínio é isolado e exposto por seu respectivo BFF.

---

## Próximos Passos

- Definir a estrutura dos projetos e soluções para cada domínio e BFF.
- Criar os modelos de dados iniciais para o MVP.
- Implementar endpoints mínimos para gerenciamento de listas de compras.

---

## Como contribuir

1. Siga a arquitetura e convenções descritas acima.
2. Sempre documente novas decisões de arquitetura neste arquivo.
3. Utilize nomes técnicos em inglês para domínios, entidades e projetos.
4. Para dúvidas ou discussões, utilize as Issues do repositório.

---

## Contato

Dúvidas ou sugestões: [@mauricionofre](https://github.com/mauricionofre)