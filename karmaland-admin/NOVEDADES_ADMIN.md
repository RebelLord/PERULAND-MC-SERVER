# ╔════════════════════════════════════════════════════════════════╗
# ║           NOVEDADES & SEGUIMIENTO — KARMALAND 5                ║
# ║                  Documento interno de Admins                   ║
# ╚════════════════════════════════════════════════════════════════╝
#
# Propósito: Registro centralizado de TODO lo que ocurre en el servidor.
# Sirve como herramienta de transparencia interna, comunicación entre admins.
#
# ────────────────────────────────────────────────────────────────
# ESTADOS DE ÍTEM
# ────────────────────────────────────────────────────────────────
#   [x]  Completado / Resuelto
#   [ ]  Pendiente / Por hacer
#   [~]  En progreso / Investigando
#   [!]  Urgente / Requiere atención inmediata
#   [?]  Sin confirmar / Necesita más info
#
# ────────────────────────────────────────────────────────────────
# CATEGORÍAS
# ────────────────────────────────────────────────────────────────
#   ## 🆕 NUEVAS CARACTERÍSTICAS Y CONTENIDO
#   ## ⚙️  CAMBIOS EN MECÁNICAS
#   ## 🌍 DIMENSIONES Y MUNDO
#   ## 🔧 CONFIGURACIÓN Y RENDIMIENTO
#   ## 🎮 AJUSTES DE JUGABILIDAD
#   ## 📦 MODS — INSTALADOS
#   ## 🔄 MODS — ACTUALIZADOS
#   ## ❌ MODS — ELIMINADOS / DESHABILITADOS
#   ## 🐛 BUGS Y ERRORES — RESUELTOS
#   ## 🔴 BUGS Y ERRORES — PENDIENTES
#   ## 💥 CRASHEOS — RESUELTOS
#   ## 🔴 CRASHEOS — PENDIENTES
#   ## 🩹 FIXES MENORES
#
# ════════════════════════════════════════════════════════════════
#                        ENTRADAS ACTIVAS
# ════════════════════════════════════════════════════════════════


---
# [2026-05-04] — Revisión inicial de balanceo y estabilidad
> **Admins** RebelLord, cracygames, WebbyPainter370
---

## 🆕 NUEVAS CARACTERÍSTICAS Y CONTENIDO

### En progreso

- [ ] Buscar mods de almacenamiento mejorado o alternativas más completas a los actuales.
      → Explorar opciones tipo `Refined Storage`, `Applied Energistics 2` u otros | 2026-05-04

### Resuelto

- [x] Integradas utilidades clave para administración desde la sección `MODS — INSTALADOS`.
      → Incluye `KubeJS` (recetas y scripts custom), `Configured` (edición de configs in-game), `Inv View` (revisión de inventarios de jugadores), `WorldEdit` (edición del mundo en juego), `Block History` (historial de bloques puestos/quitados) y otras herramientas de staff.

---

## ⚙️ CAMBIOS EN MECÁNICAS

### En progreso

- (Sin ítems en progreso de momento.)

### Resuelto

- [x] Script KubeJS `time_weather_control.js` aplicado y actualizado en servidor.
      → Ralentiza el avance del día ejecutando `time add 1` cada 4 ticks (`DAY_SPEED_DIVIDER = 4`).
      → Fuerza clima despejado de forma periódica con `weather clear 120000` cada 36000 ticks del servidor.
      → Añade salto manual de noche cuando duerme al menos el 50% de jugadores conectados (`SLEEP_PERCENTAGE = 50`).
      → Al cumplirse el porcentaje, ejecuta `time set day`, limpia clima y avisa globalmente con `tellraw`.
- [x] Script KubeJS `admin_reload.js` detectado y revisado en servidor.
      → Añade el comando `/serverreload` (permiso admin nivel 4), con cuenta regresiva de 10 segundos y avisos globales antes de ejecutar `reload`.
- [x] Script KubeJS `economy_cuy_coins_commands.js` actualizado y subido al servidor. [2026-06-02]
      → Se normalizó el formato del archivo (indentación y saltos de línea) y se reemplazó en la ruta remota `kubejs/server_scripts/economy_cuy_coins_commands.js`.
- [x] Economía de Cuy Coins migrada a flujo KubeJS más cómodo para admins. [2026-06-02]
      → Se consolidó el comando en `economy_cuy_coins_commands.js` para reemplazar la gestión previa por datapack y facilitar entrega manual.
      → Nuevo uso recomendado: `/cuy give <gold|silver|bronze> <cantidad>` con validaciones de cantidad y mensajes de ayuda (`/cuy help`).
      → Se mantienen alias antiguos (`/cuy gold`, `/cuy silver`, `/cuy bronze`) para compatibilidad.

