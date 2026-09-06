# Presentación IL1.1 - Introducción a LLMs y Conexiones API

## Slide 1: Título y Objetivos
**Título:** IL1.1 - Introducción a LLMs y Conexiones API  
**Subtítulo:** Fundamentos de Modelos de Lenguaje Grandes

**Objetivos:**
- Comprender los fundamentos de los LLMs
- Establecer conexiones API con diferentes proveedores
- Implementar patrones básicos de uso
- Aplicar mejores prácticas de seguridad

---

## Slide 2: ¿Qué son los LLMs?
**Título:** Fundamentos de los Modelos de Lenguaje Grandes

**Contenido:**
- **Arquitectura:** Basados en Transformers
- **Funcionamiento:** Predicción de tokens basada en contexto
- **Capacidades:** Generación, comprensión y análisis de texto
- **Proveedores principales:** OpenAI, Gemini, Anthropic, Google

**Conceptos clave:**
- Tokens, embeddings, atención
- Entrenamiento y fine-tuning

---

## Slide 3: Configuración del Entorno
**Título:** Preparación Técnica

**Variables de entorno requeridas:**
```bash
export GEMINI_BASE_URL="https://generativelanguage.googleapis.com/v1beta/openai/"
export GEMINI_API_KEY="tu_token_de_gemini"
```

**Dependencias:**
```bash
pip install openai langchain langchain-openai
```

**Mejores prácticas de seguridad:**
- Nunca hardcodear API keys
- Usar variables de entorno
- Implementar rate limiting

---

## Slide 4: Conexión Directa con API
**Título:** Notebook 1 - Gemini API

**Pasos a seguir:**
1. Configurar cliente OpenAI con base_url personalizada
2. Realizar primera llamada básica al modelo
3. Explorar parámetros: temperature, max_tokens
4. Implementar manejo de errores
5. Usar mensajes de sistema para definir comportamiento

**Código básico:**
```python
client = OpenAI(
    base_url=os.environ.get("GEMINI_BASE_URL"),
    api_key=os.environ.get("GEMINI_API_KEY")
)
```

---

## Slide 5: Framework LangChain
**Título:** Notebook 2 - LangChain Model API

**Ventajas de LangChain:**
- Interfaz unificada para múltiples proveedores
- Abstracción de complejidad
- Herramientas adicionales integradas
- Mejor para prototipado rápido

**Implementación:**
```python
llm = ChatOpenAI(
    base_url=os.getenv("OPENAI_BASE_URL"),
    api_key=os.getenv("GEMINI_API_KEY"),
    model="gpt-4o"
)
```

**Tipos de mensajes:** HumanMessage, AIMessage, SystemMessage

---

## Slide 6: Streaming en Tiempo Real
**Título:** Notebook 3 - LangChain Streaming

**¿Qué es el streaming?**
- Recibir respuesta token por token
- Mejora percepción de velocidad
- Interfaces más reactivas

**Cuándo usar streaming:**
- Respuestas largas (>100 tokens)
- Chatbots y asistentes
- Aplicaciones interactivas
- Demostraciones en vivo

**Implementación:**
```python
for chunk in llm.stream([HumanMessage(content=prompt)]):
    print(chunk.content, end="", flush=True)
```

---

## Slide 7: Gestión de Memoria
**Título:** Notebook 4 - LangChain Memory

**Tipos de memoria:**
- **ConversationBufferMemory:** Mantiene todo el historial
- **ConversationBufferWindowMemory:** Solo N mensajes recientes
- **ConversationSummaryMemory:** Resume conversaciones largas

**Cuándo usar cada tipo:**
- Buffer: Conversaciones cortas e importantes
- Window: Contexto reciente limitado
- Summary: Sesiones largas con optimización de tokens

---

## Slide 12: Casos de Uso Prácticos
**Título:** Aplicaciones Comunes

**Análisis de texto:**
- Extracción de temas principales
- Análisis de sentimiento
- Identificación de palabras clave

**Generación de contenido:**
- Artículos y documentación
- Respuestas personalizadas
- Creatividad dirigida

**Asistentes conversacionales:**
- Chatbots con memoria
- Soporte técnico automatizado
- Interfaces de usuario naturales

---

## Slide 13: Evaluación del Módulo
**Título:** Componentes de Evaluación

**Quiz teórico (8 preguntas):**
- Fundamentos de LLMs
- Conceptos de tokens y arquitectura
- Mejores prácticas de seguridad
- Comparación de enfoques

**Práctica dirigida:**
- Ejecución de los 4 notebooks
- Experimentación con parámetros
- Implementación de casos de uso

**Ejercicios adicionales:**
- Crear asistente especializado
- Optimización de tokens
- Chatbot con memoria

---

## Slide 14: Recursos y Próximos Pasos
**Título:** Continuando el Aprendizaje

**Recursos adicionales:**
- [Documentación OpenAI API](https://platform.openai.com/docs)
- [Gemini API Documentation](https://ai.google.dev/gemini-api/docs)
- [LangChain Documentation](https://python.langchain.com/docs/)
- [Transformer Architecture Paper](https://arxiv.org/abs/1706.03762)

**Próximos módulos:**
- **IL1.2:** Técnicas avanzadas de prompt engineering
- **IL1.3:** Implementación de sistemas RAG
- **IL1.4:** Evaluación y optimización de LLMs

---