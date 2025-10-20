#  Mini-ORM en Java

## Objetivo
Construir un **mini-ORM en Java** desde cero siguiendo una **arquitectura en capas**, aplicando principios **SOLID**, uso de **reflexión**, **Lombok**, y **Maven**.  
El propósito es comprender cómo funcionan internamente frameworks como Hibernate o JPA, pero implementando un sistema propio y simplificado.



## Arquitectura del proyecto

La aplicación sigue una **arquitectura en capas**, donde cada paquete cumple una función específica:


mini-orm/
├─ pom.xml
└─ src/
   ├─ main/java/com/miniorm/
   │  ├─ annotations/      → Define anotaciones personalizadas (@Entity, @Id, @Column, @GeneratedValue)
   │  ├─ enums/            → Define tipos de estrategias de generación de IDs
   │  ├─ models/           → Entidades del dominio (User, Product, etc.)
   │  ├─ repository/       → Interfaces genéricas de persistencia
   │  ├─ core/             → EntityManager e implementación In-Memory del repositorio
   │  ├─ service/          → Lógica de negocio (UserService, ProductService)
   │  ├─ dto/              → Objetos de transferencia de datos (RegisterUserDto)
   │  └─ app/              → Capa de presentación (Main.java)



## Principios aplicados

- **SRP:** Cada clase tiene una única responsabilidad.
- **OCP:** Abierto a extensión, cerrado a modificación.
- **LSP:** Las implementaciones pueden sustituirse sin romper la lógica.
- **ISP:** Interfaces específicas (GenericRepository).
- **DIP:** Inversión de dependencias (servicios dependen de abstracciones, no implementaciones concretas).


##  Componentes principales

###  1. Anotaciones personalizadas
Permiten agregar metadatos a las entidades para su mapeo con el repositorio, usando **reflexión** en tiempo de ejecución.

###  2. Entidades
Representan tablas en memoria, con anotaciones que indican las columnas y estrategias de ID.  
Se usa **Lombok** para generar automáticamente getters, setters y constructores.

###  3. Repositorio Genérico
Define las operaciones CRUD (Create, Read, Update, Delete) de forma genérica.

### 4. Implementación In-Memory
Guarda las entidades en un `ConcurrentHashMap`, simulando una base de datos.  
Usa **reflexión** para acceder al campo anotado con `@Id` y genera IDs automáticos si no se proporcionan.

###  5. EntityManager
Fábrica de repositorios: se encarga de proveer instancias de repositorios a la capa de servicio.

###  6. Servicios
Orquesta las operaciones de negocio, aplica lógica antes de persistir o actualizar datos.

###  7. DTOs
Ejemplo: `RegisterUserDto` encapsula los datos necesarios para registrar un usuario, separando la capa de presentación de la de dominio.

###  8. Aplicación principal
Demuestra el uso del ORM: crea usuarios, los lista y simula operaciones CRUD.
