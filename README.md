<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SMART AQUA CART | 3D Premium Experience</title>
    <!-- Three.js CDN for 3D Hero Effect -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <style>
        :root {
            --primary: #0ea5e9;
            --dark: #0f172a;
            --glass: rgba(255, 255, 255, 0.1);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Segoe UI', sans-serif; }
        
        body { background: var(--dark); color: white; overflow-x: hidden; }

        /* --- 3D HERO SECTION --- */
        #hero-canvas { position: absolute; top: 0; left: 0; z-index: -1; width: 100%; height: 100vh; }
        .hero { height: 80vh; display: flex; align-items: center; justify-content: center; text-align: center; position: relative; }
        .hero-content { background: rgba(0,0,0,0.4); backdrop-filter: blur(10px); padding: 2rem; border-radius: 20px; border: 1px solid rgba(255,255,255,0.1); }

        /* --- 3D PRODUCT CARDS --- */
        .product-grid { 
            display: grid; 
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); 
            gap: 2rem; 
            padding: 2rem; 
            perspective: 1000px; /* Essential for 3D effect */
        }

        .product-card {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 1.5rem;
            border: 1px solid rgba(255,255,255,0.1);
            transition: all 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            transform-style: preserve-3d;
            cursor: pointer;
        }

        .product-card:hover {
            transform: translateY(-10px) rotateY(10deg);
            box-shadow: 0 20px 30px rgba(0,0,0,0.5);
            border-color: var(--primary);
        }

        .product-card img { width: 100%; height: 200px; object-fit: cover; border-radius: 15px; }

        /* --- UI ELEMENTS --- */
        .btn-add { background: var(--primary); color: white; border: none; padding: 10px 20px; border-radius: 10px; cursor: pointer; margin-top: 10px; }
        .btn-add:hover { background: #0284c7; }

    </style>
</head>
<body>

    <!-- 3D Background Canvas -->
    <canvas id="hero-canvas"></canvas>

    <header class="hero">
        <div class="hero-content">
            <h1>SMART AQUA CART</h1>
            <p>PREMIUM QUALITY FISHES AND ACCESSORIES</p>
        </div>
    </header>

    <main>
        <div class="product-grid" id="productGrid">
            <!-- Product Card Example -->
            <div class="product-card">
                <img src="https://i.ibb.co/4ZxR9JpS/1782745859148.webp" alt="Filter">
                <h3>Bluepet Powerfilter</h3>
                <p>₹320</p>
                <button class="btn-add">Add to Cart</button>
            </div>
        </div>
    </main>

    <script>
        // --- 3D ANIMATED BACKGROUND (THREE.JS) ---
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth/window.innerHeight, 0.1, 1000);
        const renderer = new THREE.WebGLRenderer({ canvas: document.getElementById('hero-canvas'), alpha: true });
        renderer.setSize(window.innerWidth, window.innerHeight);

        const geometry = new THREE.TorusKnotGeometry(10, 3, 100, 16);
        const material = new THREE.MeshBasicMaterial({ color: 0x0ea5e9, wireframe: true, transparent: true, opacity: 0.2 });
        const torus = new THREE.Mesh(geometry, material);
        scene.add(torus);

        camera.position.z = 30;

        function animate() {
            requestAnimationFrame(animate);
            torus.rotation.x += 0.01;
            torus.rotation.y += 0.005;
            renderer.render(scene, camera);
        }
        animate();

        // Responsive Resizing
        window.addEventListener('resize', () => {
            renderer.setSize(window.innerWidth, window.innerHeight);
            camera.aspect = window.innerWidth / window.innerHeight;
            camera.updateProjectionMatrix();
        });
    </script>
</body>
</html># Smartaquacart-final
