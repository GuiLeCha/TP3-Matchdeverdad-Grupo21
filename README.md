# Matchdeverdad — Dos sentencias, dos soluciones | IFTS 29
## Práctica Formativa TP3 · Desarrollo de Sistemas Web / Front End (2026 - 2do Cuatrimestre)

Landing page técnica e interactiva desarrollada por el **Grupo 21** para presentar dos propuestas de automatización agéntica aplicadas a la startup **Matchdeverdad**, resolviendo el bloque asignado **Candidatos y urgencia** (Sorteo **S07-A**: Sentencias **FRASE 1 · R1** y **FRASE 2 · R2**).

🔗 **Landing en vivo:** [tp3-matchdeverdad-grupo21.vercel.app](https://tp3-matchdeverdad-grupo21.vercel.app/) · **Repositorio:** [GuiLeCha/TP3-Matchdeverdad-Grupo21](https://github.com/GuiLeCha/TP3-Matchdeverdad-Grupo21)

**Stack:** HTML5 · CSS3 · JavaScript (ES6, sin frameworks) · Vite 6 · Deploy en Vercel

### Índice

1. [Datos del Proyecto y Asignación Académica](#1-datos-del-proyecto-y-asignación-académica)
2. [Integrantes del Grupo 21 y Aportes Concretos](#2-integrantes-del-grupo-21-y-aportes-concretos)
3. [Sobre la Startup Matchdeverdad](#3-sobre-la-startup-matchdeverdad-y-la-articulación-ifts-16--ifts-29)
4. [Formalización en Lógica Proposicional](#4-formalización-en-lógica-proposicional-y-auditoría-de-estados)
5. [Las Dos Propuestas Agénticas](#5-desglose-detallado-de-las-dos-propuestas-agénticas-y-casos-límite)
6. [Tecnologías y Arquitectura](#6-tecnologías-y-arquitectura-del-proyecto)
7. [Estructura del Repositorio y Secciones de la Landing](#7-estructura-del-repositorio-y-secciones-de-la-landing)
8. [Cómo Ejecutar el Proyecto Localmente](#8-instrucciones-para-ejecutar-el-proyecto-localmente)
9. [Cómo Colaborar (Ramas y Pull Requests)](#9-cómo-colaborar-ramas-y-pull-requests)
10. [Herramientas de IA y Evidencia de Construcción Agéntica](#10-herramientas-de-ia-y-evidencia-de-construcción-agéntica)
11. [Enlaces Públicos del Proyecto](#11-enlaces-públicos-del-proyecto)

---

## 1. Datos del Proyecto y Asignación Académica

- **Institución:** Instituto de Formación Técnica Superior Nº 29 (IFTS 29) — Articulación pedagógica con IFTS 16.
- **Carrera:** Tecnicatura Superior en Desarrollo de Software.
- **Asignatura:** Desarrollo de Sistemas Web / Front End (2do Año · 2do Cuatrimestre).
- **Instancia Evaluativa:** Trabajo Práctico Nº 3 (TP3) – *Dos sentencias, dos soluciones*.
- **Comisión y Grupo:** Grupo 21.
- **Asignación Docente Oficial:** Sorteo `S07-A` · Grupo 21.
- **Startup Asignada:** Matchdeverdad.
- **Rubro:** Deportes y organización de partidos de fútbol 5 amateur.
- **Bloque Asignado:** Candidatos y urgencia.
- **Objetivo de la Startup:** Organizador inteligente de fútbol 5 que ayuda a reunir diez jugadores confirmados sin poner en riesgo la reserva de la cancha.
- **Logo Oficial:** Incorporado en formato WebP nativo (`public/logos/S07.webp`) con descarga directa desde la interfaz.

---

## 2. Integrantes del Grupo 21 y Aportes Concretos

| Integrante | Localidad / GitHub | Rol en el Equipo | Aportes Concretos y Tareas Realizadas en el TP3 |
| :--- | :--- | :--- | :--- |
| **Florencia Guzmán** | Cañuelas · [`@fguzman3026`](https://github.com/fguzman3026) | Front End & Diseño UI/UX | Dirección de arte con estética de cancha sintética nocturna (*"La Cantera F5"*), definición de paleta de alto contraste (verde césped `#22c55e`, ámbar de urgencia `#f59e0b`, cal blanca), tipografía deportiva (*Barlow Condensed*) y diseño de las 10 camisetas interactivas de la pizarra. |
| **Sonia Raquel Andrada** | CABA · [`@Raqu28`](https://github.com/Raqu28) | Lógica Proposicional & Accesibilidad | Formalización de las sentencias R1 y R2 recibidas del IFTS 16 en variables atómicas ($p, q, r, s, t, u$), construcción de la tabla de verdad de 8 estados, maquetación semántica de desplegables `<details>` y validación de accesibilidad por teclado (`:focus-visible`, roles ARIA). |
| **Eitel Hugo Belinzoni** | Mar del Plata · [`@Apoteotico`](https://github.com/Apoteotico) | Arquitectura & Testing | Configuración del entorno en Vite, armado de los árboles de decisión visuales en HTML/CSS con filtros interactivos por rama (*Completo / Camino SÍ / Camino NO*), pruebas de compilación (`npm run build`) y verificación de layout responsive sin desbordes. |
| **Guillermo Alberto Chacon** | CABA · [`@GuiLeCha`](https://github.com/GuiLeCha) | Coordinación & Simulador Interactivo | Coordinación de prompts y directivas al entorno agéntico, programación de la lógica reactiva de *La Pizarra del Capitán* en `src/main.js`, auditoría de casos borde (ventana de 30 min, invitación en 1 clic) y despliegue en GitHub / Vercel. |

### Evidencia de Colaboración y Revisión Cruzada entre Integrantes (Nivel Supera / Propone)

Durante el desarrollo realizamos tres rondas internas de revisión de código y lógica sobre lo que generaba el agente de IA:

1. **Revisión 1 (Guzmán & Chacon — Invariante de No-Cancelación $\neg u$ en R2):**
   En la primera iteración, el agente había generado para la Frase 2 una rama que daba de baja la reserva del turno cuando faltaban menos de 3 horas y no había candidatos, bajo el supuesto de "liberar al usuario del compromiso". **Florencia** detectó de inmediato que eso violaba textualmente la consigna del sorteo S07-A (*"sin cancelar el partido automáticamente"*). **Guillermo** sumó el argumento de negocio real del fútbol 5 amateur: en cualquier complejo deportivo, cancelar sobre la hora implica perder el 100% de la seña abonada y que encima el grupo se quede sin cancha, cuando muchas veces los equipos prefieren jugar 4 vs 4 o sumar a último momento a un conocido. A partir de esta revisión, rediseñamos el flujo para que el consecuente de R2 sea $(t \land \neg u)$, destacando un escudo visual de **Reserva de Cancha Protegida**.
2. **Revisión 2 (Andrada & Belinzoni — Tabla de Verdad y Caso Borde $p \land q \land r$ en el Simulador):**
   Al probar el simulador con la tabla de verdad en mano, **Sonia** notó que cuando el radar barrial estaba activo ($q = V$) y faltaban jugadores ($p = V$), cambiar los botones de tiempo entre *4 Horas* ($\neg r$), *2 Horas* ($r$) y *30 Minutos* ($r$) no producía ningún cambio visible en la respuesta del agente, y además un estilo inline en el indicador luminoso (`beacon.style.background`) dejaba trabado el color gris tras pasar por el estado de búsqueda pasiva. **Eitel** propuso separar explícitamente el estado $p \land q \land \neg r$ (propuesta de candidatos con margen holgado) del caso borde $p \land q \land r$ (propuesta de incorporación inmediata en ventana $< 3\text{h}$, donde R1 prevalece sobre R2 porque $q = V$ anula $\neg q$), y reemplazar los estilos inline por clases CSS limpias.
3. **Revisión 3 (Equipo Completo — Criterios de Compatibilidad y Escalamiento Humano):**
   Acordamos entre los cuatro acotar qué significa en la práctica "candidato compatible con la zona y el horario" ($q$): definimos un radio de geocercanía inicial de $\le 5\text{ km}$ respecto del predio y una ventana horaria con margen de llegada de $\pm 15\text{ minutos}$. Para alcanzar el nivel *Supera / Propone*, diseñamos protocolos de intervención humana concretos para ambos flujos: ampliación de radar a $10\text{ km}$ + código QR de invitación externa en R1, y notificación espejo al subcapitán + aviso al WhatsApp del complejo deportivo cuando restan $\le 45\text{ minutos}$ en R2.

---

## 3. Sobre la Startup Matchdeverdad y la Articulación IFTS 16 – IFTS 29

### Contexto Académico Interinstitucional
Las reglas de negocio de **Matchdeverdad** fueron modeladas originalmente en lenguaje de lógica proposicional por estudiantes del **IFTS 16** dentro de la asignatura *Lógica Computacional*.

En este Trabajo Práctico Nº 3 de *Desarrollo de Sistemas Web / Front End* en el **IFTS 29**, nuestro equipo (**Grupo 21**) tomó esas fórmulas proposicionales como especificación formal de entrada para diseñar dos flujos de decisión agénticos, construir sus diagramas interactivos y plasmarlos en una aplicación web funcional donde cualquier usuario puede experimentar cómo responde el sistema ante cada combinación de variables.

### Problemática que Resuelve
En el fútbol 5 amateur, el problema clásico no es reservar la cancha, sino **sostener los 10 jugadores confirmados** hasta la hora del partido. Una baja imprevista a las 18:30 para un turno de las 20:00 suele desencadenar cadenas caóticas de mensajes en grupos de WhatsApp, incertidumbre sobre si se llega a armar el partido y el riesgo constante de perder la seña económica dejada en el predio.

**Matchdeverdad** actúa como un copiloto táctico para el organizador (capitán):
- Monitorea en vivo el quórum de la planilla ($n / 10$).
- Cruza las vacantes con un radar comunitario de jugadores libres cercanos ($\le 5\text{ km}$) que coinciden en franja horaria y posición.
- Propone candidatos listos para invitar con un clic, y si el reloj entra en zona crítica ($< 3\text{ horas}$) sin postulantes cercanos, alerta de inmediato al capitán con alternativas reales de contingencia, **protegiendo siempre la reserva de la cancha**.

---

## 4. Formalización en Lógica Proposicional y Auditoría de Estados

Para garantizar una trazabilidad exacta entre el modelo de *Lógica Computacional* (IFTS 16) y nuestra interfaz en *Front End* (IFTS 29), formalizamos las dos sentencias del bloque **Candidatos y urgencia (Sorteo S07-A)** mediante seis proposiciones atómicas.

### 4.1. Diccionario de Proposiciones Atómicas (Variables Lógicas)

| Símbolo | Tipo | Definición Proposicional Formal | Criterio Operativo en el Sistema / Simulador | Negación ($\neg$) |
| :---: | :---: | :--- | :--- | :--- |
| **$p$** | Entrada (Premisa) | *"Faltan jugadores para completar el partido."* | Recuento de confirmados $n < 10$ (existen entre 1 y 10 vacantes en cancha). | **$\neg p$**: Quórum completo ($n = 10$ jugadores confirmados). |
| **$q$** | Entrada (Premisa) | *"Hay candidatos compatibles con la zona y el horario."* | Padrón activo arroja $\ge 1$ jugador libre en radio $\le 5\text{ km}$ y margen $\pm 15\text{ min}$. | **$\neg q$**: Radar vacío ($0$ candidatos compatibles en zona y horario). |
| **$r$** | Entrada (Premisa) | *"Quedan menos de tres horas para el inicio del partido."* | Reloj regresivo estricto $t_{\text{restante}} < 180\text{ min}$ (botones `2 Horas` o `30 Minutos`). | **$\neg r$**: Margen holgado o límite exacto ($t_{\text{restante}} \ge 180\text{ min}$, botones `4 Horas` y caso borde `3 Horas Exactas`). |
| **$s$** | Salida (Acción R1) | *"El sistema propone esos candidatos al organizador."* | El agente *MatchFinder* despliega fichas de postulantes con invitación en 1 clic. | **$\neg s$**: No se despliegan sugerencias de candidatos. |
| **$t$** | Salida (Acción R2) | *"El sistema alerta al organizador."* | El agente *MatchGuard Urgency* dispara alerta prioritaria con opciones tácticas. | **$\neg t$**: No se emite alerta de urgencia por escasez. |
| **$u$** | Salida (Restricción) | *"El sistema cancela el partido automáticamente."* | Acción destructiva prohibida por regla de negocio. | **$\neg u$**: **Invariante de seguridad** — el sistema **NO** cancela el partido automáticamente. |

---

### 4.2. Fórmulas Moleculares de las Reglas R1 y R2

1. **Regla R1 (Frase 1 — Propuesta de Candidatos Compatibles):**
   > *«Si faltan jugadores y hay candidatos compatibles con la zona y el horario, el sistema propone esos candidatos al organizador.»*
   
   $$(p \land q) \rightarrow s$$

2. **Regla R2 (Frase 2 — Alerta de Urgencia sin Cancelación Automática):**
   > *«Si faltan jugadores, quedan menos de tres horas y no hay candidatos compatibles, el sistema alerta al organizador sin cancelar el partido automáticamente.»*
   
   $$(p \land r \land \neg q) \rightarrow (t \land \neg u)$$

### 4.3. Propiedades Lógicas Demostradas por el Equipo

- **Exclusión Mutua de Antecedentes (Determinismo sin Colisiones):**
  Los antecedentes de R1 y R2 contienen literales complementarios respecto de la proposición $q$: R1 exige $q$ verdadero, mientras que R2 exige $\neg q$ verdadero. Por el *Principio de No Contradicción* ($q \land \neg q \equiv \bot$):
  $$((p \land q) \land (p \land r \land \neg q)) \equiv \bot$$
  Esto demuestra formalmente que **R1 y R2 jamás pueden dispararse al mismo tiempo**, evitando condiciones de carrera o mensajes contradictorios en la interfaz del organizador.
- **Invariante de Dominio ($\neg u$ siempre Verdadero):**
  En la regla R2, la conjunción del consecuente $(t \land \neg u)$ obliga a que la alerta ($t = V$) vaya acompañada invariablemente por la no-cancelación ($u = F \iff \neg u = V$). En los restantes estados donde no se activa R2, el sistema tampoco cancela la reserva, por lo que $\neg u = V$ se mantiene como propiedad de seguridad global.
- **Verdad por Vacuidad con Equipo Completo ($\neg p$):**
  Cuando los 10 jugadores están confirmados ($p = F$), tanto $(p \land q)$ como $(p \land r \land \neg q)$ se evalúan como Falsos ($F$). En lógica clásica, una implicación material $A \rightarrow B$ con antecedente falso ($F \rightarrow B$) es siempre **Verdadera por vacuidad**, lo que valida que el agente permanezca en reposo ($\neg s \land \neg t \land \neg u$) cuando la cancha está llena.

---

### 4.4. Tabla de Verdad Completa de las Variables de Entrada $(p, q, r)$

A continuación documentamos las $2^3 = 8$ combinaciones posibles de las proposiciones de entrada $(p, q, r)$ y su correspondencia exacta con los estados del simulador **La Pizarra del Capitán**:

| Fila | $p$ (Faltan $<10$) | $q$ (Hay candidatos) | $r$ (Tiempo $<3\text{h}$) | $\neg q$ | Antecedente R1: $(p \land q)$ | Antecedente R2: $(p \land r \land \neg q)$ | Consecuente Activo ($s$ / $t \land \neg u$) | Estado Operativo en el Simulador y la Interfaz |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :--- |
| **1** | **V** | **V** | **V** | F | **V** | F | **$s = V$** ($\neg t, \neg u$) | **Caso Borde R1 en Ventana $<3\text{h}$:** Faltan jugadores y queda poco tiempo (`2h` o `30m`), pero hay candidatos en zona. **Prevalece R1**: se propone refuerzo inmediato sin alerta de escasez. |
| **2** | **V** | **V** | **F** | F | **V** | F | **$s = V$** ($\neg t, \neg u$) | **Regla R1 Estándar (Margen Holgado):** Faltan jugadores a `4h` del turno y el radar detecta postulantes en $\le 5\text{ km}$. El agente *MatchFinder* propone candidatos con invitación en 1 clic. |
| **3** | **V** | **F** | **V** | **V** | F | **V** | **$t = V \land \neg u = V$** ($\neg s$) | **Regla R2 Activa (Urgencia Crítica):** Faltan jugadores, restan `< 3h` (`2h` o `30m`) y no hay candidatos ($\neg q$). Dispara **Alerta Prioritaria**, opciones 4 vs 4 / escalamiento a los 30m y **NO cancela ($\neg u$)**. |
| **4** | **V** | **F** | **F** | **V** | F | F | $\neg s \land \neg t \land \neg u$ | **Caso Borde de Espera / Monitoreo Pasivo:** Faltan jugadores y no hay candidatos en $5\text{ km}$, pero faltan $\ge 3\text{h}$ (`4h`). No se alarma por urgencia; ofrece ampliar radar a $10\text{ km}$ o link QR externo. |
| **5** | **F** | **V** | **V** | F | F | F | $\neg s \land \neg t \land \neg u$ | **Quórum Completo (`10/10` Confirmados):** Aunque haya postulantes libres y falten $<3\text{h}$, al ser $p = F$ ambas reglas quedan satisfechas por vacuidad. Equipo listo para jugar. |
| **6** | **F** | **V** | **F** | F | F | F | $\neg s \land \neg t \land \neg u$ | **Quórum Completo (`10/10` Confirmados):** Planilla llena con margen de `4h` y radar con candidatos. Sistema en reposo operativo ($\neg p$). |
| **7** | **F** | **F** | **V** | **V** | F | F | $\neg s \land \neg t \land \neg u$ | **Quórum Completo (`10/10` Confirmados):** Planilla llena a $<3\text{h}$ sin candidatos externos. No se requiere ningún reemplazo ni alerta ($\neg p$). |
| **8** | **F** | **F** | **F** | **V** | F | F | $\neg s \land \neg t \land \neg u$ | **Quórum Completo (`10/10` Confirmados):** Planilla llena a `4h` del partido. Estado ideal de partido confirmado sin intervención agéntica. |

---

## 5. Desglose Detallado de las Dos Propuestas Agénticas y Casos Límite

### 5.1. Propuesta 1 — FRASE 1 · REGLA R1 (*MatchFinder Agent*)
> **Sentencia Oficial:** *«Si faltan jugadores y hay candidatos compatibles con la zona y el horario, el sistema propone esos candidatos al organizador.»* — **Fórmula:** $(p \land q) \rightarrow s$

- **Datos de Entrada:**
  - Planilla del partido con $n < 10$ jugadores confirmados ($p = V$).
  - Coordenadas del complejo deportivo (*La Cantera F5*) y radio de búsqueda estándar ($\le 5\text{ km}$).
  - Horario de inicio del turno (`20:00 hs`) con margen de tolerancia de llegada de $\pm 15\text{ minutos}$.
  - Padrón de jugadores comunitarios disponibles en esa franja horaria ($q = V$).
- **Acción Agéntica ($s$):**
  El agente *MatchFinder* filtra los postulantes que cumplen la doble cota (geocercanía + horario), los ordena por puntaje de asistencia/juego limpio y presenta sus fichas al capitán para que pueda invitarlos con un clic. **El agente sugiere pero no invita a espaldas del organizador.**
- **Auditoría de Casos Límite e Intervención Humana (Nivel Supera / Propone):**
  1. *Caso Borde A — Rechazo de candidatos o falta de perfiles con buena reputación en 5 km:* Si el capitán descarta a los candidatos sugeridos o el radar en $5\text{ km}$ queda vacío cuando aún faltan más de 3 horas ($p \land \neg q \land \neg r$), el agente habilita el protocolo de intervención humana: permite activar la **"Zona Extendida" (ampliando el radio de 5 km a 10 km)** y genera un **enlace temporal con código QR** para compartir la vacante en grupos externos de confianza.
  2. *Caso Borde B — Vacante de último momento con candidatos disponibles ($p \land q \land r$):* Si se baja un jugador faltando 2 horas o 30 minutos pero el radar sí tiene candidatos compatibles ($q = V$), prevalece R1 sobre R2 y se destaca la etiqueta de **"Incorporación Inmediata"** para cubrir el puesto sin entrar en pánico.

---

### 5.2. Propuesta 2 — FRASE 2 · REGLA R2 (*MatchGuard Urgency Agent*)
> **Sentencia Oficial:** *«Si faltan jugadores, quedan menos de tres horas y no hay candidatos compatibles, el sistema alerta al organizador sin cancelar el partido automáticamente.»* — **Fórmula:** $(p \land r \land \neg q) \rightarrow (t \land \neg u)$

- **Datos de Entrada:**
  - Planilla incompleta con $n < 10$ jugadores confirmados ($p = V$).
  - Cuenta regresiva del servidor en ventana crítica: $t_{\text{restante}} < 180\text{ minutos}$ ($r = V$).
  - Consulta al radar barrial ($\le 5\text{ km}$) con resultado de $0$ postulantes compatibles ($\neg q = V$).
- **Acción Agéntica Compuesta ($t \land \neg u$):**
  - **$t$ (Alerta Prioritaria):** El agente *MatchGuard Urgency* envía una notificación crítica al dispositivo del organizador con tres vías tácticas de resolución inmediata: *(1) Confirmar formato reducido 4 vs 4*, *(2) Prorratear el costo de la cancha entre los presentes*, o *(3) Solicitar jugador comodín a la recepción del predio*.
  - **$\neg u$ (Prohibición de Cancelación Automática):** El sistema mantiene blindada la reserva de la cancha, evitando la pérdida económica de la seña abonada.
- **Auditoría de Casos Límite e Intervención Humana (Nivel Supera / Propone):**
  - *Caso Borde Crítico — Silencio del organizador a $\le 45\text{ minutos}$ del inicio (`30 Minutos` en el simulador):* Si el partido está a punto de empezar y el capitán no acusó recibo de la alerta (por ejemplo, porque está viajando hacia la cancha o se quedó sin batería), el sistema ejecuta un **Escalamiento Humano en Dos Niveles** sin cancelar el turno:
    1. Dispara una **notificación espejo al Subcapitán** (el segundo jugador confirmado más antiguo de la lista) para que pueda tomar la decisión táctica.
    2. Envía un **aviso preventivo de cortesía al WhatsApp de la recepción del predio** (*La Cantera F5*) informando el quórum actual para que el encargado asista al grupo al llegar a la cancha.

---

## 6. Tecnologías y Arquitectura del Proyecto

- **HTML5 Semántico y Accesible:** Uso estructurado de `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<details>`, `<summary>` y `<footer>`, enlace de salto al contenido principal (`.skip-link`), atributos ARIA dinámicos (`aria-expanded`, `aria-label`, `role="button"`) y navegación íntegra por teclado (`Tab`, `Enter`, `Espacio`).
- **CSS3 Moderno (Custom Properties + Grid/Flexbox):** Diseño temático *"Cancha Sintética Nocturna"* con franjas de césped alternadas, líneas de cal, navbar sticky con enlaces a todas las secciones, resaltado automático de la sección visible (*scroll spy*) y menú hamburguesa accesible en tablet y celular, árboles de decisión en HTML/CSS inmunes a recortes de texto y tarjetas de alerta de alto contraste.
- **JavaScript Modular (ES6 — `src/main.js`):**
  - Función pura verificable `evaluateRules({ confirmed, minutesLeft, hasCandidates })` que evalúa en forma determinista las proposiciones $p, q, r$, los antecedentes $(p \land q)$ y $(p \land r \land \neg q)$, y los consecuentes $s, t, u$ (con $u = \text{false}$ invariante).
  - Controlador interactivo de los dos diagramas de flujo (*Ver Flujo Completo*, *Camino SÍ*, *Camino NO*) con estado accesible `aria-pressed`.
  - Motor reactivo de **La Pizarra del Capitán**: 10 camisetas clickeables para simular bajas o confirmaciones en tiempo real, selector de 4 ventanas temporales (`4h`, `3h exactas` como caso borde de desigualdad estricta $r = F$, `2h` y `30m`), interruptor del radar barrial ($\le 5\text{ km}$), visualización de la fórmula proposicional evaluada en vivo (`#agent-logic-formula`) y botón funcional para invitar e incorporar candidatos recomendados directamente a la cancha.
  - Navegación: *scroll spy* que marca en el menú la sección visible (`aria-current`), menú hamburguesa con `aria-expanded` que se cierra al elegir una sección, con `Escape` o tocando afuera, y botón *Volver arriba*.
- **Vite 6:** Empaquetador de desarrollo y construcción optimizada para producción (`dist/`).

---

## 7. Estructura del Repositorio y Secciones de la Landing

### 7.1. Estructura de Carpetas

```text
TP3-Matchdeverdad-Grupo21/
├── index.html          # Landing completa (todas las secciones)
├── src/
│   ├── style.css       # Estilos: tema "cancha nocturna", navbar, flujos, simulador, responsive
│   └── main.js         # Diagramas interactivos, Pizarra del Capitán, navbar y scroll
├── public/
│   └── logos/          # Logo oficial de la startup (S07.webp) y variante Matchdeverdad.webp
├── agentic/
│   ├── CONTEXTO.md     # Consigna, sentencias asignadas y requisitos del TP3
│   └── AUDITORIA.md    # Auditoría de la lógica y del trabajo generado por el agente
├── vite.config.js      # Configuración de Vite (servidor en puerto 3000, salida en dist/)
└── package.json        # Scripts: dev, build y preview
```

### 7.2. Secciones de la Landing (Menú de Navegación)

Cada ítem del menú lleva a su sección con desplazamiento suave y el título queda visible debajo del header fijo.

| Ítem del menú | Ancla | Contenido |
| :--- | :--- | :--- |
| Inicio | `#hero` | Presentación de Matchdeverdad y accesos rápidos a los diagramas y la pizarra. |
| Startup | `#startup` | Startup asignada, logo oficial descargable y articulación IFTS 16 – IFTS 29. |
| Reglas | `#sentencias` | Sentencias R1 y R2 desarmadas en premisas, condición y acción, más el diccionario proposicional. |
| Flujo R1 | `#propuesta-1` | Propuesta *MatchFinder* con diagrama de flujo interactivo y desplegables. |
| Flujo R2 | `#propuesta-2` | Propuesta *MatchGuard Urgency* con diagrama de flujo interactivo y desplegables. |
| Pizarra | `#simulador` | Simulador interactivo *La Pizarra del Capitán*. |
| Equipo | `#equipo` | Integrantes del Grupo 21 y sus aportes. |
| FAQ | `#faq` | Preguntas técnicas frecuentes. |

---

## 8. Instrucciones para Ejecutar el Proyecto Localmente

### Requisitos Previos
Contar con [Node.js](https://nodejs.org/) (versión 18 o superior) y `npm` instalados.

### Paso a Paso
1. **Clonar el repositorio y entrar a la carpeta del proyecto:**
   ```bash
   git clone https://github.com/GuiLeCha/TP3-Matchdeverdad-Grupo21.git
   cd TP3-Matchdeverdad-Grupo21
   ```

2. **Instalar las dependencias:**
   ```bash
   npm install
   ```

3. **Levantar el servidor de desarrollo local:**
   ```bash
   npm run dev
   ```
   Abrir en el navegador la URL que muestra la consola: `http://localhost:3000` (puerto definido en `vite.config.js`).

4. **Generar la compilación para producción:**
   ```bash
   npm run build
   ```
   Verifica que el proyecto compile con `0 errores` generando los archivos estáticos optimizados en `dist/`.

5. **Previsualizar el build de producción localmente:**
   ```bash
   npm run preview
   ```

---

## 9. Cómo Colaborar (Ramas y Pull Requests)

Para no romper lo que ya funciona, ningún cambio se sube directo a `main`. El flujo de trabajo del grupo es:

1. **Actualizar `main` antes de empezar:**
   ```bash
   git checkout main
   git pull origin main
   ```
2. **Crear una rama con un nombre descriptivo** (por ejemplo `feature/...` para mejoras o `fix/...` para correcciones):
   ```bash
   git checkout -b feature/nombre-del-cambio
   ```
3. **Hacer los cambios y verificar que compile** con `npm run build` y revisar la página con `npm run dev`.
4. **Commitear y subir la rama:**
   ```bash
   git add .
   git commit -m "feat: descripción corta del cambio"
   git push -u origin feature/nombre-del-cambio
   ```
5. **Abrir un Pull Request en GitHub** contra `main`, explicando qué se cambió y cómo probarlo.
6. **Revisión del coordinador:** Guillermo Chacon ([`@GuiLeCha`](https://github.com/GuiLeCha)) revisa el PR y, si está todo bien, lo integra a `main`. Vercel vuelve a desplegar la landing automáticamente.

---

## 10. Herramientas de IA y Evidencia de Construcción Agéntica

Siguiendo la modalidad pedagógica del TP3 (*"Construcción 100% Agéntica: ustedes dirigen, el agente construye"*), documentamos las herramientas empleadas y el proceso real de dirección e iteración del Grupo 21:

- **Entorno de Desarrollo Agéntico:** Google Antigravity (AGY IDE).
- **Modelos Utilizados en la Orquestación:** `Gemini 3.8 Flash (High)`, `Gemini 4 Argon (High)` (auditoría de lógica proposicional y documentación académica) y `Claude Sonnet 5.5 (High)` (refinamiento visual UI/UX y simulador interactivo).
- **Funciones Delegadas bajo Dirección del Grupo:**
  - Traducción de las fórmulas proposicionales de Matchdeverdad ($(p \land q) \rightarrow s$ y $(p \land r \land \neg q) \rightarrow (t \land \neg u)$) a componentes visuales y tablas de verdad.
  - Maquetación semántica en HTML5 y hojas de estilo CSS3 con estética deportiva nocturna.
  - Programación de los árboles de flujo interactivos y del simulador táctico de 10 camisetas en `src/main.js`.
  - Pruebas de compilación con Vite y verificación de accesibilidad.

### Registro de Iteración y Reprompting del Equipo (Nivel Supera / Propone)

1. **Prompt / Instrucción Inicial del Grupo:**
   > *"Necesitamos armar la landing page para la startup Matchdeverdad (Sorteo S07-A, bloque Candidatos y urgencia) con las dos sentencias asignadas, sus diagramas de flujo y una sección para probar cómo funciona."*
2. **Problemas Detectados por el Grupo en la Primera Respuesta del Agente:**
   - En la regla R2, el borrador inicial sugería cancelar automáticamente el partido cuando no había candidatos a menos de 3 horas, contradiciendo la consigna y haciendo perder la seña de la cancha.
   - Los primeros diagramas en SVG tenían textos largos que se cortaban en pantallas medianas y poca diferenciación visual entre las ramas SÍ y NO.
   - En el simulador, al dejar activo el radar de candidatos, cambiar el tiempo entre 4 horas, 2 horas y 30 minutos no actualizaba la explicación lógica, y un estilo inline (`beacon.style.background`) dejaba trabado el color del indicador luminoso tras pasar por el estado de búsqueda pasiva.
   - Faltaba explicitar la tabla de verdad formal de 8 filas que vincula el trabajo del IFTS 16 con nuestro desarrollo en el IFTS 29.
3. **Directiva de Corrección y Reprompting Aplicada por el Grupo 21:**
   > *"Aplicar estas correcciones obligatorias: 1) En R2 jamás se cancela el partido automáticamente (invariante ¬u); destacar un banner de Reserva de Cancha Protegida y sumar el protocolo de escalamiento al subcapitán y al WhatsApp del predio cuando quedan 30-45 minutos. 2) Reemplazar los SVG rígidos por árboles de flujo interactivos en HTML/CSS con pestañas para filtrar el flujo completo, el Camino SÍ y el Camino NO. 3) En el simulador ('La Pizarra del Capitán'), mostrar en vivo la evaluación de las proposiciones (p, q, r), corregir el bug del estilo inline del beacon, diferenciar el caso borde donde faltan < 3h pero SÍ hay candidatos (prevalece R1 con incorporación inmediata) y hacer que el botón 'Invitar con 1 Clic' sume realmente al refuerzo en una camiseta vacante. 4) Documentar en el README la formalización proposicional completa y la tabla de verdad de 8 estados."*
4. **Resultado Validado:**
   La aplicación resultante refleja fielmente la tabla de verdad en sus 8 combinaciones posibles, ofrece diagramas interactivos 100% legibles, permite completar el quórum en vivo invitando candidatos a la cancha y preserva el invariante de no-cancelación en todos los escenarios de urgencia.

---

## 11. Enlaces Públicos del Proyecto

- **Repositorio Público en GitHub:** [https://github.com/GuiLeCha/TP3-Matchdeverdad-Grupo21](https://github.com/GuiLeCha/TP3-Matchdeverdad-Grupo21)
- **Landing Page Desplegada en Vercel:** [https://tp3-matchdeverdad-grupo21.vercel.app/](https://tp3-matchdeverdad-grupo21.vercel.app/)

*(Ambos enlaces son públicos y de acceso directo desde cualquier navegador sin necesidad de iniciar sesión).*

