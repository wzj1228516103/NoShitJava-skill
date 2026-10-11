# NoShitJava-skill

[English](README.en.md) · [简体中文](README.md) · [日本語](README.ja.md) · Español

<div align="center">
  <img src="data/images/noshitjava-skill-logo.png" alt="Imagen del proyecto NoShitJava-skill" width="260">
  <p><strong>Java sin montaña de mierda — un asistente con IA para todo el ciclo de desarrollo Java</strong><br>
  <sub>A Java development skill for keeping codebases maintainable.</sub></p>
</div>

> Un skill de carga bajo demanda para backends Java/Spring: la generación de código, el diseño de APIs, los cambios de base de datos, la revisión de código y las pruebas siguen restricciones consistentes de nivel producción.

[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![CI](https://github.com/wzj1228516103/NoShitJava-skill/actions/workflows/quality.yml/badge.svg?branch=master)](https://github.com/wzj1228516103/NoShitJava-skill/actions/workflows/quality.yml)
[![Java](https://img.shields.io/badge/Java-17%2B-orange.svg)](https://www.oracle.com/java/technologies/javase/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-brightgreen.svg)](https://spring.io/projects/spring-boot)
[![Teoría: No-Shit](https://img.shields.io/badge/teoría-No--Shit-2563EB)](THEORY.md)
[![Efecto secundario: código mantenible](https://img.shields.io/badge/efecto__secundario-código__mantenible-success)](THEORY.md)

![Arquitectura de NoShitJava-skill: enrutamiento raíz, siete entradas, biblioteca de reglas bajo demanda, configuración de proyecto y regresiones de evaluación](data/images/noshitjava-skill-architecture.png)

![Introducción general de NoShitJava-skill: siete entradas de flujo de trabajo, stack técnico y capacidades de ingeniería](data/images/noshitjava-skill-overview.png)

## Acerca de

NoShitJava-skill está pensado para proyectos backend Java/Spring. Se basa en el *Manual de Desarrollo Java de Alibaba (Edición Huangshan)* y prácticas de ingeniería comunes, lee solo las reglas relevantes para la tarea actual y ayuda con desarrollo, diseño, revisión, pruebas, corrección de bugs, refactorización y consulta de normas; no sustituye las convenciones del proyecto ni la revisión de seguridad.

Para la documentación completa de reglas, la estructura del repositorio y el mantenimiento, consulta el [README detallado](README-DETAILS.md) (en chino).

## La teoría No-Shit

Hermana de la teoría del Agua Grande (bebe más agua) y la del Sueño Grande (duerme más), pero gobierna la tercera gran cosa de tu día: **escribir código**. En una frase:

> Una montaña de mierda nunca se escribe de una sola vez — se acumula un "así vale por ahora, ya lo arreglaremos" cada vez.

Tres mandamientos: **piensa antes de construir; respalda los límites y los caminos de fallo con pruebas; nunca negocies la seguridad ni la corrección de datos.** Este skill pone la teoría en práctica con IA — siete entradas que la hacen cumplir, normas bajo demanda. Texto completo: el [Manifiesto de la Teoría No-Shit](THEORY.md) (en chino).

## Siete entradas

| Entrada | Úsala para | Entregable principal |
|---|---|---|
| `/java-dev` | Escribir funcionalidades | Implementa APIs, lógica de negocio o esqueletos siguiendo el estilo del proyecto |
| `/java-design` | Diseñar primero | Organiza APIs, diseño de tablas, transacciones y riesgos probables |
| `/java-review` | Revisar código | Señala problemas con evidencia, su ubicación y sugerencias de corrección |
| `/java-test` | Añadir pruebas | Cubre casos normales, límites y fallos |
| `/java-fix` | Depurar | Encuentra la causa, aplica correcciones necesarias y añade pruebas de regresión |
| `/java-refactor` | Limpiar código heredado | Mejora el código paso a paso sin cambiar el comportamiento |
| `/java-rules` | Consultar normas | Explica reglas y condiciones de aplicación con ejemplos concretos |

`/java-dev` y los demás nombres son nombres de entrada, no necesariamente comandos slash de tu herramienta de IA. Si no funcionan, no pasa nada: con el skill activado basta con describir lo que necesitas en lenguaje natural.

## Resultados medidos

El mismo conjunto de tareas Java/Spring se evaluó con y sin el skill, puntuando cada regla:

| **Métrica** | **Con este skill** | **Sin skill** | **Mejora** |
|---|---:|---:|---:|
| **Tasa de aprobación media de aserciones de calidad (holdout-v6)** | **100.00%** | 88.89% | **+11.11pp** |
| **Tasa de casos totalmente aprobados (holdout-v6)** | **100.00%** (15/15) | 73.33% (11/15) | **+26.67pp** |
| **Tasa de calidad media del peor caso (holdout-v6)** | **100.00%** | 77.78% | **+22.22pp** |
| **Tasa de aprobación media de aserciones de calidad (eval-v9)** | **100.00%** | 91.67% | **+8.33pp** |

Las tasas de aserciones de calidad se contabilizan sobre las aserciones del Judge (evaluador automático) y excluyen el umbral `expect`. holdout-v6 es el conjunto de tareas reservado para verificación y eval-v9 la suite principal; las configuraciones, casos y métricas están en [`evals/`](evals/README.md). Las tareas de origen participaron en el ajuste, así que estos resultados sirven como verificación de regresión, no como prueba de ganancias de generalización independientes.

## Cobertura

| Área | Contenido cubierto |
|---|---|
| Fundamentos de Java | Nomenclatura, fecha/hora, dinero, colecciones, concurrencia, liberación de recursos |
| APIs Spring | Controllers, DTOs, validación, respuestas y compatibilidad de API |
| Datos y transacciones | SQL, índices, paginación, transacciones, idempotencia, migraciones |
| Seguridad y fiabilidad | Autorización, enmascaramiento de logs, caché, mensajería, timeouts, reintentos |
| Pruebas y arquitectura | Pruebas unitarias/de integración, capas y límites de módulos |

## Instalación

Ejecuta este comando para instalar NoShitJava-skill en Codex:

```bash
npx skills add https://github.com/wzj1228516103/NoShitJava-skill -g -a codex -y
```

Tras instalar, comprueba que está disponible:

```bash
npx skills list -g -a codex
```

Si ves `noshitjava-skill`, está instalado. Reabre Codex, escribe `$noshitjava-skill` seguido de tu tarea. Si no aparece, reinicia Codex y comprueba de nuevo.

## Ejemplos de uso

Con el skill activado, describe tu tarea en lenguaje natural; no hace falta memorizar los nombres de entrada:

| Puedes decir | Qué hace |
|---|---|
| "Siguiendo el estilo actual del proyecto, añade una API de creación de pedidos y ejecuta las pruebas relacionadas." | Primero lee el código y el stack del proyecto, luego implementa y verifica. |
| "Revisa este cambio buscando problemas de autorización, transacciones o SQL; solo revisa, no modifiques el código." | Señala problemas, ubicaciones y sugerencias basadas en evidencia del código, sin cambios no solicitados. |
| "¿Cómo diseñar la deducción de inventario? Incluye control de concurrencia y manejo de fallos; primero dame un plan." | Organiza el diseño y los riesgos antes de escribir código. |
| "Esta API a veces lee un estado de pedido obsoleto; encuentra la causa, arréglalo y añade una prueba de regresión." | Investiga, aplica las correcciones necesarias y revisa las pruebas relacionadas. |

## Configuración del proyecto

- `memory.md` guarda preferencias personales; copia `project/_template.md` para registrar el stack y las convenciones de un proyecto concreto.
- Las convenciones del proyecto tienen prioridad sobre las preferencias personales, pero los requisitos de seguridad y corrección de datos nunca se relajan. No conviertas decisiones puntuales en configuración permanente, ni commitees credenciales o información interna.

Consulta [`project/README.md`](project/README.md) para la documentación completa de configuración.

## Límites de uso

- Las reglas se aplican solo a la tarea actual; los demos y scripts desechables pueden mantenerse ligeros.
- Las convenciones existentes del proyecto tienen prioridad; las reglas de seguridad y corrección de datos nunca se relajan. Si el usuario pide no usar este skill, deja de aplicar sus reglas.

Este proyecto ofrece orientación de ingeniería y no sustituye las auditorías de seguridad, las aprobaciones de cambios de base de datos ni los procesos de despliegue del equipo.

## Referencias y créditos

- [**Manual de Desarrollo Java de Alibaba (Edición Huangshan)**](https://github.com/alibaba/p3c) — fuente de las reglas de este skill, destilado por la comunidad Java de Alibaba; este proyecto solo selecciona y reorganiza el contenido relevante.
- [Alibaba Java Development Guide](https://github.com/Sxuan-Coder/alibaba-java-development-guide) — enrutamiento bajo demanda, niveles de reglas y configuración de proyecto.
- [backend-skill](https://github.com/zhangloveyan/backend-skill) — flujo de desarrollo, plantillas de código y ciclo de pruebas.
- [**skill-up**](https://github.com/alibaba/skill-up) — la herramienta de evaluación detrás de los benchmarks y regresiones de `evals/`.

Este proyecto no es un producto oficial de Alibaba ni cuenta con su respaldo. El contenido original se publica bajo [MIT License](LICENSE); el contenido citado y los materiales de terceros siguen sus propias licencias.
Consulta [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md) para fuentes de terceros, alcance de adaptación y licencias.

## Mantenimiento y comentarios

Issues y sugerencias de mejora son bienvenidos. Tras hacer cambios, ejecuta las comprobaciones de mantenimiento del repositorio:

```powershell
pwsh -NoProfile -File ./data/maintenance/scripts/validate-registry.ps1
pwsh -NoProfile -File ./data/maintenance/scripts/validate-content.ps1
```

Consulta el [CHANGELOG](CHANGELOG.md) para el historial de versiones y [SECURITY](SECURITY.md) para la política de seguridad.
Quienes contribuyan deben leer la [guía de contribución](CONTRIBUTING.md) y el [código de conducta](CODE_OF_CONDUCT.md).
