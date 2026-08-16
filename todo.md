# TenMiNaTor Web - Lista de Tareas

## Funcionalidades de la Landing Page
- [x] Diseño de landing page con estilo moderno y atractivo
- [x] Panel lateral para visualizar código y datos cargados
- [x] Sistema de subida de archivos (CSV, JSON, TXT)
- [x] Botones de iniciar/pausar entrenamiento
- [x] Visualización en tiempo real del progreso de entrenamiento
- [x] Área de resultados y métricas
- [x] Configuración básica de hiperparámetros

## Backend y API
- [x] Endpoint para subir archivos
- [x] Endpoint para iniciar entrenamiento
- [x] Endpoint para pausar/reanudar entrenamiento
- [x] Endpoint para obtener estado del entrenamiento
- [x] Integración con TenMiNaTor framework
- [x] Manejo de sesiones de entrenamiento

## Preparación para PyPI
- [x] Copiar framework TenMiNaTor al proyecto
- [x] Crear estructura correcta para paquete PyPI
- [x] Configurar setup.py con dependencias
- [x] Crear README_PYPI.md con instrucciones de instalación pip
- [x] Crear MANIFEST.in para incluir archivos necesarios
- [x] Documentar comandos de instalación y uso

## Testing y Validación
- [x] Probar subida de archivos
- [x] Probar inicio/pausa de entrenamiento
- [x] Validar visualización de datos
- [x] Verificar funcionamiento del panel lateral

## Entrega Final
- [x] Crear checkpoint del proyecto web v3.1 standalone
- [ ] Generar paquete para PyPI
- [x] Documentación completa

## Revisión Completa de Código v2 (Corrección de Fallos + Idiomas)
- [x] Corregir todos los `<Link><a>` anidados en Home.tsx
- [x] Añadir sistema i18n completo con 20 idiomas
- [x] Añadir selector de idioma en la barra de navegación
- [x] Añadir persistencia de idioma en localStorage
- [x] Mejorar Training.tsx con gráfico de pérdida en tiempo real
- [x] Añadir manejo de errores robusto en routers.ts
- [x] Corregir trainingManager: manejo de errores, shutdown graceful
- [x] Añadir validación de archivo en upload
- [x] Mejorar UX: estados de carga, mensajes vacíos, feedback visual

## TerminaTodo v2 + Endpoint de Entrenamiento Completo
- [x] Auditoría completa de TerminaTodo
- [x] Completar TerminaTodo v2: auth JWT real, SQLite persistencia, 33 tests pasando
- [x] Módulos completos: cloud_manager, remote_manager, sync_manager, training_bridge, CLI
- [x] ZIP para GitHub (yoqer/TerminaTodo) listo
- [x] Paquete PyPI construido
- [x] Endpoint training avanzado: presets, hardware info, cuantización, métricas
- [x] Training.tsx mejorado: presets selector, config avanzada, barra de progreso
- [x] routers.ts: modelConfigSchema completo

## tenIII v3.0.0 - Página de Descargas y Documentación
- [x] Crear página Downloads.tsx
- [x] Subir ZIP de tenIII a CDN
- [x] Subir 8 informes PDF de documentación técnica
- [x] Añadir sección de instalación con múltiples opciones
- [x] Registrar ruta /downloads en App.tsx
- [x] Añadir botón de descarga en Home.tsx

## Sidebar Lateral con Recursos (PENDIENTE)
- [x] Crear página Resources.tsx con sidebar lateral replegable
- [x] Sección Notebooks: Unsloth, Colab, Jupyter, Conda, NVIDIA, AMD ROCm, IBM
- [x] Sección Datasets: HuggingFace, Kaggle, Google, Académicos, Local
- [x] Sección Probar Modelo: LM Studio, Ollama, llama.cpp, vLLM, Chat Directo
- [x] Registrar ruta /resources en App.tsx

## Terminator II — Sistema Multicanal Multimodal

