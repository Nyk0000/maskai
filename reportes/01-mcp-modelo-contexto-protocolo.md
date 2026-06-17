# MCP — Model Context Protocol
### Informe Cualitativo y Cuantitativo

**Autora:** Nykoll Ortiz Vasquez  
**Fecha:** Junio 2026  
**Categoría:** Inteligencia Artificial · Automatización · CRM  
**Versión del informe:** 1.0  

---

## Resumen Ejecutivo

El **Model Context Protocol (MCP)** es un protocolo de comunicación abierto desarrollado por Anthropic y lanzado en noviembre de 2024. Su objetivo es estandarizar la forma en que los modelos de lenguaje grande (LLMs) se conectan con herramientas externas, fuentes de datos y sistemas de terceros — eliminando la necesidad de integraciones punto a punto y permitiendo que la IA actúe directamente en aplicaciones como HubSpot, Google Drive, Notion, GitHub, entre otras.

En términos prácticos: MCP le da "llaves" al modelo de IA para que entre a tus herramientas y ejecute tareas sin que el usuario tenga que copiar, pegar ni actuar de intermediario.

---

## 1. Contexto y Origen

### 1.1 Problema que resuelve

Antes de MCP, conectar un modelo de IA a una herramienta externa requería:
- Desarrollar una integración específica (API custom) para cada combinación de modelo × herramienta
- El usuario actuar como intermediario: copiar datos de la herramienta → pegar en el chat → copiar respuesta → llevar de vuelta a la herramienta
- Las empresas de IA duplicar esfuerzo de desarrollo para conectar con cada plataforma

**El resultado:** Fragmentación, alto costo de mantenimiento y experiencias de usuario lentas e inconsistentes.

### 1.2 Lanzamiento

| Dato | Valor |
|---|---|
| Organización que lo desarrolló | Anthropic |
| Fecha de lanzamiento público | 25 de noviembre de 2024 |
| Versión inicial del protocolo | 2024-11-05 |
| Licencia | Open Source — MIT License |
| Repositorio oficial | github.com/modelcontextprotocol |
| Tipo de protocolo | Abierto (no propietario) |

### 1.3 Analogías frecuentes en la industria

- **"USB-C para la IA"** — Un conector estándar que funciona sin importar el dispositivo (la herramienta) o el cargador (el modelo de IA).
- **"LSP para modelos de IA"** — Similar al Language Server Protocol que unificó cómo los IDEs se conectan con compiladores y linters.
- **"El Infinity de Gojo (JJK)"** — El modelo no necesita filtrar cada dato manualmente; MCP lo hace de forma automática y transparente *(analogía de uso personal)*.

---

## 2. Análisis Cualitativo

### 2.1 Arquitectura del protocolo

MCP define tres roles principales:

```
┌─────────────────────────────────────────────────┐
│                    HOST                          │
│         (Ej: Claude Desktop, Cursor)            │
│                                                  │
│  ┌────────────┐       ┌────────────────────┐    │
│  │   CLIENT   │◄─────►│   MCP SERVER       │    │
│  │ (gestiona  │       │ (expone recursos:  │    │
│  │ conexión)  │       │  HubSpot, Drive,   │    │
│  └────────────┘       │  GitHub, etc.)     │    │
│                       └────────────────────┘    │
└─────────────────────────────────────────────────┘
```

| Componente | Rol | Ejemplos |
|---|---|---|
| **Host** | Aplicación que aloja el modelo de IA | Claude Desktop, Cursor, Cline, Continue |
| **Client** | Mantiene la conexión con los servidores MCP | Embebido en el Host |
| **Server** | Expone capacidades de una herramienta al modelo | HubSpot MCP, Google Drive MCP, GitHub MCP |

### 2.2 Primitivas del protocolo

MCP define tres tipos de capacidades que un servidor puede exponer:

| Primitiva | Descripción | Ejemplo práctico |
|---|---|---|
| **Resources** | Datos que el modelo puede leer | Contactos de HubSpot, archivos de Drive |
| **Tools** | Acciones que el modelo puede ejecutar | Crear deal, enviar email, editar documento |
| **Prompts** | Plantillas de instrucciones reutilizables | "Resumen de reunión", "Follow-up de ventas" |

### 2.3 Tipos de transporte

