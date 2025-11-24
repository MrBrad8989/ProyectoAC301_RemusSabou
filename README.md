# 🚀 ProyectoAC301_RemusSabou

> Aplicación Java (Maven) para persistencia con JPA/Hibernate y MariaDB  
> ArtifactId: `ProyectoAC301_RemusSabou` — GroupId: `es.iesjuanbosco` — Versión: `1.0-SNAPSHOT`

---

✨ Resumen
- Proyecto Java construido con Maven que utiliza JPA/Hibernate para persistir datos en MariaDB.
- Dependencias principales: Lombok, Hibernate, Jakarta Persistence API, MariaDB JDBC driver y Hibernate Validator.
- Generé este README a partir del `pom.xml` y la estructura del repositorio; ajusta las secciones de ejecución según el contenido real de `src/`.

📦 Tecnologías
- Java (configurado en el POM como source/target = 25)
- Maven
- Hibernate (JPA)
- MariaDB
- Lombok
- Hibernate Validator

🧾 Dependencias (extraídas de pom.xml)
- org.projectlombok:lombok:1.18.42
- org.hibernate:hibernate-core:7.2.0.CR1
- jakarta.persistence:jakarta.persistence-api:3.2.0
- org.mariadb.jdbc:mariadb-java-client:3.5.6
- org.hibernate.validator:hibernate-validator:8.0.3.Final

---

📁 Estructura principal del repositorio
- .gitignore
- .idea/ (configuración del IDE)
- pom.xml
- src/ (código fuente Java — revisar para clases, Main y ficheros de configuración)
  
Si quieres, puedo listar el contenido de `src/` y añadir ejemplos basados en las clases que haya allí.

---

⚙️ Requisitos previos
- JDK 25 (o ajustar según JDK disponible)
- Maven 3.x
- Instalar plugin Lombok en tu IDE (recomendado)
- Base de datos MariaDB accesible

---

⚡ Quick start — compilar y ejecutar

1. Compilar:
```bash
mvn clean package
```

2. Ejecutar (si el proyecto tiene un jar ejecutable con Main):
```bash
java -jar target/ProyectoAC301_RemusSabou-1.0-SNAPSHOT.jar
```

Si no existe un JAR ejecutable, abre el proyecto en tu IDE y ejecuta la clase que contenga el método `public static void main`.

---

🔌 Configuración de la base de datos (ejemplo)
Ajusta según uses `persistence.xml`, `application.properties` o `hibernate.cfg.xml`.

Ejemplo de `persistence.xml` (resumen):
```xml
<persistence>
  <persistence-unit name="miUnidad">
    <provider>org.hibernate.jpa.HibernatePersistenceProvider</provider>
    <class>tu.paquete.Entidad</class>
    <properties>
      <property name="jakarta.persistence.jdbc.url" value="jdbc:mariadb://localhost:3306/mi_basedatos"/>
      <property name="jakarta.persistence.jdbc.user" value="mi_usuario"/>
      <property name="jakarta.persistence.jdbc.password" value="mi_contraseña"/>
      <property name="hibernate.dialect" value="org.hibernate.dialect.MariaDBDialect"/>
      <property name="hibernate.hbm2ddl.auto" value="update"/>
      <property name="hibernate.show_sql" value="true"/>
    </properties>
  </persistence-unit>
</persistence>
```

⚠️ No subas credenciales al repositorio. Usa variables de entorno o ficheros fuera del control de versiones.

---

✅ Buenas prácticas y recomendaciones
- Añadir pruebas unitarias e integración (usar DB en memoria o Docker para MariaDB).
- Mantener perfiles para dev/test/prod con propiedades de BD separadas.
- Documentar clases públicas y añadir ejemplos de uso en README si hay APIs públicas.
- Añadir un fichero LICENSE si vas a publicar el repositorio (p. ej. MIT o Apache-2.0).

---

🤝 Cómo contribuir
1. Fork → crea una rama: `feature/mi-cambio`
2. Commit claros y descriptivos
3. Pull Request con descripción del cambio y cómo probarlo

---

📬 Contacto / Soporte
- Usa los Issues del repositorio para errores o peticiones de mejora.
- Perfil del autor: https://github.com/MrBrad8989

---

¿Quieres que haga alguna de estas opciones ahora?
- 🧩 Generar un ejemplo completo de `persistence.xml` o `application.properties` para MariaDB.
- 🧪 Añadir un ejemplo de test de integración con MariaDB (Docker).
- 📂 Listar y documentar las clases dentro de `src/` y actualizar el README con ejemplos concretos.

Dime cuál prefieres y lo preparo. ¡Vamos a dejarlo bonito! ✨
