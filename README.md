# Electronics Lab

Plataforma abierta, **offline-first** y **local-first** de ingeniería electrónica en español que unifica:
- **Electronics Studio:** Ensamblaje físico en **Protoboard 3D (Three.js)** y **Protoboard CAD de precisión**, sincronizados en tiempo real con **Esquemático 2D** y **PCB + Ratsnest** sobre un único grafo de proyecto (`.elab` v1.0.0).
- **Simulación y Emulación Verificable:** Co-simulación ciclo-exacta **ATmega328P (`avr8js`)** + compilador nativo **`avr-gcc`** (con fallback offline integrado) acoplada a un solver no lineal **MNA + Shockley Newton-Raphson** y contrastable con **`ngspice`**.
- **Electronics Intelligence:** Asistente técnico local (funciona 100% sin IA ni red; soporta **Ollama `/api/chat`** y **`llama.cpp`** locales) + **AI Component Factory** con banco de pruebas MNA aislado antes de instalar componentes.
- **Electronics Ecosystem:** **Universal Extension System** con permisos mínimos (`network: false` por defecto) y **MCP Server (`stdio`)** + **MCP Client Hub** de primera clase.

## Inicio Rápido (100% Local)

```bash
# 1. Instalar dependencias Node
npm install

# 2. (Opcional) Instalar motores nativos C++/SPICE en Debian/Ubuntu
./scripts/install-native-engines.sh

# 3. Iniciar Electronics Lab (UI en 0.0.0.0:5173 + Daemon local en 127.0.0.1:8787)
npm run dev
```

## Verificación y Servidor MCP

```bash
npm run typecheck   # Verificación estricta TypeScript
npm test            # 13 pruebas unitarias, integración, ngspice, avr-gcc y MCP stdio E2E
npm run build       # Compilación estática de producción
npm run mcp:stdio   # Servidor Model Context Protocol local sobre stdio
```


## Aplicación de escritorio Windows y Linux

Se incluye el proyecto nativo Tauri 2 y scripts para generar un instalador NSIS .exe en Windows y paquetes .AppImage, .deb y .rpm en Linux. Consultá docs/DESKTOP_BUILD.md para compilar localmente o usar .github/workflows/build-desktop.yml en GitHub Actions. La interfaz se empaqueta desde web-bundle/.

## Hardware visual fidelity

The first CAD-grounded development board is the Arduino UNO R3 A000066. Its 3D board envelope, connector coordinates, pad layout, top copper and silkscreen reference are derived from the official EAGLE board CAD. See [`docs/HARDWARE_VISUAL_FIDELITY.md`](docs/HARDWARE_VISUAL_FIDELITY.md) for CAD provenance, attribution and the distinction between visible physical header contacts and pins currently implemented in the electrical model.
