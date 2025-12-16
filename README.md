<!DOCTYPE html>
<html lang="en" data-theme="light">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="The VFX - Creative Developer & UI Designer Portfolio">
    <title>The VFX | Web Designer & Programmer</title>

    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">

    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <style>
        /* ===== CSS VARIABLES ===== */
        :root {
            /* Light Theme (Default) */
            --color-bg-primary: #ffffff;
            --color-bg-secondary: #f4f8fb;
            --color-accent-blue: #2563eb;
            --color-accent-navy: #1e293b;
            --color-text-primary: #334155;
            --color-text-light: #64748b;
            --color-white: #ffffff;
            --color-card-bg: #ffffff;
            --color-border: rgba(37, 99, 235, 0.1);
            
            --font-primary: 'Poppins', sans-serif;
            --transition-smooth: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            --transition-theme: background-color 0.5s ease, color 0.5s ease, border-color 0.5s ease;
            --shadow-sm: 0 2px 8px rgba(0, 0, 0, 0.08);
            --shadow-md: 0 4px 20px rgba(0, 0, 0, 0.12);
            --shadow-lg: 0 10px 40px rgba(0, 0, 0, 0.15);
        }

        /* Dark Theme Overrides */
        [data-theme="dark"] {
            --color-bg-primary: #0f172a;
            --color-bg-secondary: #1e293b;
            --color-accent-blue: #3b82f6;
            --color-accent-navy: #f8fafc;
            --color-text-primary: #f1f5f9;
            --color-text-light: #94a3b8;
            --color-white: #1e293b;
            --color-card-bg: #1e293b;
            --color-border: rgba(255, 255, 255, 0.1);
            --shadow-sm: 0 2px 8px rgba(0, 0, 0, 0.3);
            --shadow-md: 0 4px 20px rgba(0, 0, 0, 0.4);
            --shadow-lg: 0 10px 40px rgba(0, 0, 0, 0.5);
        }

        /* ===== RESET & BASE ===== */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
            overflow-x: hidden; /* Prevents side scrolling */
            width: 100%;
        }

        body {
            font-family: var(--font-primary);
            color: var(--color-text-primary);
            background: var(--color-bg-primary);
            line-height: 1.6;
            overflow-x: hidden; /* Critical fix for side space */
            width: 100%;
            position: relative;
            transition: var(--transition-theme);
        }

        ::selection {
            background: var(--color-accent-blue);
            color: #ffffff;
        }

        /* ===== NAVIGATION ===== */
        nav {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            width: 100%; /* Ensures full width */
            z-index: 1000;
            padding: 1.5rem 0;
            background: var(--color-bg-primary);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border-bottom: 1px solid var(--color-border);
            transition: var(--transition-smooth), background-color 0.5s ease;
        }

        nav.scrolled {
            padding: 1rem 0;
            box-shadow: var(--shadow-sm);
        }
        
        [data-theme="light"] nav {
            background: rgba(255, 255, 255, 0.85);
        }
        
        [data-theme="dark"] nav {
            background: rgba(15, 23, 42, 0.85);
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: 800;
            color: var(--color-accent-navy);
            text-decoration: none;
            letter-spacing: -0.5px;
            transition: color 0.5s ease;
        }

        .logo span {
            color: var(--color-accent-blue);
        }

        .nav-actions {
            display: flex;
            align-items: center;
            gap: 2rem;
        }

        .nav-links {
            display: flex;
            gap: 2.5rem;
            list-style: none;
        }

        .nav-links a {
            color: var(--color-text-primary);
            text-decoration: none;
            font-weight: 500;
            font-size: 0.95rem;
            position: relative;
            transition: var(--transition-smooth), color 0.5s ease;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--color-accent-blue);
            transition: var(--transition-smooth);
        }

        .nav-links a:hover {
            color: var(--color-accent-blue);
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        .theme-toggle {
            background: none;
            border: 2px solid var(--color-border);
            color: var(--color-text-primary);
            padding: 0.5rem;
            border-radius: 50%;
            cursor: pointer;
            width: 40px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: var(--transition-smooth);
            font-size: 1.1rem;
        }

        .theme-toggle:hover {
            background: var(--color-bg-secondary);
            border-color: var(--color-accent-blue);
            color: var(--color-accent-blue);
            transform: rotate(15deg);
        }

        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            font-size: 1.5rem;
            color: var(--color-accent-navy);
            cursor: pointer;
            transition: color 0.5s ease;
        }

        /* ===== HERO SECTION ===== */
        #hero {
            position: relative;
            min-height: 100vh;
            width: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
            background: linear-gradient(135deg, var(--color-bg-secondary) 0%, var(--color-bg-primary) 100%);
            overflow: hidden;
            padding-top: 80px;
            transition: background 0.5s ease;
        }

        #particleCanvas {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
        }

        .hero-content {
            position: relative;
            z-index: 2;
            text-align: center;
            padding: 2rem;
            max-width: 900px;
            width: 100%; /* Ensures content stays within bounds */
        }

        .hero-subtitle {
            font-size: 1.1rem;
            font-weight: 500;
            color: var(--color-accent-blue);
            margin-bottom: 1rem;
            opacity: 0;
            animation: fadeInUp 0.8s ease forwards;
        }

        .hero-title {
            font-size: clamp(2.5rem, 8vw, 4.5rem);
            font-weight: 800;
            color: var(--color-accent-navy);
            line-height: 1.1;
            margin-bottom: 1.5rem;
            opacity: 0;
            animation: fadeInUp 0.8s ease 0.2s forwards;
            transition: color 0.5s ease;
        }

        .hero-title .gradient-text {
            background: linear-gradient(135deg, var(--color-accent-blue) 0%, #3b82f6 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .hero-description {
            font-size: 1.2rem;
            color: var(--color-text-light);
            margin-bottom: 2.5rem;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            opacity: 0;
            animation: fadeInUp 0.8s ease 0.4s forwards;
            transition: color 0.5s ease;
        }

        .hero-buttons {
            display: flex;
            gap: 1.5rem;
            justify-content: center;
            flex-wrap: wrap;
            opacity: 0;
            animation: fadeInUp 0.8s ease 0.6s forwards;
        }

        .btn {
            padding: 1rem 2.5rem;
            border-radius: 50px;
            font-weight: 600;
            font-size: 1rem;
            text-decoration: none;
            transition: var(--transition-smooth);
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            cursor: pointer;
            border: none;
        }

        .btn-primary {
            background: var(--color-accent-blue);
            color: #ffffff;
            box-shadow: 0 4px 15px rgba(37, 99, 235, 0.3);
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 25px rgba(37, 99, 235, 0.4);
        }

        .btn-secondary {
            background: transparent;
            color: var(--color-accent-navy);
            border: 2px solid var(--color-accent-navy);
        }

        .btn-secondary:hover {
            background: var(--color-accent-navy);
            color: var(--color-bg-primary);
            transform: translateY(-2px);
        }

        /* ===== SECTIONS ===== */
        section {
            padding: 6rem 2rem;
            max-width: 1200px;
            margin: 0 auto;
            width: 100%;
        }

        .section-header {
            text-align: center;
            margin-bottom: 4rem;
        }

        .section-subtitle {
            font-size: 0.95rem;
            font-weight: 600;
            color: var(--color-accent-blue);
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-bottom: 0.5rem;
        }

        .section-title {
            font-size: clamp(2rem, 5vw, 3rem);
            font-weight: 800;
            color: var(--color-accent-navy);
            margin-bottom: 1rem;
            transition: color 0.5s ease;
        }

        .section-description {
            font-size: 1.1rem;
            color: var(--color-text-light);
            max-width: 600px;
            margin: 0 auto;
            transition: color 0.5s ease;
        }

        /* ===== PORTFOLIO GRID ===== */
        .portfolio-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 2rem;
        }

        .portfolio-card {
            background: var(--color-card-bg);
            border-radius: 16px;
            overflow: hidden;
            box-shadow: var(--shadow-sm);
            transition: var(--transition-smooth), background-color 0.5s ease;
            cursor: pointer;
            border: 1px solid var(--color-border);
        }

        .portfolio-card:hover {
            transform: translateY(-8px);
            box-shadow: var(--shadow-lg);
            border-color: var(--color-accent-blue);
        }

        .portfolio-image {
            width: 100%;
            height: 250px;
            background: linear-gradient(135deg, var(--color-accent-blue) 0%, #3b82f6 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 4rem;
            color: #ffffff;
            position: relative;
            overflow: hidden;
        }

        .portfolio-image::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0, 0, 0, 0);
            transition: var(--transition-smooth);
        }

        .portfolio-card:hover .portfolio-image::after {
            background: rgba(0, 0, 0, 0.1);
        }

        .portfolio-content {
            padding: 2rem;
        }

        .portfolio-title {
            font-size: 1.4rem;
            font-weight: 700;
            color: var(--color-accent-navy);
            margin-bottom: 0.75rem;
            transition: color 0.5s ease;
        }

        .portfolio-description {
            color: var(--color-text-light);
            margin-bottom: 1.5rem;
            line-height: 1.7;
            transition: color 0.5s ease;
        }

        .portfolio-tags {
            display: flex;
            gap: 0.5rem;
            flex-wrap: wrap;
        }

        .tag {
            padding: 0.4rem 1rem;
            background: var(--color-bg-secondary);
            color: var(--color-accent-blue);
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 500;
            transition: background-color 0.5s ease;
        }

        /* ===== SKILLS SECTION ===== */
        #skills {
            background: var(--color-bg-secondary);
            transition: background-color 0.5s ease;
            max-width: 100%; /* Fix for side space */
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .skill-card {
            background: var(--color-card-bg);
            padding: 2rem;
            border-radius: 16px;
            text-align: center;
            transition: var(--transition-smooth), background-color 0.5s ease;
            box-shadow: var(--shadow-sm);
            border: 1px solid var(--color-border);
        }

        .skill-card:hover {
            transform: translateY(-5px);
            box-shadow: var(--shadow-md);
            border-color: var(--color-accent-blue);
        }

        .skill-icon {
            font-size: 3rem;
            color: var(--color-accent-blue);
            margin-bottom: 1rem;
        }

        .skill-name {
            font-weight: 600;
            color: var(--color-accent-navy);
            font-size: 1.1rem;
            transition: color 0.5s ease;
        }

        /* ===== CONTACT SECTION ===== */
        #contact {
            background: var(--color-accent-navy);
            color: var(--color-white);
            text-align: center;
            transition: background-color 0.5s ease;
            max-width: 100%; /* Fix for side space */
        }
        
        [data-theme="dark"] #contact {
            background: #0f172a;
            border-top: 1px solid var(--color-border);
        }

        #contact .section-subtitle {
            color: var(--color-accent-blue);
        }

        #contact .section-title,
        #contact .section-description {
            color: #ffffff;
        }
        
        [data-theme="dark"] #contact .section-title,
        [data-theme="dark"] #contact .section-description {
            color: var(--color-text-primary);
        }

        .contact-email {
            font-size: 2rem;
            font-weight: 700;
            color: #ffffff;
            text-decoration: none;
            display: inline-block;
            margin: 2rem 0;
            transition: var(--transition-smooth);
        }
        
        [data-theme="dark"] .contact-email {
            color: var(--color-accent-blue);
        }

        .contact-email:hover {
            color: var(--color-accent-blue);
            transform: scale(1.05);
        }

        .social-links {
            display: flex;
            gap: 1.5rem;
            justify-content: center;
            margin-top: 2rem;
        }

        .social-link {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.1);
            display: flex;
            align-items: center;
            justify-content: center;
            color: #ffffff;
            font-size: 1.3rem;
            text-decoration: none;
            transition: var(--transition-smooth);
        }
        
        [data-theme="dark"] .social-link {
            background: var(--color-bg-secondary);
            color: var(--color-text-primary);
        }

        .social-link:hover {
            background: var(--color-accent-blue);
            transform: translateY(-3px);
            color: #ffffff;
        }

        .footer-text {
            margin-top: 3rem;
            padding-top: 2rem;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            color: rgba(255, 255, 255, 0.6);
            font-size: 0.9rem;
        }

        /* ===== SCROLL REVEAL ===== */
        .reveal {
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.8s ease;
        }

        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }

        /* ===== ANIMATIONS ===== */
        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* ===== RESPONSIVE ===== */
        @media (max-width: 768px) {
            .nav-container {
                padding: 0 1.5rem;
            }
            
            .nav-actions {
                gap: 1rem;
            }

            .nav-links {
                position: fixed;
                top: 80px;
                left: -100%;
                width: 100%;
                height: calc(100vh - 80px);
                background: rgba(255, 255, 255, 0.98);
                backdrop-filter: blur(12px);
                flex-direction: column;
                align-items: center;
                justify-content: center;
                gap: 2rem;
                transition: var(--transition-smooth);
            }
            
            [data-theme="dark"] .nav-links {
                background: rgba(15, 23, 42, 0.98);
            }

            .nav-links.active {
                left: 0;
            }

            .mobile-menu-btn {
                display: block;
            }

            section {
                padding: 4rem 1.5rem;
            }

            .hero-title {
                font-size: 2.5rem;
            }

            .portfolio-grid {
                grid-template-columns: 1fr;
            }

            .skills-grid {
                grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
                gap: 1.5rem;
            }

            .hero-buttons {
                flex-direction: column;
                align-items: center;
            }

            .btn {
                width: 100%;
                max-width: 300px;
                justify-content: center;
            }
        }
    </style>
