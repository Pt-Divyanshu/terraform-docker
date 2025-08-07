# 🚀 Terraform Docker NGINX Deployment

This project provisions a **local Docker container** running **NGINX** using **Terraform**. It automates container creation through infrastructure-as-code.

---

## ✅ Objective

> Provision a local Docker container using Terraform.

---

## 🧰 Tools & Technologies Used

- **Terraform** (~> 1.0)
- **Docker** (Desktop or Engine)
- **NGINX** (Official Docker Image)

---

## 📁 Project Structure

```
.
├── main.tf               # Terraform configuration file
├── README.md             # Project documentation
└── .terraform.lock.hcl   # Auto-generated lock file (after init)
```

---

## ⚙️ Setup Instructions

### 📌 Prerequisites
- Docker installed and running  
- Terraform installed (`terraform -v` to check)

### 🔧 Steps

1. **Clone the repository** (if applicable)
   ```bash
   git clone <your-repo-url>
   cd <project-directory>
   ```

2. **Initialize Terraform**
   ```bash
   terraform init
   ```

3. **Review the execution plan**
   ```bash
   terraform plan
   ```

4. **Apply configuration**
   ```bash
   terraform apply
   ```

5. **Access NGINX**
   - Open browser:  
     [http://localhost:8081](http://localhost:8081)

   - You should see the **"Welcome to NGINX!"** page.

---

## 📄 main.tf Code Overview

```hcl
terraform {
  required_providers {
    docker = {
      source  = "kreuzwerker/docker"
      version = "~> 2.20.0"
    }
  }
}

provider "docker" {
  host = "npipe:////./pipe/docker_engine"
}

resource "docker_image" "nginx" {
  name = "nginx:latest"
}

resource "docker_container" "nginx_container" {
  name  = "nginx_terraform"
  image = docker_image.nginx.name

  ports {
    internal = 80
    external = 8081
  }
}
```

---

## 🧪 Output

After applying Terraform, you will see logs indicating:

- Docker image pull for nginx
- Docker container creation
- Port 8081 bound to container's port 80

---

## 🧹 Cleanup

To destroy the container and image:

```bash
terraform destroy
```

---

## 📌 Deliverables

- ✅ `main.tf` with working configuration
- ✅ Terraform logs (init, plan, apply)
- ✅ Working NGINX on `localhost:8081`

---

## 🙏 Acknowledgements

Thanks to:
- [Terraform by HashiCorp](https://www.terraform.io/)
- [Docker](https://www.docker.com/)
- [Kreuzwerker Docker Provider](https://registry.terraform.io/providers/kreuzwerker/docker/latest)

---

## 👤 Author

**Divyanshu Sharma**
