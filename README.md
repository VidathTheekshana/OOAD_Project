# 🏋️‍♂️ Fitness Club — Spring Boot Application

## 📖 Project Overview

This is a **Spring Boot web application** for a fitness club.
It uses **Thymeleaf** templates for server-rendered pages and **Spring Data JPA** for persistence.
The app is configured to run with **MySQL** in production but includes a **development profile (H2 in-memory DB)** so you can easily run it locally without installing MySQL.

---

## ⚙️ Requirements

* ☕ **Java 11+** (Project built with Spring Boot 2.3.4.RELEASE)
* 🧰 **Git**
* 🐬 *(Optional)* **MySQL** or **MariaDB** server for production-like runs
* 🧱 **No global Maven install required** — includes the Maven Wrapper (`mvnw`)

---

## 🚀 Quick Start (Dev Profile — H2 In-Memory DB)

1. **Make Maven Wrapper executable** *(macOS/Linux only, one-time)*

   ```bash
   ./mvnw -v
   ```

2. **Run the app with the dev profile**

   ```bash
   ./mvnw -Dspring-boot.run.profiles=dev spring-boot:run
   ```

3. **Open your browser:**
   👉 [http://localhost:8088/](http://localhost:8088/)

> 💡 **Note:**
>
> * The `dev` profile uses **H2**, so it won’t try to connect to MySQL.
> * If you see `Cannot load driver class: org.h2.Driver`, ensure H2 dependency scope is set to `runtime`.

---

## 🗄️ Running with MySQL (Production Mode)

1. **Start a MySQL server and create a database:**

   ```bash
   mysql -u root -p
   CREATE DATABASE fitness_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
   ```

2. **Set database credentials** in `src/main/resources/application.yml` or use environment variables:

   ```yaml
   spring.datasource.url=jdbc:mysql://localhost:3306/fitness_db
   spring.datasource.username=your_user
   spring.datasource.password=your_password
   ```

3. **Run the app (default or custom profile):**

   ```bash
   ./mvnw spring-boot:run
   ```

---

## 🧱 Build and Run the Packaged JAR

**Package the app:**

```bash
./mvnw clean package -DskipTests
```

**Run the JAR:**

```bash
java -jar target/*.jar
```

---

## 🧪 Testing

**Run all tests:**

```bash
./mvnw test
```

> 🧠 Tests use an in-memory **H2 database**, so no MySQL setup is needed for CI or local runs.

---

## 🛠️ What’s Changed (Repo Notes)

* 🧩 Cleaned up Thymeleaf templates — removed demo credits & redundant “Blog” links.
* ⚡ Added H2 configuration for `test` and `dev` profiles.
* 🔧 Ensured H2 dependency is available at runtime for smooth dev runs.

---

## 🔒 Git & Sensitive Files

✅ **Commit these:**

* `mvnw`, `mvnw.cmd`, and `.mvn/wrapper/*` (for consistent builds)

🚫 **Do NOT commit secrets or credentials!**
If you have credentials in `application.yml`:

* Move them to **environment variables**, or
* Add `application.yml` to `.gitignore` and include an example file like `application.yml.example`.

---

## 🧭 Common Git Commands

Check repo status:

```bash
git status
```

Stage & commit changes:

```bash
git add .
git commit -m "Describe your change"
```

Push to your branch:

```bash
git push origin main
```

---

## 🗃️ Database Checks (Local)

Check MySQL client:

```bash
which mysql
```

List databases (will ask for password):

```bash
mysql -u root -p -e "SHOW DATABASES;"
```

---

## 🧩 Troubleshooting

⚠️ **Port Conflict:**
If `8088` is in use, change it via:

```yaml
server.port=9090
```

or run with:

```bash
-Dserver.port=9090
```

⚙️ **Hibernate Dialect Issues:**
Ensure:

```yaml
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL57Dialect
```

🧪 **Test DB Access Errors:**
Run tests with:

```bash
-Dspring.profiles.active=test
```

to force H2 test profile usage.

---

## 🤝 Contributing

1. Create a feature branch:

   ```bash
   git checkout -b feature/short-description
   ```

2. Make small, clear commits.

3. Open a Pull Request to **main** when ready.

---

## 📜 License

Check the repository root for license details.
If none exists, consider adding an open-source license such as **MIT** or **Apache 2.0**.

