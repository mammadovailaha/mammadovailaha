<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ilaha Mammadova - Junior Front-End Developer</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #ff8c42;
            --secondary: #ff6b35;
            --accent: #ffa500;
            --dark-bg: #0a0e27;
            --dark-card: #1a1f3a;
            --dark-border: #2d3561;
            --dark-text: #e8ecf1;
            --light-bg: #f5f7fa;
            --light-card: #ffffff;
            --light-border: #e2e8f0;
            --light-text: #1e293b;
        }

        body.light-mode {
            background: linear-gradient(135deg, #f5f7fa 0%, #eef2f7 100%);
            color: var(--light-text);
        }

        body.dark-mode {
            background: linear-gradient(135deg, #0a0e27 0%, #12172d 100%);
            color: var(--dark-text);
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            transition: all 0.3s ease;
            min-height: 100vh;
            padding: 20px;
            background-attachment: fixed;
        }

        .theme-toggle {
            position: fixed;
            top: 20px;
            right: 20px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            border: none;
            color: white;
            width: 50px;
            height: 50px;
            border-radius: 12px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 20px;
            z-index: 1000;
            box-shadow: 0 8px 32px rgba(255, 140, 66, 0.4);
            transition: all 0.3s ease;
        }

        .theme-toggle:hover {
            transform: scale(1.1) rotate(10deg);
            box-shadow: 0 12px 48px rgba(255, 140, 66, 0.6);
        }

        .container {
            max-width: 1000px;
            margin: 0 auto;
        }

        /* Header Section */
        .header {
            text-align: center;
            margin-bottom: 60px;
            animation: slideDown 0.8s cubic-bezier(0.34, 1.56, 0.64, 1);
        }

        .header-content {
            background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 50%, var(--accent) 100%);
            padding: 80px 40px;
            border-radius: 25px;
            position: relative;
            overflow: hidden;
            box-shadow: 0 20px 60px rgba(255, 140, 66, 0.3);
        }

        .header-content::before {
            content: '';
            position: absolute;
            top: -50%;
            right: -10%;
            width: 400px;
            height: 400px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            animation: float 8s ease-in-out infinite;
        }

        .header-content::after {
            content: '';
            position: absolute;
            bottom: -20%;
            left: -5%;
            width: 300px;
            height: 300px;
            background: rgba(255, 255, 255, 0.08);
            border-radius: 50%;
            animation: float 10s ease-in-out infinite reverse;
        }

        .header-content h1 {
            color: white;
            font-size: 3.5em;
            margin-bottom: 15px;
            position: relative;
            z-index: 1;
            font-weight: 900;
            letter-spacing: -2px;
        }

        .header-content p {
            color: rgba(255, 255, 255, 0.95);
            font-size: 1.3em;
            position: relative;
            z-index: 1;
            font-weight: 500;
        }

        .subtitle {
            font-size: 1.15em;
            opacity: 0.85;
            margin-top: 30px;
            line-height: 1.6;
        }

        /* Cards */
        .card {
            background: var(--light-card);
            border: 1px solid var(--light-border);
            border-radius: 20px;
            padding: 40px;
            margin-bottom: 30px;
            transition: all 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
            backdrop-filter: blur(10px);
            position: relative;
            overflow: hidden;
        }

        .dark-mode .card {
            background: var(--dark-card);
            border-color: var(--dark-border);
        }

        .card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 140, 66, 0.1), transparent);
            transition: left 0.5s ease;
        }

        .card:hover::before {
            left: 100%;
        }

        .card:hover {
            transform: translateY(-8px) translateX(0);
            box-shadow: 0 25px 50px rgba(255, 140, 66, 0.2);
            border-color: var(--primary);
        }

        .section-title {
            font-size: 2em;
            font-weight: 800;
            margin-bottom: 30px;
            display: flex;
            align-items: center;
            gap: 15px;
            position: relative;
        }

        .section-title::before {
            content: '';
            width: 6px;
            height: 35px;
            background: linear-gradient(180deg, var(--primary), var(--secondary));
            border-radius: 3px;
            box-shadow: 0 0 20px rgba(255, 140, 66, 0.5);
        }

        /* Tech Stack */
        .tech-stack {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(90px, 1fr));
            gap: 20px;
        }

        .tech-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            gap: 12px;
            padding: 20px;
            border-radius: 16px;
            background: linear-gradient(135deg, rgba(255, 140, 66, 0.1), rgba(255, 107, 53, 0.05));
            border: 2px solid transparent;
            transition: all 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
            cursor: pointer;
            position: relative;
        }

        .tech-item:hover {
            background: linear-gradient(135deg, rgba(255, 140, 66, 0.2), rgba(255, 107, 53, 0.15));
            transform: translateY(-12px) rotate(5deg);
            border-color: var(--primary);
            box-shadow: 0 15px 35px rgba(255, 140, 66, 0.3);
        }

        .tech-item img {
            width: 45px;
            height: 45px;
            filter: drop-shadow(0 4px 8px rgba(255, 140, 66, 0.2));
            transition: transform 0.3s ease;
        }

        .tech-item:hover img {
            transform: scale(1.15) rotate(-5deg);
        }

        .dark-mode .tech-item img {
            filter: drop-shadow(0 4px 8px rgba(255, 140, 66, 0.4)) brightness(1.1);
        }

        .tech-item p {
            font-size: 0.9em;
            text-align: center;
            opacity: 0.85;
            font-weight: 600;
        }

        /* Stats */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
            gap: 25px;
            margin-bottom: 30px;
        }

        .stat-box {
            text-align: center;
            padding: 30px 20px;
            border-radius: 16px;
            background: linear-gradient(135deg, rgba(255, 140, 66, 0.1), rgba(255, 107, 53, 0.05));
            border: 2px solid transparent;
            transition: all 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
            position: relative;
            overflow: hidden;
        }

        .stat-box::before {
            content: '';
            position: absolute;
            top: -50%;
            right: -50%;
            width: 200px;
            height: 200px;
            background: radial-gradient(circle, rgba(255, 140, 66, 0.3), transparent);
            transition: all 0.5s ease;
        }

        .stat-box:hover {
            background: linear-gradient(135deg, rgba(255, 140, 66, 0.2), rgba(255, 107, 53, 0.15));
            transform: scale(1.08) translateY(-10px);
            border-color: var(--primary);
            box-shadow: 0 20px 45px rgba(255, 140, 66, 0.25);
        }

        .stat-box:hover::before {
            top: -20%;
            right: -20%;
        }

        .stat-number {
            font-size: 2.5em;
            font-weight: 900;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 8px;
            position: relative;
            z-index: 1;
        }

        .stat-label {
            font-size: 0.95em;
            opacity: 0.8;
            font-weight: 600;
            position: relative;
            z-index: 1;
        }

        /* Projects */
        .project-item {
            padding: 25px;
            border-radius: 16px;
            background: linear-gradient(135deg, rgba(255, 140, 66, 0.08), rgba(255, 107, 53, 0.03));
            border-left: 5px solid var(--primary);
            transition: all 0.4s ease;
            margin-bottom: 20px;
            position: relative;
        }

        .project-item:hover {
            background: linear-gradient(135deg, rgba(255, 140, 66, 0.15), rgba(255, 107, 53, 0.08));
            border-left-color: var(--secondary);
            transform: translateX(8px);
            box-shadow: 0 15px 35px rgba(255, 140, 66, 0.15);
        }

        .project-item h3 {
            color: var(--primary);
            margin-bottom: 10px;
            font-size: 1.2em;
        }

        .project-item p {
            opacity: 0.85;
            margin-bottom: 12px;
            line-height: 1.6;
        }

        .project-tech {
            font-size: 0.9em;
            opacity: 0.7;
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
        }

        .tech-badge {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 0.85em;
            font-weight: 600;
        }

        /* Skills */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 25px;
        }

        .skill-category {
            padding: 25px;
            border-radius: 16px;
            background: linear-gradient(135deg, rgba(255, 140, 66, 0.1), rgba(255, 107, 53, 0.05));
            border: 2px solid transparent;
            transition: all 0.4s ease;
        }

        .skill-category:hover {
            border-color: var(--primary);
            transform: translateY(-8px);
            box-shadow: 0 15px 40px rgba(255, 140, 66, 0.2);
            background: linear-gradient(135deg, rgba(255, 140, 66, 0.15), rgba(255, 107, 53, 0.1));
        }

        .skill-category h4 {
            color: var(--primary);
            margin-bottom: 15px;
            font-size: 1.15em;
        }

        .skill-category p {
            opacity: 0.8;
            line-height: 1.7;
            font-size: 0.95em;
        }

        /* Contact */
        .contact-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
            gap: 20px;
        }

        .contact-btn {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            padding: 18px 25px;
            border: 2px solid var(--primary);
            background: transparent;
            color: var(--primary);
            border-radius: 14px;
            cursor: pointer;
            font-weight: 700;
            transition: all 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
            text-decoration: none;
            font-size: 0.95em;
            position: relative;
            overflow: hidden;
        }

        .contact-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            transition: left 0.4s ease;
            z-index: -1;
        }

        .contact-btn:hover::before {
            left: 0;
        }

        .contact-btn:hover {
            color: white;
            transform: translateY(-4px);
            box-shadow: 0 12px 32px rgba(255, 140, 66, 0.4);
        }

        .contact-btn i {
            font-size: 1.3em;
        }

        /* GitHub Stats */
        .github-section {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
            margin-top: 30px;
        }

        .github-section img {
            border-radius: 16px;
            transition: all 0.4s ease;
        }

        .github-section img:hover {
            transform: scale(1.02);
            box-shadow: 0 15px 40px rgba(255, 140, 66, 0.2);
        }

        /* Animations */
        @keyframes slideDown {
            from {
                opacity: 0;
                transform: translateY(-40px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes float {
            0%, 100% {
                transform: translateY(0px);
            }
            50% {
                transform: translateY(-30px);
            }
        }

        .card {
            animation: slideDown 0.8s ease 0.1s both;
        }

        .card:nth-child(2) {
            animation-delay: 0.2s;
        }

        .card:nth-child(3) {
            animation-delay: 0.3s;
        }

        /* Footer */
        .footer {
            text-align: center;
            padding: 50px 0;
            opacity: 0.7;
            font-size: 1.05em;
        }

        .footer p {
            margin-bottom: 10px;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .header-content {
                padding: 50px 25px;
            }

            .header-content h1 {
                font-size: 2.2em;
            }

            .card {
                padding: 25px;
            }

            .section-title {
                font-size: 1.5em;
            }

            .tech-stack {
                grid-template-columns: repeat(auto-fit, minmax(70px, 1fr));
                gap: 15px;
            }

            .contact-grid {
                grid-template-columns: repeat(2, 1fr);
            }

            .stats-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }
    </style>
</head>
<body class="dark-mode">
    <button class="theme-toggle" onclick="toggleTheme()">
        <i class="fas fa-moon"></i>
    </button>

    <div class="container">
        <!-- Header -->
        <div class="header">
            <div class="header-content">
                <h1>👋 Hi, I'm Ilaha</h1>
                <p>Junior Front-End Developer</p>
            </div>
            <p class="subtitle">Self-motivated & growth-oriented developer passionate about creating responsive, user-friendly, and scalable web interfaces using modern technologies</p>
        </div>

        <!-- About Me -->
        <div class="card">
            <div class="section-title">💡 About Me</div>
            <p style="line-height: 1.8; opacity: 0.9; font-size: 1.05em;">
                I'm passionate about crafting beautiful and functional web experiences. I specialize in building responsive interfaces using cutting-edge technologies. Currently, I'm expanding my skills in <strong>Next.js</strong> and <strong>Node.js</strong> to transition into a Full-Stack Developer role.
            </p>
            <p style="margin-top: 15px; line-height: 1.8; opacity: 0.85;">
                I'm committed to writing clean, maintainable code and working in collaborative environments where I can contribute and grow.
            </p>
        </div>

        <!-- Stats -->
        <div class="card">
            <div class="section-title">📊 My Stats</div>
            <div class="stats-grid">
                <div class="stat-box">
                    <div class="stat-number">50+</div>
                    <div class="stat-label">Projects Completed</div>
                </div>
                <div class="stat-box">
                    <div class="stat-number">3+</div>
                    <div class="stat-label">Years Learning</div>
                </div>
                <div class="stat-box">
                    <div class="stat-number">15+</div>
                    <div class="stat-label">Tech Skills</div>
                </div>
                <div class="stat-box">
                    <div class="stat-number">100%</div>
                    <div class="stat-label">Commitment</div>
                </div>
            </div>
        </div>

        <!-- Tech Stack -->
        <div class="card">
            <div class="section-title">🧰 Tech Stack</div>
            <div class="tech-stack">
                <div class="tech-item">
                    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" alt="HTML5">
                    <p>HTML5</p>
                </div>
                <div class="tech-item">
                    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" alt="CSS3">
                    <p>CSS3</p>
                </div>
                <div class="tech-item">
                    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" alt="JavaScript">
                    <p>JavaScript</p>
                </div>
                <div class="tech-item">
                    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg" alt="TypeScript">
                    <p>TypeScript</p>
                </div>
                <div class="tech-item">
                    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg" alt="React">
                    <p>React</p>
                </div>
                <div class="tech-item">
                    <img src="https://www.vectorlogo.zone/logos/tailwindcss/tailwindcss-icon.svg" alt="Tailwind CSS">
                    <p>Tailwind CSS</p>
                </div>
                <div class="tech-item">
                    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nextjs/nextjs-original.svg" alt="Next.js">
                    <p>Next.js</p>
                </div>
                <div class="tech-item">
                    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg" alt="Node.js">
                    <p>Node.js</p>
                </div>
                <div class="tech-item">
                    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" alt="Git">
                    <p>Git</p>
                </div>
                <div class="tech-item">
                    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg" alt="GitHub">
                    <p>GitHub</p>
                </div>
            </div>
        </div>

        <!-- Featured Projects -->
        <div class="card">
            <div class="section-title">⭐ Featured Projects</div>
            <div class="project-item">
                <h3>🎨 Interactive Portfolio</h3>
                <p>Modern portfolio website with smooth animations and responsive design that showcases projects beautifully</p>
                <div class="project-tech">
                    <span class="tech-badge">React</span>
                    <span class="tech-badge">Tailwind CSS</span>
                    <span class="tech-badge">Vercel</span>
                </div>
            </div>
            <div class="project-item">
                <h3>🛍️ E-Commerce Platform</h3>
                <p>Full-featured e-commerce application with product filtering, cart management, and seamless checkout flow</p>
                <div class="project-tech">
                    <span class="tech-badge">React</span>
                    <span class="tech-badge">JavaScript</span>
                    <span class="tech-badge">CSS3</span>
                </div>
            </div>
            <div class="project-item">
                <h3>📱 Weather App</h3>
                <p>Real-time weather application with location-based forecasts and beautiful UI animations</p>
                <div class="project-tech">
                    <span class="tech-badge">React</span>
                    <span class="tech-badge">API</span>
                    <span class="tech-badge">Tailwind</span>
                </div>
            </div>
        </div>

        <!-- Skills -->
        <div class="card">
            <div class="section-title">💪 Skills & Expertise</div>
            <div class="skills-grid">
                <div class="skill-category">
                    <h4>⚡ Frontend Development</h4>
                    <p>React, Next.js, HTML5, CSS3, JavaScript, TypeScript, Tailwind CSS, Responsive Design, Component Architecture</p>
                </div>
                <div class="skill-category">
                    <h4>🛠️ Tools & Tech</h4>
                    <p>Git, GitHub, VS Code, Vercel, RESTful APIs, Local Storage, Figma, Chrome DevTools, NPM</p>
                </div>
                <div class="skill-category">
                    <h4>🧠 Soft Skills</h4>
                    <p>Problem Solving, Team Collaboration, Communication, Attention to Detail, Time Management, Self-learning</p>
                </div>
            </div>
        </div>

        <!-- GitHub Stats -->
        <div class="card">
            <div class="section-title">📈 GitHub Activity</div>
            <div class="github-section">
                <img src="https://github-readme-stats.vercel.app/api?username=mammadovailaha&show_icons=true&theme=radical&hide_border=true" alt="GitHub Stats">
                <img src="https://github-readme-stats.vercel.app/api?username=mammadovailaha&show_icons=true&theme=radical&count_private=true&hide_border=true" alt="GitHub Stats Private">
            </div>
            <div style="margin-top: 25px;">
                <img src="https://github-readme-activity-graph.vercel.app/graph?username=mammadovailaha&theme=github-dark&hide_border=true&radius=16" alt="Contribution Graph" style="width: 100%; border-radius: 16px;">
            </div>
        </div>

        <!-- Contact -->
        <div class="card">
            <div class="section-title">📫 Get In Touch</div>
            <div class="contact-grid">
                <a href="mailto:mammadovailaha03@gmail.com" class="contact-btn">
                    <i class="fas fa-envelope"></i> Email
                </a>
                <a href="https://my-portfolio-woad-three-68.vercel.app/" target="_blank" class="contact-btn">
                    <i class="fas fa-globe"></i> Portfolio
                </a>
                <a href="https://www.linkedin.com/in/ilaha-mammadova-0ab538356/" target="_blank" class="contact-btn">
                    <i class="fab fa-linkedin"></i> LinkedIn
                </a>
                <a href="https://www.instagram.com/ilahahub" target="_blank" class="contact-btn">
                    <i class="fab fa-instagram"></i> Instagram
                </a>
            </div>
        </div>

        <!-- Footer -->
        <div class="footer">
            <p>💖 Made with passion by Ilaha</p>
            <p>⭐ If you find my work interesting, consider giving me a star!</p>
        </div>
    </div>

    <script>
        function toggleTheme() {
            const body = document.body;
            const toggle = document.querySelector('.theme-toggle');
            
            body.classList.toggle('dark-mode');
            body.classList.toggle('light-mode');
            
            if (body.classList.contains('light-mode')) {
                toggle.innerHTML = '<i class="fas fa-sun"></i>';
            } else {
                toggle.innerHTML = '<i class="fas fa-moon"></i>';
            }
        }
    </script>
</body>
</html>
