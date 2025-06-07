# 🧩 Módulo 3: Variables, Salidas y Buenas Prácticas en Terraform

## 🎯 Objetivo del módulo  
Aprender a parametrizar configuraciones con variables, utilizar salidas para exportar información útil y aplicar buenas prácticas en la organización de tu código Terraform.

---

## 📦 3.1 Uso de variables en Terraform

Las **variables** te permiten hacer tu código más flexible y reutilizable. Se definen en un archivo `variables.tf`.

### 📄 variables.tf

```hcl
variable "resource_group_name" {
  description = "Nombre del grupo de recursos"
  type        = string
  default     = "tf-ejemplo-rg"
}

variable "location" {
  description = "Ubicación del recurso"
  type        = string
  default     = "East US"
}
```

### 📄 main.tf

```hcl
provider "azurerm" {
  features {}
}

resource "azurerm_resource_group" "rg" {
  name     = var.resource_group_name
  location = var.location
}
```

---

## 📤 3.2 Uso de outputs (salidas)

Puedes **exportar información útil** como el nombre del grupo de recursos, direcciones IP, nombres, etc.

### 📄 outputs.tf

```hcl
output "resource_group_name" {
  value = azurerm_resource_group.rg.name
}
```

Después de `terraform apply`, verás:

```
Outputs:

resource_group_name = "tf-ejemplo-rg"
```

---

## 🧠 3.3 Buenas prácticas en organización del código

- 🔹 Separa tus archivos: `main.tf`, `variables.tf`, `outputs.tf`
- 🔹 Usa nombres descriptivos para tus recursos
- 🔹 Usa módulos para reutilizar código
- 🔹 Controla el código con Git
- 🔹 Usa el comando `terraform fmt` para dar formato al código
- 🔹 Valida antes de aplicar:

```bash
terraform validate
```

---

## 🧪 3.4 Ejemplo completo

### 📁 Estructura

```
terraform-azure/
├── main.tf
├── variables.tf
└── outputs.tf
```

### Contenido de los archivos

#### main.tf

```hcl
provider "azurerm" {
  features {}
}

resource "azurerm_resource_group" "rg" {
  name     = var.resource_group_name
  location = var.location
}
```

#### variables.tf

```hcl
variable "resource_group_name" {
  default = "mi-grupo-de-ejemplo"
}

variable "location" {
  default = "West Europe"
}
```

#### outputs.tf

```hcl
output "rg_name" {
  value = azurerm_resource_group.rg.name
}
```

---

## 📝 Ejercicio práctico

1. Crea un nuevo directorio llamado `terraform-variables`.
2. Divide el código en `main.tf`, `variables.tf`, y `outputs.tf`.
3. Ejecuta `terraform init`, `plan` y `apply`.
4. Verifica el output y asegúrate de que el grupo de recursos tiene el nombre y ubicación definidos.
5. Ejecuta `terraform destroy` si ya no lo necesitas.

---

## 📚 Recursos útiles

- [Guía sobre variables en Terraform](https://developer.hashicorp.com/terraform/language/values/variables)
- [Guía sobre outputs en Terraform](https://developer.hashicorp.com/terraform/language/values/outputs)
- [Terraform best practices](https://developer.hashicorp.com/terraform/tutorials/configuration-language/format)

---

## ✅ Revisión del módulo

| ¿Qué lograste? |
|----------------|
| ✅ Parametrizar tu infraestructura con variables |
| ✅ Exportar datos útiles con outputs |
| ✅ Organizar tu código profesionalmente |
