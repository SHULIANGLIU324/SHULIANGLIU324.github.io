# Replit.md

## Overview

This project contains both a multiplayer drawing game (WordDraw) and an ultra-light personal website. The personal website is built with pure HTML/CSS following minimalist design principles, requiring no frameworks or build processes.

## User Preferences

Preferred communication style: Simple, everyday language.
Website approach: Ultra-light, static HTML/CSS only, minimalist design.
Personal info: Name is Shuliang Liu, email is 2509293907@qq.com, has provided profile photo.
Personal details: 20 years old (born March 24, 2005), from China, studying at Hong Kong Baptist University.
Main interests: Photography and theater - enjoys capturing quiet moments and bringing stories to life on stage.
Social media: Added virtual accounts - @shuliangphoto (Twitter), @shuliangdev (GitHub), @shuliang_captures (Instagram), LinkedIn profile.
Design updates: Added modern gradient background, glass-morphism effects, smooth animations, and enhanced color scheme for better visual appeal.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Styling**: Tailwind CSS with shadcn/ui component library
- **State Management**: React Query for server state, local React state for UI
- **Routing**: Wouter for client-side routing
- **Real-time Communication**: WebSocket client for live game updates

### Backend Architecture
- **Framework**: Express.js with TypeScript
- **Real-time**: WebSocket server for live game functionality
- **Database**: PostgreSQL with Drizzle ORM
- **Session Management**: In-memory storage with session IDs
- **Development**: Vite for development server and hot reload

### Database Schema
- **rooms**: Game room data (code, settings, current state)
- **players**: Player information (nickname, score, session)
- **chatMessages**: Chat and guess messages
- **achievements**: Player achievement tracking
- **drawingStrokes**: Real-time drawing data

## Key Components

### Game Flow
1. **Home Page**: Create or join game rooms with nickname
2. **Game Room**: Real-time drawing, guessing, and chat
3. **Round System**: Timed rounds with word selection and scoring
4. **Achievement System**: Unlock achievements based on gameplay

### Real-time Features
- **Drawing Canvas**: HTML5 canvas with real-time stroke synchronization
- **Live Chat**: Instant messaging with guess detection
- **Player Status**: Real-time player list with scores and status
- **Game State**: Synchronized game progression across all players

### UI Components
- Responsive design with mobile support
- Card-based layout for game sections
- Real-time status indicators
- Achievement notifications and progress

## Data Flow

1. **Room Creation**: Player creates room → generates code → stores in database
2. **Join Room**: Player joins via code → WebSocket connection established
3. **Game State**: Server broadcasts game state to all connected players
4. **Drawing**: Canvas events → WebSocket → broadcast to other players
5. **Guessing**: Chat input → server validation → score updates → broadcast
6. **Round Management**: Timer-based progression with automatic word selection

## External Dependencies

### Core Libraries
- **@tanstack/react-query**: Server state management
- **drizzle-orm**: Database ORM and query builder
- **@neondatabase/serverless**: PostgreSQL driver for Neon
- **ws**: WebSocket implementation
- **zod**: Runtime type validation

### UI Libraries
- **@radix-ui**: Accessible component primitives
- **tailwindcss**: Utility-first CSS framework
- **lucide-react**: Icon library
- **class-variance-authority**: Component variant styling

### Development Tools
- **vite**: Build tool and development server
- **tsx**: TypeScript execution for Node.js
- **esbuild**: Fast bundling for production

## Deployment Strategy

### Build Process
1. **Frontend**: Vite builds React app to `dist/public`
2. **Backend**: esbuild bundles server code to `dist/index.js`
3. **Database**: Drizzle migrations applied via `db:push`

### Environment Requirements
- **DATABASE_URL**: PostgreSQL connection string
- **NODE_ENV**: Environment setting (development/production)

### Production Setup
- Express serves static files in production
- WebSocket server runs on same port as HTTP
- Database connection pooling for scalability
- Session-based player identification

### Development Features
- Hot reload with Vite middleware
- Runtime error overlay for debugging
- Replit-specific development banner
- TypeScript checking and validation