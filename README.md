<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Elite GitHub Profile</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap');
        
        :root {
            --bg-primary: #0a0a0a;
            --bg-secondary: #111111;
            --bg-tertiary: #1a1a1a;
            --accent-primary: #00d9ff;
            --accent-secondary: #7c3aed;
            --accent-gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            --text-primary: #ffffff;
            --text-secondary: #a0a0a0;
            --text-muted: #6b7280;
            --border-color: #2a2a2a;
            --glow-color: rgba(0, 217, 255, 0.3);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
            background: var(--bg-primary);
            color: var(--text-primary);
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
        }

        /* Animated background */
        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at 20% 20%, rgba(120, 119, 198, 0.1) 0%, transparent 50%),
                        radial-gradient(circle at 80% 80%, rgba(255, 119, 198, 0.1) 0%, transparent 50%),
                        radial-gradient(circle at 40% 40%, rgba(120, 219, 255, 0.1) 0%, transparent 50%);
            animation: backgroundShift 20s ease-in-out infinite alternate;
            pointer-events: none;
            z-index: 0;
        }

        @keyframes backgroundShift {
            0% { transform: scale(1) rotate(0deg); }
            100% { transform: scale(1.1) rotate(2deg); }
        }

        .floating-particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }

        .particle {
            position: absolute;
            width: 4px;
            height: 4px;
            background: var(--accent-primary);
            border-radius: 50%;
            opacity: 0.6;
            animation: float 6s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); opacity: 0.6; }
            25% { transform: translateY(-20px) rotate(90deg); opacity: 1; }
            50% { transform: translateY(-40px) rotate(180deg); opacity: 0.8; }
            75% { transform: translateY(-20px) rotate(270deg); opacity: 1; }
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 2rem;
            position: relative;
            z-index: 2;
        }

        /* Header Section */
        .profile-header {
            text-align: center;
            margin-bottom: 4rem;
            animation: slideInFromTop 1s cubic-bezier(0.25, 0.46, 0.45, 0.94);
        }

        .avatar-container {
            position: relative;
            width: 220px;
            height: 220px;
            margin: 0 auto 2rem;
            animation: profileGlow 3s ease-in-out infinite alternate;
        }

        .avatar-container::before {
            content: '';
            position: absolute;
            inset: -4px;
            background: conic-gradient(from 0deg at 50% 50%, var(--accent-primary), var(--accent-secondary), var(--accent-primary));
            border-radius: 50%;
            animation: spin 4s linear infinite;
            z-index: -1;
        }

        .avatar {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 5rem;
            color: white;
            border: 4px solid var(--bg-primary);
            transition: transform 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            cursor: pointer;
        }

        .avatar:hover {
            transform: scale(1.1) rotate(5deg);
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        @keyframes profileGlow {
            0% { filter: drop-shadow(0 0 20px var(--glow-color)); }
            100% { filter: drop-shadow(0 0 40px var(--glow-color)); }
        }

        .username {
            font-size: 3.5rem;
            font-weight: 800;
            margin-bottom: 1rem;
            background: linear-gradient(135deg, var(--accent-primary), var(--accent-secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            position: relative;
        }

        .username::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 4px;
            background: var(--accent-gradient);
            border-radius: 2px;
            animation: expandLine 2s ease-out;
        }

        @keyframes expandLine {
            from { width: 0; }
            to { width: 100px; }
        }

        .title {
            font-size: 1.4rem;
            font-weight: 500;
            color: var(--text-secondary);
            margin-bottom: 1rem;
            animation: typeWriter 2s steps(30) 1s forwards;
            width: 0;
            overflow: hidden;
            white-space: nowrap;
            border-right: 3px solid var(--accent-primary);
            margin-left: auto;
            margin-right: auto;
        }

        @keyframes typeWriter {
            from { width: 0; }
            to { width: 400px; }
        }

        .bio {
            font-size: 1.1rem;
            color: var(--text-muted);
            max-width: 600px;
            margin: 0 auto 2rem;
            line-height: 1.6;
        }

        .location-badge {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border: 1px solid var(--border-color);
            border-radius: 25px;
            padding: 0.5rem 1rem;
            font-size: 0.9rem;
            color: var(--text-secondary);
            transition: all 0.3s ease;
        }

        .location-badge:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 20px rgba(0, 217, 255, 0.2);
        }

        /* Stats Grid */
        .stats-section {
            margin-bottom: 4rem;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
        }

        .stat-card {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 20px;
            padding: 2rem;
            text-align: center;
            position: relative;
            overflow: hidden;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            animation: slideInFromBottom 1s ease-out;
            animation-fill-mode: both;
        }

        .stat-card:nth-child(1) { animation-delay: 0.1s; }
        .stat-card:nth-child(2) { animation-delay: 0.2s; }
        .stat-card:nth-child(3) { animation-delay: 0.3s; }
        .stat-card:nth-child(4) { animation-delay: 0.4s; }

        .stat-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.1), transparent);
            transition: left 0.5s ease;
        }

        .stat-card:hover::before {
            left: 100%;
        }

        .stat-card:hover {
            transform: translateY(-10px) scale(1.02);
            border-color: var(--accent-primary);
            box-shadow: 0 20px 40px rgba(0, 217, 255, 0.2);
        }

        .stat-icon {
            font-size: 2.5rem;
            margin-bottom: 1rem;
            display: block;
        }

        .stat-number {
            font-size: 3rem;
            font-weight: 800;
            color: var(--accent-primary);
            display: block;
            margin-bottom: 0.5rem;
            animation: countUp 2s ease-out;
        }

        .stat-label {
            font-size: 1rem;
            font-weight: 500;
            color: var(--text-secondary);
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        /* Skills Section */
        .skills-section {
            margin-bottom: 4rem;
        }

        .section-title {
            font-size: 2.2rem;
            font-weight: 700;
            margin-bottom: 2rem;
            text-align: center;
            color: var(--text-primary);
            position: relative;
        }

        .section-title::before {
            content: attr(data-text);
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            background: var(--accent-gradient);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: shimmer 3s ease-in-out infinite;
        }

        @keyframes shimmer {
            0%, 100% { opacity: 0.8; }
            50% { opacity: 1; }
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 1.5rem;
        }

        .skill-card {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 1.5rem;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .skill-card:hover {
            transform: translateY(-5px);
            border-color: var(--accent-primary);
            box-shadow: 0 15px 30px rgba(0, 217, 255, 0.15);
        }

        .skill-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1rem;
        }

        .skill-name {
            font-size: 1.1rem;
            font-weight: 600;
            color: var(--text-primary);
        }

        .skill-percentage {
            font-size: 0.9rem;
            font-weight: 500;
            color: var(--accent-primary);
        }

        .skill-bar {
            height: 8px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 4px;
            overflow: hidden;
            position: relative;
        }

        .skill-progress {
            height: 100%;
            background: var(--accent-gradient);
            border-radius: 4px;
            position: relative;
            transition: width 2s cubic-bezier(0.25, 0.46, 0.45, 0.94);
            animation: progressLoad 2s ease-in-out;
        }

        .skill-progress::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(45deg, transparent 30%, rgba(255, 255, 255, 0.3) 50%, transparent 70%);
            animation: progressShine 2s ease-in-out infinite;
        }

        @keyframes progressLoad {
            from { width: 0%; }
        }

        @keyframes progressShine {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(100%); }
        }

        /* Activity Graph */
        .activity-section {
            margin-bottom: 4rem;
        }

        .activity-container {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 20px;
            padding: 2rem;
            position: relative;
            overflow: hidden;
        }

        .activity-grid {
            display: grid;
            grid-template-columns: repeat(53, 1fr);
            gap: 3px;
            margin-top: 1.5rem;
            justify-items: center;
        }

        .activity-day {
            width: 14px;
            height: 14px;
            background: var(--bg-tertiary);
            border-radius: 3px;
            transition: all 0.3s ease;
            cursor: pointer;
            position: relative;
        }

        .activity-day:hover {
            transform: scale(1.2);
            z-index: 10;
        }

        .activity-day.level-1 { background: rgba(0, 217, 255, 0.3); }
        .activity-day.level-2 { background: rgba(0, 217, 255, 0.5); }
        .activity-day.level-3 { background: rgba(0, 217, 255, 0.7); }
        .activity-day.level-4 { background: var(--accent-primary); box-shadow: 0 0 10px var(--glow-color); }

        /* Projects Section */
        .projects-section {
            margin-bottom: 4rem;
        }

        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
            gap: 2rem;
        }

        .project-card {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 20px;
            padding: 2rem;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            position: relative;
            overflow: hidden;
            animation: slideInFromBottom 1s ease-out;
            animation-fill-mode: both;
        }

        .project-card:nth-child(odd) { animation-delay: 0.1s; }
        .project-card:nth-child(even) { animation-delay: 0.2s; }

        .project-card:hover {
            transform: translateY(-10px) rotateX(5deg);
            border-color: var(--accent-primary);
            box-shadow: 0 25px 50px rgba(0, 217, 255, 0.2);
        }

        .project-header {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            margin-bottom: 1rem;
        }

        .project-title {
            font-size: 1.4rem;
            font-weight: 700;
            color: var(--text-primary);
            margin-bottom: 0.5rem;
        }

        .project-status {
            background: var(--accent-gradient);
            color: white;
            padding: 0.25rem 0.75rem;
            border-radius: 15px;
            font-size: 0.8rem;
            font-weight: 500;
        }

        .project-description {
            color: var(--text-secondary);
            line-height: 1.6;
            margin-bottom: 1.5rem;
        }

        .project-tech {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
            margin-bottom: 1.5rem;
        }

        .tech-tag {
            background: rgba(255, 255, 255, 0.1);
            color: var(--accent-primary);
            padding: 0.25rem 0.75rem;
            border-radius: 12px;
            font-size: 0.8rem;
            font-weight: 500;
            border: 1px solid rgba(0, 217, 255, 0.3);
            transition: all 0.3s ease;
        }

        .tech-tag:hover {
            background: var(--accent-primary);
            color: var(--bg-primary);
            transform: translateY(-2px);
        }

        .project-stats {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .project-links {
            display: flex;
            gap: 1rem;
        }

        .project-link {
            color: var(--accent-primary);
            text-decoration: none;
            font-weight: 500;
            transition: all 0.3s ease;
            position: relative;
        }

        .project-link:hover {
            color: var(--accent-secondary);
            transform: translateY(-2px);
        }

        .project-link::after {
            content: '';
            position: absolute;
            bottom: -2px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--accent-primary);
            transition: width 0.3s ease;
        }

        .project-link:hover::after {
            width: 100%;
        }

        /* Footer */
        .footer {
            text-align: center;
            padding: 3rem 0;
            border-top: 1px solid var(--border-color);
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin-bottom: 2rem;
        }

        .social-link {
            width: 60px;
            height: 60px;
            border-radius: 15px;
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--text-primary);
            text-decoration: none;
            font-size: 1.5rem;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            position: relative;
            overflow: hidden;
        }

        .social-link::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: var(--accent-gradient);
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        .social-link:hover {
            transform: translateY(-10px) scale(1.1);
            box-shadow: 0 15px 30px var(--glow-color);
        }

        .social-link:hover::before {
            opacity: 1;
        }

        .social-link span {
            position: relative;
            z-index: 1;
        }

        /* Animations */
        @keyframes slideInFromTop {
            from {
                opacity: 0;
                transform: translateY(-50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes slideInFromBottom {
            from {
                opacity: 0;
                transform: translateY(50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes countUp {
            from { 
                opacity: 0;
                transform: translateY(20px);
            }
            to { 
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .container {
                padding: 1rem;
            }
            
            .username {
                font-size: 2.5rem;
            }
            
            .avatar-container {
                width: 180px;
                height: 180px;
            }
            
            .avatar {
                font-size: 4rem;
            }
            
            .stats-grid {
                grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            }
            
            .projects-grid {
                grid-template-columns: 1fr;
            }
            
            .social-links {
                gap: 1rem;
            }
        }

        /* Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }

        ::-webkit-scrollbar-track {
            background: var(--bg-primary);
        }

        ::-webkit-scrollbar-thumb {
            background: var(--accent-primary);
            border-radius: 4px;
        }

        ::-webkit-scrollbar-thumb:hover {
            background: var(--accent-secondary);
        }
    </style>
</head>
<body>
    <div class="floating-particles"></div>
    
    <div class="container">
        <!-- Profile Header -->
        <div class="profile-header">
            <div class="avatar-container">
                <div class="avatar">🚀</div>
            </div>
            <h1 class="username">YourDevName</h1>
            <div class="title">Full Stack Developer & Tech Innovator</div>
            <p class="bio">Passionate about creating exceptional digital experiences with cutting-edge technologies. Specialized in React, Node.js, and cloud architecture. Always learning, always building.</p>
            <div class="location-badge">
                <span>📍</span>
                <span>San Francisco, CA</span>
            </div>
        </div>

        <!-- Stats Section -->
        <section class="stats-section">
            <div class="stats-grid">
                <div class="stat-card">
                    <span class="stat-icon">📚</span>
                    <span class="stat-number" data-target="247">0</span>
                    <span class="stat-label">Repositories</span>
                </div>
                <div class="stat-card">
                    <span class="stat-icon">⭐</span>
                    <span class="stat-number" data-target="1849">0</span>
                    <span class="stat-label">Stars Earned</span>
                </div>
                <div class="stat-card">
                    <span class="stat-icon">🔥</span>
                    <span class="stat-number" data-target="365">0</span>
                    <span class="stat-label">Day Streak</span>
                </div>
                <div class="stat-card">
                    <span class="stat-icon">👥</span>
                    <span class="stat-number" data-target="892">0</span>
                    <span class="stat-label">Followers</span>
                </div>
            </div>
        </section>

        <!-- Skills Section -->
        <section class="skills-section">
            <h2 class="section-title" data-text="🛠️ Skills & Technologies">🛠️ Skills & Technologies</h2>
            <div class="skills-grid">
                <div class="skill-card">
                    <div class="skill-header">
                        <span class="skill-name">JavaScript/TypeScript</span>
                        <span class="skill-percentage">95%</span>
                    </div>
                    <div class="skill-bar">
                        <div class="skill-progress" style="width: 95%;"></div>
                    </div>
                </div>
                <div class="skill-card">
                    <div class="skill-header">
                        <span class="skill-name">React/Next.js</span>
                        <span class="skill-percentage">92%</span>
                    </div>
                    <div class="skill-bar">
                        <div class="skill-progress" style="width: 92%;"></div>
                    </div>
                </div>
                <div class="skill-card">
                    <div class="skill-header">
                        <span class="skill-name">Node.js/Express</span>
                        <span class="skill-percentage">88%</span>
                    </div>
                    <div class="skill-bar">
                        <div class="skill-progress" style="width: 88%;"></div>
                    </div>
                </div>
                <div class="skill-card">
                    <div class="skill-header">
                        <span class="skill-name">Python/Django</span>
                        <span class="skill-percentage">85%</span>
                    </div>
                    <div class="skill-bar">
                        <div class="skill-progress" style="width: 85%;"></div>
                    </div>
                </div>
                <div class="skill-card">
                    <div class="skill-header">
                        <span class="skill-name">Cloud/DevOps</span>
                        <span class="skill-percentage">80%</span>
                    </div>
                    <div class="skill-bar">
                        <div class="skill-progress" style="width: 80%;"></div>
                    </div>
                </div>
                <div class="skill-card">
                    <div class="skill-header">
                        <span class="skill-name">UI/UX Design</span>
                        <span class="skill-percentage">78%</span>
                    </div>
                    <div class="skill-bar">
                        <div class="skill-progress" style="width: 78%;"></div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Activity Section -->
        <section class="activity-section">
            <h2 class="section-title" data-text="📈 Contribution Activity">📈 Contribution Activity</h2>
            <div class="activity-container">
                <p style="color: var(--text-secondary); margin-bottom: 1rem;">Total contributions: <strong>2,847</strong> in the last year</p>
                <div class="activity-grid" id="activityGrid"></div>
            </div>
        </section>

        <!-- Projects Section -->
        <section class="projects-section">
            <h2 class="section-title" data-text="🚀 Featured Projects">🚀 Featured Projects</h2>
            <div class="projects-grid">
                <div class="project-card">
                    <div class="project-header">
                        <div>
                            <h3 class="project-title">Neural Network Visualizer</h3>
                        </div>
                        <span class="project-status">Active</span>
                    </div>
                    <p class="project-description">Interactive web application for visualizing neural network architectures and training processes. Built with Three.js and WebGL for smooth 3D animations.</p>
                    <div class="project-tech">
                        <span class="tech-tag">TypeScript</span>
                        <span class="tech-tag">Three.js</span>
                        <span class="tech-tag">WebGL</span>
                        <span class="tech-tag">React</span>
                    </div>
                    <div class="project-stats">
                        <div style="color: var(--text-muted);">⭐ 234 🍴 67</div>
                        <div class="project-links">
                            <a href="#" class="project-link">Live Demo</a>
                            <a href="#" class="project-link">Code</a>
                        </div>
                    </div>
                </div>

                <div class="project-card">
                    <div class="project-header">
                        <div>
                            <h3 class="project-title">CloudSync API</h3>
                        </div>
                        <span class="project-status">Production</span>
                    </div>
                    <p class="project-description">Scalable REST API for real-time data synchronization across multiple cloud platforms. Handles 10M+ requests daily with 99.9% uptime.</p>
                    <div class="project-tech">
                        <span class="tech-tag">Node.js</span>
                        <span class="tech-tag">PostgreSQL</span>
                        <span class="tech-tag">Redis</span>
                        <span class="tech-tag">Docker</span>
                    </div>
                    <div class="project-stats">
                        <div style="color: var(--text-muted);">⭐ 456 🍴 89</div>
                        <div class="project-links">
                            <a href="#" class="project-link">Documentation</a>
                            <a href="#" class="project-link">Code</a>
                        </div>
                    </div>
