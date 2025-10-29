# Anamaya Health Platform

## Overview

Anamaya is a free healthcare platform designed to provide accessible medical services to rural and semi-urban Indian populations. The platform offers AI-powered symptom diagnosis using Google's Gemini AI, doctor discovery with filtering capabilities, patient registration and management, and appointment booking. Built with a mobile-first approach, it supports multiple Indian languages (English, Hindi, Tamil, Telugu) to ensure accessibility for users with varying digital literacy levels.

The application serves as a comprehensive healthcare solution that bridges the gap between patients and medical professionals, with emphasis on trust, cultural sensitivity, and simplicity in design.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Technology Stack:**
- **Framework**: React 18 with TypeScript, using Vite as the build tool
- **Routing**: Wouter for lightweight client-side routing
- **State Management**: TanStack Query (React Query) for server state management
- **UI Library**: Shadcn UI components built on Radix UI primitives
- **Styling**: Tailwind CSS with custom design system based on "new-york" style

**Design System:**
- Typography uses Poppins font for excellent readability in Latin and Devanagari scripts
- Mobile-first responsive grid system (collapses to single column on mobile)
- Custom color system with HSL values supporting light/dark modes
- Hover and active elevation states for interactive elements
- Consistent spacing primitives (4, 6, 8, 12, 16, 20 Tailwind units)

**Key Pages:**
- Home: Hero section with service cards and how-it-works flow
- Diagnosis: AI-powered symptom checker with doctor recommendations
- Doctors: Searchable doctor directory with specialty filtering
- Add Patient: Patient registration form with medical history
- Subscription: Membership plans and government scheme information

**Internationalization:**
- Context-based language system supporting 4 languages (en, hi, ta, te)
- Language selection persisted to localStorage
- Translation file provides localized strings for all UI elements

### Backend Architecture

**Technology Stack:**
- **Runtime**: Node.js with Express.js framework
- **Language**: TypeScript with ESM modules
- **ORM**: Drizzle ORM for type-safe database operations
- **Database Driver**: Neon serverless PostgreSQL with WebSocket support
- **AI Service**: Google Generative AI (Gemini 1.5 Flash)

**API Structure:**
RESTful API endpoints organized by resource:
- `/api/patients` - Patient CRUD operations
- `/api/doctors` - Doctor listings and filtering
- `/api/appointments` - Appointment booking and management
- `/api/diagnosis` - AI-powered symptom analysis

**Rate Limiting:**
Diagnosis endpoint protected with express-rate-limit (10 requests per 15 minutes per IP) to manage free tier API costs.

**Data Validation:**
Zod schemas generated from Drizzle table definitions ensure type-safe validation across client and server.

**Error Handling:**
Graceful degradation when GEMINI_API_KEY is not configured - returns mock diagnosis responses to allow development without API key.

### Database Design

**ORM**: Drizzle ORM chosen for:
- Type-safe queries with TypeScript inference
- Lightweight compared to traditional ORMs
- Excellent PostgreSQL support
- Schema-first approach with migrations

**Schema Structure:**

**Patients Table:**
- Stores patient demographics, contact information, medical history
- Includes emergency contact details
- UUID primary keys for security

**Doctors Table:**
- Comprehensive doctor profiles with qualifications, specialties
- Multi-language support (array field)
- Location data (city, state, distance)
- Availability scheduling (days array)
- Rating system and profile images

**Appointments Table:**
- Links patients to doctors with status tracking
- Date/time scheduling with reason for visit
- Notes field for additional information

**Diagnosis Results Table:**
- Stores AI-generated diagnosis reports
- Links to patient records
- Preserves symptom input and AI analysis output

**Database Connection:**
- Neon serverless PostgreSQL for scalable, serverless deployment
- WebSocket-based connection pooling for optimal performance
- Environment-based configuration with validation

### AI Integration

**Service**: Google Generative AI (Gemini 1.5 Flash model)

**Choice Rationale:**
- Cost-effective for free tier usage
- Fast response times suitable for real-time diagnosis
- JSON output mode for structured responses
- Multilingual support matching platform requirements

**Implementation:**
- Graceful fallback to mock responses when API key unavailable
- Language-aware prompts (analysis provided in user's selected language)
- Structured output including severity levels, likely conditions, recommended specialties, self-care tips, and follow-up actions
- Disclaimer included with all AI responses for medical liability

**Response Structure:**
Returns severity assessment (mild/moderate/severe/emergency), list of likely conditions, recommended medical specialties, self-care tips, and follow-up action items.

### Development Tooling

**Build System:**
- Vite for fast HMR and optimized production builds
- ESBuild for server-side bundling
- TypeScript compilation with path aliases

**Code Quality:**
- Strict TypeScript configuration
- ESM module system throughout
- Path aliases for clean imports (@/, @shared/, @assets/)

**Replit Integration:**
- Runtime error modal plugin for development
- Cartographer plugin for code navigation
- Dev banner for environment indication

## External Dependencies

### Third-Party Services

**Neon Database:**
- Serverless PostgreSQL database
- WebSocket-based connection pooling
- Auto-scaling and branching capabilities
- Required: DATABASE_URL environment variable

**Google Generative AI:**
- Gemini 1.5 Flash model for AI diagnosis
- Optional: GEMINI_API_KEY environment variable
- Gracefully degrades to mock responses if not configured

### UI Component Libraries

**Radix UI:**
Comprehensive set of unstyled, accessible React primitives including dialogs, dropdowns, forms, navigation menus, popovers, and tooltips. Chosen for accessibility compliance and headless architecture allowing custom styling.

**Shadcn UI:**
Pre-styled component collection built on Radix UI, customized to "new-york" style variant with Tailwind CSS integration.

### Key NPM Packages

**Form Management:**
- react-hook-form: Form state management and validation
- @hookform/resolvers: Zod schema integration
- zod: Runtime type validation
- drizzle-zod: Automatic schema generation from database tables

**Date Handling:**
- date-fns: Date formatting and manipulation
- react-day-picker: Calendar component for appointment booking

**Routing & State:**
- wouter: Lightweight routing (~1KB)
- @tanstack/react-query: Server state management with caching

**Styling:**
- tailwindcss: Utility-first CSS framework
- class-variance-authority: Type-safe component variants
- clsx & tailwind-merge: Conditional class name utilities

**Development:**
- tsx: TypeScript execution for development
- vite: Frontend build tool
- drizzle-kit: Database migration management