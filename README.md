# 🛠️ Sistema de Gestión de Servicios – Centro de Atención Tecnológica (CAT)

Este proyecto implementa un sistema para gestionar solicitudes de soporte tecnológico en un Centro de Atención Tecnológica (CAT) universitario.  
El sistema reemplaza el proceso actual basado en correos electrónicos, permitiendo mayor organización, trazabilidad y eficiencia.

---

## 🚀 Características principales

- Registro de solicitudes de soporte.
- Asignación de solicitudes a técnicos.
- Gestión de estados (Nuevo, En proceso, Resuelto).
- Gestión de prioridades.
- Panel para técnicos y panel para usuarios.
- Reportes generales.
- Consultas del estado de solicitudes por parte de los usuarios.

---

## 🗂️ Metodología del Proyecto

El proyecto se administra con:

### ✔ **GitHub Projects**
- Board con columnas: **To Do**, **In Progress**, **Review**, **Done**
- Auto-add activado para issues del repositorio
- Issues priorizados con labels
- Historias de usuario incluidas

### ✔ **Scrum**
- Product Backlog inicial
- Sprint backlog tomado desde GitHub Project
- Poker planning documentado
- Entregas incrementales

---

## 📌 Estructura del Backlog

El backlog inicial (10+ items) incluye:
- Registro de solicitudes
- Gestión de usuarios
- Asignación de tickets a técnicos
- Cambios de estado
- Prioridades
- Reportes
- Interfaz para usuarios
- Interfaz para técnicos
- Inicio de sesión
- Integración con GitHub Actions

> Detalles completos disponibles en el documento PDF del proyecto.

---

## 📄 Historias de Usuario (Ejemplo)

Formato: **Como [usuario], quiero [acción], para [beneficio].**

- Como estudiante, quiero registrar una solicitud de soporte, para recibir asistencia técnica.
- Como técnico, quiero ver las solicitudes asignadas, para gestionar mi trabajo.
- Como administrador, quiero gestionar prioridades, para atender primero los casos urgentes.

---

## ⚙️ Requerimientos del Sistema

### **Requerimientos funcionales**
1. El sistema debe permitir registrar solicitudes de soporte.
2. El sistema debe permitir asignar solicitudes a técnicos.
3. El sistema debe mostrar el estado de cada solicitud.
4. El sistema debe permitir modificar la prioridad de una solicitud.
5. El sistema debe generar reportes de solicitudes.

### **Requerimientos no funcionales**
1. El sistema debe responder cada acción en menos de 2 segundos.
2. Debe garantizar disponibilidad del 99% en horario laboral.
3. Debe permitir acceso desde dispositivos móviles.
4. Debe contar con autenticación segura.
5. La interfaz debe ser intuitiva y fácil de usar.

---

## 🧪 Integración continua (CI) – GitHub Actions

Este repositorio usa un pipeline de CI basado en Java + Maven.

**Archivo:** `.github/workflows/ci.yml`

```yaml
name: Java CI

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout repository
      uses: actions/checkout@v3

    - name: Set up JDK
      uses: actions/setup-java@v3
      with:
        java-version: "17"
        distribution: "temurin"

    - name: Build with Maven
      run: mvn -B package --file pom.xml

    - name: Run Tests
      run: mvn test
