# Memora

Memora combines a **spaced-repetition study tracker** with a **personal file-storage platform**. It is a collection of two independent full-stack applications, each with its own React client and Express/MongoDB server.

## Projects

### Memory Revision

Create an account and manage study tasks with review intervals. The app includes views for today's reviews, all tasks, upcoming reviews, and progress statistics. Completing reviews advances tasks through Day 1, Day 3, Day 7, and Day 14 intervals.

- Client: `memory-revision-client/` (React, Vite)
- Server: `memory-revision-server/` (Express, MongoDB)
- API port: `5000`

### Storage Platform

Create an account and organize files in directories. The app supports creating and renaming directories, uploading and downloading files, and deleting files or directories.

- Client: `storage-client/` (React, Vite)
- Server: `storage-server/` (Express, MongoDB)
- API port: `4000`

## Requirements

- Node.js and npm
- MongoDB running locally at `mongodb://127.0.0.1:27017`

The memory revision server reads its MongoDB connection string and JWT signing key from environment variables. Create `memory-revision-server/.env` with:

```env
MONGO_URI=mongodb://127.0.0.1:27017/memoryRevision
JWT_SECRET=replace-this-with-a-long-random-secret
```

Do not commit `.env` files or real secrets. The storage server currently connects to the local `storageApp` database directly in its source.

## Install

Run `npm install` in each of the four project folders:

```powershell
cd memory-revision-client
npm install

cd ..\memory-revision-server
npm install

cd ..\storage-client
npm install

cd ..\storage-server
npm install
```

## Run locally

Start MongoDB first. Then run the selected application with separate terminals.

### Memory Revision

Terminal 1:

```powershell
cd memory-revision-server
node app.js
```

Terminal 2:

```powershell
cd memory-revision-client
npm run dev
```

Open the Vite URL shown in the terminal (normally `http://localhost:5173`).

### Storage Platform

Terminal 1:

```powershell
cd storage-server
npm run dev
```

Terminal 2:

```powershell
cd storage-client
npm run dev
```

Open the Vite URL shown in the terminal (normally `http://localhost:5173`).

Both clients use port `5173` by default, so run one client at a time unless you also update the relevant server's CORS origin and the Vite port configuration.

## Repository layout

```text
memory-revision-client/   Memory revision web app
memory-revision-server/   Memory revision API
storage-client/           File storage web app
storage-server/           File storage API and local file data
```
