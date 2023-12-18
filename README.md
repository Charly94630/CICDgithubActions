Project Documentation: Product Service

This repository contains GitHub Actions workflows for the Product Service microservice. The project aims to provide a microservice with comprehensive testing, analysis, and deployment processes.

Overview of Workflows for Different Branches
The workflows implemented in the files workflow-prod.yml, workflow-stage.yml, and workflow-dev.yml are designed to manage different environments of the Product Service project (production, staging, and development) using GitHub Actions. Although they are triggered on different branches, they share a similar structure and logic. Here is a technical overview of what they do:

Common Structure
Event Activation:

All workflows are triggered on push events to the corresponding branch (main, test, dev), repository_dispatch, and workflow_dispatch.

Concurrency Management:

Concurrency is configured using the concurrency block, ensuring that only one instance of the workflow runs for a specific concurrency group. Additionally, in-progress instances are canceled if another one is started.

Main Work:

Each workflow uses the same main job (build-), corresponding to the specific branch (production, staging, or development). This job uses the workflow defined in productservice.yml@ for the corresponding environment.

Environment Variables and Secrets Configuration:

Analysis:
Checkout and Code Analysis:

Extracts code from the repository using the checkout command and performs static code analysis using SonarQube.

Code Quality Assurance:

Verifies code quality, ensuring compliance with coding standards and highlighting potential areas for improvement.

Functional Testing:
Checkout, Unit Testing, and Application Startup:

Extracts code from the repository, runs unit tests, and starts the application for functional testing.

Execution of Functional Tests with Newman:

Uses Newman to run tests defined in the Postman collection, ensuring the correct functionality of the application.

HTML Report Generation:

Creates a detailed HTML report summarizing the results of the performed tests.

Description of Files
Dockerfile:

Specifies the Docker image build process. Uses Maven to build the application and OpenJDK for runtime.

collection.json:

Contains the definition of a Postman collection for functional testing. The test script in the collection validates the HTTP response status codes.

productservice.yml:

This file represents the main GitHub Actions workflow. It consists of several jobs for static analysis, functional testing, versioning, and Docker image building/publishing.

BUILD_AND_PUBLISH:

Builds the Docker image and publishes it to Amazon ECR.

Workflow Invocation:
Workflows are triggered in a versatile manner:

Automatically by Repository Dispatch Events:

Automatically initiated in response to code dispatch events to the repository.

Automatically by Push to Specific Branches:

Activated when changes are detected in specific branches of the repository.

Manually through Manual Triggers:

Can be invoked manually through the GitHub user interface.



------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Documentación del Proyecto Product Service

Este repositorio contiene los flujos de trabajo de GitHub Actions para el microservicio Product Service. El proyecto tiene como objetivo proporcionar un MS con procesos integrales de prueba, análisis e implementación.

Descripción General de los Flujos de Trabajo para Diferentes Ramas Los flujos de trabajo implementados en los archivos workflow-prod.yml, workflow-stage.yml, y workflow-dev.yml están diseñados para gestionar distintos entornos del proyecto product Service (producción, staging y desarrollo) utilizando GitHub Actions. Aunque se activan en ramas diferentes, comparten una estructura y lógica similares. Aquí hay una descripción general de lo que hacen en términos técnicos:

Estructura Común Activación de Eventos:

Todos los flujos de trabajo se activan en eventos de push a la rama correspondiente (main, test, dev), repository_dispatch, y workflow_dispatch.

Gestión de Concurrencia:

Se configura la concurrencia utilizando el bloque concurrency, asegurando que solo se ejecute una instancia del flujo de trabajo para un grupo de concurrencia específico. Además, se cancelan instancias en progreso si se inicia otra. Trabajo Principal:

Cada flujo de trabajo utiliza el mismo trabajo principal (build-), donde corresponde a la rama específica (producción, staging o desarrollo). Este trabajo utiliza el flujo de trabajo definido en prodcutservice.yml@ para el entorno correspondiente. Configuración de Variables de Entorno y Secretos:

Análisis:

Checkout y Análisis de Código: Realiza la extracción del código desde el repositorio mediante el comando de checkout y lleva a cabo un análisis de código estático utilizando SonarQube.

Aseguramiento de la Calidad del Código: Verifica la calidad del código, asegurando el cumplimiento de estándares de codificación y señalando posibles áreas de mejora.

Pruebas Funcionales: Checkout, Pruebas Unitarias y Arranque de la Aplicación: Extrae el código del repositorio, ejecuta pruebas unitarias y pone en marcha la aplicación para las pruebas funcionales.

Ejecución de Pruebas Funcionales con Newman: Utiliza Newman para ejecutar pruebas definidas en la colección de Postman, asegurando la funcionalidad correcta de la aplicación.

Generación de Informe HTML: Crea un informe detallado en formato HTML que resume los resultados de las pruebas realizadas.

Descripción de Archivos Dockerfile:

Especifica el proceso de construcción de la imagen de Docker. Utiliza Maven para construir la aplicación y OpenJDK para el tiempo de ejecución.

collection.json:

Contiene la definición de una colección de Postman para pruebas funcionales. El script de prueba en la colección valida el código de estado de las respuestas HTTP.

productservice.yml:

Este archivo representa el flujo de trabajo principal de GitHub Actions. Se compone de varios trabajos para realizar análisis estático, pruebas funcionales, creación de versiones y construcción/publicación de la imagen Docker.

BUILD_AND_PUBLISH

Construye la imagen Docker y la publica en Amazon ECR.

Invocación del Flujo de Trabajo: Los flujos de trabajo se activan de manera versátil:

Automáticamente por Eventos de Envío al Repositorio: Se inician automáticamente en respuesta a eventos de envío de código al repositorio. Automáticamente por push a Ramas Específicas: Se activan al detectar cambios en ramas particulares del repositorio. Manualmente mediante Activadores Manuales: Pueden ser invocados manualmente a través de la interfaz de usuario de GitHub.