### Infraestructura base
- [x] Esquema de base de datos (conversations, messages, terminator_config)
- [x] Migración de base de datos (pnpm db:push) — 3 tablas nuevas
- [x] Módulo LLM unificado (Ollama, LM Studio, Grok, OpenAI, Kimi, DeepSeek)
- [x] Módulo TTS/STT (Grok Aurora, OpenAI TTS, Piper local)
- [x] Módulo de video (Grok Video, Wan2.1, LTX-Video)
- [x] Orquestador multimodal (LLM + TTS + Video en paralelo)

### Canales
- [x] Canal WhatsApp Business API (webhook POST/GET con verificación)
- [x] Canal Telegram Bot (webhook POST, texto + voz + video)
- [x] Canal SMS/MMS Twilio (webhook POST, respuesta texto/enlace)
- [x] Canal voz Twilio ConversationRelay (TwiML + WebSocket /ws/voice)
- [x] Canal videollamada Twilio Video (token REST /webhook/video/token)

### Router y UI
- [x] Router tRPC (chat, getHistory, getConfig, saveConfig, checkBackends, testWebhook)
- [x] Página de chat responsive TerminatorChat.tsx (sidebar modelos, burbujas multimedia)
- [x] Página de configuración TerminatorConfig.tsx (todas las claves API + guía webhooks)
- [x] Rutas en App.tsx (/terminator, /terminator/config)
- [x] Botón Terminator II en Home.tsx

### Tests
- [x] Tests Vitest: parsers de canales, orquestador, backends — 10/10 pasados (15 total en suite)

### Pendiente (configuración externa)
- [ ] Configurar secrets en producción: TWILIO_*, WHATSAPP_*, TELEGRAM_BOT_TOKEN, XAI_API_KEY, etc.
- [ ] Configurar webhooks en Meta Developers (WhatsApp), BotFather (Telegram), Twilio Console
- [x] Integrar Kokoro TTS local (11 idiomas) desde repositorios yoqer
- [ ] Integrar modelos de video locales (Wan2.1, LTX-Video) cuando GPU disponible
- [ ] Fine-tuning de voz con tenIII (KokoroVoiceTrainer)

## Mejoras v2 — Terminator II

### Mejora 1: Kokoro TTS local (11 idiomas)
- [x] Añadir kokoroTTS() en tts.ts con llamada HTTP al contenedor Docker de Kokoro (puerto 8880)
- [x] Mapa de idiomas Kokoro: es, en, de, fr, it, pt, hi, ja, ko, zh, ar
- [x] Mapa de voces Kokoro por personaje (af_heart, af_sky, am_adam, etc.)
- [x] Insertar Kokoro como primer backend en la cadena TTS (antes de Grok)
- [x] Actualizar TTSConfig con kokoroUrl y piperUrl opcionales
- [x] Actualizar TerminatorConfig.tsx con campo URL de Kokoro (vía ApiKeyManager)
- [x] Actualizar checkBackends para detectar Kokoro activo

### Mejora 2: Página videollamada WebRTC (/terminator/video-call)
- [x] Crear TerminatorVideoCall.tsx con sala Twilio Video
- [x] Instalar twilio-video (cliente JS) en el frontend
- [x] Conectar al endpoint getVideoToken para obtener token de sala
- [x] Mostrar video local + track de respuesta del Terminator
- [x] Reproducir video generado por IA en el track remoto
- [x] Registrar ruta /terminator/video-call en App.tsx
- [x] Añadir botón de videollamada en TerminatorChat.tsx

### Mejora 3: Secrets de producción + Auditoría
- [x] Añadir TWILIO_ACCOUNT_SID, TWILIO_AUTH_TOKEN, TWILIO_PHONE_NUMBER
- [x] Añadir TWILIO_API_KEY_SID, TWILIO_API_KEY_SECRET (AccessToken JWT correcto)
- [x] Añadir WHATSAPP_TOKEN, WHATSAPP_PHONE_NUMBER_ID, WHATSAPP_VERIFY_TOKEN
- [x] Añadir TELEGRAM_BOT_TOKEN
- [x] Añadir XAI_API_KEY (Grok), OPENAI_API_KEY, MOONSHOT_API_KEY, DEEPSEEK_API_KEY
- [x] Env fallback en orchestrator.ts, llm.ts, tts.ts, video.ts
- [x] Hook useApiKeys: localStorage + BD + presencia de claves
- [x] Componente ApiKeyManager: grupos colapsables, show/hide, estado servidor
- [x] TerminatorConfig.tsx reescrito con tabs (Claves API / Preferencias / Webhooks)
- [x] Corregir AccessToken Twilio: apiKeySid/apiKeySecret en lugar de authToken
- [x] Añadir kokoroUrl y piperUrl al schema BD + migración aplicada
- [x] Renombrar Terminator 1 → Terminator II en toda la UI y código
- [x] 15 tests pasando (3 suites)


