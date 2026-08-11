# Parchís

Parchís contra la máquina, en el navegador. Sin cuenta, sin anuncios, sin servidor y sin conexión una vez cargado.

**Jugar:** https://azertida.github.io/parchis/

Para instalarlo en el móvil: ábrelo en el navegador y elige «Añadir a la pantalla de inicio». Desde ahí funciona como una aplicación normal, también en el metro.

## Las reglas de esta casa

El parchís se juega distinto en cada familia. Estas son las reglas que aplica el programa, fijadas de antemano y sin opciones:

- Un **5** saca una ficha de casa, y sacarla es obligatorio si se puede.
- Un **6** vuelve a tirar. Tres seises seguidos mandan a casa la ficha movida con el último seis.
- Con las cuatro fichas fuera, el **6 avanza 7**.
- Dos fichas del mismo color en una casilla forman una **barrera**: no pasa nadie, ni quien la ha puesto. Solo se montan en los seguros.
- Con una barrera puesta, un 6 obliga a **abrirla**.
- No se puede comer en un seguro, **salvo en una casilla de salida**.
- Comer da **20** y meter una ficha da **10**. Ambos son obligatorios; si ninguna ficha puede contar exacto, el premio se pierde.
- Hace falta el **número exacto** para llegar al centro.

Se juega con un solo dado.

## Modos y niveles

Dos formaciones: en solitario contra tres colores, o por parejas (teja y azafrán contra petróleo y oliva). En parejas, quien termina sus cuatro fichas sigue jugando con las de su compañero.

Tres niveles de máquina:

| Nivel | Cómo juega |
|---|---|
| Principiante | Al azar; solo aprovecha la mitad de las capturas. |
| Correcta | Come, mete fichas y avanza, sin mirar más allá del turno. |
| Astuta | Valora la posición resultante: cuenta las amenazas que deja detrás, monta barreras donde estorban y protege las fichas adelantadas. |

Los tres niveles se midieron jugando partidas entre ellos. Sobre 40 partidas, la astuta gana en torno al 47 % contra tres máquinas correctas, donde el azar puro daría el 25 %.

## Cómo está hecho

Una sola página. Nada de servidor, base de datos ni seguimiento; la partida en curso se guarda en `localStorage` bajo la clave `parchis_partida` y no sale del aparato.

El tablero es SVG generado por código: la corona de 68 casillas, los cuatro pasillos de 7 y la meta se construyen a partir de una rejilla de 19 × 19, así que la geometría no está dibujada a mano en ninguna parte.

Las tipografías van incrustadas en el HTML en base64, recortadas a los caracteres que la aplicación usa de verdad. No se pide ni un solo archivo a un servidor ajeno.

## Archivos

    index.html                 la aplicación entera, tipografías incluidas
    manifest.json              instalación como aplicación
    service-worker.js          caché para funcionar sin conexión
    icon-180.png               icono de iOS
    icon-192.png               icono
    icon-512.png               icono y pantalla de inicio
    icon-maskable-512.png      icono recortable de Android
    OFL.txt                    licencia de las tipografías

### Al actualizar

El service worker sirve primero lo que tiene en caché. Después de subir cambios hay que **subir el número de `VERSION`** en `service-worker.js` (`parchis-v1` → `parchis-v2`), o el navegador seguirá enseñando la versión anterior.

## Tipografías

Fraunces, Space Grotesk y Atkinson Hyperlegible, las tres bajo SIL Open Font License 1.1. Los avisos de copyright y el texto de la licencia están en `OFL.txt`.
