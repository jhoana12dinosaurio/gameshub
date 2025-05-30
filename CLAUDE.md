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

This is a complete and fully functional Angular 19.2.0 gaming portal using standalone components. GameHub showcases modern Angular patterns with premium gaming-themed UI/UX.

### Project Status: ✅ FULLY IMPLEMENTED
All components, services, routing, and data loading are complete and functional. The project is ready for educational use and further development.

### Key Structure
- **Bootstrap**: `src/main.ts` uses `bootstrapApplication()` with standalone `AppComponent`
- **Configuration**: `src/app/app.config.ts` provides HttpClient, router and zone.js providers
- **Routing**: Complete routing system in `src/app/app.routes.ts` with full navigation
- **Components**: All components use `standalone: true` flag with modern Angular patterns
- **Assets**: Properly configured in angular.json to serve JSON data from src/assets/

### Component Architecture
**Main Components (All Fully Implemented):**
- `InicioComponent` - Hero section with stats, popular games grid, category preview
- `ListaJuegosComponent` - Complete game listing with search bar, filters sidebar, responsive grid
- `DetalleJuegoComponent` - Full game details with tabs (info, requirements, screenshots), similar games
- `CategoriasComponent` - Category overview with counters, stats visualization, navigation

**Reusable Components (All Fully Implemented):**
- `TarjetaJuegoComponent` - Game card with image, rating stars, platform icons, price display
- `FiltrosComponent` - Advanced filter panel with category, platform, price, rating filters

**Navigation & Layout:**
- `AppComponent` - Gaming navbar with mobile toggle, footer with links and social media
- Responsive navigation with active route highlighting
- Sticky navbar with gaming design theme

### Services & Data Management
- `JuegosDataService` - Complete game data management with RxJS observables, filtering, search
- `CategoriasService` - Category management with game counters and statistics
- **Data source**: `src/assets/data/juegos.json` with 15 popular games across 6 categories
- **HTTP Integration**: Proper HttpClient setup for data loading

### Advanced Features Implemented
**Search & Filtering:**
- Real-time search by game name, developer, or category
- Multi-criteria filtering (category, platform, price, rating)
- Filter state management with BehaviorSubject
- Active filter display with remove options
- Results counter and empty states

**Gaming Theme Features:**
- Custom CSS variables for gaming aesthetic (purples, cyan, neon green)
- Bootstrap 5.3.3 + Bootstrap Icons fully integrated
- Advanced animations: card hovers, gradients, glowing effects
- Responsive design optimized for mobile gaming
- Gaming-focused typography with gradient text effects

**User Experience:**
- Loading states with spinners
- Empty states with helpful messages
- Error handling for missing data
- Smooth transitions and hover effects
- Mobile-optimized navigation and layouts
- Optimized image handling with fixed dimensions and lazy loading

### Data Structure
**Games Include:** id, name, image, category, developer, release date, description, rating, platforms array, price, free flag, system requirements (min/recommended), screenshots array, tags array

**Categories Include:** id, name, icon (Bootstrap Icons), description, color (for theming)

**15 Popular Games Included:** Fortnite, Minecraft, League of Legends, Valorant, Genshin Impact, FIFA 24, Free Fire, Roblox, Counter-Strike 2, Apex Legends, PUBG Mobile, Call of Duty Warzone, Dota 2, NBA 2K24, Mobile Legends

**6 Gaming Categories:** Battle Royale, Sandbox, MOBA, FPS, RPG, Sports

### Complete Routing System
- `/` - Home page with hero section, stats, popular games, category preview
- `/juegos` - All games listing with search and filters
- `/juego/:id` - Individual game details with tabs and similar games
- `/categorias` - Category overview with statistics and navigation
- `/categoria/:id` - Games filtered by specific category
- `**` - Wildcard redirect to home

### Development Workflow
1. **Assets Configuration**: angular.json properly configured to serve assets from src/assets/
2. **Modern Angular**: Uses latest Angular 19 features including new control flow (@if, @for)
3. **TypeScript Strict Mode**: Full type safety with interfaces for Game and Category
4. **RxJS Patterns**: Proper observable usage with combineLatest, map, BehaviorSubject
5. **Responsive Design**: Mobile-first approach with Bootstrap grid system

### Student Extension Ideas
**Beginner Level:**
- Add new games to `juegos.json`
- Modify game data (images, descriptions, ratings)
- Add new gaming categories
- Customize colors and themes in CSS variables

**Intermediate Level:**
- Implement favorites system with localStorage
- Add user reviews and ratings
- Create advanced sorting options
- Implement virtual scrolling for large lists
- Add animation libraries (AOS, Lottie)

**Advanced Level:**
- Integrate real gaming APIs (Steam, IGDB)
- Add user authentication and profiles
- Implement game comparison features
- Add PWA capabilities
- Create admin panel for game management
- Add internationalization (i18n)

### Troubleshooting
- **JSON not loading**: Ensure `ng serve` is running and assets are properly configured in angular.json
- **Routing issues**: Check that all components are properly imported in routes
- **Styling problems**: Verify Bootstrap CSS is loaded in angular.json styles array
- **Component errors**: Ensure all standalone components have proper imports array
- **Image sizing issues**: All game images have fixed heights with `object-fit: cover` to maintain proportions:
  - Lista de juegos (tarjeta-juego): 200px height
  - Detalle de juego principal: 300px height in container
  - Screenshots y juegos similares: 200px height
  - Uses `loading="lazy"` for performance optimization
  - Container elements prevent image overflow