# mrln-trrs-stats

Instancia personal de [github-readme-stats](https://github.com/anuraghazra/github-readme-stats) desplegada en Vercel para generar las tarjetas del perfil [mrln-trrs](https://github.com/mrln-trrs), incluidos los repositorios privados.

![Estado](https://img.shields.io/badge/estado-mantenimiento-yellow)
![Licencia](https://img.shields.io/badge/licencia-MIT-blue)
![Node](https://img.shields.io/badge/node-22-339933)

## Estado del proyecto

**Mantenimiento.** El proyecto original dejó de mantenerse (aviso de obsolescencia publicado en el repositorio upstream). Esta copia solo recibe parches de seguridad de dependencias; no se desarrollan funciones nuevas.

## Qué sirve

Despliegue en `https://mrln-trrs-stats.vercel.app`, rama `mrln`:

| Ruta | Tarjeta |
|---|---|
| `/api?username=mrln-trrs` | Estadísticas generales |
| `/api/top-langs?username=mrln-trrs` | Lenguajes más usados |
| `/api/pin?username=mrln-trrs&repo=<repo>` | Tarjeta de un repositorio |

Los parámetros de cada ruta (colores, `count_private`, `cache_seconds`, etc.) son los del proyecto original.

## Stack

- Node.js 22 (funciones serverless de Vercel en `api/`)
- axios, dotenv; pruebas con Jest

## Despliegue

Cada push a la rama `mrln` redespliega el proyecto en Vercel. Variable de entorno requerida en Vercel: `PAT_1` (token de GitHub de solo lectura). Nunca se versiona el token.

Pruebas locales (sin Node instalado, con Docker):

```bash
docker run --rm --memory=1500m -v "$PWD":/app -w /app node:22 \
  bash -c "npm ci --ignore-scripts && npm test"
```

## Limitaciones y pendientes

- El upstream no tiene mantenimiento. Alternativas activas: `stats-organization/github-stats-extended` o generar las tarjetas con `stats-organization/github-readme-stats-action` desde el repositorio de perfil.
- Quedan avisos de `npm audit` en dependencias de desarrollo (pruebas y lint) que solo se corrigen con saltos de versión mayor; no afectan al despliegue. Las dependencias de producción no tienen vulnerabilidades conocidas.
- La documentación completa de parámetros está en el repositorio original.

## Autoría y licencia

Código original de Anurag Hazra y colaboradores de github-readme-stats, bajo licencia MIT (ver [LICENSE](LICENSE), que se conserva sin cambios). Mantenimiento de esta instancia: Marlon Torres Espinoza.
