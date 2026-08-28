# TER I

## Ten III - Generation 3 - Inference Runtime

**TER I** is the standalone, local-first multimodal inference runtime built for models trained with **TenMiNaTor III** and [**TenMiNaTor III-II**](https://github.com/yoqer/TenII). It is the operational model/runtime line that succeeds the earlier Terminator I prototype and extends it for web, robotics and constrained devices without requiring a shared provider account.

TER I is not a generic deep-learning library. Its purpose is to load trained model descriptors and adapters, route inference through local or user-selected remote backends, and orchestrate text, audio, translation, realtime voice and video when the corresponding local gateway or user-owned account is configured.

## Capabilities

| Area | TER I capability |
|---|---|
| Runtime | TenIII model descriptors, LoRA/QLoRA adapters, steering and CPU/GPU resource policy |
| Local-first | Ollama, LM Studio, Kokoro, Coqui XTTS, Silero, Piper and configurable video gateways |
| User-owned accounts | Per-user encrypted providers for LLM, TTS, video, translation and Realtime |
| Channels | Web, Meta/WhatsApp, Telegram, X-compatible custom channels, SMS/Twilio, voice and video |
| Privacy | Anonymous web sessions are ephemeral; provider secrets are encrypted server-side and never returned to the browser |
| Deployment | Local API with controlled HTTPS exposure through a reverse proxy or tunnel |

## Naming and distributions

The public project and both distribution artifacts use the name **TER I**:

- GitHub source archive: `TER-I-GitHub.zip`.
- PyPI companion distribution: `ter-i`, a small installer/runtime package for the model card, CLI metadata and local deployment helpers. It is not marketed as a general-purpose neural-network library.
- Web project title: `TER I — TenIII Generation 3 Inference Runtime`.

Model weights and external provider credentials are deliberately not embedded in the distribution. Operators provide their own model files, local endpoints and third-party accounts.

## User-owned provider flow

An authenticated user can register a provider under **Configuration → Providers**. The catalog accepts categories such as `llm`, `tts`, `video`, `translation`, `realtime`, `channel` and `social`, together with an endpoint, resource identifier and optional secret. The server encrypts the secret with AES-256-GCM, isolates the record by user identity and exposes only masked metadata to the browser.

The supported account patterns include Meta/WhatsApp Business tokens and phone-number resources, Telegram bot tokens, X-compatible API endpoints, Twilio account or API-key credentials, ElevenLabs voices and private local gateways. The operator must supply credentials obtained from the relevant provider and configure webhooks separately where required.

## Local deployment

```bash
pnpm install
pnpm test
pnpm build
pnpm start
```

Copy `deploy/ENVIRONMENT_LOCAL_TEMPLATE.md` to a private environment file, generate a stable `PROVIDER_ENCRYPTION_KEY`, keep local AI gateways bound to localhost, and expose the API only through HTTPS with authentication and rate limiting.

## Validation

The consolidated checkpoint is validated with Vitest, TypeScript and a production build. The exact test count is recorded in `docs/INDEX.md` and in the latest checkpoint metadata.

## Documentation

Start with [the documentation index](docs/INDEX.md), then read the [local deployment guide](docs/GUIA_DESPLIEGUE_LOCAL_API.md), the [operational manual](docs/MANUAL_TERMINATOR_II_V3_1.md) and the [local-first provider audit](docs/AUDITORIA_LOCAL_FIRST_PROVEEDORES.md).

## Scope boundary

Persistent user memory, RAG, relational training by language and shared Warfare.net synchronization remain a separate V4 branch. TER I keeps anonymous standalone conversations ephemeral by design.
