# Sistemas-f-sicos-interactivos-2


## Fase de investigación: 

Me llamó la atención la plataforma Strudel, no la conocía antes y me parece una herramienta interesante para experimentar.


### Experimentos

### Versión #1

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
