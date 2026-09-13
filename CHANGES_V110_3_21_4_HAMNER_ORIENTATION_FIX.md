# V110.3.21.4 · Hamner Orientation Fix

Parte de V110.3.21.3 y conserva:
- OpenSim Hamner Full-Body
- esqueleto interno SKEL
- FIX de la pestaña 12 en modo NPZ autónomo

## Problema corregido
En Hamner Full-Body la morfología era visualmente mejor, pero pelvis/sacro,
manos y pies podían quedar rotados o invertidos porque se utilizaban PCA o
marcos no restringidos.

## Nuevo criterio de orientación

### Pelvis / sacro
Se usa el convenio nativo OpenSim:
- +X = anterior
- +Y = superior
- +Z = derecha

Se proyecta sobre un frame SKEL construido con:
- eje medio-lateral = cadera izquierda -> cadera derecha
- eje superior = pelvis -> lumbar
- eje anterior = superior × derecha

### Pies
El frame se deriva de:
- longitudinal = calcáneo -> dedos
- vertical = talo -> tibia proyectado perpendicularmente
- medio-lateral = producto vectorial con signo bilateral consistente

Ya no se usa PCA libre para orientar el pie.

### Manos
El frame se deriva de:
- antebrazo -> mano
- plano del codo/antebrazo
- lateralidad derecha/izquierda

Ya no se usa PCA libre para orientar la mano.

### Astrágalo / retropié
Usa el mismo frame anatómico del pie para mantener continuidad con tobillo y calcáneo.

## Alcance
Sigue siendo geometría genérica OpenSim registrada a SKEL, no anatomía individual CT/RM.
