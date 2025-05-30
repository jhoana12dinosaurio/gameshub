# PRÁCTICA CALIFICADA - JAVASCRIPT AVANZADO
## Aplicación Angular "GameHub"

**Duración:** 1 hora 40 minutos  
**Fecha:** _______________  
**Docente:** Ms. Johan López Heredia  
**Semestre:** 2025-I

---

## INSTRUCCIONES GENERALES

1. **Clone el repositorio** en su equipo local:
   ```bash
   git clone https://github.com/GxJohan/GameHub.git
   cd GameHub
   npm install
   ```

2. **Inicie el servidor de desarrollo:**
   ```bash
   npm start
   ```

3. **Lea todas las instrucciones** antes de comenzar.

4. **Prohibido** el uso de ChatGPT, Copilot o cualquier IA durante el examen.

5. **Entrega:** Al finalizar, realice un commit con sus cambios y notifique al docente.

---

## PARTE 1: MODIFICACIÓN DE DATOS (25 puntos)

### 1.1 Agregar Nuevos Juegos (10 puntos)
En el archivo `src/assets/data/juegos.json`, agregue **DOS (2) nuevos juegos** con las siguientes características:

**Juego 1:**
- ID: 16
- Nombre: "Gran Turismo 7"
- Categoría: "Sports" 
- Desarrollador: "Polyphony Digital"
- Plataformas: ["PlayStation", "PC"]
- Precio: 69.99
- Rating: 4.5
- Incluya todos los campos requeridos según la estructura existente

**Juego 2:**
- ID: 17
- Nombre: "The Legend of Zelda: Breath of the Wild"
- Categoría: (Deberá crear una nueva categoría - ver punto 1.2)
- Desarrollador: "Nintendo EPD"
- Plataformas: ["Nintendo Switch"]
- Precio: 59.99
- Rating: 4.9
- Incluya todos los campos requeridos

### 1.2 Agregar Nueva Categoría (5 puntos)
Agregue una nueva categoría en el mismo archivo JSON:
- ID: "adventure"
- Nombre: "Adventure"
- Icono: "bi-compass"
- Descripción: "Juegos de aventura y exploración con narrativas épicas"
- Color: "#9b59b6"

### 1.3 Actualizar Imágenes (10 puntos)
Para los DOS juegos que agregó, utilice las siguientes URLs de imágenes:
- Gran Turismo 7: `https://media.direct.playstation.com/is/image/sierialto/gran-turismo-7-screenshot-01-en-01oct21?$Background_Large$`
- Zelda BOTW: `https://assets.nintendo.com/image/upload/c_fill,w_1200/q_auto:best/f_auto/dpr_2.0/ncom/software/switch/70010000000025/7137262b5a64d921e193653f8aa0b722925abc5680380ca0e18a5cfd91697f58`

**Nota:** Asegúrese de que las imágenes mantengan las proporciones correctas en todas las vistas.

---

## PARTE 2: COMPONENTES Y NAVEGACIÓN (40 puntos)

### 2.1 Crear Componente de Estadísticas (20 puntos)
Cree un nuevo componente llamado `estadisticas` que muestre:

1. **Genere el componente:**
   ```bash
   ng generate component components/estadisticas --standalone
   ```

2. **Implemente las siguientes funcionalidades:**
   - Total de juegos en la plataforma
   - Número de juegos gratuitos vs de pago
   - Juego con mejor rating
   - Promedio de precios de juegos de pago

3. **Requisitos técnicos:**
   - Use el servicio `JuegosDataService` existente
   - Implemente correctamente las suscripciones a Observables
   - Utilice pipes para formatear números y moneda

### 2.2 Configurar Navegación (20 puntos)

1. **Agregue la nueva ruta** en `app.routes.ts`:
   - Path: `/estadisticas`
   - Componente: `EstadisticasComponent`

2. **Agregue el enlace en la navegación** del `app.component.html`:
   - Texto: "Estadísticas"
   - Icono: `bi-graph-up`
   - Debe aparecer después de "Categorías"
   - Implemente `routerLinkActive` correctamente

---

## PARTE 3: SERVICIOS Y FUNCIONALIDAD (25 puntos)

### 3.1 Extender el Servicio de Juegos (15 puntos)
En `juegos-data.service.ts`, agregue los siguientes métodos:

1. **`getJuegosPorPrecio(min: number, max: number)`**
   - Retorna Observable con juegos en el rango de precio especificado
   - Debe funcionar con el sistema de filtros existente

2. **`getEstadisticas()`**
   - Retorna Observable con un objeto que contenga:
     - totalJuegos: number
     - juegosGratis: number
     - juegosPago: number
     - mejorRating: Juego
     - promedioPrecio: number

### 3.2 Implementar Ordenamiento (10 puntos)
En el componente `lista-juegos`, agregue un selector de ordenamiento:

1. **Opciones de ordenamiento:**
   - Por nombre (A-Z, Z-A)
   - Por precio (menor a mayor, mayor a menor)
   - Por rating (mejor a peor)

2. **Ubicación:** Debajo de la barra de búsqueda, antes de la lista de juegos

---

## PARTE 4: ANÁLISIS Y COMPRENSIÓN (10 puntos)

### 4.1 Identificación de Archivos (5 puntos)
Responda en comentarios al inicio del archivo `estadisticas.component.ts`:

```typescript
/*
RESPUESTAS PARTE 4.1:
1. ¿En qué archivo se define la interfaz Juego?
   Respuesta: 

2. ¿Qué archivo maneja el estado global de los filtros?
   Respuesta: 

3. ¿Dónde se configura el HttpClient para la aplicación?
   Respuesta: 
*/
```

### 4.2 Comprensión de Arquitectura (5 puntos)
Responda en el mismo archivo:

```typescript
/*
RESPUESTAS PARTE 4.2:
1. ¿Por qué este proyecto NO tiene app.module.ts?
   Respuesta: 

2. ¿Qué ventaja tiene usar BehaviorSubject en el servicio de juegos?
   Respuesta: 
*/
```

---

## CRITERIOS DE EVALUACIÓN

| Criterio | Puntos |
|----------|---------|
| **Funcionalidad Correcta** | 40% |
| - Los componentes funcionan sin errores | |
| - Los datos se muestran correctamente | |
| - La navegación funciona | |
| **Código Limpio** | 30% |
| - Uso correcto de TypeScript | |
| - Manejo adecuado de Observables | |
| - Imports correctos en componentes | |
| **Comprensión de Conceptos** | 20% |
| - Respuestas correctas en Parte 4 | |
| - Uso apropiado de servicios | |
| **Cumplimiento de Requisitos** | 10% |
| - Siguió todas las instrucciones | |
| - Completó todas las tareas | |

---

## NOTAS IMPORTANTES

1. **NO modifique** archivos que no se mencionan en las instrucciones.
2. **Asegúrese** de que la aplicación compile sin errores antes de entregar.
3. **Verifique** que todas las imágenes se muestran correctamente.
4. **Pruebe** la navegación completa antes de finalizar.
5. **Recuerde** hacer commit de sus cambios al terminar.

---

## ENTREGA

Al finalizar:
1. Ejecute: `git add .`
2. Ejecute: `git commit -m "Examen completado - [SU NOMBRE]"`
3. Notifique al docente que ha terminado

**¡Éxito en su evaluación!**