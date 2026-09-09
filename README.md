# Pimcheewa2547.github.io
Visual Reality and Augmented Reality By Pimcheewa Sansuk
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pimcheewa Sansuk (Raddish47) - 3D Portfolio</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Kanit', 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            overflow: hidden;
            background-color: #111e14;
            color: #ffffff;
        }

        #webgl-container {
            position: absolute;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            z-index: 1;
        }

        /* UI Overlay */
        .ui-overlay {
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
            padding: 2rem;
            background: radial-gradient(circle at center, transparent 40%, rgba(10, 25, 15, 0.6) 100%);
        }

        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            pointer-events: auto;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: 700;
            letter-spacing: 2px;
            color: #4ade80;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .logo-badge {
            background: rgba(74, 222, 128, 0.2);
            border: 1px solid #4ade80;
            padding: 2px 8px;
            border-radius: 12px;
            font-size: 0.8rem;
            color: #ffffff;
        }

        nav ul {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        nav a {
            color: #e2e8f0;
            text-decoration: none;
            font-size: 1rem;
            transition: all 0.3s ease;
            position: relative;
        }

        nav a:hover {
            color: #4ade80;
            text-shadow: 0 0 8px rgba(74, 222, 128, 0.6);
        }

        .hero-info {
            max-width: 500px;
            pointer-events: auto;
            background: rgba(15, 30, 20, 0.65);
            backdrop-filter: blur(12px);
            padding: 2.5rem;
            border-radius: 24px;
            border: 1px solid rgba(74, 222, 128, 0.3);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.4);
            animation: fadeInUp 1s ease-out;
        }

        .tagline {
            color: #4ade80;
            font-size: 0.95rem;
            font-weight: 600;
            letter-spacing: 3px;
            text-transform: uppercase;
            margin-bottom: 0.5rem;
        }

        h1 {
            font-size: 2.8rem;
            line-height: 1.2;
            margin-bottom: 0.5rem;
            background: linear-gradient(135deg, #ffffff 40%, #c1f2d0 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .pen-name {
            font-size: 1.4rem;
            color: #a7f3d0;
            margin-bottom: 1.2rem;
            font-weight: 300;
        }

        .description {
            color: #cbd5e1;
            font-size: 1rem;
            line-height: 1.6;
            margin-bottom: 2rem;
        }

        .cta-buttons {
            display: flex;
            gap: 1rem;
        }

        .btn {
            padding: 0.8rem 1.8rem;
            border-radius: 30px;
            font-size: 0.95rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
        }

        .btn-primary {
            background: linear-gradient(135deg, #4ade80 0%, #22c55e 100%);
            color: #052e16;
            border: none;
            box-shadow: 0 4px 15px rgba(74, 222, 128, 0.4);
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(74, 222, 128, 0.6);
        }

        .btn-secondary {
            background: transparent;
            color: #ffffff;
            border: 1px solid rgba(255, 255, 255, 0.3);
        }

        .btn-secondary:hover {
            background: rgba(255, 255, 255, 0.1);
            border-color: #ffffff;
        }

        footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 0.85rem;
            color: #94a3b8;
            pointer-events: auto;
        }

        .hint {
            display: flex;
            align-items: center;
            gap: 8px;
            color: #a7f3d0;
            font-size: 0.85rem;
        }

        .hint-icon {
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); opacity: 0.8; }
            50% { transform: scale(1.2); opacity: 1; }
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

        @media (max-width: 768px) {
            .ui-overlay { padding: 1.2rem; }
            h1 { font-size: 2.2rem; }
            .hero-info { padding: 1.5rem; }
            nav ul { display: none; }
        }
    </style>
    <!-- Import Google Font -->
    <link href="https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;600;700&display=swap" rel="stylesheet">
    <!-- Import Three.js & OrbitControls -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/three@0.128.0/examples/js/controls/OrbitControls.js"></script>
