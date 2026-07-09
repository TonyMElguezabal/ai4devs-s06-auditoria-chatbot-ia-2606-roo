# Ejercicio · Sesión 6 — Auditoría de privacidad, seguridad y cumplimiento de un chatbot IA

## 🎯 Objetivo del ejercicio

Aprender a **auditar un sistema de IA antes de su puesta en producción**, integrando tres dimensiones vistas en el módulo: clasificación regulatoria (EU AI Act y GDPR), análisis de riesgos (OWASP Top 10 for LLM Applications) y decisión de arquitectura entre LLM comercial en la nube y modelo local.

Al terminar, serás capaz de argumentar ante dirección qué obligaciones legales aplican a tu sistema, qué ataques concretos debe resistir y qué arquitectura conviene — y entenderás que la respuesta correcta **no es técnica sino contextual**: el mismo chatbot tiene obligaciones y riesgos radicalmente distintos según el sector y los datos que procesa.

---

## ✅ Prerequisitos

- [ ] Haber completado las lecciones 🔴 del Módulo 6:
  - *"GDPR, marcos regulatorios de AI y agencias de AI"*
  - *"Principales riesgos de seguridad y privacidad"*
  - *"Mejores prácticas de seguridad en la interacción con LLMs"*
  - *"El auge de los modelos LLM locales"*
- [ ] Cuenta de **GitHub** y **Git** instalado en tu equipo (para la entrega por Pull Request).

---

## 📖 Escenario

Trabajas en una empresa que quiere lanzar un **chatbot de atención al cliente basado en un LLM comercial en la nube**. El chatbot tendrá acceso al historial de pedidos, los datos de contacto y las conversaciones previas de los clientes para dar respuestas personalizadas.

Antes del lanzamiento, dirección te pide una **auditoría de privacidad, seguridad y cumplimiento regulatorio**. Tu trabajo es entregarla.

---

## Paso 0 — Elige tu sector

Elige el sector de tu empresa ficticia: **e-commerce, banca, salud, educación o RRHH**.

Anótalo al inicio de tu entregable: esta elección condiciona el resto del ejercicio.

---

## Parte 1 — Clasificación regulatoria

1. Clasifica tu chatbot según las **cuatro categorías de riesgo del EU AI Act** y justifica tu elección. Ten en cuenta el sector que elegiste en el Paso 0: la respuesta depende de él.
2. Lista las obligaciones que implica tu categoría y las sanciones máximas por incumplimiento vigentes desde agosto de 2026.
3. Identifica los **principios del GDPR** que aplican al procesar datos de clientes en el chatbot: base legal, minimización de datos, privacidad por diseño y por defecto.

> 📖 Apóyate en la lección *"GDPR, marcos regulatorios de AI y agencias de AI"* 🔴.

---

## Parte 2 — Análisis de riesgos

1. Del **OWASP Top 10 for LLM Applications 2025**, selecciona los **3 riesgos más críticos** para tu chatbot y describe un escenario de ataque concreto y realista para cada uno. Piensa, por ejemplo, en qué podría escribir un cliente malintencionado en el chat, qué información de otros clientes podría filtrarse, o qué pasaría si el bot tiene permisos para ejecutar acciones (cancelar pedidos, emitir reembolsos…).
2. Enumera qué **PII** maneja tu chatbot y explica qué pasaría si esas conversaciones llegan sin filtrar al proveedor del LLM.

> 📖 Apóyate en las lecciones *"Principales riesgos de seguridad y privacidad"* 🔴 y *"Mejores prácticas de seguridad en la interacción con LLMs"* 🔴.

---

## Parte 3 — ¿Y si lo ejecutamos en local?

Argumenta en **máximo media página**: ¿recomendarías ejecutar el chatbot con un **modelo local** (por ejemplo, Ollama + Qwen 2.5 o DeepSeek-R1) en lugar del LLM comercial en la nube?

Compara **coste, privacidad, cumplimiento regulatorio y calidad** con los datos del módulo (por ejemplo: la amortización del hardware en 6–12 meses para cargas de 1.500–2.500 consultas/mes, o que el 44% de las empresas cita la privacidad como principal barrera para LLMs en la nube).

También puedes proponer una **arquitectura híbrida** (modelo local para consultas que tocan PII, cloud para el resto). Tu conclusión debe ser coherente con el sector que elegiste en el Paso 0.

> 📖 Apóyate en la lección *"El auge de los modelos LLM locales"* 🔴.

---

## 📦 Entregable

Un documento único **`auditoria-chatbot-ia.md`** con:

- Sector elegido (Paso 0)
- Clasificación EU AI Act justificada + obligaciones + principios GDPR (Parte 1)
- Los 3 riesgos OWASP con sus escenarios de ataque + inventario de PII (Parte 2)
- Recomendación argumentada local vs. cloud vs. híbrida (Parte 3)

Tienes una plantilla opcional en [`entregas/plantilla-auditoria-chatbot-ia.md`](entregas/plantilla-auditoria-chatbot-ia.md).

---

## 📤 Pasos para entregar mediante Pull Request

1. Haz un **fork** de este repositorio usando el botón ubicado arriba a la derecha.
2. **Clona tu fork** en tu computadora. Será un proyecto con el mismo nombre, pero bajo tu usuario.
3. **Completa el ejercicio:**
   - Desarrolla las tres partes de la auditoría.
   - Agrega el documento único `auditoria-chatbot-ia.md` dentro de **tu carpeta** en `entregas/` (con tu nombre o usuario de GitHub), por ejemplo: `entregas/jorge-pilo/auditoria-chatbot-ia.md`.
4. Crea una **nueva rama** para tu solución:

```bash
git checkout -b solved-chatbot-audit
```

5. Haz **commit** de tus cambios:

```bash
git add .
git commit -m "Solve chatbot AI audit exercise"
```

6. **Sube tu rama** a tu fork:

```bash
git push origin solved-chatbot-audit
```

7. En la interfaz de GitHub de tu fork aparecerá un aviso para **crear el Pull Request**.
8. Crea el Pull Request hacia el repositorio original. **Esa será tu entrega final.**

---

## 🟢 Bonus (opcional)

Elige uno (o varios) e inclúyelo en el mismo documento del PR:

- **Anonimización en acción:** instala **Microsoft Presidio** (`pip install presidio-analyzer presidio-anonymizer`), pásale 3 mensajes ficticios de clientes con nombre, email, teléfono y número de pedido, y adjunta el antes/después comentando qué detectó bien y qué se le escapó.
- **Política de IA:** redacta las **5 reglas de una política de uso de IA generativa** para los empleados de tu empresa ficticia: qué datos se pueden compartir con herramientas de IA y cuáles no. Este tema se retoma en el **Módulo 15. DevSecOps: monitorización, observabilidad y seguridad por diseño**.
- **LLM local en acción:** instala **Ollama**, descarga un modelo (Qwen 2.5 o una variante destilada de DeepSeek-R1) y hazle 5 preguntas típicas de atención al cliente en español. Incluye tu veredicto: ¿lo pondrías delante de un cliente real?

> 📌 **No hace falta perfección.** Lo importante es el razonamiento: una auditoría con argumentos específicos de tu sector vale más que una lista genérica de riesgos copiada de la documentación.