---

## 🌍 DIMENSIONES Y MUNDO

### En progreso

- [ ] Investigar cómo crear portales a dimensiones adicionales más allá del Nether y el End.
      → Explorar mods de dimensiones custom o integraciones con portales configurables | 2026-05-04

### Resuelto

- (Sin ítems resueltos de momento.)

---

## 🔧 CONFIGURACIÓN Y RENDIMIENTO

### En progreso

- (Sin ítems en progreso de momento.)

### Resuelto

- [x] Nerf del mod `Paraglider`: límite de corazones ajustado para evitar acumulación excesiva.
      → Config aplicado: `maxHeartContainers = 10` (máximo final: 20 corazones totales) | Resuelto: 2026-05-04
- [x] Buscar cómo automatizar el reinicio del server avisando a los players con 15 minutos de antelación.
      → El Panel de WinterNode deja configurar reinicios en la sección Advanced - Schedules
      hace guardado de mundo y avisa a los jugadores de un reinicio por chat general 15 min antes, 10 mins antes, 1 min antes. | Resuelto: 2026-05-04

---

## 🎮 AJUSTES DE JUGABILIDAD

### En progreso

- [~] Revisar y mejorar la experiencia del mod `Better Combat`.
      → Ver qué opciones de config ofrece para ajustar combate, animaciones o comportamiento

### Resuelto

- [x] Script KubeJS `remove_recipes.js` aplicado para balance de progresión.
      → Eliminadas recetas con salida `minecraft:ender_pearl`.
      → Eliminadas recetas con salida `minecraft:nether_star`.
      → Eliminadas recetas con salida `minecraft:totem_of_undying`.
      → Eliminadas recetas con salida `create:potato_cannon`.
- [x] Script KubeJS `restore_stick.js` aplicado en servidor.
      → Se elimina la receta por defecto de `minecraft:stick`.
      → Se añade receta manual: `4x minecraft:stick` usando 2 tablones (`#minecraft:planks`) en columna.
- [x] Buff a jefes y mini-jefes de Cataclysm mediante Infernal Mobs.
      → En `SERVER FILES/infernalmobs.cfg`, sección `entitiesalwaysinfernal`, se marcaron en `true` las entidades equivalentes de Cataclysm para forzar variante infernal.
      → Incluye: The Prowler, The Harbinger, The Leviathan, Ancient Remnant, Maledictus, Scylla, Ender Guardian, Ender Golem, Ignis, Ignited Revenant, Clawdian, Kobolediator, Wadjet, Aptrgangr y Amethyst Crab.
- [x] Script KubeJS `custom_recipes.js` detectado y revisado en servidor.
      → Añade receta `create:compacting` para obtener `minecraft:tuff` usando `minecraft:cobblestone` + `minecraft:quartz` + 250 mB de agua.
- [x] Script KubeJS `theurgy_recipes.js` detectado y revisado en servidor.
      → Añade receta de incubación de Theurgy para obtener `minecraft:nether_star` con ingredientes alquímicos del mod.
- [x] Script KubeJS `custom_recipes.js` actualizado en servidor.
      → Mantiene receta `create:compacting` para obtener `minecraft:tuff` con `minecraft:cobblestone` + `minecraft:quartz` + agua.
      → Elimina la receta previa `create:crushing` para `minecraft:tuff` y define una nueva versión personalizada.
      → Nueva salida de trituración de `minecraft:tuff`: `minecraft:flint` (35%), `minecraft:gold_nugget` (15%), `create:copper_nugget` (20%), `create:zinc_nugget` (20%) y `minecraft:iron_nugget` (20%).

---

## 📦 MODS — INSTALADOS

- [x] `Corpse-neoforge-121.1-1.1.13`
      → Mantiene el cuerpo del jugador en el mundo al morir para recuperar el inventario
- [x] `Better Combat-neoforge-2.3.2+1.21.1`
      → Sistema de combate mejorado con animaciones y mecánicas extendidas
- [x] `Create Aeronautics-bundled-1.21.1-1.1.3`
      → Expansión de Create para construir aeronaves funcionales
- [x] `Ritchie's Projectile Library-2.1.2-mc.1.21.1` `[LIB]`
      → Librería de soporte para proyectiles (requerida por otros mods)