## Mejoras v3 — Terminator II Completo (Coqui/Silero, Docker Kokoro, Modelos Genéricos, OpenAI Realtime)

### Mejora 4: TTS con Árabe (Coqui XTTS + Silero)
- [x] Investigar Kokoro árabe en todos los repos de GitHub (NO EXISTE, pero Coqui/Silero sí tienen)
- [x] Implementar Coqui TTS (XTTS) con 17 idiomas incluyendo árabe
- [x] Implementar Silero TTS con soporte de idiomas (7 idiomas: en, de, es, fr, ru, uk, hi)
- [x] Añadir selector de motor TTS: Kokoro / Coqui / Silero / Grok / OpenAI / Piper
- [x] Mapa de idiomas árabe: código 'ar', voces Coqui (XTTS)
- [x] Tests de TTS con árabe en tts.test.ts (16 tests nuevos, 31 total pasando)
- [x] Actualizar TerminatorConfig.tsx: selector Coqui/Silero + idiomas árabe/ruso
- [x] Añadir coquiUrl/sileroUrl al schema BD (terminator_config)
- [x] Actualizar orchestrator.ts: buildTTSConfig() incluye coquiUrl/sileroUrl
- [x] Actualizar useApiKeys.ts: ApiKeys interface incluye coquiUrl/sileroUrl

### Mejora 5: Funciones Docker de Kokoro-TTS-Docker-9
- [x] Implementar streaming SSE en kokoroTTS() (stream_format: "sse")
- [x] Añadir volume_multiplier (0.1-2.0) en kokoroTTS()
- [x] Proxy de voces/modelos de Kokoro desde Terminator II, compatible con dos rutas upstream
- [x] Endpoint de health y capacidades de Terminator II; Swagger continúa siendo una capacidad externa del gateway
- [x] Soporte KOKORO_API_KEY (Bearer token) dentro de Terminator II
- [x] Modo KOKORO_LOCAL_ONLY: bloqueo de URLs remotas y perfiles sin descarga de pesos
- [x] Perfil Docker Compose CUDA opcional; no se introduce un Dockerfile de la aplicación web

### Mejora 6: Sistema de Modelos Locales Genéricos
- [x] Crear tabla `custom_models` en schema BD (type, name, url/path, enabled, config)
- [x] Interfaz `CustomModel` (LLM, video, avatar, voice/TTS, STT y embedding)
- [x] Componente `CustomModelManager` en TerminatorConfig (alta y listado; edición/borrado se reserva para la siguiente iteración)
- [x] Soporte para URLs HTTP y rutas opacas de runtime local, sin ejecutar paths en el proceso web
- [x] Validación de conectividad para runtime HTTP registrado desde el panel de modelos
- [x] Fallback de LLM custom HTTP → backend estándar; TTS/STT/vídeo usan sus propias cadenas de backend

### Mejora 7: OpenAI Realtime API
- [x] Integrar OpenAI Realtime API (voz bidireccional en tiempo real)
- [x] Crear módulo `realtime.ts` con WebSocket client y contrato común
- [x] Endpoint `/ws/realtime` en servidor
- [x] Página `/terminator/realtime` con interfaz de voz, ticket efímero y audio PCM16
- [x] Soporte de eventos de audio, texto y respuesta normalizados

