# Plan: World Cup 2026 Predictor

## 1. Tech Stack

| Capa         | Tecnología                          |
| ------------ | ----------------------------------- |
| Framework    | Vue 3 (Composition API)             |
| Build        | Vite                                |
| Lenguaje     | JavaScript (con TypeScript opcional)|
| Hosting      | GitHub Pages (static build)         |
| Backend      | Ninguno — datos embebidos           |

## 2. Estructura del Proyecto

```
wc2026-predictor/
├── index.html
├── package.json
├── vite.config.js
├── src/
│   ├── main.js
│   ├── App.vue
│   ├── components/
│   │   ├── GroupCard.vue        # Muestra equipos de un grupo
│   │   └── MatchPredictor.vue   # Selector de resultado por partido
│   ├── data/
│   │   └── groups.js            # Datos hardcodeados (12 grupos, 48 equipos)
│   └── style.css
└── README.md
```

## 3. Datos

- **48 equipos** en **12 grupos** (A–L), 4 equipos por grupo.
- Solo **jornada 1**: un partido por grupo (12 partidos total).
- Fechas: 11–16 de junio 2026.

### Grupos y Primeros Partidos

| Grupo | Equipos                          | Partido J1                  | Fecha    |
|-------|----------------------------------|-----------------------------|----------|
| A     | Mexico, South Africa, South Korea, Czechia | Mexico vs South Africa | Jun 11 |
| B     | Canada, Bosnia & Herzegovina, Qatar, Switzerland | Canada vs Bosnia & Herzegovina | Jun 12 |
| C     | Brazil, Morocco, Haiti, Scotland | Brazil vs Morocco           | Jun 13   |
| D     | USA, Paraguay, Australia, Türkiye | USA vs Paraguay            | Jun 12   |
| E     | Germany, Curaçao, Netherlands, Japan | Germany vs Curaçao        | Jun 14   |
| F     | Ivory Coast, Ecuador, Sweden, Tunisia | Ivory Coast vs Ecuador   | Jun 14   |
| G     | Belgium, Egypt, Iran, New Zealand | Belgium vs Egypt           | Jun 15   |
| H     | Spain, Cape Verde, Saudi Arabia, Uruguay | Spain vs Cape Verde   | Jun 15   |
| I     | France, Senegal, Iraq, Norway    | France vs Senegal           | Jun 16   |
| J     | Argentina, Algeria, Austria, Jordan | Argentina vs Algeria      | Jun 16   |
| K     | Portugal, DR Congo, Uzbekistan, Colombia | Portugal vs DR Congo    | Jun 16   |
| L     | England, Croatia, Ghana, Panama   | England vs Croatia          | Jun 16   |

## 4. Funcionalidades

1. **Vista de Grupos** — mostrar los 12 grupos con sus 4 equipos cada uno.
2. **Partidos Jornada 1** — listar el primer partido de cada grupo.
3. **Sistema de Predicción:**
   - Seleccionar ganador (local, visitante) o empate por partido.
   - Persistir en `localStorage`.
   - Mostrar resumen de predicciones realizadas (cuántas, cuáles).

## 5. Decisiones de Implementación

| Aspecto      | Decisión                                      |
|-------------|-----------------------------------------------|
| Datos       | Hardcodeados en `src/data/groups.js`          |
| Estado      | Vue reactivity + `localStorage`               |
| Persistencia| `watch` + `JSON.parse/stringify`              |
| Estilo      | CSS simple, responsive, tema deportivo        |
| Deploy      | `vite.config.js` con `base: '/<repo>/'`       |

## 6. Flujo de Ejecución

1. `npm create vite@latest` con template `vue`
2. Crear `src/data/groups.js` con grupos y partidos
3. Crear `src/components/GroupCard.vue`
4. Crear `src/components/MatchPredictor.vue`
5. Implementar `App.vue` con lógica de predicción + localStorage
6. Configurar `vite.config.js` para GitHub Pages (`base`)
7. `npm run build` y deploy a `gh-pages`

## 7. Comandos

```bash
npm install
npm run dev        # Desarrollo
npm run build      # Build producción → /dist
npm run preview    # Vista previa del build
```

## 8. GitHub Pages

- Repositorio: `https://github.com/EduardoFriesen/wc2026-predictor`
- Rama: `gh-pages` (o `main` con `/docs`)
- Output: `dist/`
- Homepage: `https://EduardoFriesen.github.io/wc2026-predictor/`
