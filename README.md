# Sistemas-f-sicos-interactivos-2


## Fase de investigación: 

## Exploración de audio:

Me llamó la atención la plataforma Strudel, no la conocía antes y me parece una herramienta interesante para experimentar.


### Experimentos


### Versión 1

```js
const ratchet = register('ratchet', (pat) => pat.sometimes(ply(2)))

setcpm(24.5)

//piano
$: s("bd*10")
  .note("c2 c2 c4 c2 g2 g2 g1 g2 c2 c4 c2")
  .gain(1)
  .sound("gm_epiano1")
  

//kick

$: s("bd*6")
  .gain(1)
  .sound("ajkpercusyn_bd")
  .note("c4 c6 c4 c2 c2")
  .speed("[1 1 0.8 1]*3")

//Claps

$: s("~ ~ cp ~ ~ ~ cp ~")
  .sound("rm50_cp")
  .gain(0.45)

```


### Versión #2

```js
const ratchet = register('ratchet', (pat) => pat.sometimes(ply(2)))

setcpm(24.5)

// Piano
$: note("c2 ~ e2 ~ g2 ~ e2 ~")
  .s("gm_epiano1")
  .gain(0.8)
  .slow(2)
  .room(0.3)

// Kick
$: s("bd ~ ~ ~ bd ~ ~ ~")
  .sound("ajkpercusyn_bd")
  .gain(0.8)

// Clap
$: s("~ ~ cp ~ ~ ~ cp ~")
  .sound("rm50_cp")
  .gain(0.45)

// Hi-Hat
$: s("~ hh ~ hh ~ hh ~ hh")
  .gain(0.18)
  .speed(0.95)

// Bajo
$: note("c2 ~ g1 ~")
  .s("gm_fingerbass")
  .gain(0.55)
  .slow(2)

// Pad
$: note("<c4 e4 g4>")
  .s("gm_pad2warm")
  .gain(0.25)
  .slow(8)
  .room(0.9)
  .size(0.95)

// Melodía
$: note("e5 ~ g5 ~ c6 ~ g5 ~")
  .s("gm_musicbox")
  .gain(0.3)
  .slow(2)
  .room(0.5)
 
 ```

### Versión final

```js
const ratchet = register('ratchet', (pat) => pat.sometimes(ply(2)))

setcpm(24.5)

// Piano
$: note("c2 ~ e2 ~ g2 ~ e2 ~")
  .s("gm_epiano1")
  .gain(0.8)
  .slow(2)
  .room(0.3)

// Kick
$: s("bd ~ ~ ~ bd ~ ~ ~")
  .sound("ajkpercusyn_bd")
  .gain(0.8)

// Clap
$: s("~ ~ cp ~ ~ ~ cp ~")
  .sound("rm50_cp")
  .gain(0.45)
  .lpf(slider (2000,200,2800))

// Hi-Hat
$: s("~ hh ~ hh ~ hh ~ hh")
  .gain(0.18)
  .speed(0.95)

// Bajo
$: note("c2 ~ g1 ~")
  .s("gm_fingerbass")
  .gain(0.55)
  .slow(2)

// Pad
$: note("<c4 e4 g4>")
  .s("gm_pad2warm")
  .gain(0.25)
  .slow(8)
  .room(0.9)
  .size(0.95)

// Melodía
$: note("e5 ~ g5 ~ c6 ~ g5 ~")
  .s("gm_musicbox")
  .gain(0.3)
  .slow(2)
  .room(0.5)
```

## Exploración de obra generativa:

- **1. Intención: ¿Qué transformación, sensación o idea debe experimentar el espectador?**
Quiero que el espectador sienta tranquilidad y serenidad con mi obra, pero a su vez esté expectante de lo que seguirá.

- **2. Entidades: ¿Qué elementos existen en el mundo del sistema? Partículas, campos, cuerpos, señales, memorias, trazos, superficies, agentes.**

  
- **3. Relaciones: ¿Cómo se afectan mutuamente? Atracción, repulsión, contagio, acumulación, erosión, cooperación, competencia.**

  
- **4. Entradas: ¿Qué alimenta al sistema? Audio, cuerpo, sensores, tiempo, datos, decisiones del participante.**

  
- **5. Reglas: ¿Cómo se transforma el estado del sistema?**

  
- **6. Invariantes: ¿Qué no puede cambiar sin que la propuesta pierda identidad? Paleta de colores, densidad, ritmo, lenguaje de movimiento, composición, comportamiento.**


- **7. Variabilidad: ¿Qué debería ser diferente en cada ejecución? Rutas, agrupaciones, tiempos internos, texturas, conexiones, detalles.**

  
- **8. Curaduría y reflexión: ¿Qué resultados son significativos y cuáles son solamente accidentes interesantes?**

## Código adaptado para TouchDesigner:

```js

const { visualid } = createParams('visualid')
const ratchet = register('ratchet', (pat) => pat.sometimes(ply(2)))

setcpm(24.5)

// Piano
const harmony = note("c2 ~ e2 ~ g2 ~ e2 ~")
  .s("gm_epiano1")
  .gain(0.8)
  .slow(2)
  .room(0.3)
  .visualid("harmony")

// Kick
const drum_bd = s("bd ~ ~ ~ bd ~ ~ ~")
  .sound("ajkpercusyn_bd")
  .gain(0.8)
  .visualid("drum_bd")

// Clap
const drum_cp = s("~ ~ cp ~ ~ ~ cp ~")
  .sound("rm50_cp")
  .gain(0.45)
  .lpf(slider (1645.6,200,2800))
  .visualid("drum_cp")

// Hi-Hat
const drum_hh = s("~ hh ~ hh ~ hh ~ hh")
  .gain(0.18)
  .speed(0.95)
  .visualid("drum_hh")

// Bajo
const drum_oh = note("c2 ~ g1 ~")
  .s("gm_fingerbass")
  .gain(0.55)
  .slow(2)
  .visualid("drum_oh")

// Pad
const melody = note("<c4 e4 g4>")
  .s("gm_pad2warm")
  .gain(0.25)
  .slow(8)
  .room(0.9)
  .size(0.95)
  .visualid("melody")

// Melodía
$: note("e5 ~ g5 ~ c6 ~ g5 ~")
  .s("gm_musicbox")
  .gain(0.3)
  .slow(2)
  .room(0.5)
  .visualid("melody")

$:stack(

harmony,
harmony.osc(),

drum_bd,
drum_bd.osc(),

drum_cp,
drum_cp.osc(),

drum_hh,
drum_hh.osc(),

drum_oh,
drum_oh.osc(),

melody,
melody.osc()    
)
```
