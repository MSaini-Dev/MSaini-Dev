<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MSaini-Dev | AI Developer & Full-Stack Engineer</title>
    
    <!-- Fonts & Icons -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:ital,wght@0,300;0,400;0,600;0,700;0,800;1,400&family=Space+Grotesk:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    
    <!-- Three.js for 3D effects -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', 'Space Grotesk', sans-serif;
            background: linear-gradient(135deg, #0a0a0a 0%, #1a1a2e 50%, #0a0a0a 100%);
            color: #ffffff;
            overflow-x: hidden;
            position: relative;
        }

        /* Animated background canvas */
        #bg-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
            opacity: 0.3;
        }

        .content {
            position: relative;
            z-index: 1;
        }

        /* Glass morphism effect */
        .glass {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            border: 1px solid rgba(167, 139, 250, 0.2);
            transition: all 0.3s ease;
        }

        .glass:hover {
            border-color: rgba(167, 139, 250, 0.5);
            box-shadow: 0 0 20px rgba(167, 139, 250, 0.2);
            transform: translateY(-5px);
        }

        /* Gradient text */
        .gradient-text {
            background: linear-gradient(135deg, #A78BFA 0%, #EC4899 50%, #06B6D4 100%);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            animation: gradientShift 5s ease infinite;
        }

        @keyframes gradientShift {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }

        /* Typing animation */
        .typing-container {
            font-size: 1.5rem;
            font-family: 'Space Grotesk', monospace;
            border-right: 3px solid #A78BFA;
            white-space: nowrap;
            overflow: hidden;
            animation: blinkCursor 0.75s step-end infinite;
        }

        @keyframes blinkCursor {
            from, to { border-color: transparent; }
            50% { border-color: #A78BFA; }
        }

        /* Skill bar animation */
        .skill-bar {
            height: 8px;
            background: rgba(255,255,255,0.1);
            border-radius: 10px;
            overflow: hidden;
            position: relative;
        }

        .skill-progress {
            height: 100%;
            background: linear-gradient(90deg, #A78BFA, #EC4899);
            border-radius: 10px;
            width: 0;
            transition: width 1.5s ease-in-out;
            position: relative;
            animation: shimmer 2s infinite;
        }

        @keyframes shimmer {
            0% { opacity: 1; }
            50% { opacity: 0.8; }
            100% { opacity: 1; }
        }

        /* Stats counter */
        .stat-number {
            font-size: 2.5rem;
            font-weight: bold;
            background: linear-gradient(135deg, #A78BFA, #EC4899);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        /* Particle effect */
        .particle {
            position: absolute;
            width: 2px;
            height: 2px;
            background: #A78BFA;
            border-radius: 50%;
            opacity: 0;
            animation: floatParticle 3s infinite;
        }

        @keyframes floatParticle {
            0% {
                transform: translateY(0) rotate(0deg);
                opacity: 0;
            }
            50% {
                opacity: 1;
            }
            100% {
                transform: translateY(-100px) rotate(360deg);
                opacity: 0;
            }
        }

        /* Responsive design */
        @media (max-width: 768px) {
            .typing-container {
                font-size: 1rem;
                white-space: normal;
            }
            
            .stat-number {
                font-size: 1.5rem;
            }
        }

        /* Scroll reveal animation */
        .reveal {
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.8s ease;
        }

        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }

        /* Custom scrollbar */
        ::-webkit-scrollbar {
            width: 10px;
        }

        ::-webkit-scrollbar-track {
            background: #1a1a2e;
        }

        ::-webkit-scrollbar-thumb {
            background: linear-gradient(135deg, #A78BFA, #EC4899);
            border-radius: 10px;
        }
    </style>
</head>
<body>

<canvas id="bg-canvas"></canvas>

<div class="content">
    <!-- Hero Section -->
    <div style="min-height: 100vh; display: flex; align-items: center; justify-content: center; padding: 2rem;">
        <div style="text-align: center; max-width: 800px;">
            <div class="glass" style="padding: 3rem; margin-bottom: 2rem;">
                <h1 style="font-size: 4rem; margin-bottom: 1rem;" class="gradient-text">
                    MSaini-Dev
                </h1>
                
                <div class="typing-container" id="typing-text" style="display: inline-block; text-align: center; margin-bottom: 2rem;"></div>
                
                <p style="font-size: 1.2rem; margin: 2rem 0; opacity: 0.9;">
                    Building autonomous AI systems that think, learn, and evolve 🚀
                </p>
                
                <div style="display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap;">
                    <a href="#projects" style="text-decoration: none;">
                        <div style="background: linear-gradient(135deg, #A78BFA, #EC4899); padding: 12px 24px; border-radius: 50px; color: white; font-weight: bold; transition: transform 0.3s;">
                            <i class="fas fa-code"></i> Explore Work
                        </div>
                    </a>
                    <a href="https://github.com/MSaini-Dev" target="_blank" style="text-decoration: none;">
                        <div style="background: rgba(255,255,255,0.1); padding: 12px 24px; border-radius: 50px; color: white; transition: transform 0.3s;">
                            <i class="fab fa-github"></i> GitHub
                        </div>
                    </a>
                </div>
            </div>
            
            <!-- Stats Row -->
            <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 1rem; margin-top: 2rem;">
                <div class="glass" style="padding: 1.5rem;">
                    <div class="stat-number" id="github-stars">0</div>
                    <div style="margin-top: 0.5rem;">GitHub Stars</div>
                    <i class="fas fa-star" style="color: #FBBF24;"></i>
                </div>
                <div class="glass" style="padding: 1.5rem;">
                    <div class="stat-number" id="github-followers">0</div>
                    <div style="margin-top: 0.5rem;">Followers</div>
                    <i class="fas fa-users"></i>
                </div>
                <div class="glass" style="padding: 1.5rem;">
                    <div class="stat-number" id="ai-projects">0</div>
                    <div style="margin-top: 0.5rem;">AI Projects</div>
                    <i class="fas fa-brain"></i>
                </div>
            </div>
        </div>
    </div>

    <!-- Expertise Section -->
    <div style="padding: 4rem 2rem;" class="reveal">
        <h2 style="text-align: center; font-size: 2.5rem; margin-bottom: 3rem;">
            <span class="gradient-text">🧠 Technical Expertise</span>
        </h2>
        
        <div style="max-width: 1200px; margin: 0 auto;">
            <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 2rem;">
                <!-- AI/ML -->
                <div class="glass" style="padding: 2rem;">
                    <i class="fas fa-robot" style="font-size: 2rem; color: #A78BFA; margin-bottom: 1rem;"></i>
                    <h3 style="margin-bottom: 1rem;">AI & Machine Learning</h3>
                    <div class="skill-bar" style="margin-bottom: 1rem;">
                        <div class="skill-progress" style="width: 95%;"></div>
                    </div>
                    <p>LLMs, RAG Systems, Deep Learning, MCP Servers</p>
                </div>
                
                <!-- Full-Stack -->
                <div class="glass" style="padding: 2rem;">
                    <i class="fas fa-layer-group" style="font-size: 2rem; color: #EC4899; margin-bottom: 1rem;"></i>
                    <h3 style="margin-bottom: 1rem;">Full-Stack Development</h3>
                    <div class="skill-bar" style="margin-bottom: 1rem;">
                        <div class="skill-progress" style="width: 90%;"></div>
                    </div>
                    <p>React, Next.js, TypeScript, FastAPI, Node.js</p>
                </div>
                
                <!-- Data Engineering -->
                <div class="glass" style="padding: 2rem;">
                    <i class="fas fa-database" style="font-size: 2rem; color: #06B6D4; margin-bottom: 1rem;"></i>
                    <h3 style="margin-bottom: 1rem;">Data & DevOps</h3>
                    <div class="skill-bar" style="margin-bottom: 1rem;">
                        <div class="skill-progress" style="width: 85%;"></div>
                    </div>
                    <p>PySpark, MongoDB, Docker, Cloud Architecture</p>
                </div>
            </div>
        </div>
    </div>

    <!-- Featured Projects -->
    <div style="padding: 4rem 2rem; background: rgba(0,0,0,0.3);" class="reveal">
        <h2 style="text-align: center; font-size: 2.5rem; margin-bottom: 3rem;">
            <span class="gradient-text">🚀 Featured Projects</span>
        </h2>
        
        <div style="max-width: 1200px; margin: 0 auto;">
            <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(350px, 1fr)); gap: 2rem;">
                <!-- Project 1 -->
                <div class="glass" style="padding: 2rem;" onclick="window.open('https://github.com/MSaini-Dev/self_evolving_agent', '_blank')" style="cursor: pointer;">
                    <i class="fas fa-brain" style="font-size: 2rem; color: #A78BFA;"></i>
                    <h3 style="margin: 1rem 0;">Self-Evolving Agent</h3>
                    <p>Autonomous agent that learns from interactions and improves over time using reinforcement learning.</p>
                    <div style="margin-top: 1rem;">
                        <span style="background: rgba(167, 139, 250, 0.2); padding: 4px 8px; border-radius: 5px; font-size: 0.8rem;">Python</span>
                        <span style="background: rgba(167, 139, 250, 0.2); padding: 4px 8px; border-radius: 5px; font-size: 0.8rem;">LangChain</span>
                        <span style="background: rgba(167, 139, 250, 0.2); padding: 4px 8px; border-radius: 5px; font-size: 0.8rem;">OpenAI</span>
                    </div>
                </div>
                
                <!-- Project 2 -->
                <div class="glass" style="padding: 2rem;">
                    <i class="fas fa-search" style="font-size: 2rem; color: #EC4899;"></i>
                    <h3 style="margin: 1rem 0;">RAG Knowledge System</h3>
                    <p>Advanced retrieval-augmented generation system for domain-specific knowledge bases.</p>
                    <div style="margin-top: 1rem;">
                        <span style="background: rgba(236, 72, 153, 0.2); padding: 4px 8px; border-radius: 5px; font-size: 0.8rem;">Vector DB</span>
                        <span style="background: rgba(236, 72, 153, 0.2); padding: 4px 8px; border-radius: 5px; font-size: 0.8rem;">LLM</span>
                        <span style="background: rgba(236, 72, 153, 0.2); padding: 4px 8px; border-radius: 5px; font-size: 0.8rem;">FAISS</span>
                    </div>
                </div>
                
                <!-- Project 3 -->
                <div class="glass" style="padding: 2rem;">
                    <i class="fas fa-chart-line" style="font-size: 2rem; color: #06B6D4;"></i>
                    <h3 style="margin: 1rem 0;">AI Dashboard Suite</h3>
                    <p>Real-time analytics dashboard for monitoring AI system performance and metrics.</p>
                    <div style="margin-top: 1rem;">
                        <span style="background: rgba(6, 182, 212, 0.2); padding: 4px 8px; border-radius: 5px; font-size: 0.8rem;">React</span>
                        <span style="background: rgba(6, 182, 212, 0.2); padding: 4px 8px; border-radius: 5px; font-size: 0.8rem;">D3.js</span>
                        <span style="background: rgba(6, 182, 212, 0.2); padding: 4px 8px; border-radius: 5px; font-size: 0.8rem;">WebSocket</span>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Tech Stack -->
    <div style="padding: 4rem 2rem;" class="reveal">
        <h2 style="text-align: center; font-size: 2.5rem; margin-bottom: 3rem;">
            <span class="gradient-text">🛠️ Tech Stack</span>
        </h2>
        
        <div style="max-width: 1000px; margin: 0 auto;">
            <div style="display: flex; flex-wrap: wrap; gap: 1rem; justify-content: center;">
                <span class="glass" style="padding: 10px 20px;"><i class="fab fa-python"></i> Python</span>
                <span class="glass" style="padding: 10px 20px;"><i class="fab fa-js"></i> JavaScript/TS</span>
                <span class="glass" style="padding: 10px 20px;"><i class="fab fa-react"></i> React/Next.js</span>
                <span class="glass" style="padding: 10px 20px;"><i class="fas fa-brain"></i> PyTorch</span>
                <span class="glass" style="padding: 10px 20px;"><i class="fas fa-database"></i> MongoDB</span>
                <span class="glass" style="padding: 10px 20px;"><i class="fab fa-docker"></i> Docker</span>
                <span class="glass" style="padding: 10px 20px;"><i class="fas fa-cloud"></i> AWS/GCP</span>
                <span class="glass" style="padding: 10px 20px;"><i class="fas fa-chart-line"></i> PySpark</span>
            </div>
        </div>
    </div>

    <!-- Connect Section -->
    <div style="padding: 4rem 2rem; text-align: center;" class="reveal">
        <div class="glass" style="padding: 3rem; max-width: 800px; margin: 0 auto;">
            <h2 style="margin-bottom: 1rem;">🤝 Let's Connect</h2>
            <p style="margin-bottom: 2rem;">Open for collaborations, AI consulting, and innovative projects</p>
            
            <div style="display: flex; gap: 1.5rem; justify-content: center; flex-wrap: wrap;">
                <a href="https://github.com/MSaini-Dev" target="_blank" style="color: white; text-decoration: none;">
                    <div style="background: #333; padding: 12px; border-radius: 50%; width: 50px; height: 50px; display: flex; align-items: center; justify-content: center; transition: transform 0.3s;">
                        <i class="fab fa-github" style="font-size: 1.5rem;"></i>
                    </div>
                </a>
                <a href="https://twitter.com/MSainiDev" target="_blank" style="color: white; text-decoration: none;">
                    <div style="background: #1DA1F2; padding: 12px; border-radius: 50%; width: 50px; height: 50px; display: flex; align-items: center; justify-content: center; transition: transform 0.3s;">
                        <i class="fab fa-twitter" style="font-size: 1.5rem;"></i>
                    </div>
                </a>
                <a href="https://linkedin.com/in/msaini-dev" target="_blank" style="color: white; text-decoration: none;">
                    <div style="background: #0A66C2; padding: 12px; border-radius: 50%; width: 50px; height: 50px; display: flex; align-items: center; justify-content: center; transition: transform 0.3s;">
                        <i class="fab fa-linkedin-in" style="font-size: 1.5rem;"></i>
                    </div>
                </a>
            </div>
            
            <p style="margin-top: 2rem;">
                <i class="fas fa-envelope"></i> msaini@example.com
            </p>
        </div>
    </div>
</div>

<script>
    // 3D Background Animation
    const scene = new THREE.Scene();
    const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
    const renderer = new THREE.WebGLRenderer({ canvas: document.getElementById('bg-canvas'), alpha: true });
    
    renderer.setSize(window.innerWidth, window.innerHeight);
    renderer.setPixelRatio(window.devicePixelRatio);
    
    // Create particle system
    const particlesGeometry = new THREE.BufferGeometry();
    const particlesCount = 2000;
    const posArray = new Float32Array(particlesCount * 3);
    
    for(let i = 0; i < particlesCount * 3; i += 3) {
        posArray[i] = (Math.random() - 0.5) * 2000;
        posArray[i+1] = (Math.random() - 0.5) * 1000;
        posArray[i+2] = (Math.random() - 0.5) * 1000 - 500;
    }
    
    particlesGeometry.setAttribute('position', new THREE.BufferAttribute(posArray, 3));
    
    const particlesMaterial = new THREE.PointsMaterial({
        size: 0.5,
        color: 0xA78BFA,
        transparent: true,
        opacity: 0.5
    });
    
    const particlesMesh = new THREE.Points(particlesGeometry, particlesMaterial);
    scene.add(particlesMesh);
    
    camera.position.z = 500;
    
    // Animation
    function animate() {
        requestAnimationFrame(animate);
        particlesMesh.rotation.x += 0.0005;
        particlesMesh.rotation.y += 0.001;
        renderer.render(scene, camera);
    }
    
    animate();
    
    // Typing animation
    const texts = [
        "AI Developer 🤖",
        "Full-Stack Engineer ⚛️",
        "Systems Architect 🏗️",
        "Open Source Contributor 🌟"
    ];
    let textIndex = 0;
    let charIndex = 0;
    let isDeleting = false;
    
    function typeEffect() {
        const currentText = texts[textIndex];
        const typingElement = document.getElementById('typing-text');
        
        if (isDeleting) {
            typingElement.textContent = currentText.substring(0, charIndex - 1);
            charIndex--;
        } else {
            typingElement.textContent = currentText.substring(0, charIndex + 1);
            charIndex++;
        }
        
        if (!isDeleting && charIndex === currentText.length) {
            isDeleting = true;
            setTimeout(typeEffect, 2000);
            return;
        }
        
        if (isDeleting && charIndex === 0) {
            isDeleting = false;
            textIndex = (textIndex + 1) % texts.length;
        }
        
        const speed = isDeleting ? 50 : 100;
        setTimeout(typeEffect, speed);
    }
    
    typeEffect();
    
    // Fetch GitHub stats
    fetch('https://api.github.com/users/MSaini-Dev')
        .then(response => response.json())
        .then(data => {
            document.getElementById('github-followers').textContent = data.followers || 0;
        })
        .catch(error => console.error('Error fetching GitHub data:', error));
    
    // Animated counter for AI projects
    let aiProjectsCount = 0;
    const aiProjectsTarget = 15;
    const aiProjectsElement = document.getElementById('ai-projects');
    
    function updateAICount() {
        if (aiProjectsCount < aiProjectsTarget) {
            aiProjectsCount++;
            aiProjectsElement.textContent = aiProjectsCount;
            setTimeout(updateAICount, 50);
        }
    }
    
    updateAICount();
    
    // Scroll reveal animation
    const reveals = document.querySelectorAll('.reveal');
    
    function reveal() {
        for (let i = 0; i < reveals.length; i++) {
            const windowHeight = window.innerHeight;
            const revealTop = reveals[i].getBoundingClientRect().top;
            const revealPoint = 150;
            
            if (revealTop < windowHeight - revealPoint) {
                reveals[i].classList.add('active');
            }
        }
    }
    
    window.addEventListener('scroll', reveal);
    reveal();
    
    // Particle effect on mouse move
    document.addEventListener('mousemove', (e) => {
        const particle = document.createElement('div');
        particle.className = 'particle';
        particle.style.left = e.clientX + 'px';
        particle.style.top = e.clientY + 'px';
        document.body.appendChild(particle);
        
        setTimeout(() => {
            particle.remove();
        }, 3000);
    });
    
    // Resize handler for canvas
    window.addEventListener('resize', () => {
        camera.aspect = window.innerWidth / window.innerHeight;
        camera.updateProjectionMatrix();
        renderer.setSize(window.innerWidth, window.innerHeight);
    });
</script>

</body>
</html>