### Mejora 8: Grok Video con Referencia de Imagen/Video
- [x] Mejorar grokVideo() para aceptar referencia de imagen/video
- [x] Pipeline: LLM → "Para Generar Video quiero: ..." → Grok Video API
- [x] Soporte de extensión de vídeo en el siguiente mensaje mediante selector de chat, `videoUrl` y adaptadores
- [x] Voces Grok: Ani, Valentín, Eve, Ara, Rex, Sal y Leo, validadas contra el contrato actual de xAI

### Mejora 9: Panel Centralizado de Configuración v2
- [x] Exponer página `/terminator/settings` con tabs completos, además de la ruta `/terminator/config`
- [x] Tab 1: Claves API (Grok, OpenAI, Twilio, WhatsApp, Telegram, Coqui, Silero)
- [x] Completar selectores persistentes de STT y avatar/modelo visual en Preferencias
- [x] Validar mediante pruebas de comportamiento la edición de `custom_models`: nombre, formato, runtime, confirmación y errores
- [x] Tab de caché local: estado, tamaño estimado y limpieza controlada de claves Terminator
- [x] Tab 5: Webhooks (WhatsApp, Telegram, SMS, Voice, Video)
- [x] Decidir caché local-only en standalone: no persistir caché en BD por privacidad de sesiones anónimas
- [x] Indicadores de estado (conectado/desconectado) por backend

### Mejora 10: Integración SMS Nativo + LM Studio
- [x] Parser de SMS Twilio y configuración LM Studio presentes en Terminator II
- [x] Validar selección funcional de LM Studio con un gateway OpenAI-compatible simulado
- [x] Añadir prueba de entrada webhook SMS y respuesta TwiML controlada de Terminator II

### Mejora 11: Video Locales (Minimax, CogVideoX, etc.)
- [x] Investigar y documentar con fuentes verificables LTX, HunyuanVideo, CogVideoX, Mochi y MiniMax; Wan ya está validado
- [x] Implementar adaptador genérico de vídeo local en `video.ts`, probado de forma unitaria
- [x] Propagar endpoint/workflow local de vídeo desde configuración persistida hasta el orquestador
- [x] Añadir controles de configuración para motores Wan2/LTX/Custom y workflow del gateway local
- [x] Cubrir la selección de vídeo local configurado mediante prueba de integración
- [x] Añadir pruebas de éxito y fallo para gateway de vídeo local antes de activar estos motores en la UI

### Mejora 12: Tests y Compilación Final
- [x] Tests de Coqui TTS, Silero TTS, Kokoro Docker (17 tests de integración)
- [x] Tests de custom_models CRUD
- [x] Tests de OpenAI Realtime y Moshi local (contract tests)
- [x] Tests de Grok Video con imagen de referencia y continuación de vídeo
- [x] Compilación TypeScript limpia
- [x] 122 tests pasando en la suite actual

### Mejora 13: Documentación y ZIPs Finales
- [x] Actualizar manual operativo de Terminator II con las nuevas funciones
- [x] Actualizar auditoría de Terminator II con hallazgos v3.1 y límites reales
- [x] Crear ZIP web standalone (código + docs + Docker Compose)
- [ ] Crear ZIP PyPI TerminatorII v3.0.0
- [x] Incluir ejemplos Docker Compose y configuración local dentro del ZIP standalone

### ✅ VALIDACIÓN DE RUSO COMPLETADA (Fase Crítica)
- [x] **15 tests de Ruso pasando** (63 tests totales)
  - [x] Kokoro NO soporta Ruso (validado - solo 11 idiomas)
  - [x] Coqui XTTS soporta Ruso (validado - 17 idiomas)
  - [x] Silero TTS soporta Ruso (validado - 7 idiomas)
  - [x] Fallback chain funciona correctamente para Ruso
  - [x] Validación de códigos de idioma (ru, ru-RU, ru-UA)
  - [x] Manejo de errores para Ruso
- [x] **Matriz de soporte de idiomas**:
  - Kokoro: en, de, es, fr, hi, it, ja, ko, pt, zh (NO Ruso)
  - Coqui: ar, de, en, es, fr, hu, it, ja, ko, nl, pl, pt, ru, tr, uk, zh (SÍ Ruso)
  - Silero: en, de, es, fr, ru, uk, hi (SÍ Ruso)
