# 🧱 Curso: Terraform en Azure desde Cero

## 🎯 Objetivo del curso

Aprender a usar Terraform para definir, desplegar y gestionar infraestructura en Microsoft Azure mediante código, incluso sin experiencia previa.

---

## 🧩 Módulo 1: Introducción a Terraform y a la Infraestructura como Código

### Contenidos

* ¿Qué es la infraestructura como código (IaC)?
* Ventajas de usar Terraform
* Casos de uso típicos en Azure
* Cómo funciona Terraform internamente (ciclo `init`, `plan`, `apply`)
* Breve introducción a Azure y sus servicios principales

### Ejercicio

* Escribir una definición básica de infraestructura como código
* Crear una cuenta gratuita de Azure

---

## ⚙️ Módulo 2: Instalación y configuración del entorno

### Contenidos

* Instalación de Terraform (Windows, Linux, macOS)
* Instalación de Azure CLI
* Autenticación con Azure: `az login`
* Estructura básica de un proyecto de Terraform

### Ejercicio

* Instalar Terraform y Azure CLI
* Iniciar sesión en Azure desde la terminal

---

## 📁 Módulo 3: Primeros pasos con Terraform

### Contenidos

* Sintaxis de HashiCorp Configuration Language (HCL)
* Primer archivo `main.tf`
* Proveedor de Azure (`azurerm`)
* Definir una `resource group`

### Ejemplo práctico

```hcl
provider "azurerm" {
  features {}
}

resource "azurerm_resource_group" "ejemplo" {
  name     = "rg-ejemplo"
  location = "East US"
}
```

### Ejercicio

* Crear una resource group personalizada en Azure con Terraform

---

## 🧩 Módulo 4: Variables, outputs y archivos separados

### Contenidos

* Uso de `variables.tf` y `terraform.tfvars`
* Uso de `output.tf`
* Separación de archivos para mejor organización

### Ejercicio

* Crear variables para el nombre y la región del `resource group`
* Mostrar el nombre del `resource group` como output

---

## 🌐 Módulo 5: Despliegue de infraestructura básica en Azure

### Contenidos

* Crear una red virtual (VNet)
* Crear subredes
* Desplegar una máquina virtual de Linux
* Asociar un IP público

### Ejemplo práctico

* Crear VNet + Subnet + VM básica usando `azurerm_virtual_network`, `azurerm_subnet`, `azurerm_linux_virtual_machine`

### Ejercicio

* Crear una infraestructura mínima con VNet, una subnet y una VM Linux

---

## 📦 Módulo 6: Módulos reutilizables en Terraform

### Contenidos

* ¿Qué son los módulos?
* Crear y usar un módulo propio
* Usar módulos públicos de Terraform Registry

### Ejercicio

* Modularizar la creación de VMs
* Reutilizar el módulo para desplegar múltiples VMs

---

## 🛠️ Módulo 7: Estado remoto y gestión de múltiples entornos

### Contenidos

* ¿Qué es el estado en Terraform?
* Backend en Azure Storage
* Separación de entornos (dev/staging/prod)
* Workspaces

### Ejercicio

* Configurar backend remoto en Azure Blob Storage
* Crear y aplicar configuraciones en dos workspaces diferentes

---

## 🔐 Módulo 8: Seguridad y buenas prácticas

### Contenidos

* Protección de secretos (Azure Key Vault)
* Variables sensibles
* Formato y validación (`fmt`, `validate`)
* Uso de `terraform-docs`

### Ejercicio

* Usar variables sensibles
* Validar y documentar un módulo

---

## 🚀 Módulo 9: Automatización con CI/CD

### Contenidos

* Introducción a pipelines CI/CD
* Automatización con GitHub Actions
* Automatización con Azure DevOps Pipelines
* Ejemplo de despliegue automático con revisión de código

### Ejercicio

* Crear un pipeline básico para ejecutar `terraform plan` y `apply` en Azure DevOps o GitHub

---

## 🧪 Proyecto final: Infraestructura completa en Azure

### Requisitos

* Resource group
* VNet con subred pública y privada
* 2 VMs Linux (1 pública, 1 privada)
* Load Balancer
* Azure Storage Account
* Backend remoto
* Separación por módulos

### Entregables

* Código modular y reutilizable
* Archivo `README.md` explicativo
* Automatización CI/CD opcional

---

## 📚 Recursos adicionales

* [Terraform Registry (Azure)](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs)
* [Documentación oficial de Terraform](https://developer.hashicorp.com/terraform/docs)
* [Documentación de Azure](https://learn.microsoft.com/en-us/azure/?product=featured)

---
