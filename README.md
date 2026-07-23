# Space Missions Explorer

A production-quality static React application for exploring space missions, rockets,
astronauts, and the history of human spaceflight.

**Live demo:** _coming soon_

## Tech Stack

| Technology   | Purpose                    | Why                                                                 |
| ------------ | -------------------------- | ------------------------------------------------------------------- |
| React 19     | UI library                 | Current standard; function components and hooks throughout           |
| TypeScript 6 | Type safety                | Strict mode enabled to catch errors at compile time, not runtime     |
| Vite 8       | Build tool and dev server  | Fast builds, first-class TS support, outputs plain static assets     |
| Tailwind CSS 4 | Styling                  | Utility-first; CSS-first configuration, no separate config file      |
| ESLint + Prettier | Code quality          | ESLint enforces correctness, Prettier owns formatting                |

## Architecture Decisions

**Vite over Next.js.** This application is fully static — no server, no database,
no authentication. Next.js is excellent, but its core strengths (server rendering,
server actions) would add weight without benefit here, and a plain Vite build
produces static files that any web server can host.

**No global state library.** Redux and Zustand solve problems this application
doesn't have. React's built-in state plus Context (for theming) is sufficient.
Adding a state library "just in case" is a common source of unnecessary complexity.

**Strict TypeScript.** `strict` and `noUncheckedIndexedAccess` are both enabled.
The stricter settings surface assumptions that would otherwise fail at runtime.

## Planned Structure

    src/
    ├── components/   Generic, reusable UI (Button, Card, Spinner)
    ├── features/     Domain modules (missions, rockets, astronauts, timeline)
    ├── pages/        Route-level components
    ├── lib/          Framework-agnostic utilities and data access
    └── types/        Shared TypeScript types

Organised by feature rather than by file type: everything related to missions
lives together. Folders are created as they are needed rather than upfront.

## Getting Started

Requires Node 22+ and pnpm.

    pnpm install
    pnpm dev

## Scripts

| Command             | Description                          |
| ------------------- | ------------------------------------ |
| `pnpm dev`          | Start the development server         |
| `pnpm build`        | Type-check and build for production  |
| `pnpm preview`      | Preview the production build locally |
| `pnpm lint`         | Run ESLint                           |
| `pnpm format`       | Format all files with Prettier       |
| `pnpm format:check` | Check formatting without writing     |

## License

MIT