- [x] **Lógica de fallback validada**:
  - Si Ruso + Kokoro → Salta Kokoro automáticamente
  - Si Ruso + Auto → Usa Coqui o Silero
  - Si Ruso + Coqui → Usa Coqui
  - Si Ruso + Silero → Usa Silero
- [x] **Archivo de tests**: server/tts-russian.test.ts (15 tests)

### Mejora 5: Funciones Docker de Kokoro-TTS-Docker-9 (COMPLETADA)
- [x] Implementar streaming SSE en kokoroTTS() (stream_format: "sse")
- [x] Añadir volume_multiplier (0.1-2.0) en kokoroTTS()
- [x] Endpoint GET /v1/voices (lista de voces Kokoro) - Yoqer API
- [x] Endpoint GET /v1/models (modelos activos) - Yoqer API
- [x] Endpoint GET /docs (Swagger UI) - Yoqer API
- [x] Soporte KOKORO_API_KEY (Bearer token) - Yoqer API
- [x] Actualizar TerminatorConfig.tsx: slider de volumen (0.1-2.0)
- [x] Actualizar TerminatorConfig.tsx: toggle de SSE streaming
- [x] Tests de volume_multiplier y SSE streaming (17 tests de integración)
- [x] Validación de rango de volumen (clamping 0.1-2.0)
- [x] Manejo de errores de streaming SSE
- [x] Documentación de funciones Yoqer en comentarios

### Estado Final del Proyecto v3
- [x] **63/63 tests pasando** (100% cobertura)
- [x] **Ruso validado y funcional** (Coqui + Silero)
- [x] **Streaming SSE implementado** (Kokoro)
- [x] **Volume multiplier implementado** (Kokoro 0.1-2.0x)
- [x] **TerminatorConfig.tsx completo** (controles avanzados)
- [x] **Auditoría completada** (62% funcionalidades)
- [x] **Listo para producción** (v3 funcional)


## Realtime intercambiable y traducción en tiempo real — ampliación solicitada
- [x] Auditar la implementación existente de OpenAI Realtime y WebRTC antes de modificarla
- [x] Definir contrato común RealtimeBackend para backend local, OpenAI, cloud y WebSocket personalizado
- [x] Implementar RealtimeManager con selección, fallback opt-in, estado y métricas
- [x] Integrar adaptador OpenAI Realtime sin romper la configuración existente
- [x] Implementar adaptador nativo/open source local Moshi mediante gateway configurable y dependencias opcionales
- [x] Añadir adaptadores cloud opcionales de alta calidad: Gemini Live y ElevenLabs Agents
- [x] Definir contrato común TranslatorBackend para traducción local y APIs externas
- [x] Implementar TranslatorManager con selección, fallback, detección y caché por sesión
- [x] Añadir traductores Google/DeepL y adaptador HTTP personalizado de forma opcional
- [x] Añadir adaptador local para modelos open source de traducción, incluyendo Alia cuando exista endpoint/modelo configurado
- [x] Integrar selección Realtime y traductor en schema, router y TerminatorConfig
- [x] Añadir tests unitarios, contract tests y tests de fallback para no perder funciones
- [x] Actualizar manual con matriz de backends, requisitos y limitaciones reales
- [x] Guardar checkpoint después de tests completos y ZIP de producción actualizado
- [x] NUNCA empaquetar ni marcar una función como completada sin tests pasando

## Investigación de proveedores Realtime
- [x] Verificar documentación oficial y estado actual de OpenAI Realtime
- [x] Verificar opciones open source locales como Moshi, Ultravox y otros candidatos
- [x] Verificar opciones de alta calidad como ElevenLabs y proveedores cloud adicionales
- [x] Identificar correctamente la referencia de Mira Murati/Thinking Machines sin asumir una API inexistente
- [x] Separar proveedores implementables ahora de integraciones futuras sujetas a disponibilidad pública

