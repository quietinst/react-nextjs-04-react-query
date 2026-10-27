# 04 — React Query

🔗 [Live demo](https://react-nextjs-04-react-query.vercel.app)

The movie search app from the previous module, extended with pagination. Search
movies on TMDB by keyword, browse the results page by page, and open any movie
in a modal with its details.

Here the data fetching moves from manual state to TanStack Query, which stores
the server responses and tracks the request status.

## Features

- Search movies by keyword (form handled with Form Actions)
- Pagination with React Paginate, shown only when the search has more than one
  page
- Request state (loading, error, data) managed by TanStack Query
- Loader while the request is in flight, error message if it fails
- Toast notifications for an empty query and for "no movies found"
- Modal with backdrop image, overview, release date, and rating, rendered
  through a portal

## Tech stack

- React + TypeScript
- Vite
- TanStack Query
- React Paginate
- Axios
- React Hot Toast
- CSS Modules
- modern-normalize
- TMDB API

## Project structure

```text
src/
├── components/
│   ├── App/
│   ├── SearchBar/
│   ├── MovieGrid/
│   ├── Loader/
│   ├── ErrorMessage/
│   └── MovieModal/
├── services/
│   └── movieService.ts
├── types/
│   └── movie.ts
└── main.tsx
```

Each component folder contains the component (`.tsx`) and its styles
(`.module.css`). The shared `Movie` type lives in `src/types/movie.ts`. The
query client is configured in `src/main.tsx`, and the query hook is used
directly in `App`.

## Getting started

Get an access token on [TMDB](https://www.themoviedb.org/) and put it in a local
`.env` file (never commit it):

```bash
cp .env.example .env   # then set VITE_TMDB_TOKEN
npm install
npm run dev
```

## Concepts covered

| Concept                                             | Where                                                    |
| --------------------------------------------------- | -------------------------------------------------------- |
| Server state with TanStack Query                    | `QueryClientProvider` in `main.tsx`, `useQuery` in `App` |
| Query keys that depend on the search query and page | `App`                                                    |
| Pagination (`page`, `total_pages`)                  | `movieService.ts`, `App`                                 |
| Paginated UI with React Paginate                    | `App`                                                    |
| Typed HTTP requests with Axios                      | `movieService.ts`                                        |
| Portals                                             | `MovieModal`                                             |
