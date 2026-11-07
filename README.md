# Estructuras de Datos II: retos del curso

Implementaciones en JavaScript de las estructuras de datos del curso Estructuras de Datos II (Universidad Autónoma de Occidente): listas enlazadas, pilas, colas, árboles, grafos, tries y heaps. Cada reto resuelve un caso concreto, tiene pruebas con el ejecutor nativo de Node.js y una página en una aplicación React que permite operar la estructura de forma visual.

## Retos

Cada reto se desarrolló en su propia rama y luego se integró en `main`, así que todo el código está disponible en `main`.

| Tema | Qué se practica | Dónde está |
| --- | --- | --- |
| Lista enlazada simple | Reproductor que pasa canciones en orden: `append`, `peek`, `size`, `remove` y `print` | [`ejercicios/01-lista-simple`](ejercicios/01-lista-simple) (rama `01-lista-simple`) |
| Lista doblemente enlazada | Historial de navegador con atrás y adelante; recorrido en ambos sentidos | [`ejercicios/02-lista-doble`](ejercicios/02-lista-doble) (rama `02-lista-doble`) |
| Lista circular (extra) | Playlist en modo repetir: el último nodo apunta al primero | [`ejercicios/03-lista-circular`](ejercicios/03-lista-circular) (rama `03-lista-circular`) |
| Pila | Pila de libros (nombre, ISBN, autor, editorial) con `push`, `pop`, `peek`, `size` e `isEmpty` | [`ejercicios/04-pila-libros`](ejercicios/04-pila-libros) (rama `04-pila-libros`) |
| Cola | Cola de un cajero ordenada por hora de llegada (FIFO); las pruebas inyectan el generador de fechas | [`ejercicios/05-cola-cajero`](ejercicios/05-cola-cajero) (rama `05-cola-cajero`) |
| Árbol binario de búsqueda | Inserción, búsqueda y recorridos inorden, preorden y postorden | [`ejercicios/08-arbol-binario`](ejercicios/08-arbol-binario) (rama `08-arbol-binario`) |
| Árbol N-ario | Menú lateral con submenús recorrido con DFS y BFS, y búsqueda de nodos | [`ejercicios/09-arbol-nario`](ejercicios/09-arbol-nario) (rama `09-arbol-nario`) |
| Grafo no dirigido | Personas y ciudades con lista de adyacencia; consulta de quién vive en cada ciudad | [`ejercicios/10-grafo-amigos`](ejercicios/10-grafo-amigos) (rama `10-grafo-amigos`) |
| Trie y min-heap | Buscador de productos por prefijo que devuelve los K más populares con un heap de tamaño K | [`ejercicios/11-busqueda-productos`](ejercicios/11-busqueda-productos) (rama `11-busqueda-productos`) |
| Aplicación React | Una página por reto con formularios y visualización de nodos, árboles (`react-d3-tree`) y grafos (`react-d3-graph`) | [`ejercicios/04-app-react`](ejercicios/04-app-react) (rama `04-app-react`) |

Cada carpeta tiene su propio `README.md` con los archivos y la fuente del enunciado. Los números de las carpetas siguen la numeración de los retos del curso, por eso no son consecutivos.

## Stack

- Node.js 18 o superior, JavaScript con módulos CommonJS y sin dependencias para las estructuras.
- Pruebas con `node --test` (ejecutor nativo de Node.js).
- Aplicación visual: React 18.3, React Router 6, Vite 5, `react-d3-tree` y `react-d3-graph` (ver [`ejercicios/04-app-react/package.json`](ejercicios/04-app-react/package.json)).

## Cómo correrlo

Las pruebas y las demostraciones por consola no necesitan instalar nada:

```bash
npm test                 # todas las pruebas
npm run demo:1           # lista simple
npm run demo:2           # lista doble
npm run demo:3           # lista circular
npm run demo:pila
npm run demo:cola
npm run demo:arbol
npm run demo:menus
npm run demo:grafo
npm run demo:busqueda
```

Aplicación React:

```bash
cd ejercicios/04-app-react
npm install
npm run dev
```

## Integración continua

El flujo [`.github/workflows/pruebas.yml`](.github/workflows/pruebas.yml) se ejecuta en cada push y pull request hacia `main`, y también de forma manual. En Ubuntu con Node.js 22:

1. Corre `npm test` en la raíz, que ejecuta las pruebas de todos los retos.
2. Instala las dependencias de la aplicación React con `npm ci` y la compila con `npm run build`, para comprobar que las páginas siguen funcionando con las estructuras actuales.

## Decisiones técnicas

- **Las estructuras no dependen de la interfaz.** La aplicación React importa las mismas clases de cada reto (por ejemplo, `LinkedList.js` o `MotorBusqueda.js`), así que las pruebas y la pantalla usan el mismo código.
- **Pruebas sin dependencias.** `node --test` evita instalar un framework de pruebas para las estructuras.
- **Pruebas deterministas.** Donde hay aleatoriedad, como la hora de llegada en la cola del cajero, el generador se inyecta para que el resultado sea fijo.
- **Adaptadores para visualizar.** Árboles y grafos exponen `paraD3`, que convierte la estructura al formato que esperan las librerías de visualización.

## Material de estudio

- [Guías de aprendizaje](guias/README.md): método de estudio, pilas y colas, árboles, React paso a paso y Git con ramas. También están en un solo PDF: [`guias/Guias-de-aprendizaje-estructuras-de-datos.pdf`](guias/Guias-de-aprendizaje-estructuras-de-datos.pdf).
- `material-clase/`: diapositivas del curso y la hoja de referencia de Git citadas como fuente de los enunciados.

---

Hecho por [Joan Mateo Cardona](https://github.com/JoanMateo77).
