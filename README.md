# 🤖 SmartTicket-AI
 
> **Reingeniería del Ciclo de Vida de Requerimientos Corporativos mediante Agentes de Inteligencia Artificial**
 
[![Estado](https://img.shields.io/badge/Estado-En%20Desarrollo-yellow)](https://github.com)
[![Precisión Objetivo](https://img.shields.io/badge/Precisión%20IA-%3E95%25-brightgreen)](https://github.com)
[![Metodología](https://img.shields.io/badge/Metodología-Lean%20Six%20Sigma%20%2B%20DevOps-blue)](https://github.com)
[![Duración](https://img.shields.io/badge/Duración-8%20Semanas-orange)](https://github.com)
[![Líder](https://img.shields.io/badge/Ingeniero%20Líder-Cesar%20Rangel%20Rios-purple)](https://github.com)
 
---
 
## 📋 Tabla de Contenidos
 
1. [Descripción del Proyecto](#-1-descripción-del-proyecto)
2. [Objetivos](#-2-objetivos)
3. [Plan de Trabajo (8 Semanas)](#-3-plan-de-trabajo-8-semanas)
4. [Metodología](#-4-metodología)
5. [Equipo y Responsabilidades](#-5-equipo-y-responsabilidades)
6. [Protocolo de Pruebas](#-6-protocolo-de-pruebas)
7. [Stack Tecnológico](#-7-stack-tecnológico)
8. [Instalación y Configuración](#-8-instalación-y-configuración)
9. [Estructura del Repositorio](#-9-estructura-del-repositorio)
10. [Contribución](#-10-contribución)
---
 
## 🧠 1. Descripción del Proyecto
 
### ¿Qué es SmartTicket-AI?
 
SmartTicket-AI es una solución de automatización inteligente diseñada para **transformar radicalmente la gestión de tickets** en Centros de Servicios Compartidos (CSC). El sistema elimina la "latencia de clasificación" —el tiempo improductivo en que una solicitud permanece en cola hasta que un agente humano la lee y redirecciona manualmente— reemplazándola por un agente de IA que actúa en **milisegundos**.
 
### Problema que Resuelve
 
En el modelo operativo tradicional de los CSC, el flujo de información presenta tres cuellos de botella críticos:
 
| Problema | Impacto Medido | Solución SmartTicket |
|---|---|---|
| Clasificación manual de tickets | 2–6 horas de latencia promedio | Clasificación automática < 500 ms |
| Enrutamiento incorrecto (bounce rate) | 35–45% de tickets reasignados | Reducción del 90% con análisis de confianza |
| Escalamiento tardío de tickets críticos | Incumplimiento de SLA en ~20% de casos | Escalamiento inmediato por análisis de sentimiento |
| Procesamiento secuencial | Colapso en horas pico | Arquitectura paralela con balanceo de carga |
 
### Funciones de Ingeniería del Agente IA
 
El núcleo del sistema implementa tres módulos de procesamiento encadenados:
 
#### 🔍 Módulo 1 — Análisis Semántico e Intencional
Clasifica la **intención real** del usuario mediante transformers de NLP fine-tuned sobre el corpus histórico corporativo. Va más allá de palabras clave: entiende el contexto, el canal de entrada (correo, chat, formulario web) y el historial del cliente para determinar si la solicitud corresponde a:
- **Soporte técnico** (incidentes, errores, fallos de sistema)
- **Solicitud de servicio** (aprovisionamiento, accesos, configuraciones)
- **Consulta comercial / venta** (cotizaciones, renovaciones, upgrades)
- **Queja formal** (insatisfacción, escalamiento ejecutivo)
- **Información general** (FAQs, dudas de procedimiento)
#### 🏷️ Módulo 2 — Extracción Automatizada de Entidades (NER)
Mediante modelos de Reconocimiento de Entidades Nombradas (Named Entity Recognition), el agente identifica y estructura automáticamente:
- `ORDER_ID`: Números de orden, ticket previo o caso relacionado
- `PRODUCT_NAME`: Nombre del producto o servicio afectado
- `ERROR_CODE`: Códigos de error técnico mencionados en el mensaje
- `CUSTOMER_ID`: Identificadores de cliente en texto libre
- `DATE_RANGE`: Rangos de fechas relevantes para el SLA
- `PRIORITY_SIGNALS`: Términos como "urgente", "caído", "producción" que elevan la prioridad
#### ⚖️ Módulo 3 — Enrutamiento Dinámico Basado en Carga (Graph Routing)
Implementa un grafo dirigido donde los nodos representan agentes/técnicos con atributos de:
- **Especialidad** (vector de competencias ponderado)
- **Carga actual** (tickets activos en tiempo real)
- **Disponibilidad** (presencia, horario, SLA comprometido)
- **Historial de resolución** (tiempo promedio por categoría)
El algoritmo selecciona al técnico óptimo usando una función de costo que balancea velocidad de respuesta esperada vs. precisión de resolución, minimizando el riesgo de reasignación.
 
---
 
## 🎯 2. Objetivos
 
### Objetivo General
 
> Diseñar e implementar un ecosistema automatizado de gestión de tickets que **elimine el 100% de la clasificación manual**, optimizando el tiempo de respuesta inicial (SLA First Response Time) de horas a milisegundos, sin degradar la calidad de resolución.
 
### Objetivos Específicos
 
#### 📊 OE-1: Ingeniería de Requisitos y Taxonomía de Datos
- Auditar y categorizar el historial de solicitudes de los **últimos 24 meses** (mínimo 50,000 tickets).
- Construir una **taxonomía de datos** de al menos 5 niveles de profundidad (categoría → subcategoría → tipo → subtipo → prioridad).
- Identificar y documentar los **20 patrones más frecuentes** de solicitud para optimizar el entrenamiento supervisado.
- Definir reglas de anonimización para cumplimiento de GDPR/LFPDPPP antes de usar datos en entrenamiento.
#### 🤖 OE-2: Desarrollo y Precisión del Modelo
- Entrenar un **clasificador multiclase** con precisión (accuracy) superior al **95%** sobre el conjunto de prueba.
- Alcanzar un F1-Score mínimo de **0.93** en cada categoría principal para evitar clases desbalanceadas.
- Implementar **umbral de confianza configurable**: tickets con confianza < 80% se derivan a revisión humana en lugar de clasificarse automáticamente.
- Documentar la curva de aprendizaje y los resultados de validación cruzada (k-fold, k=10).
#### ⚙️ OE-3: Optimización de Procesos Operativos
- Reducir la tasa de **"tickets rebotados"** (incorrectly routed) en un mínimo del **90%** respecto a la línea base actual.
- Disminuir el **First Response Time (FRT)** promedio de 4 horas a menos de 30 segundos para tickets de clasificación automática.
- Lograr que el **90% de los tickets críticos** (sentimiento negativo extremo) sean escalados en menos de 60 segundos.
- Establecer un **tablero de métricas en tiempo real** (dashboard) para monitoreo continuo de KPIs operativos.
#### 🔌 OE-4: Integración Tecnológica Multi-Canal
- Desarrollar **conectores REST API** para los canales:
  - **Microsoft Outlook / Exchange**: Parsing de correos entrantes, extracción de adjuntos.
  - **WhatsApp Business API**: Ingesta de mensajes de texto e imágenes.
  - **Jira Software**: Creación, actualización y cierre de issues automático.
  - **ServiceNow** *(opcional, fase 2)*: Sincronización bidireccional.
- Garantizar que todos los conectores operen bajo esquema **OAuth 2.0** y soporten webhooks para procesamiento en tiempo real.
- Publicar documentación OpenAPI 3.0 (Swagger) para todos los endpoints desarrollados.
---
 
## 📅 3. Plan de Trabajo (8 Semanas)
 
```
SEMANA  1    2    3    4    5    6    7    8
        ├────┤
FASE I  ▓▓▓▓▓▓▓▓
FASE II           ▓▓▓▓▓▓▓▓
FASE III                   ▓▓▓▓▓▓▓▓
FASE IV                              ▓▓▓▓▓▓▓▓
```
 
### 🔬 Fase I — Diagnóstico y Extracción (Semanas 1–2)
 
**Entregables:** Informe AS-IS, Dataset limpio, Taxonomía preliminar
 
#### Semana 1 — Auditoría de Procesos (AS-IS)
- Mapeo completo del flujo actual de tickets usando notación **BPMN 2.0**.
- Medición de tiempos por etapa: recepción → lectura → clasificación → asignación → primera respuesta.
- Entrevistas con agentes clave para identificar patrones no documentados y excepciones frecuentes.
- Cálculo de la **línea base de KPIs**: FRT promedio, bounce rate, SLA compliance %, volumen diario por canal.
- Identificación de los **top 10 cuellos de botella** y su impacto económico estimado.
#### Semana 2 — Extracción y Preparación del Dataset
- Extracción de histórico de tickets desde el sistema actual (CRM/ITSM) con script ETL automatizado.
- **Limpieza de datos**: eliminación de PII (nombres, emails, teléfonos, datos bancarios) mediante técnicas de anonimización por reemplazo y hashing.
- Análisis exploratorio (EDA): distribución de categorías, longitud de texto, idiomas detectados, detección de clases desbalanceadas.
- División estratificada del dataset: **70% entrenamiento / 15% validación / 15% prueba**.
- Versionado del dataset con DVC (Data Version Control) para trazabilidad del experimento.
---
 
### 🏗️ Fase II — Diseño de Arquitectura y Modelado (Semanas 3–4)
 
**Entregables:** Diagrama TO-BE, Arquitectura de software, Contratos API
 
#### Semana 3 — Diseño del Proceso TO-BE
- Creación del nuevo mapa de procesos donde la IA gestiona el **90% de las entradas** sin intervención humana.
- Diseño de flujos de excepción: tickets de baja confianza, idiomas no soportados, adjuntos complejos.
- Definición de la **matriz de escalamiento**: criterios para derivación a nivel L2, L3 o gerencia.
- Validación del diseño con stakeholders mediante sesiones de **Design Thinking** (prototipo en papel).
#### Semana 4 — Arquitectura de Software
- Definición del stack tecnológico:
  - **Python 3.11+**: Motor de IA, pipelines NLP, APIs (FastAPI)
  - **C++ (módulo crítico)**: Pre-procesamiento de texto de alto rendimiento para garantizar < 100 ms de latencia
  - **PostgreSQL**: Almacenamiento de tickets y metadatos
  - **Redis**: Caché de modelos y gestión de colas en tiempo real
  - **Docker + Kubernetes**: Contenedores y orquestación para escalabilidad horizontal
- Diseño de los contratos de API (OpenAPI 3.0) para todos los conectores de integración.
- Definición de la estrategia de seguridad: autenticación, cifrado en tránsito (TLS 1.3) y en reposo (AES-256).
---
 
### 💻 Fase III — Desarrollo y Entrenamiento (Semanas 5–6)
 
**Entregables:** Modelo entrenado, Conectores funcionales, Reglas de negocio implementadas
 
#### Semana 5 — Entrenamiento del Modelo
- Experimentación con arquitecturas de clasificación:
  - **Baseline**: TF-IDF + Logistic Regression (referencia de velocidad)
  - **Intermedio**: FastText con embeddings pre-entrenados en español
  - **Avanzado**: Fine-tuning de `bert-base-multilingual-cased` o `roberta-base-bne` (español)
- Optimización de hiperparámetros con **Optuna** (búsqueda bayesiana).
- Registro de experimentos en **MLflow**: métricas, parámetros, artefactos de modelo.
- Implementación del módulo NER para extracción de entidades usando **spaCy** con modelo personalizado.
#### Semana 6 — Integración y Reglas de Negocio
- Desarrollo de conectores para Outlook, WhatsApp y Jira con manejo de errores robusto y reintentos exponenciales.
- Programación del **motor de reglas de negocio**:
  - Escalamiento inmediato (< 60 s) ante sentimiento de insatisfacción extrema (score VADER/BETO < -0.7)
  - Reglas de VIP: clientes estratégicos siempre a cola prioritaria
  - Reglas de compliance: tickets que mencionan términos legales/regulatorios → revisión humana obligatoria
- Implementación del **dashboard de monitoreo** en tiempo real (Grafana + Prometheus).
---
 
### 🚀 Fase IV — Pruebas, Despliegue y Control (Semanas 7–8)
 
**Entregables:** Sistema en producción, Documentación, Personal capacitado
 
#### Semana 7 — Pruebas de Aceptación (UAT)
- Ejecución del protocolo completo de pruebas (ver sección 6).
- Sesiones de UAT con **al menos 15 usuarios reales** de diferentes perfiles (agentes, supervisores, clientes).
- Corrección de defectos críticos y de alta prioridad antes del despliegue.
- Prueba de regresión para garantizar que las correcciones no introducen nuevos errores.
#### Semana 8 — Cierre, Despliegue y Capacitación
- **Despliegue Blue-Green**: migración sin downtime al entorno de producción.
- Monitoreo intensivo las primeras 72 horas post-lanzamiento con equipo de guardia.
- Entrega de documentación técnica: manual de arquitectura, runbooks operativos, guía de troubleshooting.
- **Capacitación del personal**: 2 sesiones (técnica para el equipo de IT, operativa para agentes de soporte).
- Definición del plan de mejora continua y ciclos de re-entrenamiento del modelo (mínimo cada 3 meses).
---
 
## 🛠️ 4. Metodología
 
SmartTicket-AI adopta un enfoque **metodológico híbrido** que combina rigor de ingeniería con agilidad operativa:
 
### ♻️ Lean Six Sigma — Eliminar Desperdicios
 
Se aplica el ciclo **DMAIC** (Define, Measure, Analyze, Improve, Control) para identificar y eliminar los 8 tipos de "Muda" (desperdicio) en el proceso actual:
 
| Tipo de Muda | Manifestación en el Proceso Actual | Solución SmartTicket |
|---|---|---|
| **Espera** | Ticket en cola esperando clasificación humana | Clasificación automática instantánea |
| **Sobreprocesamiento** | Agente re-lee el ticket que ya leyó el sistema | Eliminado: el agente recibe ticket ya clasificado |
| **Defectos** | Tickets asignados al técnico incorrecto | Motor de enrutamiento con 95%+ de precisión |
| **Movimiento** | Escalamiento manual entre sistemas | APIs automáticas entre plataformas |
| **Sobreproducción** | Generación de informes manuales redundantes | Dashboard automatizado en tiempo real |
 
Las métricas del proceso se controlarán mediante **Cartas de Control** (Control Charts) para detectar desviaciones estadísticamente significativas antes de que se conviertan en problemas operativos.
 
### 🔄 DevOps — Mejora Continua sin Interrupción
 
La práctica DevOps garantiza que SmartTicket-AI sea un sistema **viviente**, no un proyecto estático:
 
- **CI/CD Pipeline** (GitHub Actions): Pruebas automáticas en cada commit, despliegue automático a staging.
- **Feature Flags**: Nuevas funcionalidades activables sin redespliegue completo.
- **Model Monitoring**: Alertas automáticas cuando la precisión del modelo cae > 2% respecto al baseline (data drift detection).
- **A/B Testing**: Evaluación controlada de nuevas versiones del modelo con porcentaje del tráfico real.
- **Incident Management**: Runbooks automatizados (PagerDuty/OpsGenie) para respuesta ante incidentes en < 15 minutos.
### 🔤 NLP Pipeline — Ingeniería de Texto
 
El pipeline de procesamiento de lenguaje natural sigue un flujo estandarizado de 6 etapas:
 
```
Texto Raw
    ↓
[1] Normalización    → Minúsculas, eliminación de caracteres especiales, Unicode
    ↓
[2] Tokenización     → División en tokens (palabras/subpalabras via BPE)
    ↓
[3] Limpieza         → Stopwords, corrección ortográfica, expansión de contracciones
    ↓
[4] Vectorización    → Embeddings contextuales (transformers) o TF-IDF según módulo
    ↓
[5] Inferencia       → Clasificación + NER + Análisis de sentimiento en paralelo
    ↓
[6] Post-proceso     → Aplicación de reglas de negocio + scoring de confianza
    ↓
Ticket Estructurado (JSON) → Enrutador de Carga
```
 
---
 
## 👥 5. Equipo y Responsabilidades
 
| Rol | Nombre | Responsabilidades Clave |
|---|---|---|
| **Ingeniero Líder / Arquitecto** | Cesar Rangel Rios | Arquitectura de sistema, integración de componentes, lógica de ingeniería de procesos, decisiones técnicas de alto nivel, coordinación de equipo, presentación a stakeholders |
| **Especialista en IA / ML Engineer** | *Por asignar* | Diseño y entrenamiento del clasificador, experimentación con modelos, optimización de hiperparámetros, evaluación de performance, gestión del ciclo de vida del modelo (MLOps) |
| **Administrador de Base de Datos / Data Engineer** | *Por asignar* | Diseño del esquema de datos, pipelines ETL, seguridad y cifrado de datos sensibles, optimización de queries, backup y recuperación, cumplimiento normativo (GDPR/LFPDPPP) |
 
> **Nota:** Dependiendo del alcance final, se recomienda incorporar un **QA Engineer** dedicado para la Fase IV y un **DevOps Engineer** para la gestión del pipeline CI/CD y la infraestructura en nube.
 
### Matriz de Comunicación
 
- **Daily Standup**: 15 min diarios (lunes a viernes) para sincronización del equipo.
- **Sprint Review**: Al final de cada fase (quincenal) con presentación de avances a stakeholders.
- **Repositorio de Decisiones**: ADR (Architecture Decision Records) en `/docs/decisions/` para trazabilidad de decisiones técnicas.
---
 
## 🧪 6. Protocolo de Pruebas
 
El plan de pruebas cubre **4 dimensiones** de calidad antes del despliegue en producción:
 
### ✅ Prueba 1 — Accuracy Test (Clasificación)
 
**Objetivo:** Verificar que el modelo clasifica correctamente las intenciones de los usuarios.
 
**Métricas a evaluar:**
- **Accuracy global** ≥ 95% sobre el conjunto de prueba reservado.
- **F1-Score por clase** ≥ 0.93 para evitar que categorías minoritarias sean ignoradas.
- **Precision y Recall** desglosados por categoría en la **Matriz de Confusión** (multiclase).
- **AUC-ROC** por clase usando enfoque One-vs-Rest.
**Herramientas:** `scikit-learn` (`classification_report`, `confusion_matrix`), visualización con `seaborn`.
 
**Criterio de falla:** Si alguna categoría principal tiene F1 < 0.90, el modelo se rechaza y se requiere re-entrenamiento.
 
### 🔥 Prueba 2 — Stress Test (Carga)
 
**Objetivo:** Garantizar estabilidad del sistema bajo condiciones de uso extremo.
 
**Escenarios a simular:**
| Escenario | Volumen | Duración | Criterio de Éxito |
|---|---|---|---|
| Carga normal | 100 req/min | 30 min | Latencia p99 < 500 ms |
| Carga pico | 1,000 req/min | 15 min | Latencia p99 < 2 s, 0 errores 5xx |
| Carga de estrés | 5,000 req/min | 5 min | Degradación controlada, sin crash |
| Prueba de soak | 200 req/min | 8 horas | Sin memory leaks, CPU estable |
 
**Herramientas:** `Locust` (Python), `k6`, monitoreo en tiempo real con Grafana.
 
**Criterio de falla:** Más del 0.1% de requests con error 5xx en cualquier escenario de carga normal o pico.
 
### 💬 Prueba 3 — Sentiment Analysis Test
 
**Objetivo:** Verificar que el agente detecta correctamente el tono emocional para asignar prioridades.
 
**Casos de prueba:**
- **100 tickets de insatisfacción extrema** (muestreados de histórico real y anonimizados): deben escalar en < 60 segundos con tasa de detección ≥ 98%.
- **100 tickets neutros**: no deben generar escalamiento (false positive rate < 2%).
- **50 tickets ambiguos**: deben derivarse a revisión humana con flag `low_confidence = true`.
- **Prueba de sarcasmo e ironía** (20 casos): validación de la robustez del modelo ante lenguaje no literal.
**Herramientas:** Modelo de sentimiento `BETO` (BERT en español) o `pysentimiento` para español latinoamericano.
 
### 🤝 Prueba 4 — UAT (User Acceptance Testing)
 
**Objetivo:** Validar que el sistema cumple las expectativas operativas de los usuarios finales.
 
**Participantes:** Mínimo 15 usuarios: 5 agentes de soporte, 5 supervisores, 5 usuarios finales (clientes internos).
 
**Metodología:**
1. Escenarios guiados: el usuario sigue un script con casos predefinidos.
2. Prueba exploratoria libre: el usuario interactúa sin guión.
3. Encuesta de satisfacción post-prueba (escala Likert 1–5, objetivo ≥ 4.0/5.0).
4. Registro de defectos en Jira con clasificación por severidad (Critical / High / Medium / Low).
**Criterio de Go/No-Go:**
- ✅ Go: 0 defectos críticos, < 3 defectos altos, satisfacción ≥ 4.0/5.0.
- ❌ No-Go: cualquier defecto crítico sin resolver.
---
 
## 💻 7. Stack Tecnológico
 
```yaml
AI/ML:
  - Python 3.11+
  - Transformers (HuggingFace)
  - spaCy 3.x (NER)
  - scikit-learn (baseline models)
  - MLflow (experiment tracking)
  - Optuna (hyperparameter optimization)
 
Performance:
  - C++17 (text preprocessing module)
  - FastAPI (async REST API)
  - Redis (caching + message queue)
 
Storage:
  - PostgreSQL 15 (tickets + metadata)
  - S3-compatible storage (model artifacts)
 
Infrastructure:
  - Docker + Docker Compose
  - Kubernetes (production)
  - GitHub Actions (CI/CD)
 
Monitoring:
  - Prometheus + Grafana (metrics)
  - ELK Stack (logs)
  - Sentry (error tracking)
 
Integrations:
  - Microsoft Graph API (Outlook)
  - WhatsApp Business API (Meta)
  - Jira REST API (Atlassian)
```
 
---
 
## ⚙️ 8. Instalación y Configuración
 
### Prerrequisitos
 
```bash
# Versiones requeridas
Python >= 3.11
Node.js >= 18 (para algunas utilidades)
Docker >= 24.0
Docker Compose >= 2.20
```
 
### Configuración del Entorno
 
```bash
# 1. Clonar el repositorio
git clone https://github.com/<org>/smartticket-ai.git
cd smartticket-ai
 
# 2. Crear entorno virtual Python
python -m venv .venv
source .venv/bin/activate  # Linux/macOS
# .venv\Scripts\activate   # Windows
 
# 3. Instalar dependencias
pip install -r requirements.txt
 
# 4. Configurar variables de entorno
cp .env.example .env
# Editar .env con las credenciales necesarias
 
# 5. Levantar servicios de soporte (DB, Redis)
docker-compose up -d postgres redis
 
# 6. Ejecutar migraciones
python manage.py migrate
 
# 7. Iniciar el servidor de desarrollo
uvicorn app.main:app --reload
```
 
### Ejecución de Pruebas
 
```bash
# Pruebas unitarias
pytest tests/unit/ -v
 
# Pruebas de integración
pytest tests/integration/ -v --cov=app
 
# Prueba de carga (requiere Locust)
locust -f tests/load/locustfile.py --headless -u 100 -r 10 --run-time 5m
```
 
---
 
## 📁 9. Estructura del Repositorio
 
```
smartticket-ai/
├── 📂 app/
│   ├── api/              # Endpoints FastAPI (routers)
│   ├── core/             # Configuración, seguridad, DB
│   ├── models/           # Modelos de datos (SQLAlchemy)
│   ├── services/         # Lógica de negocio
│   │   ├── classifier/   # Motor de clasificación NLP
│   │   ├── ner/          # Extracción de entidades
│   │   ├── sentiment/    # Análisis de sentimiento
│   │   └── router/       # Enrutamiento dinámico (grafo)
│   └── connectors/       # Integraciones externas
│       ├── outlook/
│       ├── whatsapp/
│       └── jira/
├── 📂 ml/
│   ├── data/             # Scripts ETL y preparación
│   ├── training/         # Scripts de entrenamiento
│   ├── evaluation/       # Métricas y visualizaciones
│   └── models/           # Artefactos de modelo (DVC)
├── 📂 cpp_modules/       # Módulos C++ de alto rendimiento
├── 📂 tests/
│   ├── unit/
│   ├── integration/
│   └── load/
├── 📂 docs/
│   ├── api/              # OpenAPI / Swagger
│   ├── architecture/     # Diagramas y ADRs
│   └── decisions/        # Architecture Decision Records
├── 📂 infra/
│   ├── docker/
│   ├── k8s/              # Manifiestos Kubernetes
│   └── monitoring/       # Configuración Grafana/Prometheus
├── .env.example
├── docker-compose.yml
├── requirements.txt
└── README.md             ← estás aquí
```
 
---
 
## 🤝 10. Contribución
 
Este proyecto sigue el flujo de **GitFlow**:
 
- `main`: Código en producción. Solo merge desde `release/*`.
- `develop`: Rama de integración. Base para nuevas features.
- `feature/<nombre>`: Desarrollo de nuevas funcionalidades.
- `hotfix/<nombre>`: Correcciones urgentes en producción.
### Proceso de Pull Request
 
1. Crear rama desde `develop`: `git checkout -b feature/nombre-feature`
2. Hacer commits con **Conventional Commits**: `feat:`, `fix:`, `docs:`, `test:`, etc.
3. Asegurarse de que todos los tests pasen localmente.
4. Abrir PR hacia `develop` con descripción detallada y capturas si aplica.
5. Requiere aprobación de **al menos 1 reviewer** antes del merge.
---
 
## 📄 Licencia
 
Este proyecto es propiedad de la organización. Uso interno. Todos los derechos reservados.
 
---
 
<div align="center">
**SmartTicket-AI** — Desarrollado con ❤️ por el equipo de ingeniería liderado por **Cesar Rangel Rios**
 
*"De la latencia manual a la inteligencia instantánea"*
 
</div>
 
