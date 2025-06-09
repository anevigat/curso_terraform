# 🧩 Módulo 6: Variables, Outputs y Archivos tfvars

## 🎯 Objetivo del módulo  
Aprender a gestionar variables de entrada, outputs y archivos `.tfvars` para hacer que nuestras configuraciones de Terraform sean más dinámicas, reutilizables y fáciles de mantener.

---

## 🧮 6.1 Uso de variables

Las variables permiten parametrizar nuestra infraestructura.

### 📄 variables.tf

```hcl
variable "location" {
  description = "Ubicación de los recursos en Azure"
  type        = string
  default     = "West Europe"
}

variable "vnet_name" {
  description = "Nombre de la red virtual"
  type        = string
}
```

### 📄 main.tf

```hcl
resource "azurerm_virtual_network" "vnet" {
  name                = var.vnet_name
  location            = var.location
  address_space       = ["10.0.0.0/16"]
  resource_group_name = azurerm_resource_group.rg.name
}
```

---

## 🧾 6.2 Valores por defecto

Puedes asignar valores por defecto en el archivo `variables.tf` para evitar definirlos cada vez.

```hcl
variable "admin_username" {
  type    = string
  default = "azureuser"
}
```

---

## 📤 6.3 Outputs

Los outputs permiten exportar valores útiles tras aplicar el plan.

### 📄 outputs.tf

```hcl
output "vnet_name" {
  value = azurerm_virtual_network.vnet.name
}

output "vm_ip" {
  value = azurerm_linux_virtual_machine.vm.public_ip_address
}
```

Se muestran al final del `terraform apply`.

---

## 📂 6.4 Archivos .tfvars

Puedes definir valores para variables en archivos `.tfvars`.

### 📄 terraform.tfvars

```hcl
vnet_name = "mi-vnet"
location  = "West Europe"
```

Y usarlo con:

```bash
terraform apply -var-file="terraform.tfvars"
```

---

## 🧪 6.5 Ejercicio práctico

### 🎯 Objetivo
Usar variables, outputs y archivos `.tfvars` en un proyecto de Terraform.

### Tareas

1. Crea los archivos `variables.tf` y `outputs.tf`.
2. Usa las variables en tus recursos (como VM, VNet...).
3. Crea un archivo `terraform.tfvars` y pruébalo.
4. Ejecuta `terraform apply` y revisa los outputs.

---

## 📚 Recursos útiles

- [Terraform Variables](https://developer.hashicorp.com/terraform/language/values/variables)
- [Terraform Outputs](https://developer.hashicorp.com/terraform/language/values/outputs)
- [Usar .tfvars](https://developer.hashicorp.com/terraform/language/values/variables#variable-definitions-tfvars-files)

---

## ✅ Revisión del módulo

| ¿Qué lograste? |
|----------------|
| ✅ Definir y usar variables |
| ✅ Usar valores por defecto |
| ✅ Crear y usar outputs |
| ✅ Gestionar variables con archivos `.tfvars` |
