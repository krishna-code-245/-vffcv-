<style>
/* --- Core Variables & Reset --- */
:root {
    --bg-gradient: linear-gradient(135deg, #0f0c29, #302b63, #24243e);
    --text-color: white;
    --primary-accent: #4facfe;
    --secondary-accent: #00f2fe;
    --card-bg: rgba(255, 255, 255, 0.12);
    --input-bg: rgba(255, 255, 255, 0.9);
    --shadow-color: rgba(79,172,254,0.4);
    --font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
    --transition: all 0.3s ease;
}

* { box-sizing: border-box; } /* Ensures consistent box model */

body {
    font-family: var(--font-family);
    margin: 0;
    min-height: 100vh;
    background: var(--bg-gradient);
    color: var(--text-color);
    display: flex;
    flex-direction: column;
}

/* --- Layout --- */
.container {
    max-width: 1100px;
    margin: 0 auto;
    padding: 20px;
    width: 100%;
}

.content {
    display: flex;
    gap: 30px;
    align-items: flex-start; /* Better alignment for varying height components */
    flex-wrap: wrap;
}

/* --- Header & Navigation --- */
header { text-align: center; padding: 20px 20px 10px; }
header h1 {
    font-size: 2.5rem;
    background: linear-gradient(to right, var(--secondary-accent), var(--primary-accent));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    margin-bottom: 10px;
}

nav { text-align: center; margin-bottom: 20px; }
nav a {
    color: var(--primary-accent);
    text-decoration: none;
    margin: 0 15px;
    font-weight: bold;
    transition: var(--transition);
}
nav a:hover { text-decoration: underline; }

/* --- Main Content & Panels --- */
.main {
    flex: 2;
    background: var(--card-bg);
    backdrop-filter: blur(12px);
    padding: 30px;
    border-radius: 20px;
    box-shadow: 0 0 25px var(--shadow-color);
}

.main h2 { text-align: center; color: var(--primary-accent); margin-top: 0; }

/* --- Forms & Inputs --- */
label { display: block; margin-top: 15px; font-weight: bold; }
input, select {
    width: 100%;
    padding: 12px;
    margin-top: 6px;
    border-radius: 10px;
    border: none;
    outline: none;
    background: var(--input-bg);
    color: #333;
    font-size: 15px;
    transition: var(--transition);
}
input:focus, select:focus { box-shadow: 0 0 10px var(--primary-accent); }

input[type=submit] {
    margin-top: 25px;
    background: linear-gradient(135deg, var(--primary-accent), var(--secondary-accent));
    color: black;
    font-weight: bold;
    cursor: pointer;
    transition: var(--transition);
}
input[type=submit]:hover {
    transform: scale(1.02);
    box-shadow: 0 0 20px var(--primary-accent);
}

#status {
    margin-top: 15px;
    font-weight: bold;
    color: var(--secondary-accent);
    text-align: center;
}

/* --- Sidebar --- */
.sidebar {
    flex: 1;
    text-align: center;
    min-width: 250px; /* Prevents too narrow sidebar */
}
.sidebar img {
    max-width: 100%;
    height: auto;
    border-radius: 20px;
    filter: drop-shadow(0 0 10px rgba(255,255,255,0.2));
}

/* --- Footer --- */
footer {
    text-align: center;
    padding: 15px;
    color: #ccc;
    margin-top: auto; /* Pushes footer down */
}

/* --- Responsive Media Queries --- */
@media (max-width: 768px) {
    .content { flex-direction: column; }
    .sidebar { order: -1; } /* Puts sidebar on top on mobile */
    .main { padding: 20px; }
}
</style>
