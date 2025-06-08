# 🧩 Módulo 5: Provisión de Recursos con Módulos en Terraform

## 🎯 Objetivo del módulo  
Aprender a reutilizar código creando y utilizando módulos en Terraform para gestionar recursos de manera más eficiente y escalable.

---

## 🧠 5.1 ¿Qué es un módulo?

Un **módulo** en Terraform es un conjunto de archivos `.tf` reutilizables. Cualquier carpeta con código Terraform puede ser un módulo.

### Ventajas:
- Reutilización
- Organización
- Escalabilidad

---

## 📁 5.2 Estructura básica de un módulo

```
modules/
└── red_virtual/
    ├── main.tf
    ├── variables.tf
    └── outputs.tf
```

### 📄 main.tf (dentro del módulo)

```hcl
resource "azurerm_virtual_network" "vnet" {
  name                = var.vnet_name
  address_space       = var.address_space
  location            = var.location
  resource_group_name = var.resource_group_name
}
```

### 📄 variables.tf

```hcl
variable "vnet_name" {}
variable "address_space" {
  type = list(string)
}
variable "location" {}
variable "resource_group_name" {}
```

### 📄 outputs.tf

```hcl
output "vnet_id" {
  value = azurerm_virtual_network.vnet.id
}
```

---

## 🧰 5.3 Usar un módulo desde el proyecto principal

En tu directorio principal:

```hcl
module "vnet_principal" {
  source              = "./modules/red_virtual"
  vnet_name           = "mi-vnet"
  address_space       = ["10.1.0.0/16"]
  location            = var.location
  resource_group_name = azurerm_resource_group.rg.name
}
```

---

## 🔁 5.4 Reutilización con distintos parámetros

Puedes instanciar el mismo módulo con otros parámetros para crear múltiples VNets:

```hcl
module "vnet_secundaria" {
  source              = "./modules/red_virtual"
  vnet_name           = "otra-vnet"
  address_space       = ["10.2.0.0/16"]
  location            = var.location
  resource_group_name = azurerm_resource_group.rg.name
}
```

---

## 🧪 5.5 Ejercicio práctico

### 🎯 Objetivo
Crear un módulo para redes virtuales y utilizarlo en el proyecto principal.

### Tareas

1. Crea el directorio `modules/red_virtual` con los archivos necesarios.
2. Implementa `main.tf`, `variables.tf`, y `outputs.tf` dentro del módulo.
3. Usa el módulo desde el `main.tf` del proyecto principal.
4. Ejecuta `terraform apply` y valida que se crean las dos redes virtuales.
5. Revisa los `outputs`.

---

## 📚 Recursos útiles

- [Documentación oficial sobre módulos](https://developer.hashicorp.com/terraform/language/modules)
- [Módulos públicos de Terraform Registry](https://registry.terraform.io/)

---

## ✅ Revisión del módulo

| ¿Qué lograste? |
|----------------|
| ✅ Crear y estructurar un módulo |
| ✅ Reutilizar código con diferentes parámetros |
| ✅ Usar múltiples instancias de un módulo |
