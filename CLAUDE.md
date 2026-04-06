# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an Expo React Native application using Expo Router for file-based routing. The project is set up with TypeScript in strict mode.

**Key Technologies:**
- Expo SDK ~55.0.11
- React Native 0.83.4
- React 19.2.0
- Expo Router ~55.0.10 (file-based routing)
- TypeScript 5.9.2 with strict mode
- React Navigation 7.x

**Project Structure:**
- `src/app/` - Application screens and layouts using file-based routing
  - `_layout.tsx` - Root layout component (Stack navigation)
  - `index.tsx` - Home screen
  - Additional screens follow Expo Router conventions: `[param]`, `(group)`, `+not-found.tsx`, etc.
- `assets/` - Images, icons, fonts, and other static assets
- `app.json` - Expo configuration (includes typedRoutes and reactCompiler experiments)
- `tsconfig.json` - TypeScript configuration with path aliases: `@/*` → `./src/*` and `@/assets/*` → `./assets/*`
- `expo-env.d.ts` - TypeScript declarations for Expo

## Common Development Commands

```bash
# Install dependencies
npm install

# Start development server
npm start
# or
npx expo start

# Platform-specific launches
npm run android   # Start with Android emulator
npm run ios       # Start with iOS simulator
npm run web       # Start in web browser

# Linting
npm run lint
# or
npx expo lint

# Reset project to blank template
npm run reset-project
```

## Architecture Notes

1. **Routing**: This project uses Expo Router with file-based routing. Screens in `src/app/` become routes automatically:
   - `src/app/index.tsx` → `/`
   - `src/app/about.tsx` → `/about`
   - `src/app/[id].tsx` → dynamic route with `id` param
   - `src/app/(group)/_layout.tsx` → nested layout within group

2. **Navigation**: The root layout (`_layout.tsx`) uses `<Stack />` from `expo-router` for stack navigation. To change navigation patterns, modify this file.

3. **Path Aliases**: Use `@/` for imports from `src/` and `@/assets/` for assets:
   ```typescript
   import Component from '@/components/Component';
   import image from '@/assets/image.png';
   ```

4. **Expo Router Stack**: The default stack navigation includes header handling, screen options, and linking configuration. See `expo-router` documentation for advanced configuration.

5. **React Compiler**: The project has `reactCompiler` experiment enabled in `app.json`. This enables automatic memoization in development. Be aware that React 19's compiler may affect how you write components.

## Development Guidelines

- Add new screens as files in `src/app/` following Expo Router conventions
- Use TypeScript for all new files
- Follow existing patterns for layout components and screen components
- Use Expo-compatible components; avoid direct React Native components when Expo alternatives exist
- Run `npm run lint` before committing to catch issues
- The project is configured with ESLint through Expo's default configuration

## Testing

Unit testing setup is not yet configured. To add Jest/Vitest, follow Expo's "Unit Testing with Jest" guide.
