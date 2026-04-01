Overview

Project: React app using Vite with routes and Tailwind.
Entry files: index.html → src/main.jsx → src/App.jsx.
Render flow

index.html: contains <div id="root">.
src/main.jsx: imports index.css, wraps App in BrowserRouter + StrictMode, and mounts to #root.
src/App.jsx: top-level layout: Navbar, Navbar2, Routes, Footer. Routes decides which page component renders.
Routing

Router: BrowserRouter enables client-side routing.
Route config: Routes + Route map paths to components, e.g. path='/' → Home.
Nested routes: Product uses <Outlet /> and Route path='/product' element={<Product/>}> with child routes (men, women, kids) — these render inside Product's <Outlet />.
Dynamic params: Route path='/courses/:courseId' and useParams() in CourseDetails.jsx read courseId.
Pages & Components

Pages folder: src/pages/* (Home, About, Product, Course, CourseDetails, Mens/Womens/Kids, NotFound).
Components: src/components/* (Navbar, Navbar2, Footer). Navbar uses Link for navigation; Navbar2 uses useNavigate() for programmatic navigation.
Tailwind

CSS entry: src/index.css has @import "tailwindcss";.
Plugin: vite.config.js includes @tailwindcss/vite plugin — Vite builds Tailwind during dev.
If styles not applied: ensure tailwind.config.* exists, restart dev server.
Common issues & fixes

Blank page: usually caused by runtime errors (e.g., wrong imports or using React.StrictMode without importing React). Check browser console and terminal. Fixed here by matching import filenames and using the imported StrictMode.
Wrong import paths/casing: filenames like Mens.jsx vs Men.jsx will break resolution—use exact names.
Port conflicts: Vite may pick another port (e.g., 5174) if 5173 in use.
How to explain this to someone

Start with the render flow: "index → main → App → Routes → Page".
Explain routing with an example: nested Product page shows its links and the child route content via Outlet.
Show dynamic route: "/courses/react maps to CourseDetails where useParams().courseId === 'react'".
Run & debug steps

To run:
cd into advance-routing
npm run dev
If blank or errors:
Open browser console and terminal logs.
Look for "Failed to resolve import" (fix path/casing).
Restart dev server after changes.