</head>
<body>

    <div id="webgl-container"></div>

    <div class="ui-overlay">
        <header>
            <div class="logo">
                🌱 RADDISH47
                <span class="logo-badge">3D Portfolio</span>
            </div>
            <nav>
                <ul>
                    <li><a href="#about">About</a></li>
                    <li><a href="#works">Works</a></li>
                    <li><a href="#contact">Contact</a></li>
                </ul>
            </nav>
        </header>

        <main>
            <div class="hero-info">
                <div class="tagline">Creative Digital Creator</div>
                <h1>Pimcheewa Sansuk</h1>
                <div class="pen-name">นามปากกา: <strong>Raddish47</strong>  radish</div>
                <p class="description">
                    ยินดีต้อนรับสู่พื้นที่สร้างสรรค์ผลงาน 3D & Digital Content ของหัวไชเท้า
                </p>
                <div class="cta-buttons">
                    <a href="#works" class="btn btn-primary">ชมผลงาน</a>
                    <a href="#contact" class="btn btn-secondary">ติดต่อ</a>
                </div>
            </div>
        </main>

        <footer>
            <div>© 2026 Pimcheewa Sansuk. All rights reserved.</div>
            <div class="hint">
                <span class="hint-icon">🖱️</span> หมุนลากและสโครลเพื่อสำรวจโลก 3D
            </div>
        </footer>
    </div>

    <script>
        // --- THREE.JS SCENE SETUP ---
        const container = document.getElementById('webgl-container');
        
        const scene = new THREE.Scene();
        scene.background = new THREE.Color(0x111e14);
        scene.fog = new THREE.FogExp2(0x111e14, 0.035);

        const camera = new THREE.PerspectiveCamera(45, window.innerWidth / window.innerHeight, 0.1, 1000);
        camera.position.set(0, 4, 11);

        const renderer = new THREE.WebGLRenderer({ antialias: true });
        renderer.setSize(window.innerWidth, window.innerHeight);
        renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
        renderer.shadowMap.enabled = true;
        renderer.shadowMap.type = THREE.PCFSoftShadowMap;
        renderer.toneMapping = THREE.ACESFilmicToneMapping;
        renderer.toneMappingExposure = 1.1;
        container.appendChild(renderer.domElement);

        const controls = new THREE.OrbitControls(camera, renderer.domElement);
        controls.enableDamping = true;
        controls.dampingFactor = 0.05;
        controls.maxPolarAngle = Math.PI / 2 - 0.02; // ไม่ให้มุมกล้องลงใต้ดิน
        controls.minDistance = 5;
        controls.maxDistance = 18;

        // --- LIGHTS ---
        const ambientLight = new THREE.AmbientLight(0xdcfce7, 0.7);
        scene.add(ambientLight);

        const sunLight = new THREE.DirectionalLight(0xffffff, 1.2);
        sunLight.position.set(8, 15, 8);
        sunLight.castShadow = true;
        sunLight.shadow.mapSize.width = 2048;
        sunLight.shadow.mapSize.height = 2048;
        sunLight.shadow.camera.near = 0.5;
        sunLight.shadow.camera.far = 30;
        sunLight.shadow.camera.left = -8;
        sunLight.shadow.camera.right = 8;
        sunLight.shadow.camera.top = 8;
        sunLight.shadow.camera.bottom = -8;
        scene.add(sunLight);

        // Green Rim Light
        const rimLight = new THREE.DirectionalLight(0x4ade80, 0.8);
        rimLight.position.set(-8, 5, -5);
        scene.add(rimLight);

        // --- GREEN GROUND WITH HILLS ---
        const groundGroup = new THREE.Group();
        
        // Main Terrain
        const groundGeo = new THREE.PlaneGeometry(30, 30, 64, 64);
        const pos = groundGeo.attributes.position;
        for (let i = 0; i < pos.count; i++) {
            const vx = pos.getX(i);
            const vy = pos.getY(i);
            const zDist = Math.sqrt(vx * vx + vy * vy);
            // สร้างเนินดินโค้งมนนุ่มนวล
            const wave = Math.sin(vx * 0.3) * Math.cos(vy * 0.3) * 0.4 + Math.sin(zDist * 0.2) * 0.3;
            pos.setZ(i, wave);
        }
        groundGeo.computeVertexNormals();

        const groundMat = new THREE.MeshStandardMaterial({
            color: 0x225429,
            roughness: 0.8,
            metalness: 0.1,
            flatShading: true
        });

        const ground = new THREE.Mesh(groundGeo, groundMat);
        ground.rotation.x = -Math.PI / 2;
        ground.receiveShadow = true;
        groundGroup.add(ground);

        // Soil mound around Radish
        const moundGeo = new THREE.CylinderGeometry(1.8, 2.6, 0.6, 16);
        const moundMat = new THREE.MeshStandardMaterial({ color: 0x1c3d1e, roughness: 0.9 });
        const mound = new THREE.Mesh(moundGeo, moundMat);
        mound.position.set(0, 0.2, 0);
        mound.receiveShadow = true;
        groundGroup.add(mound);

        scene.add(groundGroup);

        // --- 3D RADISH MODEL (หัวไชเท้าโผล่พ้นดิน) ---
        const radishGroup = new THREE.Group();

        // 1. Radish Body (Gradient Material using Custom Shader or Procedural Colors)
        // สร้างทรงหัวไชเท้าทรงหยดน้ำ/เรียว
        const bodyGeo = new THREE.CylinderGeometry(1.2, 0.3, 3.2, 32, 16);
        
        // ดัดรูปทรง Cylinder ให้ป่องช่วงบน เรียวช่วงล่าง
        const bodyPos = bodyGeo.attributes.position;
        for(let i = 0; i < bodyPos.count; i++) {
            let y = bodyPos.getY(i); // range -1.6 to 1.6
            let factor = Math.sin((y + 1.6) / 3.2 * Math.PI);
            let radiusScale = 0.6 + factor * 0.6;
            bodyPos.setX(i, bodyPos.getX(i) * radiusScale);
            bodyPos.setZ(i, bodyPos.getZ(i) * radiusScale);
        }
        bodyGeo.computeVertexNormals();

        // สร้าง Canvas Texture Gradient สีเขียวอ่อน -> สีขาวนวล
        const canvas = document.createElement('canvas');
        canvas.width = 16;
        canvas.height = 256;
        const ctx = canvas.getContext('2d');
        const gradient = ctx.createLinearGradient(0, 0, 0, 256);
        gradient.addColorStop(0.0, '#4ade80'); // เขียวสดส่วนหัว
        gradient.addColorStop(0.25, '#a7f3d0'); // เขียวพาสเทล
        gradient.addColorStop(0.55, '#f8fafc'); // ขาวนวล
        gradient.addColorStop(1.0, '#e2e8f0'); // ขาวอมเทาช่วงปลาย
        ctx.fillStyle = gradient;
        ctx.fillRect(0, 0, 16, 256);

        const radishTexture = new THREE.CanvasTexture(canvas);
        const radishMat = new THREE.MeshStandardMaterial({
            map: radishTexture,
            roughness: 0.3,
            metalness: 0.05,
        });

        const radishBody = new THREE.Mesh(bodyGeo, radishMat);
        radishBody.position.y = 1.1; // ฝังไว้ในดินครึ่งหนึ่ง ให้ส่วนหัวโผล่พ้นดิน
        radishBody.castShadow = true;
        radishBody.receiveShadow = true;
        radishGroup.add(radishBody);

        // 2. Radish Leaves (ใบไม้ด้านบน)
        const createLeaf = (rotY, curveAngle, scale = 1) => {
            const leafGroup = new THREE.Group();
            
            // ก้านใบ
            const stemGeo = new THREE.CylinderGeometry(0.06, 0.12, 1.8, 8);
            const stemMat = new THREE.MeshStandardMaterial({ color: 0x22c55e, roughness: 0.5 });
            const stem = new THREE.Mesh(stemGeo, stemMat);
            stem.position.y = 0.9;
            stem.castShadow = true;
            leafGroup.add(stem);

            // ตัวใบ
            const leafShape = new THREE.Shape();
            leafShape.moveTo(0, 0);
            leafShape.quadraticCurveTo(0.6, 0.8, 0.5, 1.8);
            leafShape.quadraticCurveTo(0, 2.3, -0.5, 1.8);
            leafShape.quadraticCurveTo(-0.6, 0.8, 0, 0);

            const extrudeSettings = { depth: 0.03, bevelEnabled: true, bevelSegments: 3, steps: 1, bevelSize: 0.02, bevelThickness: 0.02 };
            const leafGeo = new THREE.ExtrudeGeometry(leafShape, extrudeSettings);
            const leafMat = new THREE.MeshStandardMaterial({ color: 0x15803d, roughness: 0.4, side: THREE.DoubleSide });
            const leafMesh = new THREE.Mesh(leafGeo, leafMat);
            leafMesh.position.set(0, 1.2, 0);
            leafMesh.rotation.x = -0.2;
            leafMesh.castShadow = true;
            leafGroup.add(leafMesh);

            leafGroup.scale.set(scale, scale, scale);
            leafGroup.rotation.y = rotY;
            leafGroup.rotation.z = curveAngle;
            leafGroup.position.y = 2.4; // วางไว้จุดยอดของหัวไชเท้า

            return leafGroup;
        };

        const leafCount = 7;
        for (let i = 0; i < leafCount; i++) {
            const angle = (i / leafCount) * Math.PI * 2;
            const tilt = 0.25 + Math.random() * 0.2;
            const size = 0.8 + Math.random() * 0.4;
            radishGroup.add(createLeaf(angle, tilt, size));
        }

        scene.add(radishGroup);

        // --- FALLING LEAVES PARTICLES (ใบไม้ร่วง) ---
        const leafParticleCount = 45;
        const leafParticles = [];

        // สร้าง Geometry ใบไม้ร่วงขนาดเล็ก
        const pLeafShape = new THREE.Shape();
        pLeafShape.moveTo(0, 0);
        pLeafShape.quadraticCurveTo(0.2, 0.3, 0.15, 0.6);
        pLeafShape.quadraticCurveTo(0, 0.8, -0.15, 0.6);
        pLeafShape.quadraticCurveTo(-0.2, 0.3, 0, 0);
        const pLeafGeo = new THREE.ShapeGeometry(pLeafShape);
        
        const leafColors = [0x4ade80, 0x22c55e, 0x86efac, 0x15803d];

        for (let i = 0; i < leafParticleCount; i++) {
            const pMat = new THREE.MeshStandardMaterial({
                color: leafColors[Math.floor(Math.random() * leafColors.length)],
                side: THREE.DoubleSide,
                roughness: 0.6
            });
            const pMesh = new THREE.Mesh(pLeafGeo, pMat);
            
            // สุ่มตำแหน่งเริ่มต้น
            pMesh.position.set(
                (Math.random() - 0.5) * 16,
                Math.random() * 10 + 2,
                (Math.random() - 0.5) * 16
            );

            pMesh.rotation.set(
                Math.random() * Math.PI,
                Math.random() * Math.PI,
                Math.random() * Math.PI
            );

            const scale = 0.4 + Math.random() * 0.5;
            pMesh.scale.set(scale, scale, scale);
            pMesh.castShadow = true;

            scene.add(pMesh);

            leafParticles.push({
                mesh: pMesh,
                speedY: 0.01 + Math.random() * 0.02,
                rotSpeedX: (Math.random() - 0.5) * 0.03,
                rotSpeedY: (Math.random() - 0.5) * 0.03,
                swaySpeed: 1 + Math.random() * 2,
                swayAmount: 0.01 + Math.random() * 0.015,
                initialX: pMesh.position.x
            });
        }

        // --- GLOWING DUST PARTICLES (ละอองไฟระยิบระยับ) ---
        const dustCount = 80;
        const dustGeo = new THREE.BufferGeometry();
        const dustPos = new Float32Array(dustCount * 3);

        for(let i = 0; i < dustCount * 3; i += 3) {
            dustPos[i] = (Math.random() - 0.5) * 15;
            dustPos[i+1] = Math.random() * 8;
            dustPos[i+2] = (Math.random() - 0.5) * 15;
        }

        dustGeo.setAttribute('position', new THREE.BufferAttribute(dustPos, 3));
        const dustMat = new THREE.PointsMaterial({
            color: 0xa7f3d0,
            size: 0.08,
            transparent: true,
            opacity: 0.7
        });
        const dustPoints = new THREE.Points(dustGeo, dustMat);
        scene.add(dustPoints);

        // --- ANIMATION LOOP ---
        let clock = new THREE.Clock();

        function animate() {
            requestAnimationFrame(animate);
            const elapsedTime = clock.getElapsedTime();

            // 1. หมุนหัวไชเท้าและใบไม้เบาๆ
            radishGroup.rotation.y = Math.sin(elapsedTime * 0.5) * 0.15;
            radishGroup.position.y = Math.sin(elapsedTime * 1.2) * 0.08;

            // 2. Animate ใบไม้ร่วง
            leafParticles.forEach(p => {
                p.mesh.position.y -= p.speedY;
                p.mesh.position.x = p.initialX + Math.sin(elapsedTime * p.swaySpeed) * 0.5;
                
                p.mesh.rotation.x += p.rotSpeedX;
                p.mesh.rotation.y += p.rotSpeedY;

                // เมื่อตกถึงพื้น ให้รีเซ็ตกลับไปด้านบน
                if (p.mesh.position.y < 0.2) {
                    p.mesh.position.y = 10 + Math.random() * 2;
                    p.mesh.position.x = (Math.random() - 0.5) * 16;
                    p.initialX = p.mesh.position.x;
                }
            });

            // 3. หมุนละอองฝุ่นเบาๆ
            dustPoints.rotation.y = elapsedTime * 0.03;

            controls.update();
            renderer.render(scene, camera);
        }

        animate();

        // --- RESIZE HANDLER ---
        window.addEventListener('resize', () => {
            camera.aspect = window.innerWidth / window.innerHeight;
            camera.updateProjectionMatrix();
            renderer.setSize(window.innerWidth, window.innerHeight);
        });
    </script>
</body>
</html>
