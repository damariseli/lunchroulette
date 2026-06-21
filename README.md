# La Ruleta del Almuerzo 🍽️

Una app web de un solo archivo para sortear, de lunes a viernes:

- **Quién cocina** ese día (Gabi o Dami), alternando día por medio. Cada vez que se gira la ruleta, se sortea al azar quién arranca el lunes.
- **Qué plato** se prepara, elegido al azar entre las especialidades de la casa (sin repetir en la misma semana).
- Un **checklist de ingredientes** por día, para marcar lo que ya tenés en la heladera/alacena.
- Un **resumen final** con Día — Chef — Plato y cuántos ingredientes tenés listos.
- Un botón **"+ Agregar plato"** para sumar nuevas especialidades sin tocar el código.
- **Recuerda el progreso entre visitas**: si cierran la página y la vuelven a abrir (en el mismo navegador), siguen viendo la misma semana sorteada y lo que ya marcaron.

No necesita instalación, build ni servidor: es un único archivo `index.html` con todo el HTML, CSS y JavaScript adentro.

## Probarlo en tu computadora

Simplemente abrí `index.html` con doble clic, o arrastralo a una pestaña del navegador.

## Subirlo a GitHub Pages

1. Creá un repositorio nuevo en GitHub (puede ser privado o público).
2. Subí el archivo `index.html` (y este `README.md` si querés) a la raíz del repositorio.
3. Entrá a **Settings → Pages** del repositorio.
4. En "Build and deployment", elegí **Deploy from a branch**, rama `main` y carpeta `/ (root)`.
5. Guardá. En un minuto te va a quedar disponible en una URL como:
   `https://tu-usuario.github.io/tu-repositorio/`

Listo, ya pueden abrirla desde el celu o la compu cada domingo para planear la semana.

## Cómo agregar o cambiar platos

**Desde la app (recomendado):** abajo de todo hay un botón **"+ Agregar plato"**. Completá el nombre y los ingredientes, le das a "Guardar plato" y queda disponible para la próxima tirada. Los platos que agreguen así se guardan en el navegador, junto con el progreso de la semana.

**Editando el código (opcional):** también podés abrir `index.html` con un editor de texto y buscar el array `DISHES`, cerca del principio del `<script>`. Cada plato es un objeto así:

```js
{ name: "Nombre del plato", ingredients: [
  "Ingrediente 1", "Ingrediente 2", "Ingrediente 3"
]},
```

Para agregar uno nuevo, copiá ese bloque, pegalo dentro del array (separado por coma) y cambiá el nombre y los ingredientes. No hay límite de cantidad de platos ni de ingredientes.

## El progreso que guarda, y dónde

La app guarda en el navegador (usando `localStorage`):
- La semana sorteada (qué chef y qué plato toca cada día).
- Los ingredientes que marcaron como disponibles.
- Los platos que agregaron con el botón "+ Agregar plato".

Importante: esto se guarda **por navegador y por dispositivo**, no en una nube compartida. Si Gabi y Dami abren la app desde sus propios celulares, cada uno va a ver su propia copia guardada — para que los dos vean exactamente lo mismo y vayan tildando juntos, conviene abrirla desde un mismo dispositivo o navegador (por ejemplo, una tablet o compu de la cocina), o que uno mire la pantalla del otro. Si más adelante quieren que el progreso se sincronice de verdad entre varios dispositivos, hace falta agregar un backend compartido (por ejemplo Firebase o Supabase) — aviso si quieren que les arme esa versión.

Al girar la ruleta de nuevo ("Volver a girar / nueva semana"), se pisa el plan guardado con uno nuevo.

## Cómo funciona el sorteo (por si quieren ajustarlo)

- **Chefs:** se elige al azar quién cocina el lunes; de ahí se alterna día por medio (esa persona cocina lunes/miércoles/viernes, la otra martes/jueves — o al revés).
- **Platos:** se mezcla la lista completa de platos (los de fábrica + los que agregaron) y se toman 5 distintos, uno por día. Si en algún momento la lista tuviera menos de 5 platos, se completa repitiendo alguno al azar.

¡Buen provecho! 👩‍🍳🧑‍🍳
