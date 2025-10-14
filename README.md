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

## API Overview

The MoviesDatabase API provides comprehensive access to movie and TV show data including titles, cast information, ratings, and metadata. It offers powerful search and filtering capabilities with support for pagination, making it ideal for building movie discovery applications. The API returns structured JSON data with detailed information about entertainment content from various sources.

## Version

API Version: v1
Base URL: `https://moviesdatabase.p.rapidapi.com`

## Available Endpoints

- **`/titles`** - Retrieve movie and TV show titles with filtering options
- **`/titles/search/title/{title}`** - Search for titles by name
- **`/titles/{id}`** - Get detailed information about a specific title
- **`/titles/random`** - Get random movie/TV show suggestions
- **`/titles/utils/genres`** - Retrieve available genres
- **`/titles/utils/countries`** - Get list of available countries
- **`/titles/utils/languages`** - Fetch supported languages

## Request and Response Format

### Request Structure
```http
GET /titles?year=2023&genre=Action&limit=10&page=1
Host: moviesdatabase.p.rapidapi.com
X-RapidAPI-Key: YOUR_API_KEY
X-RapidAPI-Host: moviesdatabase.p.rapidapi.com
```

### Response Structure
```json
{
  "page": 1,
  "next": "/titles?year=2023&genre=Action&limit=10&page=2",
  "entries": 250,
  "results": [
    {
      "_id": "tt1234567",
      "id": "tt1234567",
      "primaryImage": {
        "id": "rm123456789",
        "width": 1080,
        "height": 1600,
        "url": "https://example.com/image.jpg",
        "caption": {
          "plainText": "Movie Title (2023)"
        }
      },
      "titleType": {
        "text": "Movie",
        "id": "movie",
        "isSeries": false,
        "isEpisode": false
      },
      "titleText": {
        "text": "Example Movie Title"
      },
      "originalTitleText": {
        "text": "Example Movie Title"
      },
      "releaseYear": {
        "year": 2023,
        "endYear": null
      },
      "releaseDate": {
        "day": 15,
        "month": 6,
        "year": 2023
      }
    }
  ]
}
```

## Authentication

The MoviesDatabase API uses RapidAPI authentication system:

### Required Headers
```http
X-RapidAPI-Key: YOUR_API_KEY
X-RapidAPI-Host: moviesdatabase.p.rapidapi.com
```

### Setup Steps
1. Sign up for a RapidAPI account at https://rapidapi.com
2. Subscribe to the MoviesDatabase API
3. Copy your API key from the dashboard
4. Add the key to your environment variables

### Environment Configuration
```env
MOVIES_API_KEY=your_rapidapi_key_here
```

## Error Handling

### Common Error Responses

**401 Unauthorized**
```json
{
  "message": "Invalid API key. Go to https://docs.rapidapi.com/docs/keys for more info."
}
```

**403 Forbidden**
```json
{
  "message": "You are not subscribed to this API."
}
```

**429 Too Many Requests**
```json
{
  "message": "Rate limit exceeded. Try again later."
}
```

**500 Internal Server Error**
```json
{
  "message": "Internal server error. Please try again later."
}
```

### Error Handling Best Practices
- Implement exponential backoff for rate limit errors
- Cache successful responses to reduce API calls
- Validate API responses before processing
- Provide fallback UI states for failed requests
- Log errors for debugging purposes

## Usage Limits and Best Practices

### Rate Limits
- **Free Tier**: 100 requests per month
- **Basic Plan**: 1,000 requests per month
- **Pro Plan**: 10,000 requests per month
- **Ultra Plan**: 100,000 requests per month

### Best Practices

1. **Caching Strategy**
   - Cache API responses for at least 1 hour
   - Use browser localStorage for client-side caching
   - Implement server-side caching for better performance

2. **Request Optimization**
   - Use pagination to limit response size
   - Request only necessary fields when possible
   - Batch multiple requests when appropriate

3. **Error Recovery**
   - Implement retry logic with exponential backoff
   - Provide meaningful error messages to users
   - Use circuit breaker pattern for API failures

4. **Security**
   - Never expose API keys in client-side code
   - Use environment variables for sensitive data
   - Implement server-side proxy for API calls

5. **Performance**
   - Use CDN for image assets when possible
   - Implement lazy loading for movie posters
   - Optimize API calls with debouncing for search

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