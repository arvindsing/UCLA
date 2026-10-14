# Photo Gallery & Portfolio

This repository is a Next.js 15 demo application for building and showcasing a professional photo gallery and portfolio UI. The code is primarily intended as a GitHub Copilot learning/demo project rather than a production-ready media backend or full-stack CMS.

## Primary purpose

The app presents a polished front-end for:

- browsing a gallery of mock photography items
- filtering by tags and search text
- uploading mock image files with a drag-and-drop upload experience
- reviewing a simple admin dashboard
- demonstrating reusable UI patterns in a component-driven Next.js app

The repo also includes a `demos/` folder with step-by-step GitHub Copilot exercises and walkthroughs for using Copilot in a realistic frontend workflow.

## Main languages, frameworks, and dependencies

The project is built with:

- TypeScript
- Next.js 15
- React 19
- Tailwind CSS 4
- Framer Motion for lightweight UI animation
- Lucide React for icons
- Radix UI primitives for dialog/select/toast behavior
- `react-dropzone` for drag-and-drop uploads
- `sharp` for image processing support in the Next.js ecosystem

Key dependencies from `package.json` are:

- `next`: "15.5.18"
- `react`: "19.1.0"
- `react-dom`: "19.1.0"
- `framer-motion`: "^12.23.11"
- `lucide-react`: "^0.533.0"
- `react-dropzone`: "^14.3.8"
- `@radix-ui/react-dialog`, `@radix-ui/react-select`, `@radix-ui/react-toast`

## Important folders and responsibilities

```bash
.
├── src/
│   ├── app/                  # App Router pages and root layout
│   │   ├── admin/            # Admin dashboard page
│   │   ├── gallery/          # Gallery browsing page with search/filter UI
│   │   ├── upload/           # Upload page
│   │   ├── globals.css       # Global styles and reusable utility classes
│   │   ├── layout.tsx        # Root layout, navigation header, metadata
│   │   └── page.tsx          # Home page
│   ├── components/
│   │   ├── gallery/          # `GalleryGrid` component
│   │   ├── ui/               # Shared layout/cards/stats components
│   │   └── upload/           # `UploadZone` component
│   └── lib/                  # Mock data for gallery, feature cards, admin stats
├── demos/                    # Copilot demo walkthroughs and exercises
├── public/                   # Default Next.js static assets (mostly starter placeholders)
├── .github/                  # Repo metadata, prompts, and Copilot-specific guides
├── package.json              # App scripts and package config
├── package-lock.json         # Lockfile for npm installs
├── next.config.ts            # Next.js config
├── tsconfig.json             # TypeScript config
├── postcss.config.mjs        # PostCSS/Tailwind config
├── eslint.config.mjs         # ESLint setup extending Next.js defaults
├── .gitignore                # Standard Node/Next ignore rules
├── COMPONENT_USAGE_GUIDE.md  # Example UI component usage docs
├── UCLA.md                   # A small factual note about UCLA; not part of the app runtime
└── README.md                 # Project overview and setup instructions
```

## Application entry points

The app entry points are conventional Next.js files:

- `src/app/layout.tsx` creates the global HTML shell and top navigation.
- `src/app/page.tsx` renders the home page.
- `src/app/gallery/page.tsx` renders the gallery experience with search and tag filters.
- `src/app/upload/page.tsx` renders the upload interface.
- `src/app/admin/page.tsx` renders a mock admin dashboard.

The main reusable UI pieces are:

- `src/components/gallery/GalleryGrid.tsx`
- `src/components/upload/UploadZone.tsx`
- `src/components/ui/layout/*`
- `src/components/ui/cards/FeatureCard.tsx`
- `src/components/ui/stats/StatsGrid.tsx`

## Build, configuration, and deployment files

The repository includes standard Next.js configuration files:

- `package.json`: defines scripts (`dev`, `build`, `start`, `lint`) and dependency metadata
- `next.config.ts`: currently a minimal config stub with no custom deployment logic
- `tsconfig.json`: TypeScript settings with `@/*` alias resolution
- `postcss.config.mjs`: Tailwind/PostCSS integration
- `eslint.config.mjs`: ESLint config extending `next/core-web-vitals` and `next/typescript`
- `.gitignore`: excludes dependencies, build output, and env files

There is no explicit deployment config such as `vercel.json`, Dockerfile, Kubernetes manifests, or a cloud deployment workflow visible in the repo. The app is therefore clearly intended to run as a local Next.js app and be deployed by a generic Node/Next hosting target such as Vercel, Render, or a standard server environment.

## Testing approach and test locations

At the time of this review, there are no automated tests in the repository.

What is visible:

- no `__tests__` directory
- no Jest/Vitest config
- no Playwright/Cypress config
- no test scripts in `package.json` beyond `lint` and build

The validation path in this repo is therefore the existing static/build pipeline:

```bash
npm run lint
npm run build
```

This is the closest thing to a test strategy currently present in the repo. The codebase relies more on visual/manual verification than automated test coverage.

## How the major components interact

The app is a client-rendered UI demo built around mock data:

1. `src/app/*` pages compose larger UI sections using shared components.
2. Example data is stored in `src/lib/*.ts` as mock records (`mockPhotoData`, `mockAdminData`, etc.).
3. The gallery page uses `GalleryGrid` and passes in filter/search state such as selected tags and query string.
4. `GalleryGrid` filters `mockPhotos` client-side and renders cards with likes, downloads, views, and modal detail behavior.
5. `UploadZone` manages local file selection and simulates upload progress in the browser using `react-dropzone` and object URLs.
6. Reusable layout primitives (`Hero`, `SectionContainer`, `SectionTitle`, `FeatureCard`, `StatsGrid`) ensure stylistic consistency across the app.

The app does not currently include a backend API, database, authentication flow, or persistent storage. The data is mock-only and exists in-memory in the frontend.

## Setup and local execution instructions

### Requirements

- Node.js 18+
- npm

### Local setup

```bash
git clone https://github.com/arvindsing/UCLA.git
cd UCLA
npm install
npm run dev
```

Then open:

- http://localhost:3000

### Production build

```bash
npm run build
npm run start
```

### Linting

```bash
npm run lint
```

## Missing documentation, configuration issues, and improvement opportunities

Observable gaps in the repository:

- The repo name and app identity are slightly disconnected: the app is a photo gallery demo, while the repository is named `UCLA`.
- There is no real deployment configuration or environment variable documentation.
- There is no database or backend API, so the application is not production-ready for real uploads or persisted gallery data.
- There are no unit/integration tests, which makes regressions harder to catch.
- The sample images are placeholders or gradient blocks rather than real assets, which is appropriate for a demo but important to note if the app is meant to look production-ready.
- Several files in the repo are demo/training oriented (`demos/*`, `.github/prompts/*`, `.github/agents/*`) and do not affect runtime behavior directly.

## Conclusion

This repository is best understood as a demo-focused, front-end-only Next.js application for demonstrating UI craftsmanship and GitHub Copilot-assisted development. It is organized around a modern app-router structure, mock data, reusable React components, and a polished gallery/admin experience, but it is intentionally lightweight and not backed by a real persistence layer or production deployment configuration.

Anything that cannot be determined confidently from the repository alone:

- a production deployment target
- real user data or authentication model
- backend services or APIs
- actual test coverage or CI workflow details beyond the local lint/build commands
- any real-world photo assets beyond the placeholder demo content