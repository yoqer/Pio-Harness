# Pio 3: Pio, Pio, Pio.
Framework de Agentes LLM Multicanal

## Introducción

**Pio** es un framework modular y extensible, desarrollado en Rust, que permite la interacción con agentes de lenguaje de gran tamaño (LLM) a través de múltiples canales de comunicación. Esta versión evoluciona para incluir capacidades de tiempo real, traducción avanzada y razonamiento profundo.

## Nuevas Capacidades Avanzadas

Pio ahora soporta tres modos de operación avanzados, configurables por proveedor:

1.  **Realtime (Voz/Tiempo Real)**:
    *   **Proveedores**: OpenAI Realtime API, Local (Whisper).
    *   Permite interacciones de baja latencia y procesamiento de audio.
2.  **Translate (Traducción)**:
    *   **Proveedores**: Qwen, DeepSeek, Google, Local.
    *   Optimizado para traducciones precisas y rápidas. Usa `!translate <texto>` en cualquier canal.
3.  **Reasoning (Razonamiento)**:
    *   **Proveedores**: GPT o1, GPT o3, DeepSeek-R1, Grok.
    *   Para tareas que requieren pensamiento profundo y descomposición de problemas. Usa `!reason <pregunta>`.

## Soporte Multi-Proveedor

Pio es agnóstico al proveedor. Puedes configurar diferentes modelos para diferentes tareas en tu `.env`:

*   **OpenAI**: gpt-4o, o1, o3, Realtime API.
*   **Grok**: Modelos de xAI.
*   **Gemini**: Modelos de Google.
*   **Qwen/DeepSeek/Doubao**: Modelos líderes en traducción y razonamiento.
*   **Local**: LM Studio, llama.cpp, Whisper local.

## Guía de Configuración

### Realtime y Voz
Para usar Realtime local, activa la feature `voice-local`. Pio buscará una instancia de Whisper o similar en la ruta configurada.

### Traducción y Razonamiento
Configura tus proveedores preferidos en el archivo `.env`:
```dotenv
TRANSLATE_PROVIDER=qwen
REASONING_PROVIDER=deepseek
```

## Instalación y Ejecución

```bash
# Compilar con todas las capacidades
cargo build --release --features "telegram engram realtime translate reasoning"

# Ejecutar
cargo run --release
```

## Licencia

MIT