| Tipo | Descripción | Caso de uso |
|---|---|---|
| **stdio** (local) | Comunicación por entrada/salida estándar | Servidores que corren en tu misma máquina |
| **HTTP + SSE** (remoto) | Comunicación por red con Server-Sent Events | Servidores alojados en la nube |

### 2.4 Ventajas cualitativas

**Para usuarios finales:**
- Elimina el rol de "intermediario" entre la IA y las herramientas
- Lenguaje natural como única interfaz ("revisa los deals sin respuesta")
- Consistencia: el mismo modelo puede usar múltiples herramientas en un solo flujo

**Para desarrolladores:**
- Un solo servidor MCP funciona con cualquier host compatible
- Protocolo estandarizado = menos código personalizado por cliente
- Debug más sencillo: JSON-RPC 2.0 como base

**Para organizaciones:**
- Reducción de costos de integración
- Mayor velocidad de automatización
- Menor dependencia de un proveedor específico de IA (vendor lock-in)

### 2.5 Limitaciones y consideraciones

| Limitación | Descripción |
|---|---|
| **Curva de aprendizaje técnica** | Requiere configurar servidores MCP (JSON, terminal), no es plug-and-play para usuarios no técnicos |
| **Ecosistema en desarrollo** | Al ser nuevo (2024), no todas las herramientas tienen servidores MCP oficiales |
| **Privacidad en servidores remotos** | Los servidores MCP remotos tienen acceso a datos sensibles; requiere evaluación de confianza |
| **Dependencia del host** | La calidad de la experiencia depende de cuánto MCP implemente el host (Claude Desktop vs otros) |
| **Sin autenticación nativa** | La versión inicial no incluye un estándar de autenticación (en desarrollo en versiones posteriores) |

---

## 3. Análisis Cuantitativo

### 3.1 Adopción del ecosistema (al momento de publicación)

| Métrica | Valor | Fuente |
|---|---|---|
| Hosts compatibles con MCP (oficiales) | 10+ | Documentación oficial MCP |
| Servidores MCP de referencia (oficiales) | 15+ en lanzamiento | github.com/modelcontextprotocol/servers |
| Servidores comunitarios (repos públicos) | 1,000+ | Directorio mcp.so y awesome-mcp-servers |
| Herramientas integradas en lanzamiento | Brave Search, Filesystem, Git, GitHub, Google Drive, Google Maps, Memory, PostgreSQL, Slack, SQLite | Anthropic Blog |

### 3.2 Hosts y aplicaciones compatibles

| Aplicación | Tipo | Estado MCP |
|---|---|---|
| Claude Desktop | Asistente IA | ✅ Nativo (creador del protocolo) |
| Cursor | Editor de código | ✅ Integrado |
| Windsurf (Codeium) | Editor de código | ✅ Integrado |
| Cline (VS Code ext.) | Asistente de código | ✅ Integrado |
| Continue | Asistente de código | ✅ Integrado |
| Zed | Editor de código | ✅ Integrado |
| OpenAI (ChatGPT) | Asistente IA | 🔄 Adoptando (2025) |

### 3.3 Comparativa con alternativas previas

| Criterio | Integración manual (API) | Function Calling puro | MCP |
|---|---|---|---|
| **Reutilización** | Por cliente | Por modelo | Universal |
| **Esfuerzo de integración** | Alto | Medio | Bajo |
| **Interoperabilidad** | Ninguna | Limitada | Total |
| **Tipos de capacidad** | Tools only | Tools only | Resources + Tools + Prompts |
| **Estándar abierto** | No | No | Sí |
| **Datos en tiempo real** | Manual | Manual | Automático |

### 3.4 Impacto en flujos de trabajo CRM

Estimación de reducción de pasos en tareas comunes con MCP vs sin MCP:

| Tarea | Pasos sin MCP | Pasos con MCP | Reducción |
|---|---|---|---|
| Revisar deals sin respuesta | 6 pasos manuales | 1 prompt | ~83% |
| Generar reporte semanal | 8 pasos | 1 prompt | ~87% |
| Redactar follow-ups personalizados | 5 pasos por contacto | 1 prompt total | ~80% |
| Segmentar contactos por criterio | 4 pasos | 1 prompt | ~75% |

*Estimaciones basadas en flujos de trabajo observados en entornos CRM reales (HubSpot). No son datos oficiales de benchmarks publicados.*

---

## 4. Aplicación en CRM y Marketing

### 4.1 Casos de uso prioritarios

**Para CRM Specialists:**

