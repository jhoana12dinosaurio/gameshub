# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

### Development
- `npm start` - Start development server at http://localhost:4200/
- `npm run build` - Build for production to dist/game-hub
- `npm run watch` - Build in watch mode for development
- `npm test` - Run unit tests with Karma and Jasmine

### Testing
- `ng test` - Run unit tests in watch mode
- `ng test --no-watch --code-coverage` - Run tests once with coverage report

Note: No linting command is currently configured. Consider adding ESLint if code quality checks are needed.

## Architecture

This is a complete Angular 19.2.0 gaming portal using standalone components. GameHub showcases modern Angular patterns with gaming-themed UI/UX.

### Key Structure
- **Bootstrap**: `src/main.ts` uses `bootstrapApplication()` with standalone `AppComponent`
- **Configuration**: `src/app/app.config.ts` provides HttpClient, router and zone.js providers
- **Routing**: Complete routing system in `src/app/app.routes.ts` with navigation
- **Components**: All components use `standalone: true` flag with modern Angular patterns

### Component Architecture
**Main Components:**
- `InicioComponent` - Hero section, statistics, popular games, categories
- `ListaJuegosComponent` - Game listing with filters and search
- `DetalleJuegoComponent` - Individual game details and requirements
- `CategoriasComponent` - Category grid with game counts

**Reusable Components:**
- `TarjetaJuegoComponent` - Game card with rating, platforms, price
- `FiltrosComponent` - Filter panel for categories, platforms, price

### Services & Data
- `JuegosDataService` - Game data management with RxJS observables
- `CategoriasService` - Category management with counters
- Data source: `src/assets/data/juegos.json` with 15 popular games

### Gaming Theme Features
- Custom CSS variables for gaming colors (purples, cyan, neon green)
- Bootstrap 5.3.3 + Bootstrap Icons integration
- Animated cards, gradients, and hover effects
- Responsive design with mobile-first approach
- Gaming-focused typography and spacing

### Data Structure
Games include: name, image, category, developer, rating, platforms, price, requirements, screenshots, tags. Categories have: id, name, icon, description, color.

### Routes
- `/` - Home page with hero and featured content
- `/juegos` - All games with filtering
- `/juego/:id` - Individual game details
- `/categorias` - Category overview
- `/categoria/:id` - Games filtered by category

Students can extend this by: adding new games to JSON, creating new components, implementing additional filters, or adding new gaming categories.