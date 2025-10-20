# Mini-ORM con Spring Boot

## Objetivo
Replicar la funcionalidad del Mini-ORM anterior pero utilizando el **framework Spring Boot**, aplicando los mismos principios arquitectónicos, ahora con **inyección de dependencias automática**, **controladores REST**, y simulación de persistencia **en memoria**.


## Arquitectura general

mini-orm-springboot/
├─ src/main/java/com/miniorm/
│  ├─ annotations/       → Reutilización de anotaciones personalizadas (opcional)
│  ├─ models/            → Entidades (User, Product)
│  ├─ repository/        → Interfaces de persistencia simulada (In-Memory)
│  ├─ service/           → Lógica de negocio (UserService, ProductService)
│  ├─ controller/        → Controladores REST
│  └─ MiniOrmApplication.java → Clase principal con @SpringBootApplication


## Dependencias

<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-jpa</artifactId>
    </dependency>
    <dependency>
        <groupId>org.projectlombok</groupId>
        <artifactId>lombok</artifactId>
    </dependency>
</dependencies>



## Capas y responsabilidades

###  1. Entidades
Modelan los objetos de negocio y definen las propiedades básicas.

###  2. Repositorio In-Memory
Simula una base de datos, gestionando CRUD básico con colecciones Java.

###  3. Servicios
Contienen la lógica de negocio y coordinan las operaciones del repositorio.

###  4. Controladores
Exponen endpoints HTTP (REST) para interactuar con las entidades.

###  5. Aplicación principal
Punto de entrada con la anotación `@SpringBootApplication`.  
Spring Boot se encarga de escanear los componentes, inyectar dependencias y exponer los endpoints.

