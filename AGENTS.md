# Dev Agent Manifest — Mountain Medicine Catering

This file defines agent roles, responsibilities, file ownership, and communication protocols for this repo. It is used by Claude, Codex, and ChatGPT as a shared contract.

## 🧠 Architecture Summary

The app is migrating from a Streamlit-based UI to a fully Firebase-hosted frontend using React (or Svelte), Firebase Auth, Firestore, and Cloud Functions.

Firebase Hosting will serve the app shell (`index.html`), React components, and static files.

## 🧱 Stack Overview

- **Frontend**: React + Tailwind (or Svelte) hosted via Firebase Hosting
- **Backend**: Firebase Cloud Functions (Node.js preferred)
- **Database**: Firestore (users, recipes, events, files, tags, etc.)
- **Auth**: Firebase Auth (Google sign-in + token persistence)
- **Storage**: Firebase Storage for file uploads
- **AI**: OpenAI API via Cloud Function middleware

## 🧠 Agent Roles

### Architect Agent (ChatGPT, Claude)

- Decomposes high-level feature specs
- Defines module structure and component ownership
- Maintains this file

### Builder Agent (Codex, GPT-4 Code Interpreter)

- Writes and modifies:
  - React components
  - Firebase functions
  - Firestore queries
  - Utility scripts
- Obeys file boundaries from Architect Agent

### Memory Agent

- Indexes file structure and API surface
- Resolves inter-component dependencies
- Maintains shared context state in memory or `filemap.json`

### Executor Agent (Optional)

- Uses CLI tools to:
  - Run `firebase deploy`
  - Run `npm run dev`
  - Build local functions with `esbuild` or `tsc`
  - Output logs to `/logs`

## 🎯 Migration Phases

### Phase 1: Core Shell

- [ ] Create `index.html` for hosting
- [ ] Build router + layout
- [ ] Set up Firebase Auth
- [ ] Add tabbed navigation
- [ ] Redirect based on login status

### Phase 2: Feature Parity with Streamlit

- [ ] Rebuild “Dashboard” view
- [ ] Implement Events tab
- [ ] Port Recipes & Menus
- [ ] Add File Upload system
- [ ] Restore assistant UI (chat)

### Phase 3: Expandability

- [ ] Offline/PWA support
- [ ] Notifications
- [ ] Multi-user scheduling
- [ ] Tag constellation graph

