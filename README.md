# Blog de Star Wars — React + SWAPI

Blog de Star Wars en React que consume la API pública de Star Wars (SWAPI): personajes, vehículos y planetas en tarjetas con imagen, página de detalle por elemento, buscador en vivo y lista de favoritos.

Ejercicio del bootcamp Full Stack de 4Geeks Academy, completado el 21 de julio de 2026.

## Qué hace

- **Tres categorías** — Characters, Vehicles y Planets — cargadas desde `https://www.swapi.tech/api/`, con navegación lateral para cambiar entre ellas.
- **Tarjetas con imagen** de cada elemento, con botón "Learn more!" que lleva a su página de detalle.
- **Página de detalle** (`/single/:theTheme/:theId`) con la foto y todas las propiedades del elemento (excepto `created`, `edited` y `url`).
- **Buscador en vivo** en la barra superior: busca en las tres categorías a la vez desde 2 caracteres y muestra hasta 6 resultados.
- **Favoritos**: corazón en cada tarjeta, contador en la barra superior y menú desplegable para verlos y quitarlos.
- **Imágenes con respaldo**: las fotos vienen del repositorio `breatheco-de/swapi-images`; si una no existe, se muestra un marcador de posición en vez de una imagen rota.

## Stack

| Tecnología | Uso |
|-----------|-----|
| React 18.2 | Componentes y hooks |
| React Router 6 | Rutas `/` y `/single/:theTheme/:theId` |
| Context API + `useReducer` | Estado global: people, vehicles, planets, favorites |
| Vite 4 | Bundler y servidor de desarrollo |
| Bootstrap 5.3 + Font Awesome | Estilos (por CDN) |
| SWAPI (`swapi.tech`) | Datos de Star Wars |

## Cómo correrlo

Requiere Node ≥ 20.

```bash
npm install
npm run start
```

La app abre en `http://localhost:3000`.

## Estructura

```
src/
├── pages/
│   ├── Home.jsx        # Categorías, carga de datos y rejilla de tarjetas
│   └── Single.jsx      # Página de detalle de un elemento
├── components/
│   ├── Card.jsx        # Tarjeta con imagen, "Learn more!" y favorito
│   ├── Navbar.jsx      # Buscador en vivo y menú de favoritos
│   └── Footer.jsx
├── store.js            # Estado inicial y reducer (set_people, set_vehicles,
│                       # set_planets, add_favorite, remove_favorite)
├── routes.jsx          # Definición de rutas
└── main.jsx
```

## Qué demuestra

- Consumo de una API REST pública con `fetch` y `async/await`, tres endpoints en paralelo al cargar.
- Estado global con Context API + `useReducer`, con favoritos que se añaden y quitan desde dos lugares distintos (tarjeta y menú).
- Rutas dinámicas con dos parámetros (`:theTheme`, `:theId`).
- Búsqueda en vivo sobre datos ya cargados, con navegación directa al detalle.
- Manejo de imágenes que fallan con `onError` y marcador de posición.

## Notas

- El repo incluye `vercel.json`, así que está listo para desplegarse en Vercel con `vercel --prod`.
- Los favoritos viven solo en memoria: se pierden al recargar la página.
- La página `/demo` es un resto de la plantilla, sin uso en la app.
- Construido sobre la plantilla `react-hello-webapp` de 4Geeks Academy.
