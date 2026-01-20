# Google OAuth Login/Signup

A React application with Google OAuth authentication using Google Identity Services.

## Tech Stack

- React 19
- TypeScript
- Vite
- React Router DOM
- @react-oauth/google

## Design Decisions

### Authentication Flow

1. **Login** - User clicks the Google Sign-In button, and Google returns a JWT credential after successful authentication
2. **JWT Decode** - The Google JWT is decoded to extract user info (name, email, picture)
3. **Storage** - User data is stored in `localStorage` and React state via Context API

### State Management

- **React Context** (`AuthContext.tsx`) - Provides authentication state across the app
- **localStorage** - Persists user session across browser refreshes
- **No external state library** - Keeps dependencies minimal for this use case

### Token-Based Authentication

The app uses a token-based approach:

- Google issues a signed JWT containing user information
- The JWT is decoded client-side to extract user details
- User data is stored locally (no server-side session storage needed)
- Stateless authentication that scales easily

## Getting Started

1. Install dependencies:
   ```bash
   npm install
   ```

2. Create a `.env` file with your Google Client ID:
   ```
   VITE_GOOGLE_CLIENT_ID=your_client_id_here
   ```

3. Run the development server:
   ```bash
   npm run dev
   ```

## Project Structure

```
src/
├── context/
│   └── AuthContext.tsx    # Authentication context provider
├── pages/
│   ├── LoginPage.tsx      # Login page with Google Sign-In
│   ├── LoginPage.css
│   ├── Dashboard.tsx      # Protected dashboard page
│   ├── Dashboard.css
│   └── jwtDecode.ts       # JWT decoding utility
├── App.tsx                # Main app with routing
└── main.tsx               # Entry point
```
