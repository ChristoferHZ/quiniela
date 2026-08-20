# Quiniela Felstofer

Pronóstico de los 15 partidos de La Quiniela española (Primera y Segunda),
calculado con la fuerza real de cada equipo, el mercado de apuestas y una
simulación de miles de jornadas.

La web es un único fichero, `index.html`, sin servidor ni base de datos.

## Cómo funciona el modelo

1. Cada equipo tiene una estimación de goles a favor y en contra por partido.
   Al principio de temporada es un nivel de partida; según se juegan jornadas,
   se sustituye por sus goles reales.
2. Con el ataque de uno y la defensa del otro salen los goles esperados de cada
   lado, ajustados por racha, ambiente, motivación, cansancio y bajas.
3. De ahí se calcula la probabilidad de cada marcador (Poisson con corrección
   Dixon-Coles) y, sumando, la de 1, X y 2.
4. Se mezcla con las cuotas del mercado sin el margen de la casa, y con el
   historial de enfrentamientos en ese campo.
5. La jornada se simula miles de veces para ver la distribución de aciertos.

## Dónde están los datos

Todo lo que se actualiza cada semana vive en el `BLOQUE DE DATOS` del
`<script id="app-js">` dentro de `index.html`:

- `DATOS_ACTUALIZADO` y `DATOS_PENDIENTE`
- `EQUIPOS_SEMILLA` — equipos y nivel de partida
- `JORNADAS` — boletos, horarios, cuotas, % del público y bajas
- `RESULTADOS` — partidos disputados de la temporada
- `H2H_HISTORICO` — enfrentamientos directos de temporadas anteriores
- `PREMIOS` y `BOTE_ACTUAL` — escrutinio oficial

No hay ningún campo rellenable en la página: se consulta, no se edita.

## Aviso

Herramienta de análisis probabilístico. Ningún modelo convierte el fútbol en
una certeza. Juega con responsabilidad.
