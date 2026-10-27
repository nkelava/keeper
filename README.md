# Keeper

Keeper is a small note-taking app inspired by Google Keep, built with React. You type a title and some text, press the add button, and the note shows up as a card on the page. Each card has a delete button to remove it.

It is a front-end-only project: there is no backend or database, and notes live in React state. Refreshing the page clears them.

## Features

- **Create notes** with a title and content. The input area starts as a single "Create new note..." field and expands into a full form when you click it.
- **Validation on submit**: a note is only added when both the title and the content are filled in.
- **Delete notes** with the trash icon on each card.
- **Material UI icons and animations** (`@material-ui/core` and `@material-ui/icons`) for the add button, delete button and header icon.

## Tech stack

- [React 17](https://reactjs.org/) with function components and hooks (`useState`)
- [Material UI v4](https://v4.mui.com/) (`@material-ui/core`, `@material-ui/icons`)
- [Create React App](https://create-react-app.dev/) (`react-scripts` 5) for the dev server, build and tests
- Jest and React Testing Library for testing

## Prerequisites

- [Node.js](https://nodejs.org/) 14 or newer (the project builds on current LTS releases)
- npm (bundled with Node.js)

## Getting started

```bash
git clone https://github.com/nkelava/keeper.git
cd keeper
npm install
npm start
```

The development server opens the app at [http://localhost:3000](http://localhost:3000) and reloads when you edit files.

## Available scripts

| Command         | What it does                                                                 |
| --------------- | ---------------------------------------------------------------------------- |
| `npm start`     | Runs the app in development mode on port 3000.                               |
| `npm run build` | Creates an optimized production build in the `build/` folder.                |
| `npm test`      | Runs Jest in interactive watch mode.                                         |
| `npm run eject` | Copies the Create React App config into the project. This is irreversible.   |

The production build is a static site, so `build/` can be served by any static host, for example with `npx serve -s build`.

> **Note:** `src/components/App.test.js` is still the default Create React App test that looks for a "learn react" link, so `npm test` currently fails. It needs to be rewritten to match the Keeper UI.

## Project structure

```text
keeper/
├── public/
│   ├── index.html            # HTML shell with the #root mount point
│   └── robots.txt
├── src/
│   ├── index.js              # Entry point; renders <App /> into #root
│   ├── index.css             # Global base styles
│   ├── reportWebVitals.js    # Optional performance reporting (CRA default)
│   ├── setupTests.js         # Loads jest-dom matchers for tests
│   └── components/
│       ├── App.js            # Root component; holds the notes array and add/delete handlers
│       ├── App.css
│       ├── App.test.js       # Placeholder test (see note above)
│       ├── Header/           # App title bar with icon
│       ├── CreateArea/       # Expanding form for writing a new note
│       ├── NoteList/         # Maps the notes array to Note components
│       ├── Note/             # Single note card with delete button
│       └── Footer/           # Copyright line with the current year
├── package.json
└── package-lock.json
```

## How it works

`App` owns a single piece of state, an array of `{ title, content }` objects. It passes `onAddNote` down to `CreateArea` and `onDeleteNote` down through `NoteList` to each `Note`. Notes are identified by their position in the array, so deleting a note filters it out by index.

## Configuration

The app does not read any environment variables or config files. Create React App's standard options (such as `PORT=4000 npm start`) still apply if you need to change the dev server's behaviour.

## Contributing

Issues and pull requests are welcome. Useful next steps for the project include persisting notes (for example in `localStorage` or a backend), editing existing notes, and replacing the placeholder test.
