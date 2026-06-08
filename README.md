<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Royal Ceylon – Sri Lanka Spice House | Premium Ceylon Spices</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;500;600;700&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet">
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        gold: '#D4AF37',
                        'dark-gold': '#8B6B1B',
                        cream: '#F5F2E8',
                        'royal-black': '#0A0A0A',
                        'soft-black': '#1A1A1A',
                    },
                    fontFamily: {
                        serif: ['Playfair Display', 'serif'],
                        sans: ['Inter', 'sans-serif'],
                    }
                }
            }
        }
    </script>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        
        body {
            font-family: 'Inter', sans-serif;
            background-color: #0A0A0A;
            color: #F5F2E8;
            overflow-x: hidden;
        }

        .font-serif { font-family: 'Playfair Display', serif; }

        /* Custom Scrollbar */
        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: #0A0A0A; }
        ::-webkit-scrollbar-thumb { background: #D4AF37; border-radius: 4px; }
        ::-webkit-scrollbar-thumb:hover { background: #8B6B1B; }

        /* Gold Gradient Text */
        .text-gold-gradient {
            background: linear-gradient(135deg, #D4AF37 0%, #F4E4BC 50%, #D4AF37 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        /* Shimmer Animation */
        @keyframes shimmer {
            0% { background-position: -200% center; }
            100% { background-position: 200% center; }
        }
        .shimmer {
            background: linear-gradient(90deg, transparent, rgba(212, 175, 55, 0.1), transparent);
            background-size: 200% 100%;
            animation: shimmer 3s infinite;
        }

        /* Floating Animation */
        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(5deg); }
        }
        .floating { animation: float 6s ease-in-out infinite; }
        .floating-delay-1 { animation-delay: 1s; }
        .floating-delay-2 { animation-delay: 2s; }
        .floating-delay-3 { animation-delay: 3s; }

        /* Glow Effect */
        .gold-glow {
            box-shadow: 0 0 20px rgba(212, 175, 55, 0.3), 0 0 40px rgba(212, 175, 55, 0.1);
        }
        .gold-glow:hover {
            box-shadow: 0 0 30px rgba(212, 175, 55, 0.5), 0 0 60px rgba(212, 175, 55, 0.2);
        }

        /* Navigation */
        .nav-glass {
            background: rgba(10, 10, 10, 0.8);
            backdrop-filter: blur(20px);
            border-bottom: 1px solid rgba(212, 175, 55, 0.1);
        }

        /* Hero Parallax */
        .hero-bg {
            background: linear-gradient(to bottom, rgba(10,10,10,0.3), rgba(10,10,10,0.9)), 
                        url('https://images.unsplash.com/photo-1564890369478-c89ca6d9cde9?ixlib=rb-4.0.3&auto=format&fit=crop&w=2000&q=80');
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
        }

        /* Product Card Hover */
        .product-card {
            transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
        }
        .product-card:hover {
            transform: translateY(-10px);
        }
        .product-card .overlay {
            opacity: 0;
            transition: all 0.4s ease;
        }
        .product-card:hover .overlay {
            opacity: 1;
        }

        /* Spice Particle Canvas */
        #spiceCanvas {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 2;
        }

        /* Custom Button */
        .btn-gold {
            background: linear-gradient(135deg, #D4AF37, #8B6B1B);
            position: relative;
            overflow: hidden;
            transition: all 0.3s ease;
        }
        .btn-gold::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            transition: left 0.5s;
        }
        .btn-gold:hover::before {
            left: 100%;
        }
        .btn-gold:hover {
            transform: scale(1.05);
            box-shadow: 0 10px 30px rgba(212, 175, 55, 0.4);
        }

        /* Form Input */
        .input-luxury {
            background: rgba(26, 26, 26, 0.8);
            border: 1px solid rgba(212, 175, 55, 0.2);
            transition: all 0.3s ease;
        }
        .input-luxury:focus {
            border-color: #D4AF37;
            box-shadow: 0 0 15px rgba(212, 175, 55, 0.2);
            outline: none;
        }

        /* Testimonial Card */
        .testimonial-card {
            background: linear-gradient(135deg, rgba(26,26,26,0.9), rgba(10,10,10,0.9));
            border: 1px solid rgba(212, 175, 55, 0.1);
        }

        /* Shipping Badge */
        .shipping-badge {
            background: linear-gradient(135deg, rgba(212,175,55,0.1), rgba(139,107,27,0.1));
            border: 1px solid rgba(212, 175, 55, 0.2);
        }

        /* Loader */
        .loader {
            border: 3px solid rgba(212, 175, 55, 0.1);
            border-top: 3px solid #D4AF37;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            animation: spin 1s linear infinite;
        }
        @keyframes spin { 0% { transform: rotate(0deg); } 100% { transform: rotate(360deg); } }

        /* Mobile Menu */
        .mobile-menu {
            transform: translateX(100%);
            transition: transform 0.3s ease;
        }
        .mobile-menu.active {
            transform: translateX(0);
        }

        /* Reveal Animation Classes */
        .reveal {
            opacity: 0;
            transform: translateY(30px);
        }
    </style>
</head>
<body class="antialiased">

    <!-- Navigation -->
    <nav id="navbar" class="fixed w-full z-50 transition-all duration-300 py-4">
        <div class="max-w-7xl mx-auto px-6 flex justify-between items-center">
            <a href="#home" class="flex items-center gap-3 group">
                <div class="w-10 h-10 rounded-full bg-gradient-to-br from-gold to-dark-gold flex items-center justify-center text-royal-black font-bold text-lg group-hover:scale-110 transition-transform">R</div>
                <div class="flex flex-col">
                    <span class="font-serif text-xl font-bold text-gold-gradient tracking-wide">ROYAL CEYLON</span>
                    <span class="text-xs text-gold/60 tracking-[0.3em] uppercase">Sri Lanka Spice House</span>
                </div>
            </a>
            
            <div class="hidden md:flex items-center gap-8">
                <a href="#home" class="text-cream/80 hover:text-gold transition-colors text-sm tracking-widest uppercase">Home</a>
                <a href="#about" class="text-cream/80 hover:text-gold transition-colors text-sm tracking-widest uppercase">About</a>
                <a href="#products" class="text-cream/80 hover:text-gold transition-colors text-sm tracking-widest uppercase">Products</a>
                <a href="#shipping" class="text-cream/80 hover:text-gold transition-colors text-sm tracking-widest uppercase">Shipping</a>
                <a href="#testimonials" class="text-cream/80 hover:text-gold transition-colors text-sm tracking-widest uppercase">Reviews</a>
                <a href="#contact" class="text-cream/80 hover:text-gold transition-colors text-sm tracking-widest uppercase">Contact</a>
                <button onclick="toggleCart()" class="relative p-2 hover:text-gold transition-colors">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M16 11V7a4 4 0 00-8 0v4M5 9h14l1 12H4L5 9z"></path></svg>
                    <span id="cartCount" class="absolute -top-1 -right-1 bg-gold text-royal-black text-xs font-bold w-5 h-5 rounded-full flex items-center justify-center hidden">0</span>
                </button>
            </div>

            <button onclick="toggleMobileMenu()" class="md:hidden text-gold">
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path></svg>
            </button>
        </div>
    </nav>

    <!-- Mobile Menu -->
    <div id="mobileMenu" class="mobile-menu fixed inset-0 bg-royal-black/98 z-40 flex flex-col items-center justify-center gap-8 md:hidden">
        <button onclick="toggleMobileMenu()" class="absolute top-6 right-6 text-gold">
            <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path></svg>
        </button>
        <a href="#home" onclick="toggleMobileMenu()" class="font-serif text-2xl text-cream hover:text-gold transition-colors">Home</a>
        <a href="#about" onclick="toggleMobileMenu()" class="font-serif text-2xl text-cream hover:text-gold transition-colors">About</a>
        <a href="#products" onclick="toggleMobileMenu()" class="font-serif text-2xl text-cream hover:text-gold transition-colors">Products</a>
        <a href="#shipping" onclick="toggleMobileMenu()" class="font-serif text-2xl text-cream hover:text-gold transition-colors">Shipping</a>
        <a href="#testimonials" onclick="toggleMobileMenu()" class="font-serif text-2xl text-cream hover:text-gold transition-colors">Reviews</a>
        <a href="#contact" onclick="toggleMobileMenu()" class="font-serif text-2xl text-cream hover:text-gold transition-colors">Contact</a>
    </div>

    <!-- Hero Section -->
    <section id="home" class="relative min-h-screen flex items-center justify-center overflow-hidden hero-bg">
        <canvas id="spiceCanvas"></canvas>
        
        <div class="absolute inset-0 bg-gradient-to-b from-royal-black/40 via-transparent to-royal-black z-1"></div>
        
        <!-- Floating Spice Elements -->
        <div class="absolute top-20 left-10 w-24 h-24 opacity-20 floating hidden md:block">
            <img src="https://images.unsplash.com/photo-1596040033229-a9821ebd058d?w=200&auto=format&fit=crop&q=60" class="w-full h-full object-cover rounded-full border-2 border-gold/30" alt="Cinnamon">
        </div>
        <div class="absolute top-40 right-20 w-20 h-20 opacity-20 floating floating-delay-1 hidden md:block">
            <img src="https://images.unsplash.com/photo-1615485290382-441e4d049cb5?w=200&auto=format&fit=crop&q=60" class="w-full h-full object-cover rounded-full border-2 border-gold/30" alt="Cardamom">
        </div>
        <div class="absolute bottom-40 left-1/4 w-16 h-16 opacity-20 floating floating-delay-2 hidden md:block">
            <img src="https://images.unsplash.com/photo-1599909533681-7c9e0bf50e3c?w=200&auto=format&fit=crop&q=60" class="w-full h-full object-cover rounded-full border-2 border-gold/30" alt="Pepper">
        </div>

        <div class="relative z-10 text-center px-6 max-w-5xl mx-auto">
            <div class="mb-6 inline-block">
                <span class="text-gold/80 text-sm tracking-[0.5em] uppercase border-b border-gold/30 pb-2">Est. Sri Lanka</span>
            </div>
            <h1 class="font-serif text-5xl md:text-7xl lg:text-8xl font-bold mb-6 leading-tight">
                <span class="block text-cream">Premium</span>
                <span class="block text-gold-gradient mt-2">Ceylon Spices</span>
            </h1>
            <p class="text-xl md:text-2xl text-cream/80 mb-4 font-light tracking-wide">From The Heart Of Sri Lanka</p>
            <div class="flex flex-wrap justify-center gap-4 text-gold/60 text-sm tracking-widest uppercase mb-12">
                <span class="flex items-center gap-2"><span class="w-1.5 h-1.5 bg-gold rounded-full"></span>Handpicked</span>
                <span class="flex items-center gap-2"><span class="w-1.5 h-1.5 bg-gold rounded-full"></span>Pure</span>
                <span class="flex items-center gap-2"><span class="w-1.5 h-1.5 bg-gold rounded-full"></span>Authentic</span>
                <span class="flex items-center gap-2"><span class="w-1.5 h-1.5 bg-gold rounded-full"></span>Export Quality</span>
            </div>
            <div class="flex flex-col sm:flex-row gap-4 justify-center">
                <a href="#products" class="btn-gold px-10 py-4 rounded-full text-royal-black font-semibold tracking-wider uppercase text-sm">Shop Now</a>
                <a href="#contact" class="border border-gold/50 text-gold px-10 py-4 rounded-full hover:bg-gold/10 transition-all tracking-wider uppercase text-sm">Contact Us</a>
            </div>
        </div>

        <div class="absolute bottom-10 left-1/2 transform -translate-x-1/2 animate-bounce">
            <svg class="w-6 h-6 text-gold/50" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"></path></svg>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" class="py-24 relative overflow-hidden">
        <div class="absolute inset-0 opacity-5">
            <div class="absolute top-0 left-0 w-full h-full bg-[radial-gradient(circle_at_50%_50%,_#D4AF37_1px,_transparent_1px)] bg-[length:40px_40px]"></div>
        </div>
        
        <div class="max-w-7xl mx-auto px-6">
            <div class="grid md:grid-cols-2 gap-16 items-center">
                <div class="reveal">
                    <span class="text-gold text-sm tracking-[0.3em] uppercase mb-4 block">Our Story</span>
                    <h2 class="font-serif text-4xl md:text-5xl font-bold text-cream mb-6">Royal Ceylon<br><span class="text-gold-gradient">Sri Lanka Spice House</span></h2>
                    <p class="text-cream/70 leading-relaxed mb-6 text-lg">
                        Dedicated to bringing the finest authentic Sri Lankan spices to customers worldwide. Our spices are handpicked from trusted local farmers and carefully processed to preserve their natural aroma, flavor, and purity.
                    </p>
                    <p class="text-cream/50 leading-relaxed mb-8">
                        Each batch undergoes rigorous quality control to ensure you receive only the most premium export-grade spices that Sri Lanka has to offer.
                    </p>
                    
                    <div class="grid grid-cols-2 gap-4">
                        <div class="flex items-start gap-3">
                            <div class="w-8 h-8 rounded-full bg-gold/10 flex items-center justify-center flex-shrink-0 mt-1">
                                <svg class="w-4 h-4 text-gold" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path></svg>
                            </div>
                            <div>
                                <h4 class="text-cream font-semibold">100% Pure & Natural</h4>
                                <p class="text-cream/50 text-sm">No additives or preservatives</p>
                            </div>
                        </div>
                        <div class="flex items-start gap-3">
                            <div class="w-8 h-8 rounded-full bg-gold/10 flex items-center justify-center flex-shrink-0 mt-1">
                                <svg class="w-4 h-4 text-gold" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path></svg>
                            </div>
                            <div>
                                <h4 class="text-cream font-semibold">Handpicked in Sri Lanka</h4>
                                <p class="text-cream/50 text-sm">Direct from local farmers</p>
                            </div>
                        </div>
                        <div class="flex items-start gap-3">
                            <div class="w-8 h-8 rounded-full bg-gold/10 flex items-center justify-center flex-shrink-0 mt-1">
                                <svg class="w-4 h-4 text-gold" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path></svg>
                            </div>
                            <div>
                                <h4 class="text-cream font-semibold">No Artificial Additives</h4>
                                <p class="text-cream/50 text-sm">Completely organic process</p>
                            </div>
                        </div>
                        <div class="flex items-start gap-3">
                            <div class="w-8 h-8 rounded-full bg-gold/10 flex items-center justify-center flex-shrink-0 mt-1">
                                <svg class="w-4 h-4 text-gold" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path></svg>
                            </div>
                            <div>
                                <h4 class="text-cream font-semibold">Sustainably Sourced</h4>
                                <p class="text-cream/50 text-sm">Eco-friendly practices</p>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="relative reveal">
                    <div class="absolute -inset-4 bg-gradient-to-r from-gold/20 to-dark-gold/20 rounded-2xl blur-2xl"></div>
                    <div class="relative rounded-2xl overflow-hidden border border-gold/20">
                        <img src="https://images.unsplash.com/photo-1596040033229-a9821ebd058d?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="Ceylon Cinnamon" class="w-full h-[500px] object-cover hover:scale-105 transition-transform duration-700">
                        <div class="absolute bottom-0 left-0 right-0 bg-gradient-to-t from-royal-black to-transparent p-8">
                            <p class="font-serif text-2xl text-gold">Ceylon True Cinnamon</p>
                            <p class="text-cream/60 text-sm">The world's finest variety</p>
                        </div>
                    </div>
                    <div class="absolute -bottom-6 -right-6 w-32 h-32 bg-gold/10 rounded-full blur-xl"></div>
                </div>
            </div>
        </div>
    </section>

    <!-- Products Section -->
    <section id="products" class="py-24 bg-soft-black/50">
        <div class="max-w-7xl mx-auto px-6">
            <div class="text-center mb-16 reveal">
                <span class="text-gold text-sm tracking-[0.3em] uppercase mb-4 block">Our Collection</span>
                <h2 class="font-serif text-4xl md:text-5xl font-bold text-cream mb-4">Premium Spice Collection</h2>
                <p class="text-cream/60 max-w-2xl mx-auto">Discover the authentic flavors of Sri Lanka, carefully curated and packaged for your culinary excellence.</p>
            </div>

            <!-- Category Filter -->
            <div class="flex flex-wrap justify-center gap-3 mb-12 reveal">
                <button onclick="filterProducts('all')" class="filter-btn active px-6 py-2 rounded-full border border-gold/30 text-gold hover:bg-gold hover:text-royal-black transition-all text-sm tracking-wider" data-filter="all">All</button>
                <button onclick="filterProducts('cinnamon')" class="filter-btn px-6 py-2 rounded-full border border-gold/30 text-cream/70 hover:border-gold hover:text-gold transition-all text-sm tracking-wider" data-filter="cinnamon">Cinnamon</button>
                <button onclick="filterProducts('pepper')" class="filter-btn px-6 py-2 rounded-full border border-gold/30 text-cream/70 hover:border-gold hover:text-gold transition-all text-sm tracking-wider" data-filter="pepper">Pepper</button>
                <button onclick="filterProducts('cardamom')" class="filter-btn px-6 py-2 rounded-full border border-gold/30 text-cream/70 hover:border-gold hover:text-gold transition-all text-sm tracking-wider" data-filter="cardamom">Cardamom</button>
                <button onclick="filterProducts('other')" class="filter-btn px-6 py-2 rounded-full border border-gold/30 text-cream/70 hover:border-gold hover:text-gold transition-all text-sm tracking-wider" data-filter="other">Others</button>
            </div>

            <div id="productGrid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <!-- Products will be populated by JS -->
            </div>
        </div>
    </section>

    <!-- Featured Products Highlight -->
    <section class="py-24 relative overflow-hidden">
        <div class="absolute inset-0 bg-gradient-to-r from-gold/5 to-transparent"></div>
        <div class="max-w-7xl mx-auto px-6 relative">
            <div class="grid md:grid-cols-3 gap-8">
                <div class="reveal text-center p-8 rounded-2xl border border-gold/10 bg-soft-black/50 hover:border-gold/30 transition-all group">
                    <div class="w-20 h-20 mx-auto mb-6 rounded-full bg-gold/10 flex items-center justify-center group-hover:scale-110 transition-transform">
                        <svg class="w-10 h-10 text-gold" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
                    </div>
                    <h3 class="font-serif text-xl text-cream mb-2">Premium Ceylon Cinnamon</h3>
                    <p class="text-cream/60 text-sm">Rich aroma and authentic Sri Lankan quality. The true cinnamon experience.</p>
                </div>
                <div class="reveal text-center p-8 rounded-2xl border border-gold/10 bg-soft-black/50 hover:border-gold/30 transition-all group" style="animation-delay: 0.1s">
                    <div class="w-20 h-20 mx-auto mb-6 rounded-full bg-gold/10 flex items-center justify-center group-hover:scale-110 transition-transform">
                        <svg class="w-10 h-10 text-gold" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
                    </div>
                    <h3 class="font-serif text-xl text-cream mb-2">Premium Black Pepper</h3>
                    <p class="text-cream/60 text-sm">Bold flavor and export-grade freshness. The king of spices.</p>
                </div>
                <div class="reveal text-center p-8 rounded-2xl border border-gold/10 bg-soft-black/50 hover:border-gold/30 transition-all group" style="animation-delay: 0.2s">
                    <div class="w-20 h-20 mx-auto mb-6 rounded-full bg-gold/10 flex items-center justify-center group-hover:scale-110 transition-transform">
                        <svg class="w-10 h-10 text-gold" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
                    </div>
                    <h3 class="font-serif text-xl text-cream mb-2">Green Cardamom</h3>
                    <p class="text-cream/60 text-sm">Naturally fragrant and hand-selected. The queen of spices.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Worldwide Shipping -->
    <section id="shipping" class="py-24 bg-soft-black/30">
        <div class="max-w-7xl mx-auto px-6">
            <div class="text-center mb-16 reveal">
                <span class="text-gold text-sm tracking-[0.3em] uppercase mb-4 block">Global Reach</span>
                <h2 class="font-serif text-4xl md:text-5xl font-bold text-cream mb-4">Worldwide Shipping</h2>
                <p class="text-cream/60 max-w-2xl mx-auto">We proudly deliver authentic Sri Lankan spices to customers around the globe.</p>
            </div>

            <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-6 gap-4 reveal">
                <div class="shipping-badge p-6 rounded-xl text-center hover:bg-gold/10 transition-all group cursor-pointer">
                    <div class="text-3xl mb-2">🇺🇸</div>
                    <p class="text-cream font-semibold text-sm group-hover:text-gold transition-colors">USA</p>
                </div>
                <div class="shipping-badge p-6 rounded-xl text-center hover:bg-gold/10 transition-all group cursor-pointer">
                    <div class="text-3xl mb-2">🇨🇦</div>
                    <p class="text-cream font-semibold text-sm group-hover:text-gold transition-colors">Canada</p>
                </div>
                <div class="shipping-badge p-6 rounded-xl text-center hover:bg-gold/10 transition-all group cursor-pointer">
                    <div class="text-3xl mb-2">🇬🇧</div>
                    <p class="text-cream font-semibold text-sm group-hover:text-gold transition-colors">UK</p>
                </div>
                <div class="shipping-badge p-6 rounded-xl text-center hover:bg-gold/10 transition-all group cursor-pointer">
                    <div class="text-3xl mb-2">🇦🇺</div>
                    <p class="text-cream font-semibold text-sm group-hover:text-gold transition-colors">Australia</p>
                </div>
                <div class="shipping-badge p-6 rounded-xl text-center hover:bg-gold/10 transition-all group cursor-pointer">
                    <div class="text-3xl mb-2">🇪🇺</div>
                    <p class="text-cream font-semibold text-sm group-hover:text-gold transition-colors">Europe</p>
                </div>
                <div class="shipping-badge p-6 rounded-xl text-center hover:bg-gold/10 transition-all group cursor-pointer">
                    <div class="text-3xl mb-2">🇦🇪</div>
                    <p class="text-cream font-semibold text-sm group-hover:text-gold transition-colors">Middle East</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Testimonials -->
    <section id="testimonials" class="py-24">
        <div class="max-w-7xl mx-auto px-6">
            <div class="text-center mb-16 reveal">
                <span class="text-gold text-sm tracking-[0.3em] uppercase mb-4 block">Testimonials</span>
                <h2 class="font-serif text-4xl md:text-5xl font-bold text-cream mb-4">What Our Customers Say</h2>
            </div>

            <div class="grid md:grid-cols-3 gap-8">
                <div class="testimonial-card p-8 rounded-2xl reveal">
                    <div class="flex gap-1 mb-4">
                        <svg class="w-5 h-5 text-gold" fill="currentColor" viewBox="0 0 20 20"><path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/></svg>
                        <svg class="w-5 h-5 text-gold" fill="currentColor" viewBox="0 0 20 20"><path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/></svg>
                        <svg class="w-5 h-5 text-gold" fill="currentColor" viewBox="0 0 20 20"><path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/></svg>
                        <svg class="w-5 h-5 text-gold" fill="currentColor" viewBox="0 0 20 20"><path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/></svg>
                        <svg class="w-5 h-5 text-gold" fill="currentColor" viewBox="0 0 20 20"><path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/></svg>
                    </div>
                    <p class="text-cream/80 italic mb-6 text-lg">"The best cinnamon I've ever purchased. The aroma is incredible and the quality is unmatched."</p>
                    <div class="flex items-center gap-3">
                        <div class="w-10 h-10 rounded-full bg-gold/20 flex items-center justify-center text-gold font-bold">S</div>
                        <div>
                            <p class="text-cream font-semibold text-sm">Sarah M.</p>
                            <p class="text-cream/50 text-xs">USA</p>
                        </div>
                    </div>
                </div>

                <div class="testimonial-card p-8 rounded-2xl reveal" style="animation-delay: 0.1s">
                    <div class="flex gap-1 mb-4">
                        <svg class="w-5 h-5 text-gold" fill="currentColor" viewBox="0 0 20 20"><path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/></svg>
                        <svg class="w-5 h-5 text-gold" fill="currentColor" viewBox="0 0 20 20"><path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/></svg>
                        <svg class="w-5 h-5 text-gold" fill="currentColor" viewBox="0 0 20 20"><path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/></svg>
                        <svg class="w-5 h-5 text-gold" fill="currentColor" viewBox="0 0 20 20"><path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/></svg>
                        <svg class="w-5 h-5 text-gold" fill="currentColor" viewBox="0 0 20 20"><path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/></svg>
                    </div>
                    <p class="text-cream/80 italic mb-6 text-lg">"Excellent quality and fast delivery. The packaging is beautiful and the spices are incredibly fresh."</p>
                    <div class="flex items-center gap-3">
                        <div class="w-10 h-10 rounded-full bg-gold/20 flex items-center justify-center text-gold font-bold">J</div>
                        <div>
                            <p class="text-cream font-semibold text-sm">James K.</p>
                            <p class="text-cream/50 text-xs">UK</p>
                        </div>
                    </div>
                </div>

                <div class="testimonial-card p-8 rounded-2xl reveal" style="animation-delay: 0.2s">
                    <div class="flex gap-1 mb-4">
                        <svg class="w-5 h-5 text-gold" fill="currentColor" viewBox="0 0 20 20"><path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/></svg>
                        <svg class="w-5 h-5 text-gold" fill="currentColor" viewBox="0 0 20 20"><path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/></svg>
                        <svg class="w-5 h-5 text-gold" fill="currentColor" viewBox="0 0 20 20"><path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/></svg>
                        <svg class="w-5 h-5 text-gold" fill="currentColor" viewBox="0 0 20 20"><path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/></svg>
                        <svg class="w-5 h-5 text-gold" fill="currentColor" viewBox="0 0 20 20"><path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/></svg>
                    </div>
                    <p class="text-cream/80 italic mb-6 text-lg">"Authentic Sri Lankan spices with premium packaging. The cardamom is absolutely divine!"</p>
                    <div class="flex items-center gap-3">
                        <div class="w-10 h-10 rounded-full bg-gold/20 flex items-center justify-center text-gold font-bold">M</div>
                        <div>
                            <p class="text-cream font-semibold text-sm">Maria L.</p>
                            <p class="text-cream/50 text-xs">Australia</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-24 bg-soft-black/30 relative">
        <div class="absolute inset-0 bg-[radial-gradient(ellipse_at_top,_var(--tw-gradient-stops))] from-gold/5 via-transparent to-transparent"></div>
        <div class="max-w-7xl mx-auto px-6 relative">
            <div class="grid md:grid-cols-2 gap-16">
                <div class="reveal">
                    <span class="text-gold text-sm tracking-[0.3em] uppercase mb-4 block">Get In Touch</span>
                    <h2 class="font-serif text-4xl md:text-5xl font-bold text-cream mb-6">Contact Us</h2>
                    <p class="text-cream/60 mb-8">Have questions about our products or shipping? We'd love to hear from you.</p>
                    
                    <div class="space-y-6">
                        <div class="flex items-center gap-4 group">
                            <div class="w-12 h-12 rounded-full bg-gold/10 flex items-center justify-center group-hover:bg-gold/20 transition-colors">
                                <svg class="w-5 h-5 text-gold" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path></svg>
                            </div>
                            <div>
                                <p class="text-cream/50 text-sm">Email</p>
                                <p class="text-cream">info@royalceylonspice.com</p>
                            </div>
                        </div>
                        <div class="flex items-center gap-4 group">
                            <div class="w-12 h-12 rounded-full bg-gold/10 flex items-center justify-center group-hover:bg-gold/20 transition-colors">
                                <svg class="w-5 h-5 text-gold" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"></path></svg>
                            </div>
                            <div>
                                <p class="text-cream/50 text-sm">Phone</p>
                                <p class="text-cream">+94 XX XXX XXXX</p>
                            </div>
                        </div>
                        <div class="flex items-center gap-4 group">
                            <div class="w-12 h-12 rounded-full bg-gold/10 flex items-center justify-center group-hover:bg-gold/20 transition-colors">
                                <svg class="w-5 h-5 text-gold" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"></path><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"></path></svg>
                            </div>
                            <div>
                                <p class="text-cream/50 text-sm">Location</p>
                                <p class="text-cream">Sri Lanka</p>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="reveal">
                    <form id="contactForm" class="space-y-6 p-8 rounded-2xl border border-gold/10 bg-royal-black/50">
                        <div>
                            <label class="block text-cream/60 text-sm mb-2 tracking-wider uppercase">Name</label>
                            <input type="text" required class="input-luxury w-full px-4 py-3 rounded-lg text-cream placeholder-cream/30" placeholder="Your name">
                        </div>
                        <div>
                            <label class="block text-cream/60 text-sm mb-2 tracking-wider uppercase">Email</label>
                            <input type="email" required class="input-luxury w-full px-4 py-3 rounded-lg text-cream placeholder-cream/30" placeholder="your@email.com">
                        </div>
                        <div>
                            <label class="block text-cream/60 text-sm mb-2 tracking-wider uppercase">Country</label>
                            <select class="input-luxury w-full px-4 py-3 rounded-lg text-cream">
                                <option value="" class="bg-royal-black">Select Country</option>
                                <option value="usa" class="bg-royal-black">USA</option>
                                <option value="canada" class="bg-royal-black">Canada</option>
                                <option value="uk" class="bg-royal-black">UK</option>
                                <option value="australia" class="bg-royal-black">Australia</option>
                                <option value="europe" class="bg-royal-black">Europe</option>
                                <option value="middle-east" class="bg-royal-black">Middle East</option>
                                <option value="other" class="bg-royal-black">Other</option>
                            </select>
                        </div>
                        <div>
                            <label class="block text-cream/60 text-sm mb-2 tracking-wider uppercase">Message</label>
                            <textarea required rows="4" class="input-luxury w-full px-4 py-3 rounded-lg text-cream placeholder-cream/30 resize-none" placeholder="Your message..."></textarea>
                        </div>
                        <button type="submit" class="btn-gold w-full py-4 rounded-lg text-royal-black font-semibold tracking-wider uppercase text-sm">Send Message</button>
                    </form>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="bg-royal-black border-t border-gold/10 py-12">
        <div class="max-w-7xl mx-auto px-6">
            <div class="grid md:grid-cols-4 gap-8 mb-8">
                <div class="md:col-span-2">
                    <div class="flex items-center gap-3 mb-4">
                        <div class="w-8 h-8 rounded-full bg-gradient-to-br from-gold to-dark-gold flex items-center justify-center text-royal-black font-bold">R</div>
                        <span class="font-serif text-xl font-bold text-gold-gradient">ROYAL CEYLON</span>
                    </div>
                    <p class="text-cream/50 text-sm leading-relaxed max-w-sm">Premium Ceylon spices from the heart of Sri Lanka. Handpicked, pure, authentic, and export quality.</p>
                </div>
                <div>
                    <h4 class="text-gold font-semibold mb-4 tracking-wider uppercase text-sm">Quick Links</h4>
                    <ul class="space-y-2">
                        <li><a href="#home" class="text-cream/50 hover:text-gold transition-colors text-sm">Home</a></li>
                        <li><a href="#about" class="text-cream/50 hover:text-gold transition-colors text-sm">About Us</a></li>
                        <li><a href="#products" class="text-cream/50 hover:text-gold transition-colors text-sm">Products</a></li>
                        <li><a href="#contact" class="text-cream/50 hover:text-gold transition-colors text-sm">Contact</a></li>
                    </ul>
                </div>
                <div>
                    <h4 class="text-gold font-semibold mb-4 tracking-wider uppercase text-sm">Products</h4>
                    <ul class="space-y-2">
                        <li><a href="#products" class="text-cream/50 hover:text-gold transition-colors text-sm">Ceylon Cinnamon</a></li>
                        <li><a href="#products" class="text-cream/50 hover:text-gold transition-colors text-sm">Black Pepper</a></li>
                        <li><a href="#products" class="text-cream/50 hover:text-gold transition-colors text-sm">Green Cardamom</a></li>
                        <li><a href="#products" class="text-cream/50 hover:text-gold transition-colors text-sm">Spice Gift Boxes</a></li>
                    </ul>
                </div>
            </div>
            <div class="border-t border-gold/10 pt-8 flex flex-col md:flex-row justify-between items-center gap-4">
                <p class="text-cream/30 text-sm">© 2026 Royal Ceylon Spice House. All rights reserved.</p>
                <div class="flex gap-4">
                    <a href="#" class="text-cream/30 hover:text-gold transition-colors">
                        <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M24 4.557c-.883.392-1.832.656-2.828.775 1.017-.609 1.798-1.574 2.165-2.724-.951.564-2.005.974-3.127 1.195-.897-.957-2.178-1.555-3.594-1.555-3.179 0-5.515 2.966-4.797 6.045-4.091-.205-7.719-2.165-10.148-5.144-1.29 2.213-.669 5.108 1.523 6.574-.806-.026-1.566-.247-2.229-.616-.054 2.281 1.581 4.415 3.949 4.89-.693.188-1.452.232-2.224.084.626 1.956 2.444 3.379 4.6 3.419-2.07 1.623-4.678 2.348-7.29 2.04 2.179 1.397 4.768 2.212 7.548 2.212 9.142 0 14.307-7.721 13.995-14.646.962-.695 1.797-1.562 2.457-2.549z"/></svg>
                    </a>
                    <a href="#" class="text-cream/30 hover:text-gold transition-colors">
                        <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/></svg>
                    </a>
                </div>
            </div>
        </div>
    </footer>

    <!-- Cart Sidebar -->
    <div id="cartSidebar" class="fixed inset-y-0 right-0 w-full md:w-96 bg-soft-black border-l border-gold/20 z-50 transform translate-x-full transition-transform duration-300 overflow-y-auto">
        <div class="p-6">
            <div class="flex justify-between items-center mb-8">
                <h3 class="font-serif text-2xl text-gold">Your Cart</h3>
                <button onclick="toggleCart()" class="text-cream/50 hover:text-gold">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path></svg>
                </button>
            </div>
            <div id="cartItems" class="space-y-4">
                <p class="text-cream/50 text-center py-8">Your cart is empty</p>
            </div>
            <div id="cartFooter" class="hidden mt-8 pt-8 border-t border-gold/10">
                <div class="flex justify-between mb-4">
                    <span class="text-cream">Total</span>
                    <span id="cartTotal" class="text-gold font-bold text-xl">$0.00</span>
                </div>
                <button onclick="checkout()" class="btn-gold w-full py-3 rounded-lg text-royal-black font-semibold">Checkout</button>
            </div>
        </div>
    </div>
    <div id="cartOverlay" onclick="toggleCart()" class="fixed inset-0 bg-black/50 z-40 hidden backdrop-blur-sm"></div>

    <!-- Toast Notification -->
    <div id="toast" class="fixed bottom-8 right-8 bg-gold text-royal-black px-6 py-3 rounded-lg shadow-lg transform translate-y-20 opacity-0 transition-all duration-300 z-50 font-semibold">
        Added to cart!
    </div>

    <script>
        // Product Data
        const products = [
            {
                id: 1,
                name: "Ceylon Cinnamon Sticks",
                category: "cinnamon",
                price: 24.99,
                image: "https://images.unsplash.com/photo-1596040033229-a9821ebd058d?w=600&auto=format&fit=crop&q=80",
                description: "Premium true Ceylon cinnamon sticks with delicate, sweet flavor"
            },
            {
                id: 2,
                name: "Cinnamon Powder",
                category: "cinnamon",
                price: 19.99,
                image: "https://images.unsplash.com/photo-1556682851-c458089365b4?w=600&auto=format&fit=crop&q=80",
                description: "Finely ground Ceylon cinnamon for baking and cooking"
            },
            {
                id: 3,
                name: "Black Pepper",
                category: "pepper",
                price: 18.99,
                image: "https://images.unsplash.com/photo-1599909533681-7c9e0bf50e3c?w=600&auto=format&fit=crop&q=80",
                description: "Bold Sri Lankan black pepper with robust flavor"
            },
            {
                id: 4,
                name: "White Pepper",
                category: "pepper",
                price: 22.99,
                image: "https://images.unsplash.com/photo-1621958054304-1b8fb4d3b239?w=600&auto=format&fit=crop&q=80",
                description: "Mild yet aromatic white pepper, perfect for light dishes"
            },
            {
                id: 5,
                name: "Green Cardamom",
                category: "cardamom",
                price: 29.99,
                image: "https://images.unsplash.com/photo-1615485290382-441e4d049cb5?w=600&auto=format&fit=crop&q=80",
                description: "Naturally fragrant green cardamom pods"
            },
            {
                id: 6,
                name: "Cloves",
                category: "other",
                price: 16.99,
                image: "https://images.unsplash.com/photo-1615485290382-441e4d049cb5?w=600&auto=format&fit=crop&q=80",
                description: "Aromatic whole cloves from Sri Lankan highlands"
            },
            {
                id: 7,
                name: "Nutmeg",
                category: "other",
                price: 21.99,
                image: "https://images.unsplash.com/photo-1599909533681-7c9e0bf50e3c?w=600&auto=format&fit=crop&q=80",
                description: "Whole nutmeg with warm, nutty sweetness"
            },
            {
                id: 8,
                name: "Spice Gift Box",
                category: "other",
                price: 89.99,
                image: "https://images.unsplash.com/photo-1596040033229-a9821ebd058d?w=600&auto=format&fit=crop&q=80",
                description: "Premium gift box with assorted Ceylon spices"
            }
        ];

        let cart = [];
        let currentFilter = 'all';

        // Initialize
        document.addEventListener('DOMContentLoaded', () => {
            renderProducts();
            initSpiceParticles();
            initScrollAnimations();
            initNavbar();
        });

        // Render Products
        function renderProducts() {
            const grid = document.getElementById('productGrid');
            const filtered = currentFilter === 'all' ? products : products.filter(p => p.category === currentFilter);
            
            grid.innerHTML = filtered.map(product => `
                <div class="product-card group relative bg-soft-black/50 rounded-2xl overflow-hidden border border-gold/10 hover:border-gold/30 reveal">
                    <div class="relative h-64 overflow-hidden">
                        <img src="${product.image}" alt="${product.name}" class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-110">
                        <div class="overlay absolute inset-0 bg-royal-black/60 flex items-center justify-center gap-3">
                            <button onclick="addToCart(${product.id})" class="bg-gold text-royal-black px-6 py-2 rounded-full font-semibold text-sm hover:scale-105 transition-transform">Add to Cart</button>
                        </div>
                        <div class="absolute top-4 right-4 bg-gold/90 text-royal-black px-3 py-1 rounded-full text-sm font-bold">$${product.price}</div>
                    </div>
                    <div class="p-6">
                        <h3 class="font-serif text-xl text-cream mb-2 group-hover:text-gold transition-colors">${product.name}</h3>
                        <p class="text-cream/50 text-sm mb-4">${product.description}</p>
                        <div class="flex items-center justify-between">
                            <span class="text-gold text-sm font-semibold">${product.category.charAt(0).toUpperCase() + product.category.slice(1)}</span>
                            <button onclick="addToCart(${product.id})" class="text-gold hover:text-cream transition-colors">
                                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M16 11V7a4 4 0 00-8 0v4M5 9h14l1 12H4L5 9z"></path></svg>
                            </button>
                        </div>
                    </div>
                </div>
            `).join('');
        }

        // Filter Products
        function filterProducts(category) {
            currentFilter = category;
            document.querySelectorAll('.filter-btn').forEach(btn => {
                if(btn.dataset.filter === category) {
                    btn.classList.add('bg-gold', 'text-royal-black', 'border-gold');
                    btn.classList.remove('text-cream/70', 'border-gold/30');
                } else {
                    btn.classList.remove('bg-gold', 'text-royal-black', 'border-gold');
                    btn.classList.add('text-cream/70', 'border-gold/30');
                }
            });
            renderProducts();
            // Re-trigger animations for new elements
            setTimeout(initScrollAnimations, 100);
        }

        // Cart Functions
        function addToCart(productId) {
            const product = products.find(p => p.id === productId);
            const existing = cart.find(item => item.id === productId);
            
            if(existing) {
                existing.quantity++;
            } else {
                cart.push({...product, quantity: 1});
            }
            
            updateCart();
            showToast();
        }

        function removeFromCart(productId) {
            cart = cart.filter(item => item.id !== productId);
            updateCart();
        }

        function updateQuantity(productId, delta) {
            const item = cart.find(item => item.id === productId);
            if(item) {
                item.quantity += delta;
                if(item.quantity <= 0) removeFromCart(productId);
                else updateCart();
            }
        }

        function updateCart() {
            const cartItems = document.getElementById('cartItems');
            const cartFooter = document.getElementById('cartFooter');
            const cartCount = document.getElementById('cartCount');
            
            if(cart.length === 0) {
                cartItems.innerHTML = '<p class="text-cream/50 text-center py-8">Your cart is empty</p>';
                cartFooter.classList.add('hidden');
                cartCount.classList.add('hidden');
            } else {
                cartItems.innerHTML = cart.map(item => `
                    <div class="flex gap-4 bg-royal-black/50 p-4 rounded-xl border border-gold/10">
                        <img src="${item.image}" class="w-20 h-20 object-cover rounded-lg" alt="${item.name}">
                        <div class="flex-1">
                            <h4 class="text-cream font-semibold text-sm">${item.name}</h4>
                            <p class="text-gold text-sm">$${item.price}</p>
                            <div class="flex items-center gap-3 mt-2">
                                <button onclick="updateQuantity(${item.id}, -1)" class="text-cream/50 hover:text-gold w-6 h-6 rounded-full border border-gold/20 flex items-center justify-center text-xs">-</button>
                                <span class="text-cream text-sm">${item.quantity}</span>
                                <button onclick="updateQuantity(${item.id}, 1)" class="text-cream/50 hover:text-gold w-6 h-6 rounded-full border border-gold/20 flex items-center justify-center text-xs">+</button>
                            </div>
                        </div>
                        <button onclick="removeFromCart(${item.id})" class="text-cream/30 hover:text-red-400 self-start">
                            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path></svg>
                        </button>
                    </div>
                `).join('');
                
                const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
                document.getElementById('cartTotal').textContent = '$' + total.toFixed(2);
                cartFooter.classList.remove('hidden');
                cartCount.classList.remove('hidden');
                cartCount.textContent = cart.reduce((sum, item) => sum + item.quantity, 0);
            }
        }

        function toggleCart() {
            const sidebar = document.getElementById('cartSidebar');
            const overlay = document.getElementById('cartOverlay');
            
            if(sidebar.classList.contains('translate-x-full')) {
                sidebar.classList.remove('translate-x-full');
                overlay.classList.remove('hidden');
            } else {
                sidebar.classList.add('translate-x-full');
                overlay.classList.add('hidden');
            }
        }

        function checkout() {
            alert('Thank you for your interest! Checkout functionality coming soon.');
        }

        function showToast() {
            const toast = document.getElementById('toast');
            toast.classList.remove('translate-y-20', 'opacity-0');
            setTimeout(() => {
                toast.classList.add('translate-y-20', 'opacity-0');
            }, 2000);
        }

        // Mobile Menu
        function toggleMobileMenu() {
            document.getElementById('mobileMenu').classList.toggle('active');
        }

        // Navbar Scroll Effect
        function initNavbar() {
            const navbar = document.getElementById('navbar');
            window.addEventListener('scroll', () => {
                if(window.scrollY > 50) {
                    navbar.classList.add('nav-glass', 'py-2');
                    navbar.classList.remove('py-4');
                } else {
                    navbar.classList.remove('nav-glass', 'py-2');
                    navbar.classList.add('py-4');
                }
            });
        }

        // Scroll Animations
        function initScrollAnimations() {
            gsap.registerPlugin(ScrollTrigger);
            
            gsap.utils.toArray('.reveal').forEach(element => {
                gsap.fromTo(element, 
                    { opacity: 0, y: 30 },
                    {
                        opacity: 1,
                        y: 0,
                        duration: 0.8,
                        ease: "power2.out",
                        scrollTrigger: {
                            trigger: element,
                            start: "top 85%",
                            toggleActions: "play none none none"
                        }
                    }
                );
            });
        }

        // Spice Particle Animation
        function initSpiceParticles() {
            const canvas = document.getElementById('spiceCanvas');
            const ctx = canvas.getContext('2d');
            
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            
            const particles = [];
            const particleCount = 25;
            
            class Particle {
                constructor() {
                    this.reset();
                }
                
                reset() {
                    this.x = Math.random() * canvas.width;
                    this.y = Math.random() * canvas.height;
                    this.size = Math.random() * 3 + 1;
                    this.speedX = (Math.random() - 0.5) * 0.5;
                    this.speedY = (Math.random() - 0.5) * 0.5;
                    this.opacity = Math.random() * 0.5 + 0.1;
                    this.color = Math.random() > 0.5 ? '#D4AF37' : '#8B6B1B';
                }
                
                update() {
                    this.x += this.speedX;
                    this.y += this.speedY;
                    
                    if(this.x < 0 || this.x > canvas.width || this.y < 0 || this.y > canvas.height) {
                        this.reset();
                    }
                }
                
                draw() {
                    ctx.beginPath();
                    ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                    ctx.fillStyle = this.color;
                    ctx.globalAlpha = this.opacity;
                    ctx.fill();
                }
            }
            
            for(let i = 0; i < particleCount; i++) {
                particles.push(new Particle());
            }
            
            function animate() {
                ctx.clearRect(0, 0, canvas.width, canvas.height);
                particles.forEach(particle => {
                    particle.update();
                    particle.draw();
                });
                requestAnimationFrame(animate);
            }
            
            animate();
            
            window.addEventListener('resize', () => {
                canvas.width = window.innerWidth;
                canvas.height = window.innerHeight;
            });
        }

        // Contact Form
        document.getElementById('contactForm').addEventListener('submit', (e) => {
            e.preventDefault();
            alert('Thank you for your message! We will get back to you soon.');
            e.target.reset();
        });

        // Smooth Scroll
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if(target) {
                    target.scrollIntoView({ behavior: 'smooth', block: 'start' });
                }
            });
        });
    </script>
</body>
</html>
