# 🐾 PetJourney API - Módulo Clínico

[![Java](https://img.shields.io/badge/Java-17-blue.svg)](https://adoptium.net/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.4.0-brightgreen.svg)](https://spring.io/projects/spring-boot)
[![H2 Database](https://img.shields.io/badge/H2-Database-blue.svg)](https://www.h2database.com/)
[![Swagger](https://img.shields.io/badge/Swagger-OpenAPI-85EA2D.svg)](https://swagger.io/)

## 👥 Equipe
Nome	RM
Lucas Grillo Alcântara	561413
Pietro Ferreira Gomes Abraâmico	561469
Pedro Peres Benítez	561792
Lucca Ramos Mussumecci	562027
Turma: 2TDSPX

## 📋 Sumário
- [Sobre o Projeto](#-sobre-o-projeto)
- [Tecnologias Utilizadas](#-tecnologias-utilizadas)
- [Arquitetura do Projeto](#-arquitetura-do-projeto)
- [Relacionamentos do Projeto](#-relacionamentos-do-projeto).
- [Requisitos Técnicos Atendidos](#-requisitos-técnicos-atendidos)
- [Endpoints da API](#-petjourney-api-endpoints)
- [Como Executar](#-como-executar)


## 📌 Sobre o Projeto
O **PetJourney** é uma solução completa para o gerenciamento de clínicas veterinárias e acompanhamento preventivo da saúde pet. Esta API foca no módulo clínico, permitindo que veterinários registrem prontuários, prescrevam medicamentos e gerenciem agendamentos, enquanto tutores acompanham o histórico de seus pets.

## 🛠️ Tecnologias Utilizadas
- **Linguagem**: Java 17
- **Framework**: Spring Boot 3.4.0
- **Persistência**: Spring Data JPA
- **Banco de Dados**: H2
- **Documentação**: SpringDoc OpenAPI (Swagger)
- **Utilidades**: Lombok, Spring Boot DevTools
- **HATEOAS**: Spring HATEOAS
- **Cache**: Spring Cache

## 🏗️ Arquitetura do Projeto
O projeto segue a arquitetura de camadas padrão do Spring Boot:
- **Controllers**: Exposição dos endpoints REST e implementação de HATEOAS.
- **Services**: Lógica de negócio, orquestração e gerenciamento de cache.
- **Repositories**: Interface de comunicação com o banco de dados via Spring Data JPA.
- **Models**: Entidades JPA com lógica de atualização interna (`updateFrom`).
- **DTOs**: Records para requisições e Classes para respostas (suporte a `RepresentationModel`).

````markdown id="j3r8jv"
## 📁 Project Structure

```
src/main/java/br/com/fiap/petjourney/
├── config/
├── controllers/
├── dtos/
│   ├── request/
│   └── response/
├── exceptions/
├── models/
│   └── enums/
├── repositories/
├── services/
└── PetJourneyApplication.java
```
````
## 🔗 Relacionamentos do Projeto

O sistema **PetJourney API** foi modelado utilizando relacionamentos entre entidades para representar o funcionamento de uma clínica veterinária de forma organizada e escalável.

### 🏥 Clinic

A entidade `Clinic` representa a clínica veterinária e possui relacionamento com os veterinários e agendamentos do sistema.

* Uma clínica pode possuir vários veterinários.
* Uma clínica pode possuir vários agendamentos.

### 👨‍⚕️ Veterinarian

A entidade `Veterinarian` representa os veterinários cadastrados no sistema.

* Cada veterinário pertence a uma clínica.
* Um veterinário pode realizar vários atendimentos.
* Um veterinário pode registrar vários prontuários médicos.
* Um veterinário pode prescrever vários medicamentos.

### 👤 Tutor

A entidade `Tutor` representa o responsável pelo pet.

* Um tutor pode possuir vários pets cadastrados.

### 🐶 Pet

A entidade `Pet` representa os animais cadastrados no sistema.

* Cada pet pertence a um tutor.
* Um pet pode possuir vários prontuários médicos.
* Um pet pode possuir vários medicamentos.
* Um pet pode possuir vários agendamentos.

### 📄 MedicalRecord

A entidade `MedicalRecord` representa os prontuários médicos dos pets.

* Cada prontuário pertence a um pet.
* Cada prontuário é registrado por um veterinário.

### 💊 Medication

A entidade `Medication` representa os medicamentos prescritos.

* Cada medicamento pertence a um pet.
* Cada medicamento é associado a um veterinário responsável pela prescrição.

### 📅 Appointment

A entidade `Appointment` representa os agendamentos realizados na clínica.

* Cada agendamento pertence a um pet.
* Cada agendamento possui um veterinário responsável.
* Cada agendamento pertence a uma clínica.


## ✅ Requisitos Técnicos Atendidos
- **CRUD Completo**: Para todas as entidades principais.
- **Busca por Parâmetros**: Filtragem de tutores, veterinários, pets e agendamentos.
- **Paginação e Ordenação**: Implementada em todos os endpoints de listagem via `Pageable`.
- **HATEOAS**: Links de auto-referência (`self`) e navegação em todos os recursos.
- **Cache**: Implementado nas consultas de Pets e Prontuários Médicos.
- **Tratamento de Exceções**: Handler global com respostas padronizadas e exceções customizadas.

## 📌 PetJourney API Endpoints

## 🏥 Clinics

| Método | Endpoint        | Descrição                |
| ------ | --------------- | ------------------------ |
| GET    | `/clinics`      | Listar todas as clínicas |
| GET    | `/clinics/{id}` | Buscar clínica por ID    |
| POST   | `/clinics`      | Criar nova clínica       |
| PUT    | `/clinics/{id}` | Atualizar clínica        |
| DELETE | `/clinics/{id}` | Deletar clínica          |

---

## 👨‍⚕️ Veterinarians

| Método | Endpoint              | Descrição                 |
| ------ | --------------------- | ------------------------- |
| GET    | `/veterinarians`      | Listar veterinários       |
| GET    | `/veterinarians/{id}` | Buscar veterinário por ID |
| POST   | `/veterinarians`      | Criar veterinário         |
| PUT    | `/veterinarians/{id}` | Atualizar veterinário     |
| DELETE | `/veterinarians/{id}` | Deletar veterinário       |

---

## 👤 Tutors

| Método | Endpoint       | Descrição           |
| ------ | -------------- | ------------------- |
| GET    | `/tutors`      | Listar tutores      |
| GET    | `/tutors/{id}` | Buscar tutor por ID |

---

## 🐶 Pets

| Método | Endpoint     | Descrição         |
| ------ | ------------ | ----------------- |
| GET    | `/pets`      | Listar pets       |
| GET    | `/pets/{id}` | Buscar pet por ID |

---

## 📋 Medical Records

| Método | Endpoint                                          | Descrição                   |
| ------ | ------------------------------------------------- | --------------------------- |
| GET    | `/medical-records/pet/{petId}`                    | Listar prontuários do pet   |
| GET    | `/medical-records/search?start={start}&end={end}` | Buscar prontuários por data |
| GET    | `/medical-records/{id}`                           | Buscar prontuário por ID    |
| POST   | `/medical-records`                                | Criar prontuário            |
| DELETE | `/medical-records/{id}`                           | Deletar prontuário          |

---

## 💊 Medications

| Método | Endpoint                   | Descrição                  |
| ------ | -------------------------- | -------------------------- |
| GET    | `/medications/pet/{petId}` | Listar medicamentos do pet |
| GET    | `/medications/{id}`        | Buscar medicamento por ID  |
| POST   | `/medications`             | Criar medicamento          |
| PUT    | `/medications/{id}`        | Atualizar medicamento      |
| DELETE | `/medications/{id}`        | Deletar medicamento        |

---

## 📅 Appointments

| Método | Endpoint                                       | Descrição                    |
| ------ | ---------------------------------------------- | ---------------------------- |
| GET    | `/appointments/pet/{petId}`                    | Listar agendamentos do pet   |
| GET    | `/appointments/search?start={start}&end={end}` | Buscar agendamentos por data |
| GET    | `/appointments/{id}`                           | Buscar agendamento por ID    |
| POST   | `/appointments`                                | Criar agendamento            |
| PUT    | `/appointments/{id}`                           | Atualizar agendamento        |
| DELETE | `/appointments/{id}`                           | Deletar agendamento          |

---


## 🚀 Como Executar
1. Clone o repositório.
2. Certifique-se de ter o JDK 17 instalado.
3. Execute o comando: `./mvnw spring-boot:run`
4. Acesse o Swagger UI: `http://localhost:8080/swagger-ui/index.html`
5. Acesse o H2 Console: `http://localhost:8080/h2-console` (JDBC URL: `jdbc:h2:mem:petjourneydb`)


