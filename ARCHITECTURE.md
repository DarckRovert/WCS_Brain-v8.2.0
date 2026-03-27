# Arquitectura de WCS_Brain v9.3.1

## Diagrama de Módulos

`mermaid
graph TD
    CORE["🧠 WCS_Brain Core (Hub Central)"]
    EVENTS["WCS_EventManager"]
    HELPERS["WCS_Helpers (Lua 5.0 Compat)"]
    RESOURCES["WCS_ResourceManager"]
    
    AI["🤖 Sistemas de IA"]
    DQN["WCS_BrainDQN (Deep Q-Network)"]
    ML["WCS_BrainML (Machine Learning)"]
    STATE["WCS_BrainState"]
    REWARD["WCS_BrainReward"]
    ACTIONS["WCS_BrainActions"]

    PET["🐺 IA de Mascotas"]
    PETAI["WCS_BrainPetAI"]
    GUARDIAN["WCS_GuardianV2"]
    EMOTIONS["WCS_BrainPetEmotions"]
    LEARNING["WCS_BrainPetLearning"]

    UI["🖥️ Interfaz de Usuario"]
    CLAN["WCS_ClanPanel (14 pestañas)"]
    HUD["WCS_BrainHUD"]
    BAR["WCS_BrainButtonBar"]
    THINKING["WCS_BrainThinkingUI"]

    INTEGRATION["🔗 Integraciones"]
    TERROR["TerrorMeter Bridge"]
    PROFILES["WCS_BrainProfiles"]
    BANK["WCS_ClanBank"]
    PVP["WCS_PvPTracker"]

    CORE --> EVENTS
    CORE --> HELPERS
    CORE --> RESOURCES
    CORE --> AI
    CORE --> PET
    CORE --> UI
    CORE --> INTEGRATION

    AI --> DQN
    AI --> ML
    AI --> STATE
    AI --> REWARD
    AI --> ACTIONS

    PET --> PETAI
    PET --> GUARDIAN
    PET --> EMOTIONS
    PET --> LEARNING

    UI --> CLAN
    UI --> HUD
    UI --> BAR
    UI --> THINKING

    INTEGRATION --> TERROR
    INTEGRATION --> PROFILES
    INTEGRATION --> BANK
    INTEGRATION --> PVP
`

## Capas del Sistema

### Capa 1: Núcleo (Core)
- WCS_Helpers.lua — Funciones de compatibilidad Lua 5.0
- WCS_EventManager.lua — Gestor centralizado de eventos con throttling
- WCS_ResourceManager.lua — Pool de recursos y gestión de memoria
- WCS_BrainCore.lua — Inicialización y orquestación principal

### Capa 2: Inteligencia Artificial
- WCS_BrainDQN.lua — Red neuronal DQN para decisiones tácticas
- WCS_BrainML.lua — Pre-procesado de datos y features
- WCS_BrainState.lua — Representación del estado del juego
- WCS_BrainReward.lua — Función de recompensa para el aprendizaje
- WCS_BrainActions.lua — Catálogo de acciones disponibles

### Capa 3: Mascotas
- WCS_BrainPetAI.lua — Motor de decisiones de mascotas
- WCS_GuardianV2.lua — Modo Guardian con comportamientos extendidos
- WCS_BrainPetEmotions.lua — Sistema de estado emocional de mascotas

### Capa 4: Interfaz
- WCS_ClanPanel.lua — Panel principal con 14 pestañas
- WCS_BrainHUD.lua — Heads-Up Display de recursos
- WCS_BrainButtonBar.lua — Barra de accesos rápidos

### Capa 5: Integraciones
- WCS_BrainTerrorMeter.lua — Bridge con TerrorMeter
- WCS_BrainIntegrations.lua — Punto de integración con ecosystem

## Flujo de Datos en Combate

1. **COMBAT_LOG_EVENT** → WCS_EventManager aplica throttle
2. → WCS_BrainState actualiza representación del mundo
3. → WCS_BrainDQN evalúa la acción óptima
4. → WCS_BrainActions ejecuta la acción seleccionada
5. → WCS_BrainReward registra resultado para aprendizaje futuro
6. → WCS_BrainTerrorMeter actualiza métricas de DPS en UI