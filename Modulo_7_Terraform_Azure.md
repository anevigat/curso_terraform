# 🧩 Módulo 7: Estado de Terraform y Gestión Remota

## 🎯 Objetivo del módulo  
Entender cómo funciona el archivo de estado (`terraform.tfstate`), su importancia, riesgos y cómo almacenarlo de forma remota para trabajar en equipo de manera segura.

---

## 📁 7.1 ¿Qué es el estado en Terraform?

Terraform guarda un archivo `terraform.tfstate` donde mantiene un registro del estado actual de los recursos creados.

### ¿Por qué es importante?

- Permite hacer el seguimiento de los cambios.
- Necesario para operaciones como `plan`, `apply` y `destroy`.
- **¡No debes editarlo manualmente!**

---

## ⚠️ 7.2 Riesgos de mal manejo

- **Pérdida del archivo** = pérdida de control sobre la infraestructura.
- Si varias personas lo modifican a la vez, puede causar errores.
- Almacenar en control de versiones (como Git) puede exponer información sensible.

---

## ☁️ 7.3 Almacenamiento remoto del estado

Terraform permite usar un **backend remoto** para almacenar el estado en la nube.

Ejemplo: Usar un blob storage de Azure.

---

## 🔧 7.4 Configurar backend remoto en Azure

### Requisitos:
- Una cuenta de almacenamiento
- Un contenedor
- Una clave (nombre del archivo tfstate)

### 📄 backend.tf

```hcl
terraform {
  backend "azurerm" {
    resource_group_name  = "mi-grupo-rg"
    storage_account_name = "mistorageaccount"
    container_name       = "terraform-state"
    key                  = "infraestructura.tfstate"
  }
}
```

### Inicialización del backend remoto

```bash
terraform init
```

> Esto migrará el estado local al remoto.

---

## 🧪 7.5 Ejercicio práctico

### 🎯 Objetivo
Configurar el almacenamiento remoto del estado usando Azure Blob Storage.

### Tareas

1. Crea manualmente desde el portal de Azure:
   - Grupo de recursos
   - Cuenta de almacenamiento
   - Contenedor llamado `terraform-state`

2. Agrega el bloque `backend` en tu proyecto.
3. Ejecuta `terraform init` para migrar el estado.
4. Verifica en el contenedor que se ha creado el archivo `.tfstate`.

---

## 📚 Recursos útiles

- [Terraform Backends](https://developer.hashicorp.com/terraform/language/settings/backends)
- [Backend azurerm](https://developer.hashicorp.com/terraform/language/settings/backends/azurerm)

---

## ✅ Revisión del módulo

| ¿Qué lograste? |
|----------------|
| ✅ Comprender el propósito del archivo `terraform.tfstate` |
| ✅ Conocer los riesgos de mal manejo del estado |
| ✅ Configurar un backend remoto en Azure |