</head>
<body>
    <nav id="navbar">
        <div class="nav-container">
            <a href="#" class="logo">Deepak<span>Gupta</span></a>
            
            <div class="nav-actions">
                <ul class="nav-links" id="navLinks">
                    <li><a href="#hero">Home</a></li>
                    <li><a href="#work">Work</a></li>
                    <li><a href="#skills">Skills</a></li>
                    <li><a href="#contact">Contact</a></li>
                </ul>
                
                <button class="theme-toggle" id="themeToggle" aria-label="Toggle Dark Mode">
                    <i class="fas fa-moon"></i>
                </button>

                <button class="mobile-menu-btn" id="mobileMenuBtn">
                    <i class="fas fa-bars"></i>
                </button>
            </div>
        </div>
    </nav>

    <section id="hero">
        <canvas id="particleCanvas"></canvas>
        <div class="hero-content">
            <p class="hero-subtitle">👋 Welcome to my digital space</p>
            <h1 class="hero-title">
                Creative Developer &<br>
                <span class="gradient-text">UI Designer</span>
            </h1>
            <p class="hero-description">
                I craft beautiful, functional digital experiences through clean code and innovative design. 
                Turning ideas into reality, one pixel at a time.
            </p>
            <div class="hero-buttons">
                <a href="#work" class="btn btn-primary">
                    <span>View My Work</span>
                    <i class="fas fa-arrow-right"></i>
                </a>
                <a href="#contact" class="btn btn-secondary">
                    <span>Get In Touch</span>
                </a>
            </div>
        </div>
    </section>

    <section id="work">
        <div class="section-header reveal">
            <p class="section-subtitle">Portfolio</p>
            <h2 class="section-title">Featured Projects</h2>
            <p class="section-description">
                A selection of recent work showcasing my expertise in web design, development, and VFX.
            </p>
        </div>
        <div class="portfolio-grid">
            <div class="portfolio-card reveal">
                <div class="portfolio-image">
                    <i class="fas fa-palette"></i>
                </div>
                <div class="portfolio-content">
                    <h3 class="portfolio-title">Brand Identity System</h3>
                    <p class="portfolio-description">
                        Complete brand identity and design system for a modern tech startup, including logo, style guide, and digital assets.
                    </p>
                    <div class="portfolio-tags">
                        <span class="tag">Figma</span>
                        <span class="tag">Branding</span>
                        <span class="tag">UI/UX</span>
                    </div>
                </div>
            </div>

            <div class="portfolio-card reveal">
                <div class="portfolio-image" style="background: linear-gradient(135deg, #8b5cf6 0%, #7c3aed 100%);">
                    <i class="fas fa-mobile-alt"></i>
                </div>
                <div class="portfolio-content">
                    <h3 class="portfolio-title">E-Commerce Platform</h3>
                    <p class="portfolio-description">
                        Full-stack e-commerce solution with modern UI, seamless checkout, and real-time inventory management.
                    </p>
                    <div class="portfolio-tags">
                        <span class="tag">React</span>
                        <span class="tag">Node.js</span>
                        <span class="tag">MongoDB</span>
                    </div>
                </div>
            </div>

            <div class="portfolio-card reveal">
                <div class="portfolio-image" style="background: linear-gradient(135deg, #f59e0b 0%, #d97706 100%);">
                    <i class="fas fa-video"></i>
                </div>
                <div class="portfolio-content">
                    <h3 class="portfolio-title">VFX Showreel</h3>
                    <p class="portfolio-description">
                        Professional VFX compositing and motion graphics for commercial projects and creative content.
                    </p>
                    <div class="portfolio-tags">
                        <span class="tag">After Effects</span>
                        <span class="tag">Premiere Pro</span>
                        <span class="tag">VFX</span>
                    </div>
                </div>
            </div>

            <div class="portfolio-card reveal">
                <div class="portfolio-image" style="background: linear-gradient(135deg, #10b981 0%, #059669 100%);">
                    <i class="fas fa-code"></i>
                </div>
                <div class="portfolio-content">
                    <h3 class="portfolio-title">Portfolio Website</h3>
                    <p class="portfolio-description">
                        Interactive portfolio with smooth animations, particle effects, and responsive design for a creative agency.
                    </p>
                    <div class="portfolio-tags">
                        <span class="tag">HTML5</span>
                        <span class="tag">CSS3</span>
                        <span class="tag">JavaScript</span>
                    </div>
                </div>
            </div>

            <div class="portfolio-card reveal">
                <div class="portfolio-image" style="background: linear-gradient(135deg, #ef4444 0%, #dc2626 100%);">
                    <i class="fas fa-chart-line"></i>
                </div>
                <div class="portfolio-content">
                    <h3 class="portfolio-title">Analytics Dashboard</h3>
                    <p class="portfolio-description">
                        Data visualization dashboard with real-time metrics, interactive charts, and clean modern interface.
                    </p>
                    <div class="portfolio-tags">
                        <span class="tag">Next.js</span>
                        <span class="tag">Chart.js</span>
                        <span class="tag">Tailwind</span>
                    </div>
                </div>
            </div>

            <div class="portfolio-card reveal">
                <div class="portfolio-image" style="background: linear-gradient(135deg, #14b8a6 0%, #0891b2 100%);">
                    <i class="fas fa-layer-group"></i>
                </div>
                <div class="portfolio-content">
                    <h3 class="portfolio-title">Design System</h3>
                    <p class="portfolio-description">
                        Comprehensive design system with reusable components, tokens, and documentation for scalable products.
                    </p>
                    <div class="portfolio-tags">
                        <span class="tag">Design System</span>
                        <span class="tag">Storybook</span>
                        <span class="tag">React</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section id="skills">
        <div class="section-header reveal">
            <p class="section-subtitle">Expertise</p>
            <h2 class="section-title">Skills & Technologies</h2>
            <p class="section-description">
                A diverse toolkit enabling me to bring creative visions to life across design and development.
            </p>
        </div>
        <div class="skills-grid">
            <div class="skill-card reveal">
                <div class="skill-icon"><i class="fab fa-html5"></i></div>
                <div class="skill-name">HTML5</div>
            </div>
            <div class="skill-card reveal">
                <div class="skill-icon"><i class="fab fa-css3-alt"></i></div>
                <div class="skill-name">CSS3</div>
            </div>
            <div class="skill-card reveal">
                <div class="skill-icon"><i class="fab fa-js"></i></div>
                <div class="skill-name">JavaScript</div>
            </div>
            <div class="skill-card reveal">
                <div class="skill-icon"><i class="fab fa-react"></i></div>
                <div class="skill-name">React</div>
            </div>
            <div class="skill-card reveal">
                <div class="skill-icon"><i class="fab fa-node"></i></div>
                <div class="skill-name">Node.js</div>
            </div>
            <div class="skill-card reveal">
                <div class="skill-icon"><i class="fab fa-figma"></i></div>
                <div class="skill-name">Figma</div>
            </div>
            <div class="skill-card reveal">
                <div class="skill-icon"><i class="fas fa-pen-nib"></i></div>
                <div class="skill-name">Adobe XD</div>
            </div>
            <div class="skill-card reveal">
                <div class="skill-icon"><i class="fas fa-film"></i></div>
                <div class="skill-name">After Effects</div>
            </div>
        </div>
    </section>

    <section id="contact">
        <div class="section-header reveal">
            <p class="section-subtitle">Get In Touch</p>
            <h2 class="section-title">Let's Work Together</h2>
            <p class="section-description">
                Have a project in mind? Let's create something amazing together.
            </p>
        </div>
        <a href="mailto:hello@thevfx.com" class="contact-email reveal">hello@thevfx.com</a>
        <div class="social-links reveal">
            <a href="https://github.com/deepakguptafx" class="social-link" target="_blank" rel="noopener">
                <i class="fab fa-github"></i>
            </a>
            <a href="https://linkedin.com/in/deepakguptafx" class="social-link" target="_blank" rel="noopener">
                <i class="fab fa-linkedin-in"></i>
            </a>
            <a href="https://twitter.com/deepakguptafx" class="social-link" target="_blank" rel="noopener">
                <i class="fab fa-twitter"></i>
            </a>
            <a href="https://dribbble.com/thevfx" class="social-link" target="_blank" rel="noopener">
                <i class="fab fa-dribbble"></i>
            </a>
            <a href="https://instagram.com/deepakguptafx" class="social-link" target="_blank" rel="noopener">
                <i class="fab fa-instagram"></i>
            </a>
        </div>
        <p class="footer-text">
            © 2025 The VFX. Crafted with <i class="fas fa-heart" style="color: #ef4444;"></i> and code.
        </p>
    </section>

    <script>
        // ===== THEME TOGGLE =====
        const themeToggle = document.getElementById('themeToggle');
        const themeIcon = themeToggle.querySelector('i');
        const htmlElement = document.documentElement;

        // Check for saved user preference, if any, on load
        const savedTheme = localStorage.getItem('theme');
        if (savedTheme) {
            htmlElement.setAttribute('data-theme', savedTheme);
            if (savedTheme === 'dark') {
                themeIcon.classList.remove('fa-moon');
                themeIcon.classList.add('fa-sun');
            }
        }

        themeToggle.addEventListener('click', () => {
            const currentTheme = htmlElement.getAttribute('data-theme');
            const newTheme = currentTheme === 'light' ? 'dark' : 'light';
            
            htmlElement.setAttribute('data-theme', newTheme);
            localStorage.setItem('theme', newTheme);

            // Toggle Icon
            if (newTheme === 'dark') {
                themeIcon.classList.remove('fa-moon');
                themeIcon.classList.add('fa-sun');
            } else {
                themeIcon.classList.remove('fa-sun');
                themeIcon.classList.add('fa-moon');
            }
        });

        // ===== PARTICLE CANVAS ANIMATION =====
        const canvas = document.getElementById('particleCanvas');
        const ctx = canvas.getContext('2d');

        let particlesArray = [];
        let mouse = {
            x: null,
            y: null,
            radius: 150
        };

        // Set canvas size (FIXED for scrollbar issue)
        function setCanvasSize() {
            // Using clientWidth excludes the scrollbar, preventing horizontal overflow
            canvas.width = document.documentElement.clientWidth || document.body.clientWidth;
            canvas.height = window.innerHeight;
        }
        setCanvasSize();

        window.addEventListener('resize', () => {
            setCanvasSize();
            init();
        });

        // Mouse movement
        canvas.addEventListener('mousemove', (e) => {
            mouse.x = e.x;
            mouse.y = e.y;
        });

        canvas.addEventListener('mouseleave', () => {
            mouse.x = null;
            mouse.y = null;
        });

        // Particle class
        class Particle {
            constructor(x, y, directionX, directionY, size, color) {
                this.x = x;
                this.y = y;
                this.directionX = directionX;
                this.directionY = directionY;
                this.size = size;
                this.color = color;
            }

            draw() {
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2, false);
                ctx.fillStyle = this.color;
                ctx.fill();
            }

            update() {
                if (this.x > canvas.width || this.x < 0) {
                    this.directionX = -this.directionX;
                }
                if (this.y > canvas.height || this.y < 0) {
                    this.directionY = -this.directionY;
                }

                // Mouse interaction
                let dx = mouse.x - this.x;
                let dy = mouse.y - this.y;
                let distance = Math.sqrt(dx * dx + dy * dy);

                if (distance < mouse.radius + this.size) {
                    if (mouse.x < this.x && this.x < canvas.width - this.size * 10) {
                        this.x += 2;
                    }
                    if (mouse.x > this.x && this.x > this.size * 10) {
                        this.x -= 2;
                    }
                    if (mouse.y < this.y && this.y < canvas.height - this.size * 10) {
                        this.y += 2;
                    }
                    if (mouse.y > this.y && this.y > this.size * 10) {
                        this.y -= 2;
                    }
                }

                this.x += this.directionX;
                this.y += this.directionY;
                this.draw();
            }
        }

        // Initialize particles
        function init() {
            particlesArray = [];
            let numberOfParticles = (canvas.width * canvas.height) / 9000;

            for (let i = 0; i < numberOfParticles; i++) {
                let size = (Math.random() * 3) + 1;
                let x = (Math.random() * ((canvas.width - size * 2) - (size * 2)) + size * 2);
                let y = (Math.random() * ((canvas.height - size * 2) - (size * 2)) + size * 2);
                let directionX = (Math.random() * 0.4) - 0.2;
                let directionY = (Math.random() * 0.4) - 0.2;
                let color = 'rgba(37, 99, 235, 0.8)';

                particlesArray.push(new Particle(x, y, directionX, directionY, size, color));
            }
        }

        // Connect particles
        function connect() {
            let opacityValue = 1;
            for (let a = 0; a < particlesArray.length; a++) {
                for (let b = a; b < particlesArray.length; b++) {
                    let dx = particlesArray[a].x - particlesArray[b].x;
                    let dy = particlesArray[a].y - particlesArray[b].y;
                    let distance = Math.sqrt(dx * dx + dy * dy);

                    if (distance < (canvas.width / 7) * (canvas.height / 7) / 1000) {
                        opacityValue = 1 - (distance / 100);
                        ctx.strokeStyle = `rgba(37, 99, 235, ${opacityValue})`;
                        ctx.lineWidth = 1;
                        ctx.beginPath();
                        ctx.moveTo(particlesArray[a].x, particlesArray[a].y);
                        ctx.lineTo(particlesArray[b].x, particlesArray[b].y);
                        ctx.stroke();
                    }
                }
            }
        }

        // Animation loop
        function animate() {
            requestAnimationFrame(animate);
            ctx.clearRect(0, 0, canvas.width, canvas.height);

            for (let i = 0; i < particlesArray.length; i++) {
                particlesArray[i].update();
            }
            connect();
        }

        init();
        animate();

        // ===== SCROLL REVEAL ANIMATION =====
        function reveal() {
            const reveals = document.querySelectorAll('.reveal');

            reveals.forEach(element => {
                const windowHeight = window.innerHeight;
                const elementTop = element.getBoundingClientRect().top;
                const elementVisible = 100;

                if (elementTop < windowHeight - elementVisible) {
                    element.classList.add('active');
                }
            });
        }

        window.addEventListener('scroll', reveal);
        reveal(); // Initial check

        // ===== NAVBAR SCROLL EFFECT =====
        const navbar = document.getElementById('navbar');

        window.addEventListener('scroll', () => {
            if (window.scrollY > 100) {
                navbar.classList.add('scrolled');
            } else {
                navbar.classList.remove('scrolled');
            }
        });

        // ===== MOBILE MENU =====
        const mobileMenuBtn = document.getElementById('mobileMenuBtn');
        const navLinks = document.getElementById('navLinks');

        mobileMenuBtn.addEventListener('click', () => {
            navLinks.classList.toggle('active');
            const icon = mobileMenuBtn.querySelector('i');

            if (navLinks.classList.contains('active')) {
                icon.classList.remove('fa-bars');
                icon.classList.add('fa-times');
            } else {
                icon.classList.remove('fa-times');
                icon.classList.add('fa-bars');
            }
        });

        // Close menu when clicking on a link
        navLinks.querySelectorAll('a').forEach(link => {
            link.addEventListener('click', () => {
                navLinks.classList.remove('active');
                const icon = mobileMenuBtn.querySelector('i');
                icon.classList.remove('fa-times');
                icon.classList.add('fa-bars');
            });
        });

        // ===== SMOOTH SCROLLING FOR ANCHOR LINKS =====
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));

                if (target) {
                    const offsetTop = target.offsetTop - 80;
                    window.scrollTo({
                        top: offsetTop,
                        behavior: 'smooth'
                    });
                }
            });
        });
    </script>
</body>
</html># medtrial
