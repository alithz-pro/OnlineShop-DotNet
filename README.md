# Online Shop — .NET

A simple online shop backend built with **ASP.NET Core Web API**, **Entity Framework Core**, and **SQL Server**, with the domain organized around **Domain-Driven Design (DDD)** principles.

This project was developed as the final project of a web development course at **Mojtama Fanni Tehran (MFT)**, before the widespread use of AI-assisted development tools.

> **Project type:** Educational backend / REST API
> **Primary focus:** Backend development, API design, DDD, and software architecture

---

## About the Project

The goal of this project was to build the backend of a simple online shopping system while applying the architectural and backend concepts taught during the course.

Rather than keeping the entire application in a single project, the solution was divided into separate layers for:

* Domain logic
* Application services
* Application contracts and DTOs
* Database access
* Web API

The domain was further organized into aggregates such as **Products**, **People**, and **Orders**.

---

## Architecture

The solution is organized into several projects:

```text
OnlineShop
│
├── OnlineShopProject.WebApi
├── OnlineShopProject.Application
├── OnlineShopProject.Application.Contract
├── OnlineShopProject.Domain
├── OnlineShopProject.Domain.Contract
└── OnlineShopProject.EntityFrameworkCore
```

### Domain Layer

The domain contains the core business concepts and is organized around aggregates:

```text
Domain
├── Aggregates
│   ├── OrderAggregate
│   ├── PersonAggregate
│   └── ProductAggregate
├── Factories
├── Frameworks
└── Repositories
```

The repository defines repository contracts for entities such as products, people, orders, and order details.

### Application Layer

The application layer coordinates use cases between the API and the domain/persistence layers.

It contains:

* Application services
* DTOs
* Interfaces
* AutoMapper profiles

Examples include:

* `PersonApplicationService`
* `ProductApplicatonService`

### Persistence Layer

The `EntityFrameworkCore` project is responsible for database persistence.

It contains:

* Entity Framework Core configuration
* `DbContext`
* Database migrations
* Persistence services

The project uses **SQL Server** as its database provider.

### Web API Layer

The Web API exposes the application's functionality through REST-style HTTP endpoints.

Controllers include:

* `ProductController`
* `PersonController`

The API uses dependency injection to communicate with application services rather than directly implementing business logic inside controllers.

---

## Features

### Product Management

The product API supports:

* Retrieve a product by ID
* Retrieve the product list
* Create a product
* Update a product
* Delete a product

### Person Management

The person API supports:

* Retrieve a person
* Retrieve people
* Create a person
* Update a person
* Delete a person

### API Documentation

The project includes Swagger/OpenAPI tooling for exploring and documenting the API.

---

## Technology Stack

| Technology            | Purpose                   |
| --------------------- | ------------------------- |
| C#                    | Programming language      |
| .NET 5                | Original target framework |
| ASP.NET Core Web API  | HTTP API                  |
| Entity Framework Core | ORM / database access     |
| SQL Server            | Database                  |
| AutoMapper            | Object-to-object mapping  |
| Swagger / NSwag       | API documentation         |
| Newtonsoft.Json       | JSON serialization        |

---

## Domain-Driven Design

One of the main goals of this project was to become familiar with **Domain-Driven Design (DDD)** concepts.

The domain is separated from the API and infrastructure concerns and is structured around aggregates:

```text
ProductAggregate
PersonAggregate
OrderAggregate
```

The project also introduces concepts such as:

* Aggregates
* Factories
* Repository abstractions
* Domain contracts
* Application services
* DTOs

The implementation should be understood in the context of an educational project: it was an early practical attempt at applying DDD concepts rather than a production-scale DDD system.

---

## API Structure

The controllers follow a relatively thin-controller approach.

For example, the product controller delegates operations to:

```text
IProductApplicationService
```

rather than directly performing database operations.

A simplified request flow is:

```text
HTTP Request
     │
     ▼
Web API Controller
     │
     ▼
Application Service
     │
     ▼
Domain / Repository Abstractions
     │
     ▼
Entity Framework Core
     │
     ▼
SQL Server
```

This separation was one of the main architectural concepts practiced in the project.

---

## Project Structure

```text
OnlineShopProject.WebApi
    Controllers
        PersonController.cs
        ProductController.cs
        WeatherForecastController.cs

OnlineShopProject.Application
    Abstracts
    DTOs
    Profiles
    Services

OnlineShopProject.Application.Contract
    Abstracts
    Base
    DTOs

OnlineShopProject.Domain
    Aggregates
        OrderAggregate
        PersonAggregate
        ProductAggregate
    Factories
        OrderFactory
        PersonFactory
        ProductFactory
    Frameworks
    Reporities

OnlineShopProject.Domain.Contract
    Abstracts

OnlineShopProject.EntityFrameworkCore
    Configurations
    Frameworks
    Migrations
    Services
    OnlineShopProjectDbContext.cs
```

---

## Learning Goals

This project was primarily an exercise in learning how to build a structured backend application rather than simply creating CRUD endpoints.

The main concepts practiced were:

* C# backend development
* ASP.NET Core Web API
* REST APIs
* Dependency Injection
* Layered architecture
* Domain-Driven Design
* Aggregates
* Repository pattern
* Factory pattern
* DTOs
* Application services
* Entity Framework Core
* SQL Server
* Database migrations
* Object mapping
* Swagger/OpenAPI

---

## Course Context

This project was created as the **final project of a web development course at Mojtama Fanni Tehran (MFT)**.

It represents an earlier stage of my software-development experience, when I was learning backend development and software architecture through hands-on implementation.

The project predates the current era of widespread AI-assisted coding, and was developed as a conventional student project using the tools and concepts I was learning at the time.

---

## Notes

The repository currently reflects the original `.NET 5` implementation.

The project was later updated to **.NET 7**, but the version currently visible in the repository contains `.NET 5` project configuration.

This distinction is intentional in the portfolio description so that the repository does not claim a framework version that is not represented by the current source tree.

---

## Disclaimer

This is an educational project created for coursework and personal learning.

It is not intended to represent a production-ready e-commerce platform.

---

## License

No license has been specified for this project.
