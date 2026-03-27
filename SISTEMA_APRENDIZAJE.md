# Sistema de Aprendizaje IA — WCS_Brain v9.3.1

## Fundamentos del DQN

WCS_Brain implementa un **Deep Q-Network (DQN)** adaptado para las limitaciones de Lua 5.0 en el motor de Turtle WoW 1.12.1.

## Representación del Estado

El estado del juego se codifica como un vector numérico que incluye:

| Variable | Rango | Descripción |
|---|---|---|
| hp_ratio | 0.0 – 1.0 | Porcentaje de vida del jugador |
| mana_ratio | 0.0 – 1.0 | Porcentaje de maná |
| 	arget_hp_ratio | 0.0 – 1.0 | Vida del objetivo |
| pet_hp_ratio | 0.0 – 1.0 | Vida de la mascota |
| 
um_dots_active | 0 – 8 | Dots activos en el objetivo |
| combo_chain | 0 – 10 | Cadena de acciones exitosas |
| 	hreat_level | 0 – 3 | Nivel de amenaza actual |
| mana_deficit | 0 – 1 | Urgencia de recuperación de maná |

## Acciones Disponibles

El modelo puede seleccionar entre:
1. CAST_CORRUPTION — Aplicar Corrupción
2. CAST_CURSE_OF_AGONY — Maldición de Agonía
3. CAST_SHADOW_BOLT — Rayo de las Sombras
4. CAST_LIFE_DRAIN — Drenar Vida
5. CAST_FEAR — Miedo
6. PET_ATTACK — Ordenar ataque a mascota
7. PET_SUPPORT — Escudo/soporte de mascota
8. WAIT — No actuar (cooldown)

## Función de Recompensa

`
R = (+2.0 si objetivo muere)
  + (+0.5 por cada dot aplicado exitosamente)
  + (+0.3 si mascota defiende correctamente)
  + (-1.0 si el jugador muere)
  + (-0.5 si se pierde maná en un spell fallido)
  + (-0.1 por tick en estado WAIT sin necesidad)
`

## Limitaciones Técnicas (Lua 5.0)
- No hay operaciones matriciales nativas; la red neuronal usa tablas anidadas.
- El entrenamiento ocurre entre combates (offline learning) para no impactar el FPS.
- El modelo se guarda en SavedVariables y persiste entre sesiones.