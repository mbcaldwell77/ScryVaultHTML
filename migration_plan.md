### **Project Upgrade: Migrating ScryVault to React**

This plan outlines the process of converting our single-page HTML application into a modern, component-based React application. This will make the app faster, easier to maintain, and much simpler to add new features to in the future.

#### **Phase 1: Setup & Core Components (The Foundation)**

The goal of this phase is to break the UI into logical, reusable pieces, just like building with LEGOs instead of trying to carve everything from one block of wood.

1.  **Initial Setup:**
    * We will use `Vite` to create a new, clean React project. This is a fast, modern tool for building web apps.
    * We will install and configure **Tailwind CSS** for styling, just like we have now.

2.  **Componentization (Breaking it Down):**
    * We'll convert the existing HTML into a set of clean, focused React components. Each will have its own file, making edits much easier.
    * **`App.js`**: The main hub that will manage which screen is visible (Login or the main App).
    * **`Auth.js`**: A component dedicated solely to the login and registration forms.
    * **`Header.js`**: For the "ScryVault" title and the "Logout" button.
    * **`Controls.js`**: For the Search, Sort, and View Toggle buttons.
    * **`BookList.js`**: This component's only job will be to display the list of books.
    * **`BookCard.js`**: For a single book entry, including its accordion and inventory. This makes it easy to change the layout of one card without breaking the others.
    * **`Modal.js`**: A generic modal that we can reuse for adding books, editing copies, showing AI descriptions, etc.

#### **Phase 2: State Management & Data Flow (The Brains)**

This phase is about managing data cleanly and efficiently. Instead of manually touching the DOM, we'll tell React what the data is, and it will handle updating the UI automatically.

1.  **Authentication State:**
    * `App.js` will hold the master state of whether a user is logged in or out.
    * It will show either the `Auth.js` component or the main application components based on this state.

2.  **Collection State:**
    * The main `App.js` will be responsible for fetching and holding the entire book collection in its state.
    * This collection data will be passed down to child components (`BookList`, `BookCard`) as "props." This is a one-way data flow that prevents the kind of cascading bugs we experienced.

3.  **Data Fetching & API Calls:**
    * We will use React's built-in `useEffect` hook to fetch data from Supabase when the application first loads for a logged-in user.
    * All API calls (to Google Books or Gemini) will be neatly contained within the specific functions that need them.

#### **Phase 3: Rebuilding Functionality (The Action)**

This is where we bring the app back to life, but in a much more organized way.

1.  **Refactor All Functions:**
    * Every JavaScript function from our old file (e.g., `lookupISBN`, `handleAddCopy`, `generateDescription`) will be moved into the React component where it's actually used.
    * DOM manipulation will be eliminated. Instead of `document.getElementById(...)`, we will simply update the state, and React will handle the rest. This is the core benefit that will make future edits painless.

2.  **User Experience:**
    * With this new structure, the app will feel faster and more responsive to you as a user.
    * Because we've separated our concerns, adding new features in the future (like a dashboard for Ældern Tomes, sales analytics, or CSV export) will be straightforward and won't risk breaking existing functionality.

This is a robust plan that addresses all the issues we've run into. It's the right way forward. When you're ready, we can start with Phase 1.
