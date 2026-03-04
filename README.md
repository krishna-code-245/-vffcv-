<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>User Data Form</title>
    <style>
        :root {
            --primary-gradient: linear-gradient(135deg, #0f0c29, #302b63, #24243e);
            --accent-gradient: linear-gradient(to right, #00f2fe, #4facfe);
            --accent-color: #4facfe;
            --glass-bg: rgba(255, 255, 255, 0.12);
            --input-bg: rgba(255, 255, 255, 0.9);
            --transition: all 0.2s ease-in-out;
        }

        body {
            font-family: 'Segoe UI', system-ui, sans-serif;
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
            align-items: flex-start;
            background: var(--glass-bg);
            backdrop-filter: blur(12px);
            padding: 40px;
            border-radius: 30px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.3);
        }

        .form-section { flex: 1.5; }
        .mascot-section { 
            flex: 1; 
            text-align: center;
            position: sticky;
            top: 20px;
        }

        h2, h3 { color: var(--accent-color); margin-top: 0; }

        label { display: block; margin-top: 15px; font-weight: 600; font-size: 0.9rem; }

        input, select {
            width: 100%;
            padding: 12px;
            margin-top: 8px;
            border-radius: 10px;
            border: none;
            outline: none;
            background: var(--input-bg);
            color: #333;
            box-sizing: border-box;
            transition: var(--transition);
        }

        input:focus, select:focus { box-shadow: 0 0 0 3px var(--accent-color); }

        .btn-group { display: flex; gap: 10px; margin-top: 20px; }

        button, input[type="submit"] {
            flex: 1;
            padding: 12px;
            border-radius: 10px;
            border: none;
            font-weight: bold;
            cursor: pointer;
            transition: var(--transition);
        }

        input[type="submit"] {
            background: var(--accent-gradient);
            color: #000;
            margin-top: 25px;
            width: 100%;
        }

        button { background: rgba(255,255,255,0.1); color: white; border: 1px solid rgba(255,255,255,0.2); }
        button:hover { background: rgba(255,255,255,0.2); }
        input[type="submit"]:hover { transform: translateY(-2px); box-shadow: 0 5px 15px rgba(79, 172, 254, 0.4); }

        #output {
            margin-top: 20px;
            padding: 15px;
            background: rgba(0,0,0,0.2);
            border-radius: 10px;
            border-left: 4px solid var(--accent-color);
            line-height: 1.6;
        }

        .mascot-img {
            max-width: 200px;
            filter: drop-shadow(0 0 15px var(--accent-color));
            margin-bottom: 15px;
        }

        .speech-bubble {
            background: white;
            color: #333;
            padding: 12px;
            border-radius: 15px;
            font-size: 0.85rem;
            position: relative;
            font-style: italic;
        }

        @media (max-width: 768px) {
            .container { flex-direction: column; align-items: center; }
            .mascot-section { order: -1; }
        }
    </style>
</head>
<body>

<div class="container">
    <div class="form-section">
        <h2>User Study Data</h2>
        <form onsubmit="saveData(event)">
            <label for="username">Name</label>
            <input type="text" id="username" placeholder="Enter your name" required>

            <label for="subject">Subject</label>
            <select id="subject" required>
                <option value="Physics">Physics</option>
                <option value="Chemistry">Chemistry</option>
                <option value="General Maths">General Maths</option>
            </select>

            <label for="classType">Class Target</label>
            <select id="classType" required>
                <option value="JEE">JEE</option>
                <option value="NEET">NEET</option>
            </select>

            <label for="hours">Daily Study Hours</label>
            <input type="number" id="hours" min="0" max="24" required>

            <input type="submit" value="Save Session Data">
        </form>

        <h3 style="margin-top: 30px;">Saved Progress</h3>
        <div class="btn-group">
            <button type="button" onclick="loadData()">Load Data</button>
            <button type="button" onclick="clearData()">Clear All</button>
        </div>
        <p id="output"></p>
    </div>

    <div class="mascot-section">
        <img src="https://vecteezy.com" alt="Study Bot" class="mascot-img">
        <div class="speech-bubble" id="motivation">
            "Ready to crush your goals today? Let's get to work!"
        </div>
    </div>
</div>

<script>
    const quotes = [
        "Consistent effort beats talent any day!",
        "Every hour you study is a step toward your dream.",
        "JEE/NEET? You've got this, just stay focused!",
        "Take a break if you need, but don't quit.",
        "Your future self will thank you for this work."
    ];

    function updateQuote() {
        const bubble = document.getElementById("motivation");
        bubble.textContent = `"${quotes[Math.floor(Math.random() * quotes.length)]}"`;
    }

    function saveData(event) {
        event.preventDefault();
        const data = {
            name: document.getElementById("username").value,
            subject: document.getElementById("subject").value,
            classType: document.getElementById("classType").value,
            hours: document.getElementById("hours").value
        };
        localStorage.setItem("studyData", JSON.stringify(data));
        updateQuote();
        alert("Data saved! Keep up the great work.");
    }

    function loadData() {
        const saved = localStorage.getItem("studyData");
        const out = document.getElementById("output");
        if (saved) {
            const data = JSON.parse(saved);
            out.innerHTML = `
                <strong>Student:</strong> ${data.name}<br>
                <strong>Focus:</strong> ${data.subject} (${data.classType})<br>
                <strong>Daily Goal:</strong> ${data.hours} Hours
            `;
        } else {
            out.textContent = "No data found. Start by saving a session!";
        }
    }

    function clearData() {
        localStorage.removeItem("studyData");
        document.getElementById("output").textContent = "";
        alert("Data cleared. Fresh start!");
    }
</script>

</body>
</html>
