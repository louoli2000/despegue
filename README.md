# Estación Espacial Cometa · Kiosko

Web horizontal (pensada para una pantalla táctil) con 4 pantallas:

1. **Registro de tripulante**: nombre y apellido, DNI y correo.
2. **¿Cuál de estas frases suena más a ti?** (A–D, incluye "Todavía estoy descubriendo qué me mueve").
3. **¿Qué tan claro tienes qué vas a estudiar?** (A–D).
4. **Resultado**: "¡Hola, Nombre!", su tripulación y su primera misión. Vuelve solo al registro a los 45 segundos.

Es un sitio estático: `index.html` + `assets/`, sin paso de build.

## Base de datos

Usa **la misma Google Sheet y el mismo Apps Script** que el quiz completo
(`comet-fest-quiz/google-apps-script/Code.gs`). Cada registro crea una fila en la
pestaña **Respuestas** con `Fuente = Kiosko`, correo, perfil, claridad,
tripulación y misión.

Si alguien ya terminó el test (aquí o en el quiz completo) y se registra con el
mismo DNI y el mismo primer nombre, va directo a su resultado: "¡Hola de nuevo, Nombre!".

## Cómo se calcula la tripulación

- Misión: según qué tan claro lo tiene (Radar, Órbita, Prueba de motores, Lanzamiento), igual que en el quiz completo.
- Tripulación: claridad A–B = explorar, C–D = enfocar; frases B o C = aprender haciendo, A o D = inspirarse escuchando.
  - Explorar + escuchar = **Telescopio** · Explorar + hacer = **Rover**
  - Enfocar + escuchar = **Satélite** · Enfocar + hacer = **Cohete**

Se cambia en la función `crewOf` de `index.html`.

## Ajustes rápidos (en `index.html`)

- `SHEET_URL`: URL del Apps Script (ya es la misma del quiz completo).
- `RESET_SECONDS`: segundos que el resultado queda en pantalla.

## Desplegar en Vercel

1. Crea un repositorio nuevo en GitHub y sube `index.html`, `vercel.json`, `README.md` y la carpeta `assets/`.
2. En https://vercel.com/new importa ese repositorio (Framework Preset: **Other**, sin build command).
3. Deploy.
