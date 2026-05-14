# Voltbike — Propuesta comercial

Sitio estático de una sola página usado como soporte visual para una llamada de ventas con Voltbike. HTML/CSS/JS planos, sin frameworks, sin build step. Se sirve detrás de nginx desde una imagen Docker liviana.

## Estructura

```
.
├── index.html        # Página única (10 secciones)
├── styles.css        # CSS custom, responsive, scroll-reveal
├── script.js         # IntersectionObserver + barra de progreso
├── Dockerfile        # nginx:alpine sirviendo estáticos en :80
├── .dockerignore
├── .gitignore
└── README.md
```

## Correr local (sin Docker)

Abrir `index.html` con doble click, o levantar un server estático:

```bash
# opción 1: Python
python -m http.server 8080

# opción 2: Node
npx serve .
```

Y abrir `http://localhost:8080`.

## Buildear y correr con Docker

```bash
# Build
docker build -t voltbike-propuesta .

# Run
docker run --rm -p 8080:80 voltbike-propuesta
```

Y abrir `http://localhost:8080`.

## Deploy en Easypanel

1. En Easypanel, crear un nuevo servicio tipo **App**.
2. Conectar al repo `mateomorbi19-maker/volt`, rama `main`.
3. Build method: **Dockerfile** (el Dockerfile está en la raíz).
4. Puerto interno: **80**.
5. Asignar el dominio que quieras y darle deploy.

Sin variables de entorno. Sin dependencias externas. La imagen es 100% portable.