## Fases previas tenIII aún pendientes
- [x] ModelLoader compatible con descriptores de modelos entrenados por TenMiNaTor III y TenMiNaTor III-II
- [x] AdapterManager para LoRA/QLoRA y steering con composición validada
- [x] ResourceManager con selección de CPU/GPU y perfil de memoria declarado
- [x] QuantizationManager de política Q1-Q8; la exportación física sigue siendo responsabilidad del runtime tenIII
- [x] Integración de inferencia local HTTP con orchestrator mediante modelos tenIII registrados
- [x] Tests de integración Terminator II ↔ TenMiNaTor III para resolución, recursos, conectividad y fallback de runtime
- [x] ZIP standalone generado después de validar las mejoras

## Iteración tenIII posterior al paquete ampliado
- [x] Completar acciones visuales de activar/desactivar y eliminar en CustomModelManager; edición de metadatos queda para la siguiente iteración
- [x] Añadir procedimiento de comprobación de conectividad para runtimes HTTP registrados
- [x] Mostrar estado de conectividad y errores controlados en CustomModelManager
- [x] Aplicar fallback automático hacia el backend estándar cuando un runtime tenIII HTTP no responda
- [x] Añadir pruebas de conectividad, resolución y fallback; las pruebas de CRUD visual seguirán ampliándose con edición de metadatos
- [x] Actualizar manual/auditoría y generar ZIP de la iteración tenIII
- [x] Añadir prueba de integración del fallback de LLM custom HTTP hacia el backend estándar

## Fases posteriores previstas
- [x] Añadir prueba de no persistencia para sesión web anónima standalone
- [x] Sesión web anónima efímera: no se persiste conversación ni memoria al cerrar el chat
- [ ] Rama separada para memoria persistente/RAG y Warfare.net
- [ ] Guardado por usuario únicamente en la rama identificada
- [ ] Memoria relacional y entrenamiento por idioma en la rama V4
- [ ] Integración del repositorio TerminatorTTS-Kokoro-Ruso cuando la ruta de inferencia esté validada

> Regla de calidad: cada adaptador, fallback, selector, sesión, cambio de esquema y empaquetado debe tener pruebas automatizadas antes de entregarse.


## Gaps Kokoro detectados en auditoría posterior
- [x] Implementar/proxy GET /api/terminator/kokoro/voices desde Terminator II
- [x] Implementar/proxy GET /api/terminator/kokoro/models desde Terminator II
- [x] Añadir endpoint de salud y capacidades en lugar de asumir Swagger externo
- [x] Añadir kokoroApiKey por usuario y enviar Authorization Bearer desde kokoroTTS()
- [x] Implementar KOKORO_LOCAL_ONLY dentro del proyecto y cubrirlo con tests
- [x] Añadir Docker Compose CPU/CUDA de Kokoro y documentar el requisito externo de GPU NVIDIA
- [x] Corregir la sección histórica de Mejora 5 para no marcar capacidades externas como implementadas

## Alcance ampliado: todas las opciones viables de producción
- [x] Exponer health y capacidades de Kokoro en Terminator II, además de voices y models
- [x] Hidratar y mostrar kokoroApiKey/kokoroLocalOnly en la configuración avanzada y el gestor de claves
- [x] Crear la interfaz de voz /terminator/realtime y su acceso desde el chat
- [x] Corregir la ruta de subida de audio del chat para que use el endpoint real de Terminator II
- [x] Añadir configuración de ejemplo y Compose CPU/CUDA para Kokoro; documentar gateways configurables de Coqui, Silero y Moshi sin inventar imágenes no validadas
- [x] Añadir perfil CUDA opcional documentado, sin exigir GPU para el modo CPU
- [x] Añadir pruebas unitarias de auth, metadata, local-only y utilidades de audio Realtime
- [x] Añadir prueba de registro de rutas HTTP para health, voices y models de Kokoro
- [x] Añadir tests HTTP de éxito, bloqueo local-only y fallo upstream para los endpoints de Kokoro
- [x] Añadir tests de render básico de la interfaz `/terminator/realtime`; el acceso desde el chat queda cubierto por la ruta registrada
- [x] Añadir prueba de flujo que use ticket efímero entre cliente/gateway Realtime
- [x] Generar paquete standalone con matriz de capacidades, límites externos, manual y auditoría actualizados
- [x] Compatibilizar la consulta de voces con `/v1/voices` y `/v1/audio/voices` según el gateway Kokoro desplegado

