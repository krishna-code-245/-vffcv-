<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Study Tracker</title>
    <style>
        /* CSS remains the same as provided previously */
        :root {
            --primary-gradient: linear-gradient(135deg, #0f0c29, #302b63, #24243e);
            --accent-gradient: linear-gradient(to right, #00f2fe, #4facfe);
            --accent-color: #4facfe;
            --glass-bg: rgba(255, 255, 255, 0.12);
            --input-bg: rgba(255, 255, 255, 0.9);
        }
        body {
            font-family: 'Segoe UI', sans-serif;
            margin: 0;
            min-height: 100vh;
            background: var(--primary-gradient);
            color: white;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }
        .container {
            max-width: 900px;
            width: 100%;
            display: flex;
            gap: 40px;
            background: var(--glass-bg);
            backdrop-filter: blur(12px);
            padding: 40px;
            border-radius: 30px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.3);
        }
        .form-section { flex: 1.5; }
        .mascot-section { flex: 1; text-align: center; }
        h2 { color: var(--accent-color); }
        input, select {
            width: 100%;
            padding: 12px;
            margin-top: 8px;
            border-radius: 10px;
            border: none;
            background: var(--input-bg);
            box-sizing: border-box;
        }
        input[type="submit"] {
            background: var(--accent-gradient);
            margin-top: 25px;
            font-weight: bold;
            cursor: pointer;
        }
        .btn-group { display: flex; gap: 10px; margin-top: 20px; }
        button { flex: 1; padding: 12px; border-radius: 10px; border: 1px solid white; background: none; color: white; cursor: pointer; }
        #output { margin-top: 20px; padding: 10px; background: rgba(0,0,0,0.2); border-radius: 10px; }
        .mascot-img { max-width: 150px; filter: drop-shadow(0 0 10px var(--accent-color)); }
        @media (max-width: 768px) { .container { flex-direction: column; } }
    </style>
</head>
<body>

<div class="container">
    <div class="form-section">
        <h2>User Study Data</h2>
        <form onsubmit="saveData(event)">
            <label>Name</label>
            <input type="text" id="username" required>

            <label>Subject</label>
            <select id="subject">
                <option value="Physics">Physics</option>
                <option value="Chemistry">Chemistry</option>
                <option value="General Maths">General Maths</option>
            </select>

            <label>Class</label>
            <select id="classType">
                <option value="JEE">JEE</option>
                <option value="NEET">NEET</option>
            </select>

            <label>Daily Study Hours</label>
            <input type="number" id="hours" required>

            <input type="submit" value="Save Data">
        </form>

        <div class="btn-group">
            <button onclick="loadData()">Load Data</button>
            <button onclick="clearData()">Clear</button>
        </div>
        <p id="output"></p>
    </div>

    <div class="mascot-section">
        <img src="https://vecteezy.com" class="mascot-img">
        <p id="motivation">"Ready to work?"</p>
    </div>
</div>

<script>
    // GitHub Pages stores all your repos under one domain. 
    // Using a unique key prevents data mixing between projects.
    const STORAGE_KEY = "study_tracker_v1"; 

    function saveData(event) {
        event.preventDefault();
        const data = {
            name: document.getElementById("username").value,
            subject: document.getElementById("subject").value,
            classType: document.getElementById("classType").value,
            hours: document.getElementById("hours").value
        };
        localStorage.setItem(STORAGE_KEY, JSON.stringify(data));
        alert("Saved to browser!");
    }

    function loadData() {
        const saved = localStorage.getItem(STORAGE_KEY);
        const out = document.getElementById("output");
        if (saved) {
            const data = JSON.parse(saved);
            out.innerHTML = `Name: ${data.name}<br>Subject: ${data.subject}<br>Hours: ${data.hours}`;
        } else {
            out.textContent = "No data found.";
        }
    }

    function clearData() {
        localStorage.removeItem(STORAGE_KEY);
        document.getElementById("output").textContent = "";
        alert("Cleared!");
    }
</script>
</body>
</html>
