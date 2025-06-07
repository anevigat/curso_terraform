# 🧩 Módulo 1: Introducción a Terraform y a la Infraestructura como Código

## 🎯 Objetivo del módulo  
Comprender qué es la infraestructura como código (IaC), por qué Terraform es una herramienta clave en este enfoque, y cómo se integra con Azure para automatizar la creación de recursos en la nube.

---

## 📘 1.1 ¿Qué es la Infraestructura como Código (IaC)?

La **infraestructura como código (IaC)** es una práctica que permite definir y administrar tu infraestructura (servidores, redes, bases de datos, etc.) utilizando archivos de texto que describen los recursos mediante código. Esto permite:

- Automatizar despliegues
- Tener trazabilidad de cambios (versionado)
- Evitar configuraciones manuales propensas a errores
- Compartir y reutilizar configuraciones fácilmente

> 🎯 En lugar de hacer clics en un portal web (como Azure Portal), defines todo con código.

---

## 🧰 1.2 ¿Qué es Terraform?

**Terraform** es una herramienta de código abierto desarrollada por HashiCorp que permite definir y gestionar infraestructura en múltiples proveedores (Azure, AWS, GCP, etc.) usando un lenguaje declarativo llamado **HCL** (HashiCorp Configuration Language).

### Características clave:
- Declarativo: describes *qué* quieres, no *cómo* lograrlo.
- Multicloud: soporta más de 100 proveedores.
- Modular: fomenta la reutilización del código.
- Automatizable: se integra con pipelines CI/CD.
- Open source (y también tiene versión Enterprise).

---

## ☁️ 1.3 ¿Por qué usar Terraform con Azure?

Terraform se integra perfectamente con Azure gracias al **proveedor oficial `azurerm`**, permitiendo:

- Crear redes, máquinas virtuales, bases de datos, contenedores, etc.
- Automatizar entornos de desarrollo y producción.
- Reutilizar infraestructura como plantillas.

Ventajas respecto al uso de ARM templates o Bicep:
- Más legible y modular.
- Más fácil de aprender para principiantes.
- Menor curva de aprendizaje.
- Más comunidad y ejemplos disponibles.

---

## 🔁 1.4 Cómo funciona Terraform (flujo de trabajo básico)

Terraform sigue un ciclo simple:

1. `terraform init`  
   Inicializa el entorno y descarga los proveedores necesarios.

2. `terraform plan`  
   Muestra los cambios que se aplicarán sin ejecutarlos.

3. `terraform apply`  
   Aplica los cambios a la infraestructura.

4. `terraform destroy` *(opcional)*  
   Elimina los recursos creados con Terraform.

```bash
# Ejemplo de ciclo básico
terraform init
terraform plan
terraform apply
```

Terraform guarda el estado actual de la infraestructura en un archivo llamado `terraform.tfstate`.

---

## 🧠 1.5 Términos clave que veremos

| Término            | Descripción |
|--------------------|-------------|
| `provider`         | El plugin que conecta Terraform con el proveedor (ej. Azure) |
| `resource`         | Un componente de infraestructura (ej. una VM, red, etc.) |
| `module`           | Conjunto reutilizable de recursos |
| `state`            | Archivo donde se almacena el estado actual de los recursos |
| `variable`         | Parámetro de entrada configurable |
| `output`           | Valor que Terraform muestra tras aplicar |

---

## 📝 Ejercicio práctico

### 🎯 Objetivo
Configurar tu cuenta de Azure y dejar el entorno listo para trabajar.

### Pasos

1. **Crea una cuenta gratuita de Azure**  
   👉 [https://azure.microsoft.com/free](https://azure.microsoft.com/free)

2. **Instala Azure CLI**  
   👉 [Guía oficial](https://learn.microsoft.com/es-es/cli/azure/install-azure-cli)

3. **Inicia sesión en tu cuenta de Azure**  
   Abre una terminal y escribe:
   ```bash
   az login
   ```

4. **Explora los recursos disponibles en tu suscripción**
   ```bash
   az group list --output table
   ```

5. *(Opcional)* Si ya sabes que trabajarás con una suscripción específica:
   ```bash
   az account set --subscription "<ID o nombre de la suscripción>"
   ```

---

## 📚 Recursos complementarios

- [¿Qué es IaC? - Microsoft Learn](https://learn.microsoft.com/es-es/devops/deliver/what-is-infrastructure-as-code)
- [Terraform vs ARM Templates](https://learn.microsoft.com/en-us/azure/developer/terraform/compare-terraform-and-arm)
- [Proveedores en Terraform](https://registry.terraform.io/browse/providers)

---

## ✅ Revisión del módulo

| ¿Qué aprendiste? |
|------------------|
| ✅ Qué es IaC y por qué es útil |
| ✅ Qué es Terraform y cómo funciona |
| ✅ Cómo se conecta con Azure |
| ✅ Flujo básico de trabajo |
| ✅ Cómo preparar tu entorno |
