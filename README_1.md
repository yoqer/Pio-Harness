# Pio 2: Pio, Pio.  🐣🐥        Framework de Agentes LLM Multicanal

## Introducción

**Pio** es un framework modular y extensible, desarrollado en Rust, que permite la interacción con agentes de lenguaje de gran tamaño (LLM) a través de múltiples canales de comunicación. Inspirado en `omp-discord-bridge` y el concepto de *harness engineering*, este proyecto busca proporcionar una plataforma robusta y segura para desplegar agentes LLM en entornos como Discord, Telegram, WhatsApp, SMS, Email y aplicaciones nativas.

## Características Principales

*   **Arquitectura Modular**: Los canales de comunicación y las herramientas se implementan como módulos opcionales, activables mediante *features* de Cargo.
*   **Soporte Multicanal**: Integración con diversas plataformas de comunicación.
    *   **Discord**: Basado en `serenity`.
    *   **Telegram**: Utilizando `Teloxide`.
    *   **WhatsApp/SMS**: Vía Twilio.
    *   **Email**: Utilizando `lettre`.
*   **Memoria Engram (Opcional)**: Un sistema de memoria persistente que almacena "engramas" (fragmentos de memoria) de las conversaciones para proporcionar contexto a largo plazo a los agentes.
*   **Ejecución Segura (Harness)**: Módulo para ejecución aislada en Docker, Kubernetes, o entornos portátiles (USB/Carpetas). Compatible con la filosofía de `Portable-AI-USB`.
*   **Soporte LLM Local/API**: Compatible con LM Studio, llama.cpp y APIs estándar (OpenAI-compatible).

## Guía de Uso e Integración

### 1. Configuración de Memoria Engram

Para habilitar la memoria engramática, activa la feature `engram`. Pio gestionará automáticamente el contexto de los últimos mensajes para cada usuario, permitiendo que el agente "recuerde" interacciones previas. Los datos se procesan en `src/core/memory.rs`.

### 2. Integración con LLMs Locales (LM Studio / llama.cpp)

Pio puede redirigir todas las consultas a un servidor local. Configura tu `.env`:

```dotenv
LOCAL_LLM_API_BASE=http://localhost:1234/v1 # Puerto por defecto de LM Studio
LOCAL_LLM_MODEL_NAME=tu-modelo-local
```

### 3. Modos de Ejecución (Harness)

Pio permite ejecutar herramientas del agente en diferentes entornos configurables en `src/harness/mod.rs`:

*   **Local**: Ejecución directa.
*   **Docker**: Aislamiento total en contenedores.
*   **Portable**: Ejecución desde una ruta específica (útil para USB o entornos aislados).

### 4. Estilo de Chat

La interfaz de chat es limpia y directa. Pio actúa como un puente inteligente que formatea las respuestas del LLM para cada plataforma específica, manteniendo el estilo de conversación natural.

## Instalación y Ejecución

1.  Clona el repositorio.
2.  Configura el archivo `.env` basándote en `.env.example`.
3.  Compila con las features deseadas:
    ```bash
    cargo build --release --features "telegram engram"
    ```
4.  Ejecuta:
    ```bash
    cargo run --release
    ```

## Referencias

[1] Teloxide: [https://github.com/teloxide/teloxide](https://github.com/teloxide/teloxide)
[2] Portable-AI-USB: [https://github.com/yoqer/IA-USB](https://github.com/yoqer/IA-USB)
[3] OMP Discord Bridge: [https://github.com/ajaxdude/omp-discord-bridge](https://github.com/ajaxdude/omp-discord-bridge)

## Licencia

MIT
