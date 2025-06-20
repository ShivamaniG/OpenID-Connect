Sure! Here's a complete `README.md` tailored for your **Nextcloud + Keycloak integration using Docker and OIDC**, including Docker setup, project overview, setup instructions, and how to run the system.

---

### ✅ `README.md`

````markdown
# Nextcloud + Keycloak OIDC Integration

This project demonstrates how to integrate **Nextcloud** with **Keycloak** using **OpenID Connect (OIDC)** for secure, centralized Single Sign-On (SSO) authentication. It uses Docker to containerize and run both services.

---

## 🚀 Project Overview

- **Nextcloud**: A self-hosted file sharing and collaboration platform.
- **Keycloak**: An open-source Identity and Access Management (IAM) solution.
- **OIDC**: OpenID Connect is an identity layer on top of OAuth 2.0, enabling Single Sign-On across services.

This setup allows:
- Secure login to Nextcloud via Keycloak
- Automatic user provisioning in Nextcloud on first login
- Proper session and logout handling
- Centralized user management in Keycloak

---

## 🧰 Tech Stack

- Docker & Docker Compose
- Nextcloud (running on port `8082`)
- Keycloak (running on port `8080`)
- Social Login app in Nextcloud
- OpenID Connect protocol

---

## ⚙️ Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/<your-username>/nextcloud-keycloak-oidc-integration.git
cd nextcloud-keycloak-oidc-integration
````

### 2. Docker Setup

This project contains a `docker-compose.yml` file that defines:

* `keycloak` (with admin credentials)
* `nextcloud` (with persistent volume)
* A shared Docker network

### 3. Start the Containers

```bash
docker-compose up -d
```

* Keycloak will be available at: [http://localhost:8080](http://localhost:8080)
* Nextcloud will be available at: [http://localhost:8082](http://localhost:8082)

---

## 🔐 Keycloak Configuration

1. Open Keycloak: [http://localhost:8080](http://localhost:8080)
2. Login with:

   * **Username**: `admin`
   * **Password**: `admin123`
3. Create a new **realm** called `nextcloud`
4. Add a new **client**:

   * Client ID: `nextcloud`
   * Access Type: `confidential`
   * Valid Redirect URI: `http://localhost:8082/*`
   * Post Logout Redirect URI: `http://localhost:8082`
   * Web Origins: `*`
5. Create test users (e.g. `user1`, `user2`) and set passwords.

---

## 🌐 Nextcloud Setup

1. Open Nextcloud: [http://localhost:8082](http://localhost:8082)
2. Complete initial setup (admin account, database config if needed)
3. Install the **Social Login** app from the Nextcloud app store
4. Configure a **Custom OpenID Connect Provider**:

   * Authorize URL: `http://localhost:8080/realms/nextcloud/protocol/openid-connect/auth?prompt=login`
   * Token URL: `http://keycloak:8080/realms/nextcloud/protocol/openid-connect/token`
   * User Info URL: `http://keycloak:8080/realms/nextcloud/protocol/openid-connect/userinfo`
   * Logout URL: `http://localhost:8080/realms/nextcloud/protocol/openid-connect/logout?redirect_uri=http://localhost:8082`

✅ On first login with a Keycloak user, Nextcloud will automatically create the user account.

---

## ✅ How to Run

1. Ensure Docker is running
2. In your terminal:

```bash
docker-compose up -d
```

3. Visit the services:

   * Keycloak: [http://localhost:8080](http://localhost:8080)
   * Nextcloud: [http://localhost:8082](http://localhost:8082)

---

## 🧼 Stopping and Cleaning Up

To stop the containers:

```bash
docker-compose down
```

To stop and remove volumes (clean reset):

```bash
docker-compose down -v
```

---

## 📌 Notes

* Make sure to set passwords for all users in Keycloak and verify their emails.
* For a production setup, replace `localhost` with actual domains and use HTTPS.
* You can monitor user sessions and login logs directly in the Keycloak admin console.

---

## 👨‍💻 Author

**Shivamani G**
IIITDM Kurnool — Final Year CSE
GitHub: [github.com/<your-username>](https://github.com/<your-username>)

---

```

Let me know if you'd also like a `.gitignore` file and a sample `docker-compose.yml` in the repo, or help publishing it to GitHub Pages for docs!
```