```
Prompt: "Revisa todos los deals del pipeline con más de 7 días sin actividad y 
redacta un follow-up personalizado para cada uno basándote en la última nota."

→ MCP + HubSpot: Lee deals → Filtra por fecha → Lee notas → Genera emails
```

```
Prompt: "¿Cuáles son los 5 contactos con mayor lead score que no han sido 
contactados esta semana?"

→ MCP + HubSpot: Accede propiedades → Filtra → Devuelve lista rankeada
```

**Para Marketing:**

```
Prompt: "Arma el reporte de KPIs de campañas de este mes comparado con el 
mes anterior en un formato para presentar."

→ MCP + Google Sheets/HubSpot: Extrae datos → Compara → Formatea reporte
```

### 4.2 Herramientas CRM con servidores MCP disponibles

| Herramienta | Servidor MCP | Estado |
|---|---|---|
| HubSpot | Community MCP (via Zapier/custom) | Disponible |
| Notion | Notion MCP oficial | Disponible |
| Google Drive | Google Drive MCP (oficial) | Disponible |
| Slack | Slack MCP (oficial) | Disponible |
| GitHub | GitHub MCP (oficial) | Disponible |
| Airtable | Community MCP | Disponible |
| Salesforce | En desarrollo | Próximo |

---

## 5. Conclusiones

### 5.1 ¿Vale la pena adoptar MCP en 2026?

**Sí, con matices:**

Para **usuarios técnicos o equipos con recursos de desarrollo**: MCP representa un cambio de paradigma real. La reducción de fricción en flujos de trabajo con múltiples herramientas es inmediata y significativa.

Para **usuarios no técnicos**: La adopción depende del host. Claude Desktop hace que la curva de configuración sea manejable, pero no es trivial. El potencial está ahí; la barrera está en la configuración inicial.

### 5.2 Tendencia esperada

MCP está en el mismo punto donde estaba la nube en 2008-2010: no es la norma todavía, pero la dirección es clara. Las empresas que empiecen a construir flujos sobre este protocolo hoy tendrán ventaja operativa en 12-18 meses cuando sea estándar en la mayoría de herramientas de trabajo.

### 5.3 Recomendación práctica (nivel usuario)

1. Instalar **Claude Desktop** (gratis con plan Claude)
2. Configurar el servidor MCP de **Filesystem** (acceso a tus archivos locales) como primer paso
3. Luego agregar **Google Drive** o **Notion** según tu stack de trabajo
4. Experimentar con prompts de tareas reales antes de conectar sistemas críticos

---

## 6. Fuentes y Referencias

| # | Fuente | Tipo | URL |
|---|---|---|---|
| 1 | Anthropic — Introducing the Model Context Protocol | Blog oficial | https://www.anthropic.com/news/model-context-protocol |
| 2 | MCP Specification — Documentación oficial | Documentación técnica | https://modelcontextprotocol.io/docs |
| 3 | GitHub — modelcontextprotocol/modelcontextprotocol | Repositorio oficial | https://github.com/modelcontextprotocol/modelcontextprotocol |
| 4 | GitHub — modelcontextprotocol/servers | Servidores de referencia | https://github.com/modelcontextprotocol/servers |
| 5 | MCP.so — Directorio de servidores MCP | Directorio comunidad | https://mcp.so |
| 6 | Awesome MCP Servers (punkpeye) | Lista curada comunidad | https://github.com/punkpeye/awesome-mcp-servers |
| 7 | JSON-RPC 2.0 Specification | Estándar técnico | https://www.jsonrpc.org/specification |
| 8 | HubSpot Developer Docs | Documentación API | https://developers.hubspot.com |

---

## Notas metodológicas

- Los datos cuantitativos de adopción corresponden al período noviembre 2024 – junio 2026.
- Las estimaciones de reducción de pasos en flujos CRM son observacionales, basadas en análisis de flujos de trabajo reales, no en benchmarks controlados publicados.
- La tabla de herramientas compatibles puede variar; el ecosistema MCP evoluciona rápidamente. Se recomienda verificar el estado actualizado en el directorio oficial.
- Este informe fue elaborado como contenido educativo de divulgación, no como investigación académica formal.

---

*Elaborado por Nykoll Ortiz Vasquez — CRM Specialist & IA Educator*  
*Repositorio: github.com/nykollortiz/nykoll-ia-contenido*  
*Licencia del contenido: CC BY 4.0 — Libre uso con atribución*
