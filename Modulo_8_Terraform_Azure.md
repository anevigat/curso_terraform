# 🧩 Módulo 8: Ciclo de Vida, Dependencias y Estrategias de Despliegue

## 🎯 Objetivo del módulo  
Comprender cómo gestionar el ciclo de vida de los recursos, declarar dependencias explícitas y usar estrategias para despliegues seguros y ordenados.

---

## 🔄 8.1 Ciclo de vida de los recursos

Terraform permite definir reglas específicas sobre cómo manejar los recursos en su ciclo de vida con el bloque `lifecycle`.

### Ejemplo:

```hcl
resource "azurerm_virtual_machine" "vm" {
  name                = "mi-vm"
  # ...
  lifecycle {
    prevent_destroy = true
    ignore_changes  = [tags]
  }
}
```

### Explicación:

- `prevent_destroy`: evita que el recurso sea destruido accidentalmente.
- `ignore_changes`: ignora ciertos cambios (por ejemplo, etiquetas).

---

## 🔗 8.2 Dependencias explícitas

Terraform maneja dependencias automáticamente, pero puedes forzarlas con `depends_on`.

### Ejemplo:

```hcl
resource "azurerm_public_ip" "ip" {
  # ...
}

resource "azurerm_network_interface" "nic" {
  # ...
  depends_on = [azurerm_public_ip.ip]
}
```

---

## 🚀 8.3 Estrategias de despliegue seguras

### Buenas prácticas:

- Usar `terraform plan` antes de cada `apply`.
- Proteger recursos críticos con `prevent_destroy`.
- Usar módulos para aislar funcionalidades.
- Validar los cambios con entornos previos (dev, test, prod).
- Usar `-target` solo si sabes lo que haces.

---

## 🧪 8.4 Ejercicio práctico

### 🎯 Objetivo
Implementar protección contra destrucción y dependencias explícitas.

### Tareas

1. Añade un recurso que tenga `prevent_destroy`.
2. Crea una dependencia explícita entre dos recursos.
3. Ejecuta `terraform plan` y prueba qué ocurre si cambias un parámetro ignorado por `ignore_changes`.
4. Elimina el recurso y verifica que `prevent_destroy` actúa como protección.

---

## 📚 Recursos útiles

- [Terraform Lifecycle](https://developer.hashicorp.com/terraform/language/meta-arguments/lifecycle)
- [Terraform Dependencies](https://developer.hashicorp.com/terraform/language/meta-arguments/depends_on)

---

## ✅ Revisión del módulo

| ¿Qué lograste? |
|----------------|
| ✅ Aplicar `lifecycle` en recursos |
| ✅ Establecer dependencias explícitas |
| ✅ Usar estrategias seguras de despliegue |
