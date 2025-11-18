# MWAD---SPA

# DEVOLOPED BY : ADITYAH M S
# REGISTER NO. : 212223220002

# AIM :
To develop a Single Page Application (SPA) using React and React Router that includes:

Home Page

Login Page

Dashboard Section (Protected)

Nested Dashboard Pages: Profile, Settings, Notifications

Protected Routing so only logged-in users can access dashboard pages.

# SOFTWARE & LIBRARIES USED

React

React Router DOM (v6+)

JavaScript (ES6)

Node.js & npm

VS Code

# PROCEDURE
Step 1: Create React App
npx create-react-app my-spa
cd my-spa

Step 2: Install React Router
npm install react-router-dom

Step 3: Create required folders
src -
 pages
 components
 App.js
 index.js

Step 4: Build pages (Home, Login, Dashboard, Profile, Settings, Notifications)

Write components inside src/pages.

Step 5: Implement ProtectedRoute

A higher-order component that checks login status.

Step 6: Configure routing in App.js

Add nested routes under /dashboard.

Step 7: Start the project

npm start

# CODES :

# index.js :
```
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<App />);

```
# App.js :
```
import React, { useState } from "react";
import { BrowserRouter, Routes, Route } from "react-router-dom";

import Home from "./pages/Home";
import Login from "./pages/Login";
import Dashboard from "./pages/Dashboard";
import Profile from "./pages/Profile";
import Settings from "./pages/Settings";
import Notifications from "./pages/Notifications";
import ProtectedRoute from "./components/ProtectedRoute";

function App() {
  const [isLoggedIn, setIsLoggedIn] = useState(false);

  return (
    <BrowserRouter>
      <Routes>

        <Route path="/" element={<Home />} />

        <Route
          path="/login"
          element={<Login setIsLoggedIn={setIsLoggedIn} />}
        />

        <Route
          path="/dashboard/*"
          element={
            <ProtectedRoute isLoggedIn={isLoggedIn}>
              <Dashboard />
            </ProtectedRoute>
          }
        >
          <Route path="profile" element={<Profile />} />
          <Route path="settings" element={<Settings />} />
          <Route path="notifications" element={<Notifications />} />
        </Route>

      </Routes>
    </BrowserRouter>
  );
}

export default App;

```
# ProtectedRoute.js :
```
import { Navigate } from "react-router-dom";

export default function ProtectedRoute({ isLoggedIn, children }) {
  if (!isLoggedIn) {
    return <Navigate to="/login" replace />;
  }
  return children;
}

```
# Home.js :
```
import { Link } from "react-router-dom";

export default function Home() {
  return (
    <div>
      <h1>Home Page</h1>
      <Link to="/login">Login</Link>
    </div>
  );
}

```
# Login.js :
```
import React, { useState } from "react";
import { useNavigate } from "react-router-dom";

export default function Login({ setIsLoggedIn }) {
  const [name, setName] = useState("");
  const navigate = useNavigate();

  const handleLogin = () => {
    if (name.trim() !== "") {
      setIsLoggedIn(true);
      navigate("/dashboard");
    } else {
      alert("Enter a username to login");
    }
  };

  return (
    <div>
      <h1>Login Page</h1>
      <input
        type="text"
        placeholder="Enter name"
        onChange={(e) => setName(e.target.value)}
      />
      <button onClick={handleLogin}>Login</button>
    </div>
  );
}

```
# Dashboard.js :
```
import { Link, Outlet } from "react-router-dom";

export default function Dashboard() {
  return (
    <div>
      <h1>Dashboard</h1>

      <nav>
        <Link to="profile">Profile</Link> |{" "}
        <Link to="settings">Settings</Link> |{" "}
        <Link to="notifications">Notifications</Link>
      </nav>

      <Outlet />
    </div>
  );
}

```
# Profile.js :
```
export default function Profile() {
  return <h2>Profile Section</h2>;
}

```
# Settings.js :
```
export default function Settings() {
  return <h2>Settings Section</h2>;
}

```
# Notifications.js :
```
export default function Notifications() {
  return <h2>Notifications Section</h2>;
}

```
# OUTPUT :

<img width="1919" height="1014" alt="image" src="https://github.com/user-attachments/assets/a9901bca-c8d3-4130-a2d3-ff69effe2dbc" />
<img width="1919" height="1015" alt="image" src="https://github.com/user-attachments/assets/f4790fe7-4dea-4d4a-acf2-4ed923513e8c" />
<img width="1919" height="1016" alt="image" src="https://github.com/user-attachments/assets/ecfdf89a-4c4d-49b5-a70c-8357a00302a6" />
<img width="1919" height="1018" alt="image" src="https://github.com/user-attachments/assets/4e58f3b0-d07d-46aa-b3df-189d02f6d691" />
<img width="1919" height="1014" alt="image" src="https://github.com/user-attachments/assets/6ba574a1-fcb6-4620-af55-4f5f4ad439ea" />