- [x] `Shoppy - Player Maintained Shops-1.21.1-2.2.0`
      → Sistema de tiendas gestionadas por jugadores
- [x] `Create: Big Cannons-5.11.3-mc.1.21.1`
      → Añade cañones y artillería al ecosistema de Create
- [x] `Create: Tracks-neoforge-1.21.1-1.0.1`
      → Vías y raíles avanzados para Create
- [x] `Claim-1.1.0-neoforge-1.21.1`
      → Sistema de reclamación y protección de chunks para jugadores
- [x] `KubeJS-neoforge-2101.7.2-build.363`
      → Motor de scripting para personalización de recetas, eventos y lógica del servidor
- [x] `Rhino-2101.2.7-build.81` `[API]`
      → Motor JavaScript (dependencia de KubeJS)
- [x] `Configured-neoforge-1.21.1-2.6.3`
      → Interfaz gráfica para editar configs de mods en juego
- [x] `ChocoCraft-1.21.1-neoforge-0.11.12`
      → Añade chocobos como monturas y criaturas del mundo
- [x] `FTB Backups 3-21.1.3`
      → Sistema automático de backups del mundo del servidor
- [x] `sliceanddice-forge-4.2.4`
      → Añadido como mod de contenido
- [x] `decocraft-3.0.11-1.21.1`
      → Añadido como mod de decoración
- [x] `create_structures_arise-174.47.46 Release-neoforge-1.21.1`
      → Añadido como mod de estructuras hechas del mod Create
- [x] `create_connected-1.1.16-mc1.21.1`
      → Añadido como mod de contenido del mod Create
- [x] `createdeco-2.1.3`
      → Añadido como mod de decoración y contenido del mod Create
- [x] `copycats-3.0.4+mc.1.21.1-neoforge`
      → Añadido como mod de contenido del Create
- [x] `createframed-1.21.1-1.7.3`
      → Añadido como mod de contenido y frames para el mod Create
- [x] `create_aquatic_ambitions-1.21.1-2.0.2`
      → Añadido como mod de contenido marino del Create
- [x] `deeper-oceans-2.0.0-neoforge-1.21.1` [22/05/26]
      → Añadido como mod de contenido oceánico
- [x] `underwater_village-1.0.2-neoforge-1.21.1` [22/05/26]
      → Añadido como mod de estructuras oceánicas
- [x] `seadwellers-1.0.0-neoforge-1.21.1` [22/05/26]
      → Añadido como mod de contenido marino (Realm RPG: Sea Dwellers)
- [x] `simple_tuff_recipe-1.0.0-neoforge-1.21.1` [22/05/26]
      → Añadido como mod de receta de estrato de Tova

---

## 🔄 MODS — ACTUALIZADOS

- [x] `create-aeronautics-bundled-1.21.1-1.2.1` [09/05/26]
      → Actualizado desde `Create Aeronautics-bundled-1.21.1-1.1.3`
- [x] `Sable Neoforge 1.2.1 for mc.1.21.1`
      → Actualización aplicada en servidor
- [x] `journeymap-neoforge-1.21.1-6.0.0-beta.76` [22/05/26]
      → Actualizado desde `journeymap-neoforge-1.21.1-6.0.0-beta.55`

---

## ❌ MODS — ELIMINADOS / DESHABILITADOS

- [x] `tombstone-neoforge-1.21.1-9.4.8` (Corail Tombstone)
      → Deshabilitado/Eliminado del servidor (Mod: Corpse usado en su lugar)
- [x] `Carry On` (última versión usada en el pack)
      → Deshabilitado/Eliminado del servidor (Ver sección CRASHEOS - Resueltos )
---

## 🐛 BUGS Y ERRORES

### En progreso

- (Sin ítems en progreso de momento.)

### Resuelto

- [x] El mod Reap, solo talaba árboles de minecraft vanilla, ahora ya tala por completo arboles del mod Biomes O'Plenty

---

## 💥 CRASHEOS

### En progreso

- (Sin ítems en progreso de momento.)

### Resuelto

- [x] El mod `Carry On` provocaba desconexión del servidor para todos los jugadores conectados cuando hacia sincronización con la tumba de player muerto.
      → Causa: el mod expulsaba al resto de jugadores cada vez que alguien moría. Resuelto: 2026-05-04 | Admin: RebelLord
---

## 🩹 FIXES MENORES

### En progreso

- (Sin ítems en progreso de momento.)

### Resuelto

- (Sin ítems en progreso de momento.)

---
