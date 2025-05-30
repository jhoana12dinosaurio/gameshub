# PRÁCTICA CALIFICADA - JAVASCRIPT AVANZADO
## Aplicación Angular "GameHub"

**Duración:** 1 hora 40 minutos  
**Fecha:** _______________  
**Docente:** Ms. Johan López Heredia  
**Semestre:** 2025-I  
**Puntaje Total:** 20 puntos

---

## INSTRUCCIONES GENERALES

1. **Complete la PARTE 0** siguiendo las instrucciones detalladas paso a paso para configurar su repositorio.

2. **Inicie el servidor de desarrollo:**
   ```bash
   npm start
   ```

3. **Lea todas las instrucciones** antes de comenzar.

4. **Prohibido** el uso de ChatGPT, Copilot o cualquier IA durante el examen.

5. **Entrega:** Al finalizar, suba sus cambios a SU repositorio de GitHub.

---

## PARTE 0: CONFIGURACIÓN INICIAL (1 punto)

### 0.1 Configuración de Repositorio - INSTRUCCIONES PASO A PASO (1 punto)

#### Paso 1: Clonar el repositorio base
Abra su terminal y ejecute:
```bash
git clone https://github.com/GxJohan/GameHub.git
```

#### Paso 2: Crear SU repositorio en GitHub
1. Vaya a [github.com](https://github.com)
2. Haga clic en el botón verde **"New"** o **"New repository"**
3. Configure su repositorio:
   - **Repository name:** `GameHub` (DEBE ser exactamente este nombre)
   - **Description:** (opcional) "Práctica Calificada - [Su Nombre]"
   - **Public/Private:** Seleccione **Public** ✅
   - **NO** marque "Add a README file"
   - **NO** agregue .gitignore
   - **NO** agregue license
4. Haga clic en **"Create repository"**

#### Paso 3: Configurar su repositorio local
En la terminal, navegue al proyecto y configure su repositorio:
```bash
cd GameHub
git remote set-url origin https://github.com/[SU-USUARIO]/GameHub.git
```
**Ejemplo:** Si su usuario es `AlumnoUtp001`, el comando sería:
```bash
git remote set-url origin https://github.com/AlumnoUtp001/GameHub.git
```

#### Paso 4: Instalar dependencias
```bash
npm install
```
Espere a que termine la instalación (puede tardar 1-2 minutos).

#### Paso 5: Verificar que funciona
```bash
npm start
```
Debe abrir el navegador en `http://localhost:4200/` y ver la aplicación funcionando.

#### Paso 6: Configuración inicial del repositorio
Realice un primer push para establecer la conexión:
```bash
git add .
git commit -m "Configuración inicial"
git push -u origin master
```

**⚠️ IMPORTANTE:** 
- Su repositorio en GitHub DEBE estar creado ANTES del paso 3
- Si el push falla, verifique que escribió correctamente su nombre de usuario
- Si tiene problemas, levante la mano para recibir ayuda

---

## PARTE 1: MODIFICACIÓN DE DATOS (5 puntos)

### 1.1 Agregar Nuevos Juegos (2 puntos)
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

### 1.2 Agregar Nueva Categoría (1 punto)
Agregue una nueva categoría en el mismo archivo JSON:
- ID: "adventure"
- Nombre: "Adventure"
- Icono: "bi-compass"
- Descripción: "Juegos de aventura y exploración con narrativas épicas"
- Color: "#9b59b6"

### 1.3 Buscar y Configurar Imágenes (2 puntos)
Para los DOS juegos que agregó:
- **Busque imágenes apropiadas** en internet (Google Imágenes, sitios oficiales, etc.)
- **Seleccione imágenes de alta calidad** que representen bien cada juego
- **Use URLs directas a las imágenes** (que terminen en .jpg, .png, etc.)
- **Verifique** que las imágenes se muestren correctamente en la aplicación

**Criterios de evaluación:**
- Calidad y relevancia de las imágenes seleccionadas
- Correcta visualización en todas las vistas de la aplicación

---

## PARTE 2: COMPONENTES Y NAVEGACIÓN (7 puntos)

### 2.1 Crear Componente de Estadísticas (3.5 puntos)
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

### 2.2 Configurar Navegación (3.5 puntos)

1. **Agregue la nueva ruta** en `app.routes.ts`:
   - Path: `/estadisticas`
   - Componente: `EstadisticasComponent`

2. **Agregue el enlace en la navegación** del `app.component.html`:
   - Texto: "Estadísticas"
   - Icono: `bi-graph-up`
   - Debe aparecer después de "Categorías"
   - Implemente `routerLinkActive` correctamente

---

## PARTE 3: SERVICIOS Y FUNCIONALIDAD (5 puntos)

### 3.1 Extender el Servicio de Juegos (3 puntos)
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

### 3.2 Implementar Ordenamiento (2 puntos)
En el componente `lista-juegos`, agregue un selector de ordenamiento:

1. **Opciones de ordenamiento:**
   - Por nombre (A-Z, Z-A)
   - Por precio (menor a mayor, mayor a menor)
   - Por rating (mejor a peor)

2. **Ubicación:** Debajo de la barra de búsqueda, antes de la lista de juegos

---

## PARTE 4: ANÁLISIS Y COMPRENSIÓN (2 puntos)

### 4.1 Identificación de Archivos (1 punto)
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

### 4.2 Comprensión de Arquitectura (1 punto)
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

| Criterio | Puntos | Descripción |
|----------|---------|-------------|
| **Parte 0** | 1 pt | Configuración correcta del repositorio |
| **Parte 1** | 5 pts | Modificación correcta de datos JSON |
| **Parte 2** | 7 pts | Componente funcional y navegación |
| **Parte 3** | 5 pts | Servicios y funcionalidades |
| **Parte 4** | 2 pts | Comprensión de conceptos |
| **TOTAL** | **20 pts** | |

### Desglose adicional:
- **Funcionalidad Correcta** (40%): Los componentes funcionan sin errores
- **Código Limpio** (30%): Uso correcto de TypeScript y Angular
- **Comprensión** (20%): Respuestas correctas y uso apropiado de patrones
- **Cumplimiento** (10%): Siguió todas las instrucciones

---

## NOTAS IMPORTANTES

1. **NO modifique** archivos que no se mencionan en las instrucciones.
2. **Pruebe** la aplicación frecuentemente durante el desarrollo.
3. **Verifique** que todas las imágenes se muestran correctamente.
4. **Asegúrese** de que la navegación funciona antes de entregar.

---

## ENTREGA

Al finalizar:
1. Guarde todos sus cambios en Visual Studio Code (Ctrl+S)
2. Ejecute los siguientes comandos en la terminal:
   ```bash
   git add .
   git commit -m "Práctica Calificada - [SU NOMBRE COMPLETO]"
   git push origin master
   ```
3. Verifique en GitHub.com que su código se subió correctamente
4. Comparta el enlace de su repositorio con el docente
   - Formato: `https://github.com/[SU-USUARIO]/GameHub`

## NOTA IMPORTANTE SOBRE ERRORES

Si por cuestiones de tiempo no logra completar todas las funcionalidades o tiene errores de compilación:
- **NO SE PREOCUPE**: Suba su avance tal como está
- Es mejor entregar un trabajo parcial que no entregar nada
- Se valorará el esfuerzo y el avance logrado
- Asegúrese de hacer push de su último commit antes del tiempo límite

**¡Éxito en su evaluación!**