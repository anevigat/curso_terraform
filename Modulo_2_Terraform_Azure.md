# 🧩 Módulo 2: Instalación y Configuración del Entorno de Trabajo

## 🎯 Objetivo del módulo  
Instalar y configurar las herramientas necesarias para trabajar con Terraform y Azure en tu equipo local.

---

## 🖥️ 2.1 Requisitos previos

Antes de comenzar, necesitas:

- Una cuenta de Azure (puedes usar la gratuita)
- Acceso a una terminal o consola (PowerShell, Terminal, o WSL en Windows; Terminal en macOS/Linux)
- Conexión a Internet

---

## 🔧 2.2 Instalación de Terraform

### ✅ Paso 1: Descargar Terraform

Ve al sitio oficial:  
👉 [https://www.terraform.io/downloads](https://www.terraform.io/downloads)

Selecciona tu sistema operativo y descarga el binario.

### ✅ Paso 2: Agregar Terraform al PATH

- En **Windows**: descomprime el ZIP y agrega la carpeta al PATH desde “Variables de entorno”.
- En **macOS/Linux**:
```bash
sudo mv terraform /usr/local/bin/
```

### ✅ Paso 3: Verificar instalación

```bash
terraform -v
```

Deberías ver algo como:

```
Terraform v1.8.2
```

---

## ☁️ 2.3 Instalación y configuración de Azure CLI

Terraform se comunica con Azure a través de la CLI.

### ✅ Instalar Azure CLI

Guía oficial según sistema operativo:  
👉 [https://learn.microsoft.com/es-es/cli/azure/install-azure-cli](https://learn.microsoft.com/es-es/cli/azure/install-azure-cli)

### ✅ Iniciar sesión en Azure

```bash
az login
```

Esto abrirá el navegador para autenticarte. Una vez logueado, verás tus suscripciones activas en la consola.

---

## 🧪 2.4 Crear un proyecto base en Terraform

### Estructura del proyecto:

```
terraform-azure/
├── main.tf
└── variables.tf (opcional)
```

### 📄 main.tf básico

```hcl
provider "azurerm" {
  features {}
}

resource "azurerm_resource_group" "rg" {
  name     = "tf-ejemplo-rg"
  location = "East US"
}
```

> Este archivo define un proveedor (Azure) y un grupo de recursos.

---

## ⚙️ 2.5 Inicializar Terraform y probar

### ✅ Inicializar el proyecto

```bash
terraform init
```

Esto descarga el proveedor `azurerm`.

### ✅ Ver el plan

```bash
terraform plan
```

Te mostrará lo que va a crear.

### ✅ Aplicar los cambios

```bash
terraform apply
```

Confirma con `yes`. Terraform creará el grupo de recursos en Azure.

---

## 🧼 2.6 Eliminar los recursos

Si solo fue una prueba, puedes destruir lo creado:

```bash
terraform destroy
```

---

## 📝 Ejercicio práctico

### 🎯 Objetivo
Dejar listo el entorno y crear un grupo de recursos desde Terraform.

### Tareas

1. Instalar Terraform y Azure CLI.
2. Crear un directorio llamado `terraform-azure`.
3. Crear el archivo `main.tf` con el contenido del ejemplo.
4. Ejecutar `terraform init`, `terraform plan` y `terraform apply`.
5. Validar que se ha creado el grupo de recursos desde el Portal de Azure.
6. Ejecutar `terraform destroy` si no lo necesitas.

---

## 🧠 Consejos

- Usa siempre nombres de recursos únicos o usa variables.
- No modifiques el archivo `terraform.tfstate` manualmente.
- Controla el código con Git desde el principio.

---

## 📚 Recursos útiles

- [Instalación de Terraform](https://developer.hashicorp.com/terraform/downloads)
- [Instalación de Azure CLI](https://learn.microsoft.com/es-es/cli/azure/install-azure-cli)
- [Documentación del proveedor azurerm](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs)

---

## ✅ Revisión del módulo

| ¿Qué lograste? |
|----------------|
| ✅ Instalar Terraform |
| ✅ Configurar Azure CLI |
| ✅ Crear tu primer recurso |
| ✅ Ejecutar `init`, `plan`, `apply` y `destroy` |
