React Testing Library Project

Both projects are built with **React 18 + Vite**, tested with **Vitest** and
**React Testing Library (RTL)**, and linted with **ESLint**.

## Projects

### 1. `color-button`

A minimal demo app: a button that toggles between two colors and can be
disabled via a checkbox. Used to teach RTL fundamentals (queries, events,
`jest-dom` matchers).

- `src/App.jsx` — main component
- `src/App.test.jsx` — RTL tests
- `src/helpers.js` — utility (`kebabCaseToTitleCase`)

### 2. `sundaes-on-demand`

A multi-step "order a sundae" app (entry → summary → confirmation) built with
React Bootstrap. Used to teach more advanced RTL topics: context providers,
API mocking with **MSW (Mock Service Worker)**, user-event interactions, and
multi-page flows.

- `src/App.jsx` — switches between `OrderEntry`, `OrderSummary`,
  `OrderConfirmation` pages based on order phase
- `src/contexts/OrderDetails.jsx` — shared order state via React Context
- `src/pages/` — `entry`, `summary`, `confirmation` page components (each
  with co-located `tests/`)
- `src/mocks/` — MSW request handlers/server for mocking the backend API in
  tests
- Requires a backend API on `http://localhost:3030` for `npm run dev` (see
  below); tests run fully mocked and don't need the API server.

## Prerequisites

- Node.js (version pinned per-project in `.nvmrc`)
- npm

## Setup & Running

Each project is independent with its own dependencies. Run commands from
inside the project folder.

```sh
cd color-button        # or: cd sundaes-on-demand
npm install
```

### Run the dev server

```sh
npm run dev
```

Opens the app at the Vite dev URL printed in the terminal (`sundaes-on-demand`
is configured to run on **port 3000**).

> **Note:** `sundaes-on-demand` expects a companion sundae ordering API at
> `http://localhost:3030`. Without it, the "Order Entry" screen data (scoop
> and topping options) won't load in the browser — the automated tests,
> however, mock this API with MSW and don't require it running.

### Run tests

```sh
npm test
```

- `color-button`: runs `vitest` in watch mode.
- `sundaes-on-demand`: runs `vitest run` (single run). Use
  `npm run test:watch` for watch mode, or `npm run test:ui` for the Vitest UI.

### Lint

```sh
npm run lint
```

### Build for production

```sh
npm run build
npm run preview   # preview the production build locally
```

## Tech Stack

| Tool | Purpose |
|---|---|
| React 18 | UI library |
| Vite | Dev server & build tool |
| Vitest | Test runner |
| React Testing Library | Component testing |
| @testing-library/user-event | Simulating user interactions (sundaes-on-demand) |
| MSW (Mock Service Worker) | API mocking in tests (sundaes-on-demand) |
| React Bootstrap | UI components (sundaes-on-demand) |
| ESLint | Linting |

## Further Details

Each project folder has its own `README.md` documenting the step-by-step
setup used to configure Vitest, RTL, and ESLint from scratch — useful if
you want to replicate the setup in a new project.
