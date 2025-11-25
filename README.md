# 🚀 ProyectoAC301_RemusSabou

[![License](https://img.shields.io/github/license/MrBrad8989/ProyectoAC301_RemusSabou?style=flat-square)](https://github.com/MrBrad8989/ProyectoAC301_RemusSabou)
[![Java](https://img.shields.io/badge/Java-25-brightgreen?style=flat-square)](https://www.oracle.com/java/)
[![Maven](https://img.shields.io/badge/Maven-3.x-blue?style=flat-square)](https://maven.apache.org/)
[![MariaDB](https://img.shields.io/badge/DB-MariaDB-orange?style=flat-square)](https://mariadb.org/)

Aplicación Java (Maven) que utiliza JPA/Hibernate para persistencia en MariaDB.  
ArtifactId: `ProyectoAC301_RemusSabou` — GroupId: `es.iesjuanbosco` — Versión: `1.0-SNAPSHOT`

---

Contenido
- [Resumen](#resumen)
- [Tecnologías](#tecnologías)
- [Requisitos](#requisitos)
- [Instalación y ejecución rápida](#instalación-y-ejecución-rápida)
- [Configuración de la base de datos](#configuración-de-la-base-de-datos)
  - [persistence.xml (ejemplo)](#persistencexml-ejemplo)
  - [application.properties (ejemplo)](#applicationproperties-ejemplo)
  - [Docker / docker-compose (opcional)](#docker--docker-compose-opcional)
- [Pruebas](#pruebas)
- [Buenas prácticas y recomendaciones](#buenas-prácticas-y-recomendaciones)
- [Estructura del proyecto](#estructura-del-proyecto)
- [Contribuir](#contribuir)
- [Licencia y contacto](#licencia-y-contacto)

---

## 📝 Resumen
Proyecto Java construido con Maven que emplea JPA/Hibernate para persistir entidades en MariaDB. Incluye dependencias como Lombok y Hibernate Validator. El README se ha generado a partir del POM y la estructura base del repo; ajusta las configuraciones según las clases reales en `src/`.

## 🛠️ Tecnologías
- Java 25
- Maven
- JPA (Hibernate)
- MariaDB
- Lombok
- Hibernate Validator

Dependencias (extraídas del `pom.xml`):
- org.projectlombok:lombok:1.18.42
- org.hibernate:hibernate-core:7.2.0.CR1
- jakarta.persistence:jakarta.persistence-api:3.2.0
- org.mariadb.jdbc:mariadb-java-client:3.5.6
- org.hibernate.validator:hibernate-validator:8.0.3.Final

## ✅ Requisitos
- JDK 25 (o ajustar el POM según tu JDK disponible)
- Maven 3.x
- MariaDB accesible (local o en contenedor)
- (Recomendado) Plugin Lombok en tu IDE

## 🚀 Instalación y ejecución rápida

1. Compilar:
```bash
mvn clean package
```

2. Ejecutar (si hay un JAR ejecutable con Main):
```bash
java -jar target/ProyectoAC301_RemusSabou-1.0-SNAPSHOT.jar
```

Si no hay JAR ejecutable, abre el proyecto en tu IDE y ejecuta la clase que contenga `public static void main(String[] args)`.

## 🔌 Configuración de la base de datos

Ajusta según uses `persistence.xml`, `application.properties` o `hibernate.cfg.xml`. Nunca subas credenciales al repositorio.

### persistence.xml (ejemplo)
```xml
<persistence xmlns="https://jakarta.ee/xml/ns/persistence"
             version="3.0">
  <persistence-unit name="miUnidad" transaction-type="RESOURCE_LOCAL">
    <provider>org.hibernate.jpa.HibernatePersistenceProvider</provider>

    <!-- Añade aquí tus clases de entidad -->
    <class>es.iesjuanbosco.modelo.MiEntidad</class>

    <properties>
      <property name="jakarta.persistence.jdbc.url" value="jdbc:mariadb://localhost:3306/mi_basedatos"/>
      <property name="jakarta.persistence.jdbc.user" value="${DB_USER:mi_usuario}"/>
      <property name="jakarta.persistence.jdbc.password" value="${DB_PASS:mi_contraseña}"/>
      <property name="jakarta.persistence.jdbc.driver" value="org.mariadb.jdbc.Driver"/>
      <property name="hibernate.dialect" value="org.hibernate.dialect.MariaDBDialect"/>
      <property name="hibernate.hbm2ddl.auto" value="update"/>
      <property name="hibernate.show_sql" value="true"/>
    </properties>
  </persistence-unit>
</persistence>
```

### application.properties (ejemplo para proyectos Spring o similar)
```properties
spring.datasource.url=jdbc:mariadb://localhost:3306/mi_basedatos
spring.datasource.username=${DB_USER:mi_usuario}
spring.datasource.password=${DB_PASS:mi_contraseña}
spring.jpa.database-platform=org.hibernate.dialect.MariaDBDialect
spring.jpa.hibernate.ddl-auto=update
logging.level.org.hibernate.SQL=DEBUG
```

### Docker / docker-compose (opcional)
Archivo `docker-compose.yml` mínimo para MariaDB:
```yaml
version: "3.8"
services:
  mariadb:
    image: mariadb:11
    environment:
      - MARIADB_ROOT_PASSWORD=rootpassword
      - MARIADB_DATABASE=mi_basedatos
      - MARIADB_USER=mi_usuario
      - MARIADB_PASSWORD=mi_contraseña
    ports:
      - "3306:3306"
    volumes:
      - mariadb-data:/var/lib/mysql

volumes:
  mariadb-data:
```
Consejo: usa variables de entorno y no dejes contraseñas en texto plano.

## 🧪 Pruebas
- Ejecutar pruebas unitarias:
```bash
mvn test
```
- Para pruebas de integración con MariaDB puedes:
  - Usar Testcontainers (recomendado) para levantar MariaDB en los tests.
  - O levantar MariaDB con docker-compose y ejecutar pruebas contra ella.

Ejemplo simple (Testcontainers, en pseudocódigo):
```java
// @Testcontainers
public class IntegrationTest {
  @Container
  public static MariaDBContainer<?> maria = new MariaDBContainer<>("mariadb:11")
      .withDatabaseName("test")
      .withUsername("test")
      .withPassword("test");
  // ...
}
```

## 💡 Buenas prácticas y recomendaciones
- No subir credenciales al repositorio — usa variables de entorno o vault.
- Mantener perfiles (dev/test/prod) con propiedades separadas.
- Añadir pruebas de integración y unitarias.
- Documentar las clases públicas y exponer ejemplos de uso en el README.
- Añadir un fichero LICENSE (MIT / Apache-2.0, según prefieras).

## 📁 Estructura principal del repositorio
- .gitignore
- .idea/
- pom.xml
- src/
  - main/java/...
  - main/resources/...
  - test/...

Si quieres, puedo listar y documentar las clases dentro de `src/` y actualizar el README con ejemplos concretos.

## 🤝 Contribuir
1. Fork del repositorio
2. Crear rama: `feature/mi-cambio`
3. Commits claros y descriptivos
4. Pull Request con descripción y cómo probar el cambio

Si quieres, te preparo una plantilla de PR y una guía de estilo de commits.

## 📜 Licencia y contacto
- Añade un fichero LICENSE si vas a publicar el repositorio (p. ej. MIT o Apache-2.0).
- Autor: https://github.com/MrBrad8989
- Usa Issues para errores o peticiones de mejora.

---

¿Quieres que:
- Genere un `persistence.xml` final adaptado a tus entidades?
- Añada un ejemplo de test de integración con Testcontainers y un test real?
- Liste las clases dentro de `src/` y agregue ejemplos concretos en el README?

Dime cuál y lo preparo.
