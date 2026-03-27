# Changelog — WCS_Brain

Todas las versiones notables de WCS_Brain están documentadas aquí.
Formato basado en [Keep a Changelog](https://keepachangelog.com/es/1.0.0/).

---

## [9.3.1] — 2024-03-27 (God-Tier — Pet AI Hotfix)
### Arreglado
- Corregido bug crítico de LocalizeSpellName que impedía a las mascotas Warlock ejecutar habilidades en español.
- Fallback de doble idioma (ES/EN) implementado en WCS_BrainPetAI:ExecuteAbility.
- Race-condition de targeteo mitigada con casteo diferido (Triple-Tap 0.3s).
- PetPassiveMode forzado durante ventana de casteo para evitar interrupciones de Firebolt.

### Cambiado
- Normalización de capitalización en WCS_SpellLocalization.lua a "Sentence case".
- Prioridad de casteo: PetAction → ChatFrame /cast como fallback.

---

## [9.3.0] — 2024-03-20 (God-Tier — Ecosystem Unification)
### Añadido
- **14 pestañas** en la UI principal (Clan, IA, HUD, Grimorio, Radar, Estadísticas, PvP, Raid, Banco, Macros, Mascotas, Alertas, Perfiles, Dashboard).
- Sistema de **IA DQN** (Deep Q-Network) con aprendizaje por refuerzo.
- **Panel P2P de Banco de Clan** — seguimiento de oro sin transferencias externas.
- **WCS_BrainButtonBar** — barra de accesos rápidos flotante y configurable.
- **Integración TerrorMeter** — DPS visible directamente en la UI del Brain.
- **Sistema de Alertas** para Demonios Mayores (Infernal, Doomguard) y eventos de raid.
- **ButtonBar** con 8 slots configurables y persistencia entre sesiones.
- Soporte multiidioma (ES/EN) en toda la UI.

### Cambiado
- Refactorización completa del sistema de eventos con throttling inteligente.
- Optimización de memoria: reducción del 40% en uso de RAM en combate.
- unpack() reemplazado por iteración manual para compatibilidad Lua 5.0.

### Arreglado
- Corrección de 
il parent en frames del panel de Trading.
- Corrección del sistema de Perfiles al cambiar de personaje.

---

## [9.2.0] — 2024-02-15
### Añadido
- **WCS_BrainPetAI** — IA de mascotas con 8 estados de comportamiento.
- **WCS_Grimoire** — base de conocimiento de hechizos y rotaciones Warlock.
- **WCS_PvPTracker** — historial de PvP y honor del clan.

### Cambiado
- Arquitectura modular: separación en módulos independientes con auto-detección.

---

## [9.1.0] — 2024-01-10
### Añadido
- **WCS_RaidManager** — organización de grupos y roles de raid.
- **WCS_ClanBank** — primer prototipo del banco de clan.
- Sistema de Perfiles mejorado con exportación.

---

## [9.0.0] — 2023-12-01 (God-Tier Init)
### Añadido
- Reescritura total del núcleo desde v8.x.
- Motor de IA basado en simulación (WCS_BrainSim, WCS_BrainML).
- Panel unificado de 10 pestañas (versión inicial).
- Compatibilidad declarada con Turtle WoW 1.12.1 / Lua 5.0.

---

## [8.x] — Versiones Legadas
Las versiones 8.x y anteriores han sido archivadas. Ver historial de git para detalles.