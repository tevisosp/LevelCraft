# Overview

Level Craft is a web-based game platform that combines a 2D platformer with level editor and a modified chess game. The platformer allows players to create custom levels using a visual editor, play through levels, and browse community-created content. The chess game implements enhanced rules including piece aging, recruitment mechanics, multi-game campaigns, and capital management. The application features a React frontend with HTML5 Canvas rendering for platformer mechanics and React components for chess gameplay, an Express.js backend API, and PostgreSQL database storage for level persistence and chess game data.

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

## Frontend Architecture
The client uses a React-based single-page application with TypeScript and Vite for development. The architecture follows a component-based pattern with:

- **Game Rendering**: HTML5 Canvas with custom 2D rendering engine for real-time gameplay
- **State Management**: Zustand stores for game state, player data, audio, and level management
- **UI Components**: Radix UI primitives with Tailwind CSS for responsive design and accessibility
- **Routing**: Client-side routing with different game modes (menu, play, editor, browser)

The game engine includes modular systems for physics simulation, collision detection, and input handling. Custom React Three Fiber integration supports 3D elements and post-processing effects.

## Backend Architecture
The server implements a RESTful API using Express.js with:

- **Route Structure**: Modular route handlers for level management (GET /api/levels, POST /api/levels, GET /api/levels/:id)
- **Storage Layer**: Abstracted storage interface supporting both in-memory storage (development) and database persistence
- **Development Setup**: Vite middleware integration for hot module replacement in development
- **Error Handling**: Centralized error handling middleware with proper HTTP status codes

## Data Storage Solutions
The application uses a hybrid storage approach:

- **Database**: PostgreSQL with Drizzle ORM for schema management and type-safe queries
- **Schema Design**: Separate tables for users, levels, ratings, and play statistics with proper foreign key relationships
- **Local Storage**: Browser localStorage for temporary level drafts and user preferences
- **Development Fallback**: In-memory storage implementation for development without database setup

Key database tables include levels with metadata (name, author, difficulty, plays, ratings), user management, and level interaction tracking.

## Authentication and Authorization
Currently implements a basic user system with:

- **User Schema**: Username/password authentication stored in PostgreSQL
- **Session Management**: Express session handling (infrastructure ready)
- **Anonymous Features**: Level playing and rating without authentication required
- **IP Tracking**: Anonymous user interaction tracking by IP address

The system is designed to support both authenticated and anonymous users, with optional user accounts for level creation and community features.

# External Dependencies

## Database Services
- **PostgreSQL**: Primary database using Neon serverless PostgreSQL (@neondatabase/serverless)
- **Drizzle ORM**: Type-safe database operations with automatic migrations
- **Session Store**: PostgreSQL session storage (connect-pg-simple) for user sessions

## UI and Styling
- **Radix UI**: Comprehensive component library for accessible UI primitives
- **Tailwind CSS**: Utility-first CSS framework with custom design tokens
- **Lucide React**: Icon library for consistent iconography
- **Inter Font**: Typography via @fontsource/inter

## Game Development
- **React Three Fiber**: 3D rendering and WebGL integration (@react-three/fiber)
- **Drei Helpers**: 3D scene utilities and controls (@react-three/drei)
- **Post-processing**: Visual effects pipeline (@react-three/postprocessing)
- **GLSL Shaders**: Custom shader support via vite-plugin-glsl

## Development Tools
- **Vite**: Build tool and development server with React plugin
- **TypeScript**: Type safety across frontend and backend
- **ESBuild**: Fast bundling for production builds
- **TanStack Query**: Server state management and API caching

## Audio and Media
- **Web Audio API**: Browser-native audio processing
- **Canvas API**: 2D graphics rendering for game elements
- **File Support**: GLTF/GLB 3D models, MP3/OGG/WAV audio assets

The application is designed to run on Replit with automatic database provisioning and deployment configuration.