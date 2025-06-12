# 🧩 Módulo 9: Integración con Azure DevOps y Automatización de Despliegues

## 🎯 Objetivo del módulo  
Aprender a integrar Terraform con Azure DevOps para automatizar despliegues de infraestructura como código en un entorno CI/CD.

---

## ⚙️ 9.1 Introducción a Azure DevOps

Azure DevOps es una plataforma de Microsoft que ofrece herramientas para la planificación, desarrollo, pruebas e implementación de software.

### Componentes clave:
- Repositorios (Repos)
- Pipelines (CI/CD)
- Tableros (Boards)
- Artefactos

---

## 🔁 9.2 Automatización con Azure Pipelines

Los pipelines permiten definir flujos automáticos de despliegue usando archivos YAML.

### Ejemplo básico de pipeline para Terraform:

```yaml
trigger:
  - main

pool:
  vmImage: 'ubuntu-latest'

steps:
  - task: UseTerraform@0
    inputs:
      command: 'init'

  - task: UseTerraform@0
    inputs:
      command: 'plan'

  - task: UseTerraform@0
    inputs:
      command: 'apply'
      args: '-auto-approve'
```

> Este pipeline realiza `init`, `plan` y `apply` cuando hay cambios en la rama `main`.

---

## 🔐 9.3 Manejo de credenciales en Azure DevOps

### Recomendaciones:
- Usa [Azure Key Vault](https://learn.microsoft.com/en-us/azure/key-vault/) para guardar secretos.
- Configura un Service Connection con permisos mínimos necesarios.
- Nunca expongas secretos directamente en el código YAML.

---

## 🧪 9.4 Ejercicio práctico

### 🎯 Objetivo
Crear una automatización básica con Azure Pipelines para desplegar infraestructura con Terraform.

### Tareas

1. Subir tus archivos `.tf` a un repositorio de Azure DevOps.
2. Crear un pipeline YAML que haga `init`, `plan` y `apply`.
3. Usar una Service Connection con una cuenta de servicio.
4. Validar que la infraestructura se despliegue automáticamente al hacer `push`.

---

## 📚 Recursos útiles

- [Terraform y Azure DevOps](https://learn.microsoft.com/en-us/azure/developer/terraform/)
- [Documentación Azure Pipelines](https://learn.microsoft.com/en-us/azure/devops/pipelines/?view=azure-devops)
- [Azure Key Vault](https://learn.microsoft.com/en-us/azure/key-vault/general/overview)

---

## ✅ Revisión del módulo

| ¿Qué lograste? |
|----------------|
| ✅ Entender qué es Azure DevOps |
| ✅ Crear un pipeline de Terraform |
| ✅ Configurar credenciales seguras |
| ✅ Automatizar despliegues con CI/CD |
