# CineSeek - Movie Discovery Application

A modern movie discovery application built with Next.js, TypeScript, and Tailwind CSS that allows users to browse movies from the MoviesDatabase API, view movie details, and search for films by year or genre.

## Features

- Browse movies with pagination
- Search movies by year and genre
- View detailed movie information
- Responsive design for all devices
- Server-side API integration
- TypeScript for type safety
- Modern UI with Tailwind CSS

## Tech Stack

- **Framework**: Next.js 14 (Pages Router)
- **Language**: TypeScript
- **Styling**: Tailwind CSS
- **Icons**: Font Awesome
- **API**: MoviesDatabase API

## Prerequisites

- Node.js (v16 or higher)
- npm or yarn
- Git

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd alx-movie-app
```

2. Install dependencies:
```bash
npm install
# or
yarn install
```

3. Create environment file:
```bash
cp .env.example .env.local
```

4. Add your MoviesDatabase API key to `.env.local`:
```
MOVIES_API_KEY=your_api_key_here
```

5. Run the development server:
```bash
npm run dev
# or
yarn dev
```

6. Open [http://localhost:3000](http://localhost:3000) in your browser.

## Project Structure

```
alx-movie-app/
├── components/
│   ├── commons/
│   │   ├── Button.tsx          # Reusable button component
│   │   ├── Loading.tsx         # Loading spinner component
│   │   └── MovieCard.tsx       # Movie display card
│   └── layouts/
│       ├── Footer.tsx          # Application footer
│       ├── Header.tsx          # Application header
│       └── Layout.tsx          # Main layout wrapper
├── interfaces/
│   └── index.ts                # TypeScript interfaces
├── pages/
│   ├── api/
│   │   └── fetch-movies.ts     # API route for movie data
│   ├── movies/
│   │   └── index.tsx           # Movies listing page
│   ├── _app.tsx                # Next.js app component
│   └── index.tsx               # Home page
├── public/                     # Static assets
├── styles/
│   └── globals.css             # Global styles
├── .env.local                  # Environment variables
├── .eslintrc.json             # ESLint configuration
├── .gitignore                 # Git ignore rules
├── next.config.js             # Next.js configuration
├── package.json               # Dependencies and scripts
└── tsconfig.json              # TypeScript configuration
```

## API Integration

### MoviesDatabase API

The application integrates with the MoviesDatabase API using the following endpoints:

- **`/titles`** - Main endpoint for fetching movie data
  - Supports filtering by year and genre
  - Implements pagination for browsing results
  - Requires API key authentication

### Authentication

- API key authentication via headers
- Environment variable storage for secure API key management
- Server-side API routes to protect client-side exposure

### Error Handling

- Loading states for better user experience
- Try/catch blocks in API routes
- Status code validation for API responses
- Type guards for API data validation

## Development Guidelines

### Code Quality

- TypeScript interfaces for all props and API responses
- Component-based architecture with clear separation of concerns
- Proper error handling in all API requests
- Loading states for enhanced UX
- Environment variables for sensitive data

### Performance

- Client-side navigation with Next.js router
- Efficient API calls with pagination
- Responsive design with Tailwind CSS
- Image optimization with Next.js Image component

### Maintainability

- Consistent code formatting with ESLint
- Clear and logical folder structure
- Reusable component architecture
- Comprehensive TypeScript typing
- Well-documented code

## Available Scripts

```bash
# Development
npm run dev          # Start development server
npm run build        # Build for production
npm run start        # Start production server
npm run lint         # Run ESLint
npm run type-check   # Run TypeScript compiler
```

## Environment Variables

Create a `.env.local` file in the root directory:

```env
MOVIES_API_KEY=your_moviesdb_api_key
NEXT_PUBLIC_APP_URL=http://localhost:3000
```

## Usage Considerations

- **Rate Limiting**: API has usage limits - implement appropriate caching
- **Pagination**: Use pagination to limit request sizes
- **Error Boundaries**: Implement graceful failure handling
- **Client-side Caching**: Cache responses where appropriate

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## Learning Objectives

This project demonstrates:

- API documentation understanding and integration
- TypeScript interface implementation for API responses
- Reusable React component creation
- Responsive layout building with Tailwind CSS
- Application state management for filtering and pagination
- Proper error handling and loading state implementation
- Next.js API routes setup for server-side data fetching
- Environment variable management for API keys

## License

This project is part of the ALX Software Engineering Program.

## Support

For support and questions, please refer to the project documentation or contact the development team.