# 🐾 PetJourney API - Módulo Clínico

[![Java](https://img.shields.io/badge/Java-17-blue.svg)](https://adoptium.net/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.4.0-brightgreen.svg)](https://spring.io/projects/spring-boot)
[![H2 Database](https://img.shields.io/badge/H2-Database-blue.svg)](https://www.h2database.com/)
[![Swagger](https://img.shields.io/badge/Swagger-OpenAPI-85EA2D.svg)](https://swagger.io/)

## 📋 Sumário
- [Sobre o Projeto](#-sobre-o-projeto)
- [Cronograma de Desenvolvimento](#-cronograma-de-desenvolvimento)
- [Tecnologias Utilizadas](#-tecnologias-utilizadas)
- [Arquitetura do Projeto](#-arquitetura-do-projeto)
- [Requisitos Técnicos Atendidos](#-requisitos-técnicos-atendidos)
- [Diagramas (UML e DER)](#-diagramas)
- [Endpoints da API](#-endpoints-da-api)
- [Como Executar](#-como-executar)
- [Testes da API (Postman)](#-testes-da-api)

## 📌 Sobre o Projeto
O **PetJourney** é uma solução completa para o gerenciamento de clínicas veterinárias e acompanhamento preventivo da saúde pet. Esta API foca no módulo clínico, permitindo que veterinários registrem prontuários, prescrevam medicamentos e gerenciem agendamentos, enquanto tutores acompanham o histórico de seus pets.

## 📅 Cronograma de Desenvolvimento
| Fase | Descrição | Status |
| :--- | :--- | :--- |
| **Sprint 1** | Planejamento, Modelagem DER e Configuração do Projeto Base | ✅ Concluído |
| **Sprint 2** | Implementação das Entidades, Repositories e DTOs (Records) | ✅ Concluído |
| **Sprint 3** | Desenvolvimento da Camada de Service com Regras de Negócio e Cache | ✅ Concluído |
| **Sprint 4** | Implementação dos Controllers REST, Paginação e Ordenação | ✅ Concluído |
| **Sprint 5** | Refinamento: Tratamento de Exceções Customizado e HATEOAS | ✅ Concluído |
| **Sprint 6** | Auditoria Final, Documentação Técnica e Testes de Endpoints | ✅ Concluído |

## 🛠️ Tecnologias Utilizadas
- **Linguagem**: Java 17
- **Framework**: Spring Boot 3.4.0
- **Persistência**: Spring Data JPA
- **Banco de Dados**: H2 (In-memory)
- **Documentação**: SpringDoc OpenAPI (Swagger)
- **Utilidades**: Lombok, Spring Boot DevTools
- **HATEOAS**: Spring HATEOAS
- **Cache**: Spring Cache (ConcurrentMapCacheManager)

## 🏗️ Arquitetura do Projeto
O projeto segue a arquitetura de camadas padrão do Spring Boot:
- **Controllers**: Exposição dos endpoints REST e implementação de HATEOAS.
- **Services**: Lógica de negócio, orquestração e gerenciamento de cache.
- **Repositories**: Interface de comunicação com o banco de dados via Spring Data JPA.
- **Models**: Entidades JPA com lógica de atualização interna (`updateFrom`).
- **DTOs**: Records para requisições e Classes para respostas (suporte a `RepresentationModel`).

## ✅ Requisitos Técnicos Atendidos
- **CRUD Completo**: Para todas as entidades principais.
- **Busca por Parâmetros**: Filtragem de tutores, veterinários, pets e agendamentos.
- **Paginação e Ordenação**: Implementada em todos os endpoints de listagem via `Pageable`.
- **HATEOAS**: Links de auto-referência (`self`) e navegação em todos os recursos.
- **Cache**: Implementado nas consultas de Pets e Prontuários Médicos.
- **Tratamento de Exceções**: Handler global com respostas padronizadas e exceções customizadas.

## 📊 Diagramas
### Diagrama de Classes UML
![UML](https://private-us-east-1.manuscdn.com/sessionFile/LDDyuNbJSthi3bxz8adDs8/sandbox/2bz1lUDff6sy4hP0gFNRgj-images_1778818021905_na1fn_L2hvbWUvdWJ1bnR1L1BldEpvdXJuZXlfVU1MX0ZpbmFs.png?Policy=eyJTdGF0ZW1lbnQiOlt7IlJlc291cmNlIjoiaHR0cHM6Ly9wcml2YXRlLXVzLWVhc3QtMS5tYW51c2Nkbi5jb20vc2Vzc2lvbkZpbGUvTEREeXVOYkpTdGhpM2J4ejhhZERzOC9zYW5kYm94LzJiejFsVURmZjZzeTRoUDBnRk5SZ2otaW1hZ2VzXzE3Nzg4MTgwMjE5MDVfbmExZm5fTDJodmJXVXZkV0oxYm5SMUwxQmxkRXB2ZFhKdVpYbGZWVTFNWDBacGJtRnMucG5nIiwiQ29uZGl0aW9uIjp7IkRhdGVMZXNzVGhhbiI6eyJBV1M6RXBvY2hUaW1lIjoxNzk4NzYxNjAwfX19XX0_&Key-Pair-Id=K2HSFNDJXOU9YS&Signature=QQvqen-xmbw-0ryRkvTt~8tThJS2fz46oSM3FS~aW7sxi9zWpUviS0oRXFWHazJzJ6DToME5DI6y6AO1LW1Dxe5AN7Q2a3~99VvzaU2wARhASKWYC71zfKpDNLGChTfKWXjzdLYyJd~ZsLmwGINXiHunIrf4V85c-516eX2dq87~s67uRgQ-s~5Z-8JIN8g9N1KzaMTfkeM9Amfxtt-6IZUUSTDWmh97pUn5jOvkh4zT7riQbOWuBOGZaygcjILZkIQ~mkSEOoB2qZNQGUpQIJDBVx~grUAvJyWoGb5JB36Q4CKItGFDIfc2Nrk7g0-nT9HYSd77Kxh8pLKRfUoaYw__)

### Diagrama Entidade-Relacionamento (DER)
![DER](https://private-us-east-1.manuscdn.com/sessionFile/LDDyuNbJSthi3bxz8adDs8/sandbox/2bz1lUDff6sy4hP0gFNRgj-images_1778818021905_na1fn_L2hvbWUvdWJ1bnR1L1BldEpvdXJuZXlfREVSX0ZpbmFs.png?Policy=eyJTdGF0ZW1lbnQiOlt7IlJlc291cmNlIjoiaHR0cHM6Ly9wcml2YXRlLXVzLWVhc3QtMS5tYW51c2Nkbi5jb20vc2Vzc2lvbkZpbGUvTEREeXVOYkpTdGhpM2J4ejhhZERzOC9zYW5kYm94LzJiejFsVURmZjZzeTRoUDBnRk5SZ2otaW1hZ2VzXzE3Nzg4MTgwMjE5MDVfbmExZm5fTDJodmJXVXZkV0oxYm5SMUwxQmxkRXB2ZFhKdVpYbGZSRVZTWDBacGJtRnMucG5nIiwiQ29uZGl0aW9uIjp7IkRhdGVMZXNzVGhhbiI6eyJBV1M6RXBvY2hUaW1lIjoxNzk4NzYxNjAwfX19XX0_&Key-Pair-Id=K2HSFNDJXOU9YS&Signature=Sje4kUIOikytJFoMi5uPedfEJwn83BGjLPqCQLVNCgGLPTSWfLASTCAdDhqbHEuaBgAWlE80C38keMkRFMB8scW30zvm80p8meLJuqrWJYDi2T7c8d5VSjc7fudsOs3BlmbEnMOdo~BtP1eizRGPf4jbg8TJEZ-gCmzZIqsrUrJX67IVUPmoAGCqTX5n2X5sws8LGHMv59Aqsyh1ynkm-Dnd5dHsTAQxsEilv9uqYAeQe5dEx9zqrb6njNLa-ABp03i2A2poDnhISmnEVUoQqFm9TAcc6CdjkNdIg2TYP7bK8IvFuObJvWyTvm11gXI5DwTKYzBHZw4Rd0i~dKoYHA__)

## 🚀 Como Executar
1. Clone o repositório.
2. Certifique-se de ter o JDK 17 instalado.
3. Execute o comando: `./mvnw spring-boot:run`
4. Acesse o Swagger UI: `http://localhost:8080/swagger-ui/index.html`
5. Acesse o H2 Console: `http://localhost:8080/h2-console` (JDBC URL: `jdbc:h2:mem:petjourneydb`)

## 🧪 Testes da API
A coleção completa do Postman está disponível no arquivo `PetJourney_Postman_Collection.json`. Abaixo, seguem as evidências dos testes realizados:

*(Aqui você pode inserir as imagens enviadas no arquivo teste-postman.zip)*
