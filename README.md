# Pimcheewa2547.github.io
Visual Reality and Augmented Reality By Pimcheewa Sansuk

<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pimcheewa Sansuk (Raddish47) - 3D Portfolio</title>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;600;700&family=Outfit:wght@400;600;800&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-grad-1: #eef7ee;
            --bg-grad-2: #d4ebd4;
            --primary-green: #2e7d32;
            --light-green: #a5d6a7;
            --accent-green: #4caf50;
            --radish-white: #ffffff;
            --text-dark: #1b4332;
            --text-muted: #4a7c59;
            --glass-bg: rgba(255, 255, 255, 0.75);
            --glass-border: rgba(46, 125, 50, 0.15);
            --shadow-color: rgba(46, 125, 50, 0.12);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body, html {
            width: 100%;
            height: 100%;
            overflow: hidden;
            font-family: 'Outfit', 'Kanit', sans-serif;
            color: var(--text-dark);
            background: radial-gradient(circle at center, var(--bg-grad-1) 0%, var(--bg-grad-2) 100%);
        }

        #canvas-container {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
        }

        /* UI Layer */
        .ui-layer {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 2;
            pointer-events: none;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            padding: 2.5rem;
        }

        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            pointer-events: auto;
        }

        .logo {
            font-weight: 800;
            font-size: 1.5rem;
            color: var(--primary-green);
            letter-spacing: 1px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .logo span {
            background: var(--primary-green);
            color: var(--radish-white);
            padding: 2px 8px;
            border-radius: 6px;
            font-size: 0.9rem;
        }

        nav ul {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        nav a {
            text-decoration: none;
            color: var(--text-dark);
            font-weight: 600;
            transition: color 0.3s ease;
        }

        nav a:hover {
            color: var(--primary-green);
        }

        /* Hero Content Card */
        .hero-card {
            pointer-events: auto;
            max-width: 460px;
            background: var(--glass-bg);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid var(--glass-border);
            padding: 2.5rem;
            border-radius: 24px;
            box-shadow: 0 20px 40px var(--shadow-color);
            transform: translateY(0);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .hero-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 25px 50px rgba(46, 125, 50, 0.18);
        }

        .tag {
            display: inline-block;
            background: rgba(76, 175, 80, 0.15);
            color: var(--primary-green);
            padding: 6px 14px;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 600;
            margin-bottom: 1rem;
            border: 1px solid rgba(76, 175, 80, 0.3);
        }

        h1 {
            font-size: 2.5rem;
            line-height: 1.15;
            color: var(--text-dark);
            margin-bottom: 0.5rem;
            font-weight: 700;
        }

        .pen-name {
            font-size: 1.25rem;
            color: var(--primary-green);
            font-weight: 600;
            margin-bottom: 1.2rem;
        }

        p.bio {
            color: var(--text-muted);
            font-size: 0.95rem;
            line-height: 1.6;
            margin-bottom: 2rem;
        }

        .cta-buttons {
            display: flex;
            gap: 1rem;
        }

        .btn {
            padding: 0.8rem 1.6rem;
            border-radius: 12px;
            font-weight: 600;
            text-decoration: none;
            transition: all 0.3s ease;
            cursor: pointer;
            border: none;
            font-size: 0.95rem;
        }

        .btn-primary {
            background: var(--primary-green);
            color: var(--radish-white);
            box-shadow: 0 8px 16px rgba(46, 125, 50, 0.25);
        }

        .btn-primary:hover {
            background: #236327;
            box-shadow: 0 12px 20px rgba(46, 125, 50, 0.35);
        }

        .btn-secondary {
            background: transparent;
            color: var(--text-dark);
            border: 1px solid var(--glass-border);
        }

        .btn-secondary:hover {
            background: rgba(255, 255, 255, 0.8);
        }

        footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 0.85rem;
            color: var(--text-muted);
            pointer-events: auto;
        }

        .controls-hint {
            display: flex;
            align-items: center;
            gap: 8px;
            background: var(--glass-bg);
            padding: 6px 14px;
            border-radius: 20px;
            border: 1px solid var(--glass-border);
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .ui-layer {
                padding: 1.5rem;
            }
            .hero-card {
                max-width: 100%;
                padding: 1.8rem;
            }
            h1 {
                font-size: 2rem;
            }
            nav {
                display: none;
            }
        }
    </style>

    <!-- Three.js Library & OrbitControls -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/three@0.128.0/examples/js/controls/OrbitControls.js"></script>
</head>
<body>

    <div id="canvas-container"></div>

    <div class="ui-layer">
        <header>
            <div class="logo">
                🌱 <span>RADDISH47</span>
            </div>
            <nav>
                <ul>
                    <li><a href="#about">About</a></li>
                    <li><a href="#projects">Works</a></li>
                    <li><a href="#contact">Contact</a></li>
                </ul>
            </nav>
        </header>

        <div class="hero-card">
            <span class="tag">✨ 3D Portfolio & Interactive Experience</span>
            <h1>Pimcheewa Sansuk</h1>
            <div class="pen-name">นามปากกา: Raddish47 🍃</div>
            <p class="bio">
                ยินดีต้อนรับสู่พื้นที่สร้างสรรค์ของหัวไชเท้า Introvert ติดดิน Interactive
            </p>
            <div class="cta-buttons">
                <a href="#projects" class="btn btn-primary">ดูผลงาน</a>
                <a href="#contact" class="btn btn-secondary">ติดต่อ</a>
            </div>
        </div>

        <footer>
            <div class="controls-hint">
                🖱️ คลิกค้างและลากเพื่อหมุนมุมมอง 3D
            </div>
            <div>© 2026 Pimcheewa Sansuk. All rights reserved.</div>
        </footer>
    </div>

    <script>
        // ----------------------------------------------------
        // 1. SETUP SCENE, CAMERA, RENDERER
        // ----------------------------------------------------
        const container = document.getElementById('canvas-container');
        const scene = new THREE.Scene();
        
        // Soft Fog for Radish Fresh Atmosphere
        scene.fog = new THREE.FogExp2(0xeef7ee, 0.035);

        const camera = new THREE.PerspectiveCamera(60, window.innerWidth / window.innerHeight, 0.1, 1000);
        camera.position.set(0, 1.5, 6);

        const renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
        renderer.setSize(window.innerWidth, window.innerHeight);
        renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
        renderer.shadowMap.enabled = true;
        renderer.shadowMap.type = THREE.PCFSoftShadowMap;
        container.appendChild(renderer.domElement);

        const controls = new THREE.OrbitControls(camera, renderer.domElement);
        controls.enableDamping = true;
        controls.dampingFactor = 0.05;
        controls.maxPolarAngle = Math.PI / 2 + 0.1;
        controls.minDistance = 3;
        controls.maxDistance = 10;

        // ----------------------------------------------------
        // 2. LIGHTING SETUP
        // ----------------------------------------------------
        const ambientLight = new THREE.AmbientLight(0xffffff, 0.7);
        scene.add(ambientLight);

        const dirLight = new THREE.DirectionalLight(0xffffff, 0.8);
        dirLight.position.set(5, 10, 7);
        dirLight.castShadow = true;
        dirLight.shadow.mapSize.width = 1024;
        dirLight.shadow.mapSize.height = 1024;
        scene.add(dirLight);

        const pointLight = new THREE.PointLight(0xa5d6a7, 1, 10);
        pointLight.position.set(-2, 3, 2);
        scene.add(pointLight);

        // ----------------------------------------------------
        // 3. CREATE 3D RADISH (หัวไชเท้า)
        // ----------------------------------------------------
        const radishGroup = new THREE.Group();

        // Material for Radish Root (White Smooth)
        const rootMaterial = new THREE.MeshStandardMaterial({
            color: 0xfcfcfc,
            roughness: 0.3,
            metalness: 0.1
        });

        // Material for Radish Top Gradient (Light Green)
        const topMaterial = new THREE.MeshStandardMaterial({
            color: 0x81c784,
            roughness: 0.4,
            metalness: 0.1
        });

        // Material for Leaves (Vibrant Green)
        const leafMaterial = new THREE.MeshStandardMaterial({
            color: 0x2e7d32,
            roughness: 0.5,
            side: THREE.DoubleSide
        });

        // Radish Main Body (Cylinder + Cone)
        const bodyGeo = new THREE.CylinderGeometry(0.7, 0.1, 2.2, 32);
        const radishBody = new THREE.Mesh(bodyGeo, rootMaterial);
        radishBody.position.y = 0;
        radishBody.castShadow = true;
        radishGroup.add(radishBody);

        // Radish Top Crown (Green Tint)
        const crownGeo = new THREE.CylinderGeometry(0.71, 0.68, 0.4, 32);
        const radishCrown = new THREE.Mesh(crownGeo, topMaterial);
        radishCrown.position.y = 0.9;
        radishGroup.add(radishCrown);

        // Radish Bottom Tip
        const tipGeo = new THREE.ConeGeometry(0.12, 0.8, 32);
        const radishTip = new THREE.Mesh(tipGeo, rootMaterial);
        radishTip.position.y = -1.4;
        radishGroup.add(radishTip);

        // Radish Leaves (สร้างใบไม้ด้านบนหัวไชเท้า)
        const leafCount = 7;
        for (let i = 0; i < leafCount; i++) {
            const leafShape = new THREE.Shape();
            leafShape.moveTo(0, 0);
            leafShape.quadraticCurveTo(0.3, 0.8, 0.1, 1.6);
            leafShape.quadraticCurveTo(0, 2.0, -0.1, 1.6);
            leafShape.quadraticCurveTo(-0.3, 0.8, 0, 0);

            const leafGeo = new THREE.ShapeGeometry(leafShape);
            const leaf = new THREE.Mesh(leafGeo, leafMaterial);
            
            leaf.position.y = 1.0;
            const angle = (i / leafCount) * Math.PI * 2;
            leaf.rotation.y = angle;
            leaf.rotation.x = 0.3 + Math.random() * 0.2;
            leaf.rotation.z = -0.1 + Math.random() * 0.2;
            leaf.scale.set(0.8, 0.9 + Math.random() * 0.3, 0.8);
            leaf.castShadow = true;

            radishGroup.add(leaf);
        }

        // Adjust initial position of Radish Group
        radishGroup.position.set(1.8, 0.2, 0);
        scene.add(radishGroup);

        // ----------------------------------------------------
        // 4. FALLING LEAVES SYSTEM (ระบบใบไม้ร่วง)
        // ----------------------------------------------------
        const fallingLeafCount = 45;
        const fallingLeaves = [];

        // Create Leaf Geometry
        const fallingLeafGeo = new THREE.PlaneGeometry(0.18, 0.35);

        for (let i = 0; i < fallingLeafCount; i++) {
            const leafMat = new THREE.MeshStandardMaterial({
                color: Math.random() > 0.3 ? 0x4caf50 : 0x81c784,
                side: THREE.DoubleSide,
                transparent: true,
                opacity: 0.85
            });

            const leaf = new THREE.Mesh(fallingLeafGeo, leafMat);

            // Random initial positions
            leaf.position.x = (Math.random() - 0.5) * 14;
            leaf.position.y = Math.random() * 8 + 2;
            leaf.position.z = (Math.random() - 0.5) * 10;

            // Random initial rotations
            leaf.rotation.x = Math.random() * Math.PI;
            leaf.rotation.y = Math.random() * Math.PI;
            leaf.rotation.z = Math.random() * Math.PI;

            // Custom speeds & oscillation params stored in userData
            leaf.userData = {
                fallSpeed: 0.008 + Math.random() * 0.012,
                rotSpeedX: (Math.random() - 0.5) * 0.03,
                rotSpeedY: (Math.random() - 0.5) * 0.03,
                rotSpeedZ: (Math.random() - 0.5) * 0.03,
                oscillationOffset: Math.random() * Math.PI * 2,
                oscillationSpeed: 1 + Math.random() * 2
            };

            scene.add(leaf);
            fallingLeaves.push(leaf);
        }

        // ----------------------------------------------------
        // 5. ANIMATION LOOP & INTERACTION
        // ----------------------------------------------------
        let clock = new THREE.Clock();

        function animate() {
            requestAnimationFrame(animate);
            const elapsedTime = clock.getElapsedTime();

            // Rotate Radish floating gently
            radishGroup.rotation.y = elapsedTime * 0.4;
            radishGroup.position.y = 0.2 + Math.sin(elapsedTime * 1.5) * 0.15;

            // Animate Falling Leaves
            fallingLeaves.forEach(leaf => {
                const data = leaf.userData;
                
                // Falling down
                leaf.position.y -= data.fallSpeed;
                
                // Gentle sway side-to-side
                leaf.position.x += Math.sin(elapsedTime * data.oscillationSpeed + data.oscillationOffset) * 0.005;
                leaf.position.z += Math.cos(elapsedTime * data.oscillationSpeed + data.oscillationOffset) * 0.003;

                // Rotation while falling
                leaf.rotation.x += data.rotSpeedX;
                leaf.rotation.y += data.rotSpeedY;
                leaf.rotation.z += data.rotSpeedZ;

                // Reset position when hitting bottom
                if (leaf.position.y < -3) {
                    leaf.position.y = 7 + Math.random() * 2;
                    leaf.position.x = (Math.random() - 0.5) * 14;
                    leaf.position.z = (Math.random() - 0.5) * 10;
                }
            });

            controls.update();
            renderer.render(scene, camera);
        }

        animate();

        // ----------------------------------------------------
        // 6. RESIZE HANDLING
        // ----------------------------------------------------
        window.addEventListener('resize', () => {
            camera.aspect = window.innerWidth / window.innerHeight;
            camera.updateProjectionMatrix();
            renderer.setSize(window.innerWidth, window.innerHeight);

            // Responsive layout adjustments for 3D elements
            if (window.innerWidth < 768) {
                radishGroup.position.set(0, -0.5, -1);
            } else {
                radishGroup.position.set(1.8, 0.2, 0);
            }
        });

        // Trigger resize check once at load
        if (window.innerWidth < 768) {
            radishGroup.position.set(0, -0.5, -1);
        }
    </script>
</body>
</html>
