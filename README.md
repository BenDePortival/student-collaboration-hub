<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Student Collaboration Hub</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary-blue: #2563eb;
            --secondary-blue: #3b82f6;
            --accent-purple: #8b5cf6;
            --light-bg: #f8fafc;
            --dark-text: #1e293b;
            --light-text: #ffffff;
            --gray-text: #64748b;
            --border-color: #e2e8f0;
            --success: #10b981;
            --warning: #f59e0b;
            --danger: #ef4444;
        }

        body {
            font-family: 'Inter', sans-serif;
            background-color: var(--light-bg);
            color: var(--dark-text);
            line-height: 1.6;
        }

        h1, h2, h3, h4, h5, h6 {
            font-family: 'Poppins', sans-serif;
            font-weight: 600;
            line-height: 1.3;
        }

        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        .btn {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            padding: 12px 24px;
            background-color: var(--primary-blue);
            color: var(--light-text);
            text-decoration: none;
            border-radius: 8px;
            font-weight: 500;
            border: none;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 14px;
        }

        .btn:hover {
            background-color: var(--secondary-blue);
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(37, 99, 235, 0.2);
        }

        .btn-outline {
            background-color: transparent;
            border: 2px solid var(--primary-blue);
            color: var(--primary-blue);
        }

        .btn-outline:hover {
            background-color: var(--primary-blue);
            color: var(--light-text);
        }

        .btn-sm {
            padding: 8px 16px;
            font-size: 12px;
        }

        .badge {
            display: inline-block;
            padding: 4px 8px;
            border-radius: 12px;
            font-size: 12px;
            font-weight: 500;
        }

        .badge-primary {
            background-color: var(--primary-blue);
            color: var(--light-text);
        }

        .badge-success {
            background-color: var(--success);
            color: var(--light-text);
        }

        /* Header */
        header {
            background-color: var(--light-text);
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .header-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 16px 0;
        }

        .logo {
            font-family: 'Poppins', sans-serif;
            font-size: 24px;
            font-weight: 700;
            color: var(--primary-blue);
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .logo i {
            color: var(--accent-purple);
        }

        nav ul {
            display: flex;
            list-style: none;
            gap: 24px;
        }

        nav ul li a {
            text-decoration: none;
            color: var(--dark-text);
            font-weight: 500;
            transition: color 0.3s ease;
            display: flex;
            align-items: center;
            gap: 6px;
        }

        nav ul li a:hover {
            color: var(--primary-blue);
        }

        .auth-buttons {
            display: flex;
            gap: 12px;
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(135deg, var(--primary-blue), var(--accent-purple));
            color: var(--light-text);
            padding: 80px 0;
            text-align: center;
        }

        .hero-content {
            max-width: 800px;
            margin: 0 auto;
        }

        .hero h1 {
            font-size: 3rem;
            margin-bottom: 20px;
            color: var(--light-text);
        }

        .hero p {
            font-size: 1.2rem;
            margin-bottom: 30px;
            opacity: 0.9;
        }

        .hero-stats {
            display: flex;
            justify-content: center;
            gap: 40px;
            margin-top: 40px;
        }

        .stat-item {
            text-align: center;
        }

        .stat-number {
            font-size: 2rem;
            font-weight: 700;
            margin-bottom: 5px;
        }

        /* Dashboard */
        .dashboard {
            padding: 40px 0;
        }

        .dashboard-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
        }

        .section-title {
            font-size: 1.8rem;
            color: var(--dark-text);
            margin-bottom: 30px;
        }

        /* Cards Grid */
        .cards-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 24px;
            margin-bottom: 40px;
        }

        .card {
            background: var(--light-text);
            border-radius: 12px;
            padding: 24px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.05);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
        }

        .card-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 16px;
        }

        .card-title {
            font-size: 1.3rem;
            color: var(--dark-text);
            margin: 0;
        }

        .chart-container {
            height: 200px;
            margin: 20px 0;
        }

        /* Forum Section */
        .forum-section {
            background-color: var(--light-text);
            padding: 60px 0;
            border-radius: 12px;
            margin: 40px 0;
        }

        .forum-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
        }

        .post-item {
            background: var(--light-text);
            border-radius: 12px;
            padding: 24px;
            margin-bottom: 20px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.05);
            border-left: 4px solid var(--primary-blue);
        }

        .post-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 12px;
        }

        .post-title {
            font-size: 1.2rem;
            margin: 0;
            color: var(--dark-text);
        }

        .post-meta {
            display: flex;
            align-items: center;
            gap: 16px;
            font-size: 0.9rem;
            color: var(--gray-text);
        }

        .post-content {
            margin: 16px 0;
            color: var(--dark-text);
        }

        .post-actions {
            display: flex;
            gap: 20px;
            margin-top: 16px;
        }

        .action-btn {
            display: flex;
            align-items: center;
            gap: 6px;
            background: none;
            border: none;
            color: var(--gray-text);
            cursor: pointer;
            font-size: 0.9rem;
            transition: color 0.3s ease;
        }

        .action-btn:hover {
            color: var(--primary-blue);
        }

        .tags {
            display: flex;
            gap: 8px;
            margin-top: 12px;
        }

        .tag {
            background-color: var(--light-bg);
            color: var(--primary-blue);
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 500;
        }

        /* Chart Editor */
        .chart-editor {
            background: var(--light-text);
            border-radius: 12px;
            padding: 30px;
            margin: 40px 0;
            box-shadow: 0 4px 6px rgba(0,0,0,0.05);
        }

        .editor-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 24px;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
            color: var(--dark-text);
        }

        .form-control {
            width: 100%;
            padding: 12px 16px;
            border: 2px solid var(--border-color);
            border-radius: 8px;
            font-family: 'Inter', sans-serif;
            font-size: 14px;
            transition: border-color 0.3s ease;
        }

        .form-control:focus {
            outline: none;
            border-color: var(--primary-blue);
        }

        .editor-tools {
            display: flex;
            gap: 12px;
            margin-bottom: 20px;
            flex-wrap: wrap;
        }

        .tool-btn {
            padding: 8px 16px;
            background-color: var(--light-bg);
            border: 1px solid var(--border-color);
            border-radius: 6px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .tool-btn:hover {
            background-color: var(--primary-blue);
            color: var(--light-text);
            border-color: var(--primary-blue);
        }

        .tool-btn.active {
            background-color: var(--primary-blue);
            color: var(--light-text);
            border-color: var(--primary-blue);
        }

        /* Profile Section */
        .profile-header {
            display: flex;
            align-items: center;
            gap: 30px;
            margin-bottom: 30px;
            padding: 30px;
            background: var(--light-text);
            border-radius: 12px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.05);
        }

        .avatar {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--primary-blue), var(--accent-purple));
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--light-text);
            font-size: 3rem;
            font-weight: bold;
        }

        .profile-info h2 {
            font-size: 2rem;
            margin-bottom: 10px;
        }

        .profile-stats {
            display: flex;
            gap: 30px;
            margin-top: 15px;
        }

        .stat {
            text-align: center;
        }

        .stat-value {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--primary-blue);
        }

        .stat-label {
            font-size: 0.9rem;
            color: var(--gray-text);
        }

        /* Footer */
        footer {
            background-color: var(--dark-text);
            color: var(--light-text);
            padding: 60px 0 30px;
            margin-top: 80px;
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 40px;
            margin-bottom: 40px;
        }

        .footer-column h3 {
            color: var(--light-text);
            margin-bottom: 20px;
            font-size: 1.3rem;
        }

        .footer-column ul {
            list-style: none;
        }

        .footer-column ul li {
            margin-bottom: 10px;
        }

        .footer-column ul li a {
            color: #94a3b8;
            text-decoration: none;
            transition: color 0.3s ease;
        }

        .footer-column ul li a:hover {
            color: var(--light-text);
        }

        .social-links {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }

        .social-links a {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 40px;
            height: 40px;
            background-color: rgba(255,255,255,0.1);
            border-radius: 50%;
            color: var(--light-text);
            transition: background-color 0.3s ease;
        }

        .social-links a:hover {
            background-color: var(--primary-blue);
        }

        .copyright {
            text-align: center;
            padding-top: 30px;
            border-top: 1px solid rgba(255,255,255,0.1);
            color: #94a3b8;
            font-size: 0.9rem;
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 2.2rem;
            }
            
            .hero-stats {
                flex-direction: column;
                gap: 20px;
            }
            
            .dashboard-header {
                flex-direction: column;
                gap: 20px;
                align-items: flex-start;
            }
            
            .forum-header {
                flex-direction: column;
                gap: 20px;
                align-items: flex-start;
            }
            
            .profile-header {
                flex-direction: column;
                text-align: center;
            }
            
            .profile-stats {
                justify-content: center;
            }
        }

        @media (max-width: 480px) {
            nav ul {
                display: none;
            }
            
            .auth-buttons {
                display: none;
            }
            
            .mobile-menu-btn {
                display: block;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="container header-container">
            <a href="#" class="logo">
                <i class="fas fa-graduation-cap"></i>
                StudentHub
            </a>
            <nav>
                <ul>
                    <li><a href="#dashboard"><i class="fas fa-home"></i> Dashboard</a></li>
                    <li><a href="#charts"><i class="fas fa-chart-bar"></i> Charts</a></li>
                    <li><a href="#forum"><i class="fas fa-comments"></i> Forum</a></li>
                    <li><a href="#profile"><i class="fas fa-user"></i> Profile</a></li>
                </ul>
            </nav>
            <div class="auth-buttons">
                <button class="btn btn-outline" id="loginBtn">Login</button>
                <button class="btn" id="signupBtn">Sign Up</button>
            </div>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero">
        <div class="container hero-content">
            <h1>Collaborate, Create, and Chart Your Academic Success</h1>
            <p>Student Collaboration Hub is the ultimate platform for students to create interactive charts, share ideas, and collaborate with peers in a dynamic academic environment.</p>
            <div class="hero-btns">
                <button class="btn btn-lg"><i class="fas fa-rocket"></i> Get Started</button>
                <button class="btn btn-outline btn-lg"><i class="fas fa-play-circle"></i> Watch Demo</button>
            </div>
            <div class="hero-stats">
                <div class="stat-item">
                    <div class="stat-number">10K+</div>
                    <div class="stat-label">Active Students</div>
                </div>
                <div class="stat-item">
                    <div class="stat-number">50K+</div>
                    <div class="stat-label">Charts Created</div>
                </div>
                <div class="stat-item">
                    <div class="stat-number">100K+</div>
                    <div class="stat-label">Ideas Shared</div>
                </div>
            </div>
        </div>
    </section>

    <!-- Dashboard -->
    <section class="dashboard" id="dashboard">
        <div class="container">
            <div class="dashboard-header">
                <h2 class="section-title">Your Dashboard</h2>
                <button class="btn"><i class="fas fa-plus"></i> Create New Chart</button>
            </div>
            
            <div class="cards-grid">
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">Recent Charts</h3>
                        <span class="badge badge-primary">3 New</span>
                    </div>
                    <div class="chart-container">
                        <canvas id="recentChart"></canvas>
                    </div>
                    <p>Your most recently created charts and visualizations.</p>
                </div>
                
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">Popular Discussions</h3>
                        <span class="badge badge-success">Hot</span>
                    </div>
                    <div class="post-item">
                        <div class="post-header">
                            <h4 class="post-title">Best Study Techniques for Exams</h4>
                        </div>
                        <div class="post-meta">
                            <span><i class="fas fa-user"></i> Sarah Johnson</span>
                            <span><i class="fas fa-clock"></i> 2 hours ago</span>
                        </div>
                        <div class="tags">
                            <span class="tag">Study Tips</span>
                            <span class="tag">Exams</span>
                        </div>
                    </div>
                    <div class="post-item">
                        <div class="post-header">
                            <h4 class="post-title">Python vs JavaScript for Data Science</h4>
                        </div>
                        <div class="post-meta">
                            <span><i class="fas fa-user"></i> Mike Chen</span>
                            <span><i class="fas fa-clock"></i> 5 hours ago</span>
                        </div>
                        <div class="tags">
                            <span class="tag">Programming</span>
                            <span class="tag">Data Science</span>
                        </div>
                    </div>
                </div>
                
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">Your Activity</h3>
                    </div>
                    <div class="activity-item">
                        <p><i class="fas fa-chart-line"></i> Created new bar chart: "Project Timeline"</p>
                        <small class="text-muted">Today, 10:30 AM</small>
                    </div>
                    <div class="activity-item">
                        <p><i class="fas fa-comment"></i> Commented on "Machine Learning Resources"</p>
                        <small class="text-muted">Yesterday, 3:45 PM</small>
                    </div>
                    <div class="activity-item">
                        <p><i 