# Overview

This is a full-stack video downloader application that allows users to download videos from multiple social media platforms including YouTube, Instagram, Facebook, Twitter/X, and TikTok. The application features a modern React frontend with TypeScript and a Node.js/Express backend, using PostgreSQL for data persistence and yt-dlp for video processing.

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

## Frontend Architecture
- **Framework**: React 18 with TypeScript for type safety
- **Build Tool**: Vite for fast development and optimized builds
- **UI Components**: shadcn/ui component library built on Radix UI primitives
- **Styling**: Tailwind CSS with CSS variables for theming support
- **State Management**: TanStack Query (React Query) for server state management
- **Routing**: Wouter for lightweight client-side routing
- **Forms**: React Hook Form with Zod validation for type-safe form handling

## Backend Architecture
- **Runtime**: Node.js with Express.js framework
- **Language**: TypeScript with ES modules
- **Database ORM**: Drizzle ORM for type-safe database operations
- **Validation**: Zod schemas for runtime type validation
- **Video Processing**: yt-dlp integration via child processes for video metadata extraction and downloading
- **Session Management**: In-memory storage with fallback to database persistence

## Data Storage
- **Primary Database**: PostgreSQL with Neon serverless driver
- **Schema Design**: Three main entities:
  - Users: Basic user management with username/password
  - Videos: Metadata storage for analyzed videos including formats, thumbnails, and platform information
  - Downloads: Download job tracking with status, progress, and file information
- **Migration System**: Drizzle Kit for database schema migrations

## API Design
- **RESTful Endpoints**: Express routes for video analysis, download management, and user operations
- **Error Handling**: Centralized error middleware with structured error responses
- **Request Logging**: Custom middleware for API request/response logging
- **CORS**: Configured for cross-origin requests with credentials support

## Video Processing Pipeline
- **Platform Detection**: Regex-based URL pattern matching for supported platforms
- **Metadata Extraction**: yt-dlp integration for video information retrieval
- **Format Selection**: Multiple quality options (720p, 480p, audio-only) with file size estimation
- **Download Management**: Background job processing with real-time progress tracking
- **File Handling**: Temporary file management with cleanup procedures

## Authentication & Security
- **User Management**: Basic username/password authentication
- **Session Handling**: Session-based authentication with secure cookie configuration
- **Input Validation**: Comprehensive validation using Zod schemas on both client and server
- **CSRF Protection**: Built-in Express security middleware

# External Dependencies

## Core Dependencies
- **@neondatabase/serverless**: Neon PostgreSQL serverless driver for database connectivity
- **drizzle-orm**: Type-safe ORM for database operations and query building
- **yt-dlp**: Command-line tool for video downloading and metadata extraction (external binary)
- **connect-pg-simple**: PostgreSQL session store for Express sessions

## UI and Styling
- **@radix-ui/***: Comprehensive set of accessible UI primitives for complex components
- **tailwindcss**: Utility-first CSS framework for responsive design
- **class-variance-authority**: Utility for creating type-safe component variants
- **lucide-react**: Icon library with consistent design language

## Development Tools
- **@tanstack/react-query**: Server state management with caching and synchronization
- **react-hook-form**: Performant form handling with minimal re-renders
- **@hookform/resolvers**: Integration layer between React Hook Form and Zod validation
- **wouter**: Lightweight routing library for single-page applications

## Build and Development
- **vite**: Fast build tool with hot module replacement and optimized production builds
- **@vitejs/plugin-react**: Vite plugin for React support with Fast Refresh
- **esbuild**: JavaScript bundler for server-side code compilation
- **@replit/vite-plugin-***: Replit-specific development tools for enhanced debugging and error handling