# Dreamlytics Developer Guide

> This guide provides detailed instructions for developers working on the Dreamlytics project. It covers project setup, development workflow, code structure, conventions, testing, deployment, and troubleshooting.

---

## 1. Project Overview
Dreamlytics is a full-stack Nuxt 3 + Capacitor application for AI-powered dream analysis and journaling. The backend uses Nuxt API routes and MongoDB, while the frontend is built with Vue 3 and SCSS. Mobile builds are supported via Capacitor for Android.

---

## 2. Prerequisites
- Node.js (v18+ recommended)
- npm (v9+ recommended)
- MongoDB (local or cloud)
- Android Studio (for mobile builds)
- Git

---

## 3. Getting Started
### Clone the repository
```bash
git clone <repo-url>
cd app
```

### Install dependencies
```bash
npm install
```

### Configure environment variables
Create a `.env` file in the root directory:
```
MONGODB_URI=<your-mongodb-uri>
OPENROUTER_API_KEY=<your-openrouter-api-key>
```

---

## 4. Development Workflow
### Start the development server
```bash
npm run dev
```
- The app runs at `http://localhost:3000`
- Hot-reload is enabled

### Linting
```bash
npm run lint
```
- Uses ESLint and Prettier for code style enforcement

### Build for production
```bash
npm run build
```

---

## 5. Mobile Development (Android)
1. Build the web app:
   ```bash
   npm run build
   ```
2. Copy assets to Android:
   ```bash
   npx cap copy android
   ```
3. Open Android Studio:
   ```bash
   npx cap open android
   ```
4. Build and run the app on an emulator or device.

---

## 6. Project Structure
```
app/
├── assets/           # Images, fonts, styles
├── composables/      # Vue composables (API, auth, analytics)
├── pages/            # Nuxt pages (views)
├── plugins/          # Nuxt/Vue plugins
├── public/           # Static assets
├── server/
│   ├── api/          # API endpoints
│   ├── models/       # Mongoose models
│   └── utils/        # Utility functions
├── package.json      # Project metadata
├── nuxt.config.ts    # Nuxt config
├── capacitor.config.ts # Capacitor config
├── tsconfig.json     # TypeScript config
└── .env              # Environment variables
```

---

## 7. Coding Conventions
- Use TypeScript for all code
- Use Composition API in Vue components
- Organize composables by feature
- Use SCSS for styles, keep variables in `assets/styles/variables.scss`
- API endpoints: validate input with Zod
- Use async/await for all asynchronous code
- Write clear, descriptive comments

---

## 8. Testing
- Unit tests recommended for composables and server logic
- Use Vitest or Jest (setup required)
- Manual testing via frontend and API endpoints

---

## 9. Deployment
- Build the app: `npm run build`
- Deploy static files to your chosen host (Vercel, Netlify, etc.)
- Ensure environment variables are set on the host
- For mobile, build and deploy via Android Studio

---

## 10. Troubleshooting
- **MongoDB connection errors:** Check your URI and network
- **API key errors:** Ensure `OPENROUTER_API_KEY` is valid
- **Build errors:** Run `npm run lint` and check TypeScript errors
- **Mobile build issues:** Ensure Capacitor and Android Studio are up to date

---

## 11. Useful Commands
- `npm run dev` – Start development server
- `npm run build` – Build for production
- `npm run lint` – Lint code
- `npx cap open android` – Open Android project

---

## 12. Resources
- [Nuxt Documentation](https://nuxt.com/docs)
- [Capacitor Documentation](https://capacitorjs.com/docs)
- [MongoDB Documentation](https://www.mongodb.com/docs)
- [OpenRouter API](https://openrouter.ai/docs)

---

## 13. Contributing
- Fork the repository
- Create a feature branch
- Commit changes with clear messages
- Submit a pull request

---

## 14. Contact
- For questions or issues, open a GitHub issue or contact the maintainer.

---

> Last updated: 2025-11-18