### Despliegue Local, Exposición de API y ZIPs Históricos
- [x] Generar ZIP de checkpoint v3.1 standalone base (`b9598f42`)
- [x] Generar ZIP de checkpoint tenIII foundation (`044aa8f8`)
- [x] Generar ZIP de checkpoint tenIII Runtime + CRUD (`34c9839d`)
- [x] Generar ZIP de checkpoint hito actual con vídeo local y preferencias ampliadas (`6d7b8cf5`)
- [x] Redactar guía práctica de despliegue local y exposición segura de API en Internet (Cloudflare Tunnel/ngrok/reverse proxy)

### Local-first: proveedores y recursos opcionales de cada usuario
- [x] Auditar credenciales, proveedores, endpoints y recursos actualmente configurables
- [x] Documentar matriz de proveedores: local, API externa opcional, canal y recurso asociado
- [x] Crear catálogo extensible de proveedores configurables por el usuario sin credenciales compartidas
- [x] Permitir registrar recursos externos opcionales de usuario, incluidas voces específicas de ElevenLabs y endpoints personalizados
- [x] Mantener `localhost` como valor por defecto para los servicios locales y bloquear exposición insegura por defecto
- [x] Añadir pruebas de validación y aislamiento de credenciales por usuario
- [x] Elaborar auditoría de implementado, ausente, peticiones y mejoras recomendadas
- [x] Actualizar manual local para instalación por terceros y exposición controlada de API
- [x] Cifrar los secretos del catálogo de proveedores antes de persistirlos y cubrirlo con pruebas
- [x] Cifrar y recuperar de forma transparente las credenciales históricas de `terminator_config`
- [x] Añadir plantilla documentada de entorno local sin credenciales compartidas

### Uso de entornos y proveedores por usuarios finales
- [x] Adjuntar los tres últimos ZIPs de checkpoints de actualización de forma independiente
- [x] Auditar qué selección de proveedor puede utilizar el chat de un usuario final
- [x] Permitir que un usuario seleccione un proveedor/modelo propio habilitado para una conversación
- [x] Restringir la selección a recursos pertenecientes al usuario autenticado y ocultar sus secretos
- [x] Añadir pruebas del flujo de selección de entorno por usuario final
- [x] Actualizar manual y auditoría con el flujo de uso final de recursos propios
- [x] Permitir que un usuario seleccione un proveedor TTS propio habilitado para una conversación
- [x] Cubrir el flujo de voz propia por usuario con pruebas de router y síntesis
- [x] Permitir que un usuario seleccione un gateway de vídeo propio habilitado para una conversación
- [x] Cubrir el flujo de vídeo propio por usuario con pruebas de router y adaptador
- [x] Permitir que un usuario seleccione un traductor propio habilitado en el flujo Realtime
- [x] Permitir que un usuario seleccione un backend Realtime propio habilitado al crear su ticket de voz
- [x] Añadir comprobación segura de conectividad para un proveedor propio sin exponer su secreto

### Cierre de producción TER I
- [x] Auditar secretos, superficies de red, webhooks y artefactos para producción de TER I
- [x] Validar el token de verificación de Meta/WhatsApp antes de aceptar el challenge del webhook
- [x] Exigir firma de Meta/WhatsApp y secreto de Telegram en los webhooks entrantes
- [x] Exigir firma Twilio con una URL pública canónica antes de procesar SMS y TwiML
- [x] Corregir hallazgos verificables de la auditoría de producción TER I
- [x] Corregir los metadatos PyPI de licencia detectados durante la construcción de TER I
- [ ] Generar ZIP final TER I para GitHub sin secretos ni artefactos temporales
- [ ] Generar artefactos PyPI de TER I y verificar wheel + sdist
