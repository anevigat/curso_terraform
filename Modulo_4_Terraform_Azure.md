# 🧩 Módulo 4: Creación de Recursos en Azure con Terraform

## 🎯 Objetivo del módulo  
Aprender a crear recursos básicos en Azure con Terraform, incluyendo grupos de recursos, redes virtuales (VNet) y máquinas virtuales (VM).

---

## 🧱 4.1 Estructura básica para recursos

Terraform permite declarar recursos como bloques reutilizables. Cada tipo de recurso tiene su propia sintaxis.

Ejemplo de sintaxis general:

```hcl
resource "tipo_de_recurso" "nombre_local" {
  propiedad1 = valor
  propiedad2 = valor
}
```

---

## 📦 4.2 Crear una red virtual (VNet)

### 📄 main.tf (fragmento)

```hcl
resource "azurerm_virtual_network" "vnet" {
  name                = "vnet-ejemplo"
  address_space       = ["10.0.0.0/16"]
  location            = var.location
  resource_group_name = azurerm_resource_group.rg.name
}
```

---

## 🌐 4.3 Crear una subred

```hcl
resource "azurerm_subnet" "subnet" {
  name                 = "subnet-ejemplo"
  resource_group_name  = azurerm_resource_group.rg.name
  virtual_network_name = azurerm_virtual_network.vnet.name
  address_prefixes     = ["10.0.1.0/24"]
}
```

---

## 🖥️ 4.4 Crear una máquina virtual (VM)

### Requiere también:

- IP pública
- Interfaz de red (NIC)
- Imagen y tamaño

### Fragmentos de configuración:

```hcl
resource "azurerm_public_ip" "public_ip" {
  name                = "public-ip"
  location            = var.location
  resource_group_name = azurerm_resource_group.rg.name
  allocation_method   = "Dynamic"
}

resource "azurerm_network_interface" "nic" {
  name                = "nic-ejemplo"
  location            = var.location
  resource_group_name = azurerm_resource_group.rg.name

  ip_configuration {
    name                          = "ipconfig1"
    subnet_id                     = azurerm_subnet.subnet.id
    private_ip_address_allocation = "Dynamic"
    public_ip_address_id          = azurerm_public_ip.public_ip.id
  }
}

resource "azurerm_linux_virtual_machine" "vm" {
  name                = "vm-ejemplo"
  resource_group_name = azurerm_resource_group.rg.name
  location            = var.location
  size                = "Standard_B1s"
  admin_username      = "azureuser"
  network_interface_ids = [
    azurerm_network_interface.nic.id,
  ]

  admin_password = "Password1234!"
  disable_password_authentication = false

  os_disk {
    caching              = "ReadWrite"
    storage_account_type = "Standard_LRS"
  }

  source_image_reference {
    publisher = "Canonical"
    offer     = "UbuntuServer"
    sku       = "20_04-lts"
    version   = "latest"
  }
}
```

---

## ⚠️ 4.5 Seguridad y buenas prácticas

- **No hardcodear contraseñas**: usa variables o Azure Key Vault.
- **Evita exponer puertos innecesarios al público**.
- Usa **`terraform plan`** para revisar antes de aplicar.

---

## 🧪 4.6 Ejercicio práctico

### 🎯 Objetivo
Crear una red virtual, subred, IP pública, NIC y VM Linux.

### Tareas

1. Agrega la definición de la VNet y la subred a tu proyecto.
2. Agrega la IP pública y la NIC.
3. Define la máquina virtual.
4. Ejecuta `terraform apply` y conéctate a la VM por SSH (si configuraste correctamente).
5. Ejecuta `terraform destroy` al finalizar.

---

## 📚 Recursos útiles

- [azurerm_virtual_network](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/virtual_network)
- [azurerm_linux_virtual_machine](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/linux_virtual_machine)
- [Mejores prácticas de seguridad](https://learn.microsoft.com/en-us/azure/security/fundamentals/)

---

## ✅ Revisión del módulo

| ¿Qué lograste? |
|----------------|
| ✅ Crear una red virtual |
| ✅ Crear una subred |
| ✅ Asignar una IP pública y una NIC |
| ✅ Lanzar una VM con Terraform |
