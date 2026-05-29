<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jindo Roy UI/UX Portfolio</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>
    
    <style>
        /* Modern Dynamic Token variables tuned for High-contrast Black & Neon Green Mode */
        :root {
            --primary-token: #39FF14; /* Fluorescent Green */
            --primary-token-glow: rgba(57, 255, 20, 0.25);
            --primary-token-glow-hover: rgba(57, 255, 20, 0.65);
            --primary-token-text: #000000;
        }

        /* Base configuration */
        body {
            font-family: 'Inter', sans-serif;
            scroll-behavior: smooth;
            background-color: #000000;
            overflow-x: hidden;
        }

        /* Custom scrollbar matching dynamic light theme token */
        body::-webkit-scrollbar {
            width: 8px;
        }
        body::-webkit-scrollbar-track {
            background: #000000;
        }
        body::-webkit-scrollbar-thumb {
            background-color: var(--primary-token);
            border-radius: 20px;
            border: 2px solid #000000;
            transition: background-color 0.3s ease;
        }

        /* Ultra-premium Scroll-Linked Animation Utility Rules */
        .reveal-item {
            opacity: 0;
            transform: translateY(40px) scale(0.96);
            filter: blur(8px);
            transition: opacity 0.8s cubic-bezier(0.16, 1, 0.3, 1), 
                        transform 0.8s cubic-bezier(0.16, 1, 0.3, 1), 
                        filter 0.8s cubic-bezier(0.16, 1, 0.3, 1);
            will-change: transform, opacity, filter;
        }

        .reveal-item.revealed {
            opacity: 1;
            transform: translateY(0) scale(1);
            filter: blur(0px);
        }

        /* Staggered Delays for Cascade Animations */
        .delay-100 { transition-delay: 100ms; }
        .delay-200 { transition-delay: 200ms; }
        .delay-300 { transition-delay: 300ms; }
        .delay-400 { transition-delay: 400ms; }

        /* Shimmering beam reflection effect for modern call-to-actions */
        .shimmer-btn {
            position: relative;
            overflow: hidden;
            transform: translateZ(0); /* Force GPU acceleration */
        }
        .shimmer-btn::after {
            content: '';
            position: absolute;
            top: -50%;
            left: -60%;
            width: 30%;
            height: 200%;
            background: linear-gradient(
                to right,
                rgba(255, 255, 255, 0) 0%,
                rgba(255, 255, 255, 0.45) 50%,
                rgba(255, 255, 255, 0) 100%
            );
            transform: rotate(25deg);
            transition: all 0.7s cubic-bezier(0.16, 1, 0.3, 1);
            pointer-events: none;
        }
        .shimmer-btn:hover::after {
            left: 140%;
        }

        /* Dynamic neon glow effect with CENTERED SPREAD instead of drop down */
        .cta-glow {
            background-color: var(--primary-token) !important;
            color: var(--primary-token-text) !important;
            box-shadow: 0 0 20px var(--primary-token-glow);
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1) !important;
            will-change: transform, box-shadow;
        }
        .cta-glow:hover {
            box-shadow: 0 0 30px var(--primary-token-glow-hover);
            transform: translateY(-3px) scale(1.02);
            filter: brightness(1.1);
        }

        /* Editorial Frosted Glassmorphism panel with CENTERED SPREAD */
        .glass-panel {
            background: rgba(10, 10, 10, 0.7);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.05);
            box-shadow: 0 0 30px rgba(0, 0, 0, 0.7);
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            transform: translateZ(0);
        }
        .glass-panel:hover {
            border-color: rgba(57, 255, 20, 0.3);
            box-shadow: 0 0 40px rgba(0, 0, 0, 0.8), 0 0 30px var(--primary-token-glow);
            transform: translateY(-6px);
        }

        /* Graphic asset integration with rich dark gradient masks */
        .hero-background {
            background-image: url('3088420239472027610.png');
            background-size: cover;
            background-position: center center;
            background-attachment: fixed;
            position: relative;
            isolation: isolate;
        }
        .hero-background::before {
            content: '';
            position: absolute;
            inset: 0;
            background: linear-gradient(135deg, rgba(0, 0, 0, 0.9) 0%, rgba(3, 7, 18, 0.95) 100%);
            z-index: -1;
        }

        /* Responsive image hover effects */
        .project-image-wrapper {
            position: relative;
            overflow: hidden;
            border-radius: 0.75rem;
            border: 1px solid rgba(255, 255, 255, 0.05);
            background-color: #030712;
        }
        .project-image-wrapper img {
            transition: transform 0.8s cubic-bezier(0.16, 1, 0.3, 1), filter 0.6s ease-in-out;
            will-change: transform;
        }
        .project-image-wrapper:hover img {
            transform: scale(1.06);
            filter: brightness(1.15);
        }
        .project-image-wrapper::after {
            content: '';
            position: absolute;
            inset: 0;
            background: linear-gradient(to top, rgba(0, 0, 0, 0.6), transparent);
            opacity: 1;
            transition: opacity 0.4s ease-in-out;
        }
        .project-image-wrapper:hover::after {
            opacity: 0.2;
        }

        /* Continuous Floating Animation */
        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-8px); }
            100% { transform: translateY(0px); }
        }
        .animate-float {
            animation: float 6s ease-in-out infinite;
        }

        /* Smooth progressive scroll bar shadow and layout alignment */
        #scrollProgressBar {
            transform-origin: left;
            transition: transform 0.1s ease-out;
            will-change: transform;
        }
    </style>
</head>
<body class="text-slate-200 antialiased bg-black overflow-x-hidden relative">

    <div id="scrollProgressBar" class="fixed top-0 left-0 w-full h-[3px] bg-[#39FF14] z-[100] scale-x-0 shadow-[0_0_15px_#39FF14]"></div>

    <canvas id="interactiveCanvasBg" class="fixed top-0 left-0 w-full h-full pointer-events-none z-0 opacity-40"></canvas>

    <header id="mainHeader" class="sticky top-0 z-50 bg-black/80 backdrop-blur-xl border-b border-white/5 shadow-[0_0_20px_rgba(0,0,0,0.8)] transition-all duration-300">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex justify-between items-center py-4">
            <div class="text-xl font-extrabold tracking-wider flex-1 md:flex-none transform transition hover:scale-105 duration-300">
                <a href="#home"><span class="text-white">Jindo</span><span style="color: var(--primary-token); transition: color 0.3s ease; text-shadow: 0 0 10px var(--primary-token-glow);">Roy</span></a>
            </div>

            <nav class="hidden md:flex justify-center items-center space-x-8 flex-1">
                <a href="#home" class="text-slate-400 hover:text-white hover:-translate-y-0.5 transform transition duration-200 font-medium text-sm sm:text-base">Home</a>
                <a href="#projects" class="text-slate-400 hover:text-white hover:-translate-y-0.5 transform transition duration-200 font-medium text-sm sm:text-base">Projects</a>
                <a href="#about" class="text-slate-400 hover:text-white hover:-translate-y-0.5 transform transition duration-200 font-medium text-sm sm:text-base">About</a>
                <a href="#skills" class="text-slate-400 hover:text-white hover:-translate-y-0.5 transform transition duration-200 font-medium text-sm sm:text-base">Skills</a>
                <a href="#contact" class="text-slate-400 hover:text-white hover:-translate-y-0.5 transform transition duration-200 font-medium text-sm sm:text-base">Contact</a>
            </nav>

            <div class="flex justify-end items-center flex-1 md:flex-none">
                <a href="#contact" class="inline-flex items-center px-4 py-2 border border-transparent text-xs sm:text-sm font-bold rounded-lg cta-glow" style="background-color: var(--primary-token); color: var(--primary-token-text); transition: all 0.3s ease;">
                    <svg class="w-4 h-4 mr-1.5" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="2.5" xmlns="http://www.w3.org/2000/svg">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M8 12h.01M12 12h.01M16 12h.01M21 12c0 4.418-4.03 8-9 8a9.863 9.863 0 01-4.255-.949L3 20l1.395-3.72C3.512 15.042 3 13.574 3 12c0-4.418 4.03-8 9-8s9 3.582 9 8z"></path>
                    </svg>
                    <span>Let's Talk</span>
                </a>
            </div>
        </div>
    </header>

    <main class="relative z-10">
        <section id="home" class="hero-background pt-24 pb-20 md:pt-32 md:pb-28 text-center overflow-hidden">
            <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10 reveal-item">
                
                <div class="inline-flex items-center gap-2.5 px-4 py-2 rounded-full bg-white/5 border border-white/10 text-slate-300 text-xs sm:text-sm font-semibold tracking-wider uppercase mb-6 backdrop-blur-md shadow-[0_0_15px_rgba(255,255,255,0.05)] transition-all duration-300 hover:bg-white/10 hover:border-[#39FF14]/30 hover:scale-105 hover:shadow-[0_0_20px_rgba(57,255,20,0.2)]">
                    <span class="flex h-2.5 w-2.5 relative">
                        <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-emerald-400 opacity-75"></span>
                        <span class="relative inline-flex rounded-full h-2.5 w-2.5 bg-emerald-500"></span>
                    </span>
                    <span>Available for New Projects</span>
                </div>

                <h1 class="text-4xl sm:text-6xl font-extrabold tracking-tight text-white mb-8 transition-transform duration-700 transform hover:scale-[1.02]">
                    Simplicity by design. 
                    <span class="block mt-3 sm:mt-4 text-[#86efac]" style="text-shadow: 0 0 15px rgba(134, 239, 172, 0.45);">Human by instinct.</span>
                </h1>
                <p class="text-lg sm:text-xl text-slate-400 max-w-2xl mx-auto mb-10 leading-relaxed">
                    I design fully responsive digital products that feel like a breath of fresh air. I build high-performance, cross-platform interfaces that look flawless on any device.
                </p>
                <div class="flex justify-center">
                    <button id="downloadResumeBtn" class="w-full sm:w-auto inline-flex justify-center items-center px-10 py-4 border border-transparent text-base font-bold rounded-lg cta-glow shimmer-btn animate-float">
                        <svg class="w-5 h-5 mr-2.5" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="2.5" xmlns="http://www.w3.org/2000/svg">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-4l-4 4m0 0l-4-4m4 4V4"></path>
                        </svg>
                        <span id="btnText">Download Resume</span>
                    </button>
                </div>
            </div>
        </section>

        <section id="projects" class="py-16 md:py-24 bg-black">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center mb-16 reveal-item">
                    <h2 class="text-4xl font-extrabold text-white mb-2">Projects</h2>
                    <p class="text-xl text-slate-400">Proof that good design isn't about adding features, it's about removing friction.</p>
                </div>

                <div class="space-y-12">
                    <div class="reveal-item flex flex-col md:flex-row bg-zinc-950 rounded-2xl overflow-hidden shadow-[0_0_30px_rgba(0,0,0,0.8)] border border-white/5 transform hover:-translate-y-2 transition duration-500 hover:shadow-[0_0_40px_rgba(57,255,20,0.25)]">
                        <div class="md:w-1/2 p-6 md:p-12 flex flex-col justify-center order-2 md:order-1">
                            <span class="text-sm font-semibold uppercase tracking-widest mb-3 font-mono" style="color: var(--primary-token);">Web Design | Digital Rework</span>
                            <h3 class="text-3xl font-bold text-white mb-4">Dreamphase Travel</h3>
                            <p class="text-slate-400 mb-6 leading-relaxed">
                                Transforming a simple travel Q&A tool into a powerful B2B trip management platform.
                            </p>
                            <div class="flex flex-wrap gap-2 text-xs mb-8">
                                <span class="bg-white/5 text-slate-300 border border-white/10 px-3.5 py-1.5 rounded-full font-mono font-semibold transition hover:bg-white/10 hover:text-white hover:border-[#39FF14]/50 hover:shadow-[0_0_10px_rgba(57,255,20,0.2)]">User Research Mapping</span>
                                <span class="bg-white/5 text-slate-300 border border-white/10 px-3.5 py-1.5 rounded-full font-mono font-semibold transition hover:bg-white/10 hover:text-white hover:border-[#39FF14]/50 hover:shadow-[0_0_10px_rgba(57,255,20,0.2)]">Figma Systemization</span>
                                <span class="bg-white/5 text-slate-300 border border-white/10 px-3.5 py-1.5 rounded-full font-mono font-semibold transition hover:bg-white/10 hover:text-white hover:border-[#39FF14]/50 hover:shadow-[0_0_10px_rgba(57,255,20,0.2)]">Token Architecture</span>
                            </div>
                            <span class="font-semibold flex items-center group cursor-pointer transition" style="color: var(--primary-token);">
                                Case Study coming soon
                                <svg class="ml-2 w-4 h-4 transition-transform duration-300 group-hover:translate-x-2" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3"></path></svg>
                            </span>
                        </div>
                        <div class="md:w-1/2 bg-zinc-900 p-8 flex items-center justify-center order-1 md:order-2 project-image-wrapper">
                            <img src="Assets/Dreamphase Mockup.png" onerror="this.src='https://images.unsplash.com/photo-1488590528505-98d2b5aba04b?auto=format&fit=crop&w=800&q=80'" alt="Sleek Enterprise Dashboard on Desktop Monitor" class="rounded-lg shadow-[0_0_20px_rgba(0,0,0,0.9)] w-full h-auto object-cover border border-white/10">
                        </div>
                    </div>

                    <div class="reveal-item flex flex-col md:flex-row bg-zinc-950 rounded-2xl overflow-hidden shadow-[0_0_30px_rgba(0,0,0,0.8)] border border-white/5 transform hover:-translate-y-2 transition duration-500 hover:shadow-[0_0_40px_rgba(57,255,20,0.25)]">
                        <div class="md:w-1/2 bg-zinc-900 p-8 flex items-center justify-center project-image-wrapper">
                            <img src="Assets/Senku Mockup.png" onerror="this.src='https://images.unsplash.com/photo-1511671782779-c97d3d27a1d4?auto=format&fit=crop&w=800&q=80'" alt="Premium Mobile App interface showing design detailing" class="rounded-lg shadow-[0_0_20px_rgba(0,0,0,0.9)] w-full h-auto object-cover border border-white/10">
                        </div>
                        <div class="md:w-1/2 p-6 md:p-12 flex flex-col justify-center">
                            <span class="text-sm font-semibold uppercase tracking-widest mb-3 font-mono" style="color: var(--primary-token);">Mobile App | Music App</span>
                            <h3 class="text-3xl font-bold text-white mb-4">Senku Music App</h3>
                            <p class="text-slate-400 mb-6 leading-relaxed">
                                Senku is an expansive, next-generation music ecosystem built to handle massive functionality without the clutter. While packing robust, advanced streaming features—including real-time sync, deep library curation, and social sharing the core design challenge was keeping the interface light and effortless. By anchoring the complex architecture in intuitive user workflows, I built a high-fidelity interface that feels simple, usable, and deeply human. Every feature is exactly where the user instinctively expects it to be.
                            </p>
                            <div class="flex flex-wrap gap-2 text-xs mb-8">
                                <span class="bg-white/5 text-slate-300 border border-white/10 px-3.5 py-1.5 rounded-full font-mono font-semibold transition hover:bg-white/10 hover:text-white hover:border-[#39FF14]/50 hover:shadow-[0_0_10px_rgba(57,255,20,0.2)]">Self Structured</span>
                                <span class="bg-white/5 text-slate-300 border border-white/10 px-3.5 py-1.5 rounded-full font-mono font-semibold transition hover:bg-white/10 hover:text-white hover:border-[#39FF14]/50 hover:shadow-[0_0_10px_rgba(57,255,20,0.2)]">Integrated Features</span>
                                <span class="bg-white/5 text-slate-300 border border-white/10 px-3.5 py-1.5 rounded-full font-mono font-semibold transition hover:bg-white/10 hover:text-white hover:border-[#39FF14]/50 hover:shadow-[0_0_10px_rgba(57,255,20,0.2)]">User Experience Tested</span>
                            </div>
                            <span class="font-semibold flex items-center group cursor-pointer transition" style="color: var(--primary-token);">
                                Case Study coming soon
                                <svg class="ml-2 w-4 h-4 transition-transform duration-300 group-hover:translate-x-2" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3"></path></svg>
                            </span>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="about" class="py-16 md:py-24 bg-zinc-950 border-t border-b border-white/5 relative overflow-hidden">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
                <div class="text-center mb-16 reveal-item">
                    <span class="font-mono tracking-wider uppercase text-sm block mb-2 text-slate-500">Behind the Design</span>
                    <h2 class="text-4xl font-extrabold text-white mb-2">Jindo Roy</h2>
                    <p class="text-xl text-slate-400 max-w-2xl mx-auto">UI UX Designer | Web Designer | Graphic Designer</p>
                </div>

                <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 items-start">
                    <div class="lg:col-span-5 space-y-6">
                        <div class="glass-panel rounded-2xl p-6 border border-white/5 bg-zinc-950/80 relative overflow-hidden group reveal-item delay-100">
                            <div class="absolute -top-24 -left-24 w-48 h-48 rounded-full blur-3xl opacity-30 transition-all duration-700 group-hover:opacity-60 group-hover:scale-150" style="background-color: var(--primary-token);"></div>
                            
                            <div class="relative z-10">
                                <div class="aspect-[4/5] rounded-xl overflow-hidden border border-white/10 relative shadow-[0_0_30px_rgba(0,0,0,0.9)] transition-all duration-500 group-hover:scale-[1.02] group-hover:shadow-[0_0_40px_var(--primary-token-glow)]" style="border-color: var(--primary-token-glow);">
                                    <img src="Assets/jindoroyportfolio.jpeg" alt="Jindo Roy" class="w-full h-full object-cover object-center transition duration-700 group-hover:scale-110">
                                    <div class="absolute inset-0 bg-gradient-to-t from-black/90 via-black/20 to-transparent"></div>
                                    <div class="absolute bottom-4 left-4 right-4 transform transition-transform duration-500 group-hover:-translate-y-2">
                                        <h4 class="text-xl font-bold text-white">Jindo Roy</h4>
                                        <p class="text-xs font-semibold tracking-wider uppercase" style="color: var(--primary-token); text-shadow: 0 0 8px var(--primary-token-glow);">UI/UX Designer & Engineer</p>
                                    </div>
                                </div>
                                
                                <div class="grid grid-cols-2 gap-3 mt-6 text-center text-xs">
                                    <div class="p-3 rounded-lg bg-white/5 border border-white/5 transition hover:bg-white/10 hover:-translate-y-1 hover:shadow-[0_0_15px_rgba(57,255,20,0.15)] hover:border-[#39FF14]/30">
                                        <span class="block text-xl font-bold text-white">5+ mths</span>
                                        <span class="text-slate-400">Design Experience</span>
                                    </div>
                                    <div class="p-3 rounded-lg bg-white/5 border border-white/5 transition hover:bg-white/10 hover:-translate-y-1 hover:shadow-[0_0_15px_rgba(57,255,20,0.15)] hover:border-[#39FF14]/30">
                                        <span class="block text-xl font-bold text-white">CS Grad</span>
                                        <span class="text-slate-400">B.Tech Engineering</span>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <div class="glass-panel rounded-2xl p-6 border border-white/5 bg-zinc-950/80 reveal-item delay-200">
                            <h4 class="text-lg font-bold text-white mb-4">Core Leadership</h4>
                            <ul class="space-y-4">
                                <li class="flex gap-3 items-center group">
                                    <div class="w-10 h-10 rounded-lg bg-white/5 border border-white/10 flex items-center justify-center flex-shrink-0 transition-transform duration-300 group-hover:scale-110 group-hover:border-[#39FF14]/50 group-hover:shadow-[0_0_10px_var(--primary-token-glow)]">
                                        <svg class="w-5 h-5 text-[#39FF14]" style="color: var(--primary-token);" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4.354a4 4 0 110 5.292M15 21H3v-1a6 6 0 0112 0v1zm0 0h6v-1a6 6 0 00-9-5.197M13 7a4 4 0 11-8 0 4 4 0 018 0z"></path></svg>
                                    </div>
                                    <div>
                                        <h5 class="font-bold text-white text-sm transition-colors group-hover:text-[#39FF14]">IEEE Design Team Lead</h5>
                                        <p class="text-xs text-slate-400">Mentored 200+ technology and engineering students across Kerala.</p>
                                    </div>
                                </li>
                                <li class="flex gap-3 items-center group">
                                    <div class="w-10 h-10 rounded-lg bg-white/5 border border-white/10 flex items-center justify-center flex-shrink-0 transition-transform duration-300 group-hover:scale-110 group-hover:border-[#39FF14]/50 group-hover:shadow-[0_0_10px_var(--primary-token-glow)]">
                                        <svg class="w-5 h-5 text-[#39FF14]" style="color: var(--primary-token);" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M11.049 2.927c.3-.921 1.603-.921 1.902 0l1.519 4.674a1 1 0 00.95.69h4.915c.969 0 1.371 1.24.588 1.81l-3.976 2.888a1 1 0 00-.363 1.118l1.518 4.674c.3.922-.755 1.688-1.538 1.118l-3.976-2.888a1 1 0 00-1.176 0l-3.976 2.888c-.783.57-1.838-.197-1.538-1.118l1.518-4.674a1 1 0 00-.363-1.118l-3.976-2.888c-.784-.57-.38-1.81.588-1.81h4.914a1 1 0 00.951-.69l1.519-4.674z"></path></svg>
                                    </div>
                                    <div>
                                        <h5 class="font-bold text-white text-sm transition-colors group-hover:text-[#39FF14]">NSS Design Lead</h5>
                                        <p class="text-xs text-slate-400">Organized visual programs for 2 years.</p>
                                    </div>
                                </li>
                            </ul>
                        </div>
                    </div>

                    <div class="lg:col-span-7 space-y-6 text-slate-300 text-base md:text-lg leading-relaxed reveal-item delay-300">
                        <h3 class="text-2xl font-bold text-white mb-2">Bridging Aesthetic Innovation with Structural Logic</h3>
                        <p>
                            Dynamic Computer Science Graduate and multidisciplinary designer dedicated to bridging the gap between technical logic and intuitive user experiences. With a specialized mastery of Figma, Photoshop, and Illustration, I possess a unique dual-lens perspective that allows me to build innovative, high-fidelity projects from the ground up. I am a rapidly adaptive problem-solver and a lifelong student of technology, recognized for delivering efficient, high-impact solutions in fast-paced environments. Driven by a deep-seated passion for computational problem-solving, I thrive at the intersection of aesthetic design and functional engineering to create digital products that matter.
                        </p>
                        <div class="pt-6 space-y-6">
                            <h4 class="text-lg font-bold uppercase tracking-wider text-white border-b border-white/10 pb-2">Academic & Professional Journey</h4>
                            <div class="relative border-l border-white/10 pl-6 ml-3 space-y-6">
                                <div class="relative group">
                                    <div class="absolute -left-9 top-1.5 w-6 h-6 rounded-full bg-black border-2 border-[#39FF14] flex items-center justify-center transition-transform duration-300 group-hover:scale-125 group-hover:shadow-[0_0_15px_#39FF14]" style="border-color: var(--primary-token);">
                                        <div class="w-2 h-2 rounded-full bg-[#39FF14] transition-opacity duration-300 group-hover:opacity-80" style="background-color: var(--primary-token);"></div>
                                    </div>
                                    <span class="font-mono text-xs font-semibold text-slate-500">May 2025 - November 2025</span>
                                    <h5 class="font-bold text-white transition-colors duration-300 group-hover:text-[#39FF14]">UI/UX Designer — Senku Music App</h5>
                                    <p class="text-sm text-slate-400 mt-1 transition-all duration-300 group-hover:text-slate-300">
                                        Senku is a massive, all-in-one music platform designed to balance high-density features like complex playlist management, live social listening, and AI discovery algorithms with a lightweight, frictionless visual footprint. As the designer, I translated this technical depth into a highly polished, responsive interface that turns a feature-heavy ecosystem into an effortless, intuitive listening experience.
                                    </p>
                                </div>
                                <div class="relative group">
                                    <div class="absolute -left-9 top-1.5 w-6 h-6 rounded-full bg-black border-2 border-[#39FF14] flex items-center justify-center transition-transform duration-300 group-hover:scale-125 group-hover:shadow-[0_0_15px_#39FF14]" style="border-color: var(--primary-token);">
                                        <div class="w-2 h-2 rounded-full bg-[#39FF14] transition-opacity duration-300 group-hover:opacity-80" style="background-color: var(--primary-token);"></div>
                                    </div>
                                    <span class="font-mono text-xs font-semibold text-slate-500">May 2025 - November 2025</span>
                                    <h5 class="font-bold text-white transition-colors duration-300 group-hover:text-[#39FF14]">UI/UX Designer — Dreamphase Travel and Tours</h5>
                                    <p class="text-sm text-slate-400 mt-1 transition-all duration-300 group-hover:text-slate-300">
                                        I designed a end-to-end design for a multi-portal travel ecosystem, conceptualizing the entire UI from scratch. I engineered tailored UX architectures and design systems for customers, staff, and B2B agents, translating complex insurance, flight, and visa workflows into simple, intuitive user journeys. To ensure a cohesive brand aesthetic, I also developed all custom visual assets, icons, and high-fidelity mockups.
                                    </p>
                                </div>
                                <div class="relative group">
                                    <div class="absolute -left-9 top-1.5 w-6 h-6 rounded-full bg-black border-2 border-[#39FF14] flex items-center justify-center transition-transform duration-300 group-hover:scale-125 group-hover:shadow-[0_0_15px_#39FF14]" style="border-color: var(--primary-token);">
                                        <div class="w-2 h-2 rounded-full bg-[#39FF14] transition-opacity duration-300 group-hover:opacity-80" style="background-color: var(--primary-token);"></div>
                                    </div>
                                    <span class="font-mono text-xs font-semibold text-slate-500">June 2024 - January 2025</span>
                                    <h5 class="font-bold text-white transition-colors duration-300 group-hover:text-[#39FF14]">UI/UX Designer | MENT APP</h5>
                                    <p class="text-sm text-slate-400 mt-1 transition-all duration-300 group-hover:text-slate-300">
                                        For a college project, I designed the end-to-end UI/UX for an AI-driven mentorship platform, creating custom, multi-user interfaces for students, mentors, and administrators. I focused on translating complex emotional intelligence data into simple, human features architecting interactive workflows for real-time chat with emotional insights, daily mood journaling, and task tracking, all while ensuring high-speed responsiveness and effortless navigation.
                                    </p>
                                </div>
                                <div class="relative group">
                                    <div class="absolute -left-9 top-1.5 w-6 h-6 rounded-full bg-black border-2 border-[#39FF14] flex items-center justify-center transition-transform duration-300 group-hover:scale-125 group-hover:shadow-[0_0_15px_#39FF14]" style="border-color: var(--primary-token);">
                                        <div class="w-2 h-2 rounded-full bg-[#39FF14] transition-opacity duration-300 group-hover:opacity-80" style="background-color: var(--primary-token);"></div>
                                    </div>
                                    <span class="font-mono text-xs font-semibold text-slate-500">March 2023 - June 2024</span>
                                    <h5 class="font-bold text-white transition-colors duration-300 group-hover:text-[#39FF14]">Web App | CAREER-CONNECT</h5>
                                    <p class="text-sm text-slate-400 mt-1 transition-all duration-300 group-hover:text-slate-300">
                                        For a college project, I led the full UI/UX design phase for a centralized college placement web application, creating custom, responsive interfaces for students, administrators, and recruiters following Material Design principles. Bridging technical logic with design, I mapped user journeys using detailed system blueprints and UML charts to build intuitive workflows for job searching, resume building, and profile management, all optimized for fast registration and effortless navigation.
                                    </p>
                                </div>
                                <div class="relative group">
                                    <div class="absolute -left-9 top-1.5 w-6 h-6 rounded-full bg-black border-2 border-[#39FF14] flex items-center justify-center transition-transform duration-300 group-hover:scale-125 group-hover:shadow-[0_0_15px_#39FF14]" style="border-color: var(--primary-token);">
                                        <div class="w-2 h-2 rounded-full bg-[#39FF14] transition-opacity duration-300 group-hover:opacity-80" style="background-color: var(--primary-token);"></div>
                                    </div>
                                    <span class="font-mono text-xs font-semibold text-slate-500">2021 – 2025</span>
                                    <h5 class="font-bold text-white transition-colors duration-300 group-hover:text-[#39FF14]">B.Tech in Computer Science & Engineering</h5>
                                    <p class="text-sm text-slate-400 mt-1 transition-all duration-300 group-hover:text-slate-300">
                                        APJ Abdul Kalam Technological University. Built a robust foundation in software design architectures and database logic.
                                    </p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="skills" class="py-16 md:py-24 bg-black border-b border-white/5 relative overflow-hidden">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
                <div class="text-center mb-16 reveal-item">
                    <span class="font-mono tracking-wider uppercase text-sm block mb-2 text-slate-500">Expertise Ecosystem</span>
                    <h2 class="text-4xl font-extrabold text-white mb-2">Skills & Design System</h2>
                    <p class="text-xl text-slate-400 max-w-3xl mx-auto">Explore categorized architectural skills and modern tools driving my process.</p>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-3 gap-8 mb-20">
                    <div class="p-6 rounded-xl bg-zinc-950 border border-white/5 transition-all duration-500 hover:-translate-y-2 hover:shadow-[0_0_30px_rgba(57,255,20,0.25)] hover:border-[#39FF14]/30 reveal-item delay-100">
                        <h4 class="text-lg font-bold text-white mb-4 flex items-center gap-2">
                            <span class="w-2 h-2 rounded-full bg-[#39FF14] animate-pulse"></span> Design Tools
                        </h4>
                        <ul class="space-y-2.5 text-sm text-slate-400 font-mono">
                            <li class="flex justify-between border-b border-white/5 pb-2 transition-colors hover:text-white"><span>Figma (Advanced)</span> <span class="text-[#39FF14]">95%</span></li>
                            <li class="flex justify-between border-b border-white/5 pb-2 transition-colors hover:text-white"><span>Adobe Photoshop</span> <span class="text-[#39FF14]">90%</span></li>
                            <li class="flex justify-between border-b border-white/5 pb-2 transition-colors hover:text-white"><span>Adobe Illustrator</span> <span class="text-[#39FF14]">85%</span></li>
                            <li class="flex justify-between transition-colors hover:text-white"><span>Canva</span> <span class="text-[#39FF14]">95%</span></li>
                        </ul>
                    </div>

                    <div class="p-6 rounded-xl bg-zinc-950 border border-white/5 transition-all duration-500 hover:-translate-y-2 hover:shadow-[0_0_30px_rgba(57,255,20,0.25)] hover:border-[#39FF14]/30 reveal-item delay-200">
                        <h4 class="text-lg font-bold text-white mb-4 flex items-center gap-2">
                            <span class="w-2 h-2 rounded-full bg-[#39FF14] animate-pulse" style="animation-delay: 200ms;"></span> Frameworks
                        </h4>
                        <ul class="space-y-2.5 text-sm text-slate-400 font-mono">
                            <li class="flex justify-between border-b border-white/5 pb-2 transition-colors hover:text-white"><span>Design Thinking</span> <span class="text-[#39FF14]">Active</span></li>
                            <li class="flex justify-between border-b border-white/5 pb-2 transition-colors hover:text-white"><span>Atomic Systems</span> <span class="text-[#39FF14]">Active</span></li>
                            <li class="flex justify-between border-b border-white/5 pb-2 transition-colors hover:text-white"><span>User-Centered</span> <span class="text-[#39FF14]">Active</span></li>
                            <li class="flex justify-between transition-colors hover:text-white"><span>Rapid Wireframing</span> <span class="text-[#39FF14]">Active</span></li>
                        </ul>
                    </div>

                    <div class="p-6 rounded-xl bg-zinc-950 border border-white/5 transition-all duration-500 hover:-translate-y-2 hover:shadow-[0_0_30px_rgba(57,255,20,0.25)] hover:border-[#39FF14]/30 reveal-item delay-300">
                        <h4 class="text-lg font-bold text-white mb-4 flex items-center gap-2">
                            <span class="w-2 h-2 rounded-full bg-[#39FF14] animate-pulse" style="animation-delay: 400ms;"></span> Collaboration
                        </h4>
                        <ul class="space-y-2.5 text-sm text-slate-400 font-mono">
                            <li class="flex justify-between border-b border-white/5 pb-2 transition-colors hover:text-white"><span>GitHub</span> <span class="text-[#39FF14]">Ready</span></li>
                            <li class="flex justify-between border-b border-white/5 pb-2 transition-colors hover:text-white"><span>Notion / Docs</span> <span class="text-[#39FF14]">Ready</span></li>
                            <li class="flex justify-between border-b border-white/5 pb-2 transition-colors hover:text-white"><span>VS Code</span> <span class="text-[#39FF14]">Ready</span></li>
                            <li class="flex justify-between transition-colors hover:text-white"><span>Jira Handoff</span> <span class="text-[#39FF14]">Ready</span></li>
                        </ul>
                    </div>
                </div>
            </div>
        </section>

        <section id="contact" class="py-20 md:py-28 bg-black relative overflow-hidden">
            <div class="absolute -top-40 -left-40 w-96 h-96 rounded-full blur-3xl pointer-events-none opacity-20" style="background-color: var(--primary-token-glow);"></div>
            <div class="absolute -bottom-40 -right-40 w-96 h-96 rounded-full blur-3xl pointer-events-none opacity-20" style="background-color: var(--primary-token-glow);"></div>
            
            <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 text-center relative z-10 reveal-item">
                <h2 class="text-4xl sm:text-5xl font-extrabold text-white mb-4">Let's Build the Next Great Experience.</h2>
                <p class="text-xl text-slate-400 mb-12 max-w-xl mx-auto">
                    I'm always open to discussing new projects, creative ideas, or opportunities to be part of your vision.
                </p>

                <div class="grid grid-cols-2 md:grid-cols-4 gap-6 max-w-4xl mx-auto mt-6">
                    <a href="https://wa.me/918330869609" target="_blank" rel="noopener noreferrer" class="group relative flex flex-col items-center justify-center p-8 rounded-2xl bg-zinc-950 border border-white/5 transition-all duration-300 hover:border-[var(--primary-token)] hover:-translate-y-2 hover:shadow-[0_0_30px_var(--primary-token-glow)] reveal-item delay-100" style="aspect-ratio: 1/1;">
                        <svg class="w-12 h-12 mb-4 transition duration-300 group-hover:scale-110 group-hover:drop-shadow-[0_0_8px_var(--primary-token)]" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="color: var(--primary-token);">
                            <path d="M21 11.5a8.38 8.38 0 0 1-.9 3.8 8.5 8.5 0 0 1-7.6 4.7 8.38 8.38 0 0 1-3.8-.9L3 21l1.9-5.7a8.38 8.38 0 0 1-.9-3.8 8.5 8.5 0 0 1 4.7-7.6 8.38 8.38 0 0 1 3.8-.9h.5a8.48 8.48 0 0 1 8 8v.5z" />
                            <g transform="translate(1.2, 0.8)">
                                <path d="M15.05 13.5c-.4.5-1 .7-1.6.5-1-.3-2.5-1.2-3.4-2.1-.9-.9-1.8-2.4-2.1-3.4-.2-.6 0-1.2.5-1.6l.6-.6c.3-.3.8-.3 1.1 0l1.2 1.2c.3.3.3.8 0 1.1l-.3.3c.4.8 1.1 1.5 1.9 1.9l.3-.3c.3-.3.8-.3 1.1 0l1.2 1.2c.3.3.3.8 0 1.1l-.6.6z" />
                            </g>
                        </svg>
                        <span class="text-white text-base font-medium tracking-wide">Chat</span>
                    </a>

                    <a href="https://mail.google.com/mail/?view=cm&fs=1&to=jindoroy1@gmail.com" target="_blank" rel="noopener noreferrer" class="group relative flex flex-col items-center justify-center p-8 rounded-2xl bg-zinc-950 border border-white/5 transition-all duration-300 hover:border-[var(--primary-token)] hover:-translate-y-2 hover:shadow-[0_0_30px_var(--primary-token-glow)] reveal-item delay-200" style="aspect-ratio: 1/1;">
                        <svg class="w-12 h-12 mb-4 transition duration-300 group-hover:scale-110 group-hover:drop-shadow-[0_0_8px_var(--primary-token)]" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="color: var(--primary-token);">
                            <rect x="2" y="4" width="20" height="16" rx="4" />
                            <path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7" />
                        </svg>
                        <span class="text-white text-base font-medium tracking-wide">Email</span>
                    </a>

                    <a href="https://www.linkedin.com/in/jindo-roy-114736227/" target="_blank" rel="noopener noreferrer" class="group relative flex flex-col items-center justify-center p-8 rounded-2xl bg-zinc-950 border border-white/5 transition-all duration-300 hover:border-[var(--primary-token)] hover:-translate-y-2 hover:shadow-[0_0_30px_var(--primary-token-glow)] reveal-item delay-300" style="aspect-ratio: 1/1;">
                        <svg class="w-12 h-12 mb-4 transition duration-300 group-hover:scale-110 group-hover:drop-shadow-[0_0_8px_var(--primary-token)]" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="color: var(--primary-token);">
                            <path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z" />
                            <rect x="2" y="9" width="4" height="12" />
                            <circle cx="4" cy="4" r="2" />
                        </svg>
                        <span class="text-white text-base font-medium tracking-wide">LinkedIn</span>
                    </a>

                    <a href="https://www.behance.net/jindoroy1" target="_blank" rel="noopener noreferrer" class="group relative flex flex-col items-center justify-center p-8 rounded-2xl bg-zinc-950 border border-white/5 transition-all duration-300 hover:border-[var(--primary-token)] hover:-translate-y-2 hover:shadow-[0_0_30px_var(--primary-token-glow)] reveal-item delay-400" style="aspect-ratio: 1/1;">
                        <svg class="w-12 h-12 mb-4 transition duration-300 group-hover:scale-110 group-hover:drop-shadow-[0_0_8px_var(--primary-token)]" viewBox="0 0 24 24" fill="currentColor" style="color: var(--primary-token);">
                            <path d="M8.2 5H4v14h4.5c2.3 0 4.1-1.5 4.1-3.7 0-1.6-1.1-2.8-2.6-3.2 1.2-.5 2-1.6 2-3 0-2.3-1.6-4.1-3.8-4.1zm-2.2 2.5h1.9c1 0 1.7.6 1.7 1.5s-.7 1.5-1.7 1.5h-1.9v-3zm0 5.5h2.2c1.1 0 1.8.7 1.8 1.7s-.7 1.7-1.8 1.7H6v-3.4z"/>
                            <path d="M17.5 10c-2.3 0-3.9 1.6-3.9 4s1.6 4 3.9 4c2.2 0 3.6-1.3 3.8-3.1h-2.2c-.2.7-.8 1.1-1.6 1.1s-1.5-.6-1.6-1.7h5.6c0-2.5-1.5-4.3-4-4.3zm-1.6 2.6c.1-1 .7-1.5 1.6-1.5s1.4.5 1.5 1.5h-3.1z"/>
                            <rect x="14.5" y="7.5" width="6" height="1.5" />
                        </svg>
                        <span class="text-white text-base font-medium tracking-wide">Portfolio</span>
                    </a>
                </div>
            </div>
        </section>
    </main>

    <footer class="bg-zinc-950 border-t border-white/5 py-10 relative z-10">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center flex flex-col sm:flex-row sm:justify-between sm:items-center gap-4">
            <p class="text-slate-500 text-sm">&copy; 2026 <span class="text-white font-medium">Jindo</span><span class="font-medium" style="color: var(--primary-token); text-shadow: 0 0 5px var(--primary-token-glow);">Roy</span>. All rights reserved.</p>
            <p class="text-slate-600 text-xs font-mono">Simplicity by design. Human by instinct.</p>
        </div>
    </footer>

    <div style="position: absolute; left: -9999px; top: -9999px;">
        <div id="resumeTemplate" style="width: 794px; padding: 50px; background: #ffffff; color: #0f172a; font-family: 'Inter', sans-serif; line-height: 1.5; font-size: 13px;">
            <div style="border-bottom: 2px solid #0f172a; padding-bottom: 15px; margin-bottom: 20px;">
                <h1 style="font-size: 32px; font-weight: 900; color: #0f172a; margin: 0 0 5px 0; letter-spacing: -0.05em;">JINDO ROY</h1>
                <div style="font-size: 12px; color: #475569; font-weight: 500; display: flex; flex-wrap: wrap; gap: 15px; margin-bottom: 10px;">
                    <span>📞 +91 8330869609</span>
                    <span>✉️ jindoroy1@gmail.com</span>
                    <span>🔗 linkedin.com/in/Jindo Roy</span>
                    <span>💻 github.com/Jindo Roy</span>
                </div>
            </div>

            <div style="margin-bottom: 25px;">
                <p style="margin: 0; color: #334155; font-size: 13px; text-align: justify; font-weight: 400;">
                    Dynamic Computer Science Graduate and multidisciplinary designer dedicated to bridging the gap between technical logic and intuitive user experiences. With a specialized mastery of Figma, Photoshop, and Illustration, I possess a unique dual-lens perspective that allows me to build innovative, high-fidelity projects from the ground up. I am a rapidly adaptive problem-solver and a lifelong student of technology, recognized for delivering efficient, high-impact solutions in fast-paced environments. Driven by a deep-seated passion for computational problem-solving, I thrive at the intersection of aesthetic design and functional engineering to create digital products that matter.
                </p>
            </div>

            <div style="margin-bottom: 25px;">
                <h2 style="font-size: 14px; font-weight: 800; color: #0f172a; margin: 0 0 10px 0; border-bottom: 1px solid #e2e8f0; padding-bottom: 4px; text-transform: uppercase; letter-spacing: 0.05em;">Education</h2>
                <div style="display: flex; justify-content: space-between; align-items: baseline; margin-bottom: 3px;">
                    <strong style="color: #0f172a; font-size: 13px;">APJ Abdul Kalam Technological University</strong>
                    <span style="color: #475569; font-size: 12px; font-weight: 500;">Kozhikode, Kerala</span>
                </div>
                <div style="display: flex; justify-content: space-between; align-items: baseline;">
                    <span style="color: #475569; font-style: italic;">B.Tech in Computer Science and Engineering</span>
                    <span style="color: #475569; font-size: 12px; font-weight: 500;">May 2025</span>
                </div>
            </div>

            <div style="margin-bottom: 25px;">
                <h2 style="font-size: 14px; font-weight: 800; color: #0f172a; margin: 0 0 10px 0; border-bottom: 1px solid #e2e8f0; padding-bottom: 4px; text-transform: uppercase; letter-spacing: 0.05em;">Experience</h2>
                <div style="display: flex; justify-content: space-between; align-items: baseline; margin-bottom: 3px;">
                    <strong style="color: #0f172a; font-size: 13px;">Dreamphase Travel and Tours</strong>
                    <span style="color: #475569; font-size: 12px; font-weight: 500;">Thiruvananthapuram, Kerala</span>
                </div>
                <div style="display: flex; justify-content: space-between; align-items: baseline; margin-bottom: 8px;">
                    <span style="color: #475569; font-style: italic; font-weight: 500;">UI UX Designer</span>
                    <span style="color: #475569; font-size: 12px; font-weight: 500;">November 2021 – October 2025</span>
                </div>
                <ul style="margin: 0; padding-left: 18px; color: #334155; font-size: 12.5px;">
                    <li style="margin-bottom: 5px;"><strong>End-to-End Product Design:</strong> Conceptualized and executed the entire UI from scratch.</li>
                    <li style="margin-bottom: 5px;"><strong>Intuitive User Journeys:</strong> Designed seamless interfaces for Insurance, Flight Bookings, Visa Booking, and Separate Travel Mart prioritizing clarity to simplify complex travel experiences.</li>
                    <li style="margin-bottom: 5px;"><strong>Multi-Portal Design System:</strong> Engineered tailored UX architectures for Customers, Staff, and B2B Agents to ensure efficient role-based navigation.</li>
                    <li style="margin-bottom: 5px;"><strong>Custom Visual Assets:</strong> Developed all original icons, illustrations, and high-fidelity mockups using Photoshop and Illustrator for a cohesive brand aesthetic.</li>
                </ul>
            </div>

            <div style="margin-bottom: 25px;">
                <h2 style="font-size: 14px; font-weight: 800; color: #0f172a; margin: 0 0 10px 0; border-bottom: 1px solid #e2e8f0; padding-bottom: 4px; text-transform: uppercase; letter-spacing: 0.05em;">Projects</h2>
                
                <div style="margin-bottom: 12px;">
                    <div style="display: flex; justify-content: space-between; align-items: baseline; margin-bottom: 4px;">
                        <strong style="color: #0f172a; font-size: 13px;">CAREER-CONNECT | <span style="font-weight: 500; font-size: 11px; color: #475569;">Figma, Material Design, Adobe Suite, User Research</span></strong>
                        <span style="color: #475569; font-size: 12px; font-weight: 500;">March 2023 – June 2024</span>
                    </div>
                    <ul style="margin: 0; padding-left: 18px; color: #334155; font-size: 12.5px;">
                        <li style="margin-bottom: 3px;">Led the full UI/UX design phase for a centralized college placement web application.</li>
                        <li style="margin-bottom: 3px;">Designed custom interfaces for students, administrators, and company recruiters.</li>
                        <li style="margin-bottom: 3px;">Created detailed system blueprints including Data Flow Diagrams and UML charts to map the user journey.</li>
                        <li style="margin-bottom: 3px;">Developed high-fidelity wireframes following Material Design principles for a clean, responsive layout.</li>
                    </ul>
                </div>

                <div>
                    <div style="display: flex; justify-content: space-between; align-items: baseline; margin-bottom: 4px;">
                        <strong style="color: #0f172a; font-size: 13px;">MENT APP | <span style="font-weight: 500; font-size: 11px; color: #475569;">Figma, AI-Driven UX, Sentiment Analysis, User Research</span></strong>
                        <span style="color: #475569; font-size: 12px; font-weight: 500;">June 2024 – January 2025</span>
                    </div>
                    <ul style="margin: 0; padding-left: 18px; color: #334155; font-size: 12.5px;">
                        <li style="margin-bottom: 3px;">Designed the UI/UX for an AI mentorship app using emotional intelligence to guide users.</li>
                        <li style="margin-bottom: 3px;">Created custom interfaces for students, mentors, and administrators.</li>
                        <li style="margin-bottom: 3px;">Designed interactive workflows for real-time chat and video calls with emotional insights.</li>
                        <li style="margin-bottom: 3px;">Architected growth features like daily mood journaling, motivational modules, and task tracking.</li>
                    </ul>
                </div>
            </div>

            <div style="margin-bottom: 25px;">
                <h2 style="font-size: 14px; font-weight: 800; color: #0f172a; margin: 0 0 10px 0; border-bottom: 1px solid #e2e8f0; padding-bottom: 4px; text-transform: uppercase; letter-spacing: 0.05em;">Technical Skills</h2>
                <div style="color: #334155; font-size: 12.5px;">
                    <div style="margin-bottom: 4px;"><strong style="color: #0f172a;">Design Tools:</strong> Figma (Advanced), Adobe Photoshop, Adobe Illustrator, Canva</div>
                    <div style="margin-bottom: 4px;"><strong style="color: #0f172a;">Design Frameworks:</strong> Design Thinking, Atomic Design Systems, User-Centered Design, Wireframing, Prototyping</div>
                    <div style="margin-bottom: 4px;"><strong style="color: #0f172a;">Web Technologies:</strong> Web3 Interface Design, Responsive Web Design, UI Components, Libraries</div>
                    <div><strong style="color: #0f172a;">Developer Collaboration:</strong> Git (Version Control), Notion, VS Code, Jira (Handoff Process)</div>
                </div>
            </div>

            <div>
                <h2 style="font-size: 14px; font-weight: 800; color: #0f172a; margin: 0 0 10px 0; border-bottom: 1px solid #e2e8f0; padding-bottom: 4px; text-transform: uppercase; letter-spacing: 0.05em;">Achievements</h2>
                <ul style="margin: 0; padding-left: 18px; color: #334155; font-size: 12.5px;">
                    <li style="margin-bottom: 3px;">Mentored 200+ students in Kerala as an IEEE Design Team lead.</li>
                    <li style="margin-bottom: 3px;">IEEE Malabar Hub design team member.</li>
                    <li style="margin-bottom: 3px;">NSS Design Team lead for 2 years.</li>
                    <li style="margin-bottom: 3px;">Represented in the National Integration Camp in 2023.</li>
                </ul>
            </div>
        </div>
    </div>

    <script>
        // Color converter to clean RGBA formatted string
        function hexToRgba(hex, alpha) {
            let c = hex.substring(1);
            let rgb = parseInt(c, 16);
            let r = (rgb >> 16) & 0xff;
            let g = (rgb >> 8) & 0xff;
            let b = (rgb >> 0) & 0xff;
            return `rgba(${r}, ${g}, ${b}, ${alpha})`;
        }

        function isLight(hex) {
            const c = hex.substring(1);
            const rgb = parseInt(c, 16);
            const r = (rgb >> 16) & 0xff;
            const g = (rgb >> 8) & 0xff;
            const b = (rgb >> 0) & 0xff;
            const luma = 0.2126 * r + 0.7152 * g + 0.0722 * b; 
            return luma > 165; 
        }

        // Dynamic status mapping function updating theme targets programmatically
        function updateDemoColor(newColor) {
            const root = document.documentElement;
            root.style.setProperty('--primary-token', newColor);
            root.style.setProperty('--primary-token-glow', hexToRgba(newColor, 0.25));
            root.style.setProperty('--primary-token-glow-hover', hexToRgba(newColor, 0.65));
            
            const textColor = isLight(newColor) ? '#000000' : '#ffffff';
            root.style.setProperty('--primary-token-text', textColor);
            
            if (window.bgNetwork) {
                window.bgNetwork.updateParticleColor(newColor);
            }
        }

        updateDemoColor('#39FF14');

        // High-performance canvas interactive particle network configuration
        class InteractiveNetworkBg {
            constructor(canvasId, defaultColorHex) {
                this.canvas = document.getElementById(canvasId);
                this.ctx = this.canvas.getContext('2d', { alpha: false }); // Optimized context
                this.particles = [];
                this.currentColor = defaultColorHex;
                
                this.mouse = { x: 0, y: 0, targetX: null, targetY: null, radiusSq: 24025 }; // 155^2
                this.maxParticles = 80;

                this.scrollVelocityBoost = 0;
                this.scrollVelocityTarget = 0;
                this.lastScrollY = window.scrollY;

                this.init();
                this.animate();

                window.addEventListener('resize', () => this.resizeCanvas());
                window.addEventListener('mousemove', (e) => this.handleMouseMove(e), { passive: true });
                window.addEventListener('mouseout', () => this.handleMouseOut());
                window.addEventListener('touchstart', (e) => this.handleTouch(e), { passive: true });
                window.addEventListener('touchmove', (e) => this.handleTouch(e), { passive: true });
                window.addEventListener('touchend', () => this.handleMouseOut());
            }

            init() {
                this.resizeCanvas();
                this.createParticles();
            }

            resizeCanvas() {
                this.canvas.width = window.innerWidth;
                this.canvas.height = window.innerHeight;
                if (this.particles.length > 0) this.draw();
            }

            createParticles() {
                this.particles = [];
                for (let i = 0; i < this.maxParticles; i++) {
                    const size = Math.random() * 2 + 1;
                    const x = Math.random() * (this.canvas.width - size * 2) + size;
                    const y = Math.random() * (this.canvas.height - size * 2) + size;
                    const directionX = (Math.random() * 0.4) - 0.2;
                    const directionY = (Math.random() * 0.4) - 0.2;
                    this.particles.push({ x, y, directionX, directionY, size });
                }
            }

            handleMouseMove(event) {
                this.mouse.targetX = event.clientX;
                this.mouse.targetY = event.clientY;
            }

            handleTouch(event) {
                if (event.touches && event.touches.length > 0) {
                    this.mouse.targetX = event.touches[0].clientX;
                    this.mouse.targetY = event.touches[0].clientY;
                }
            }

            handleMouseOut() {
                this.mouse.targetX = null;
                this.mouse.targetY = null;
            }

            updateParticleColor(hexColor) {
                this.currentColor = hexColor;
            }

            handleScrollBoost(scrollY) {
                const scrollDelta = Math.abs(scrollY - this.lastScrollY);
                this.scrollVelocityTarget = Math.min(this.scrollVelocityTarget + scrollDelta * 0.08, 15);
                this.lastScrollY = scrollY;
            }

            draw() {
                // Clear using a solid fill for alpha: false optimization
                this.ctx.fillStyle = '#000000';
                this.ctx.fillRect(0, 0, this.canvas.width, this.canvas.height);

                if (this.mouse.targetX !== null && this.mouse.targetY !== null) {
                    if (this.mouse.x === 0 && this.mouse.y === 0) {
                        this.mouse.x = this.mouse.targetX;
                        this.mouse.y = this.mouse.targetY;
                    } else {
                        this.mouse.x += (this.mouse.targetX - this.mouse.x) * 0.08;
                        this.mouse.y += (this.mouse.targetY - this.mouse.y) * 0.08;
                    }
                } else {
                    this.mouse.x += (0 - this.mouse.x) * 0.1;
                    this.mouse.y += (0 - this.mouse.y) * 0.1;
                }

                this.scrollVelocityBoost += (this.scrollVelocityTarget - this.scrollVelocityBoost) * 0.08;
                this.scrollVelocityTarget *= 0.92; 

                this.ctx.fillStyle = hexToRgba(this.currentColor, 0.8);

                for (let i = 0; i < this.particles.length; i++) {
                    let p = this.particles[i];

                    p.x += p.directionX * (1 + this.scrollVelocityBoost);
                    p.y += (p.directionY * (1 + this.scrollVelocityBoost)) + (this.scrollVelocityBoost * 0.05);

                    if (p.x > this.canvas.width || p.x < 0) p.directionX = -p.directionX;
                    if (p.y > this.canvas.height || p.y < 0) p.directionY = -p.directionY;

                    if (this.mouse.targetX !== null && this.mouse.targetY !== null) {
                        let dx = p.x - this.mouse.x;
                        let dy = p.y - this.mouse.y;
                        let distSq = dx * dx + dy * dy; // Optimized: Avoid sqrt where possible
                        
                        if (distSq < this.mouse.radiusSq) {
                            let distance = Math.sqrt(distSq);
                            let force = (155 - distance) / 155; // 155 is mouse.radius
                            p.x += (dx / distance) * force * 2.5;
                            p.y += (dy / distance) * force * 2.5;
                        }
                    }

                    this.ctx.beginPath();
                    this.ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2, false);
                    this.ctx.fill();
                }

                this.ctx.lineWidth = 1;
                const connectionRadiusSq = 12100; // 110^2

                for (let a = 0; a < this.particles.length; a++) {
                    for (let b = a + 1; b < this.particles.length; b++) {
                        let dx = this.particles[a].x - this.particles[b].x;
                        let dy = this.particles[a].y - this.particles[b].y;
                        let distSq = dx * dx + dy * dy;

                        // Optimized: check squared distance before costly sqrt
                        if (distSq < connectionRadiusSq) {
                            let distance = Math.sqrt(distSq);
                            let opacityValue = (1 - (distance / 110)) * 0.12;
                            this.ctx.strokeStyle = hexToRgba(this.currentColor, opacityValue);
                            this.ctx.beginPath();
                            this.ctx.moveTo(this.particles[a].x, this.particles[a].y);
                            this.ctx.lineTo(this.particles[b].x, this.particles[b].y);
                            this.ctx.stroke();
                        }
                    }
                }
            }

            animate() {
                this.draw();
                requestAnimationFrame(() => this.animate());
            }
        }

        window.addEventListener('load', () => {
            window.bgNetwork = new InteractiveNetworkBg('interactiveCanvasBg', '#39FF14');
        });

        // Resume PDF extraction compiler triggers
        const downloadBtn = document.getElementById('downloadResumeBtn');
        const btnText = document.getElementById('btnText');

        downloadBtn.addEventListener('click', () => {
            btnText.textContent = "Generating PDF...";
            downloadBtn.style.opacity = "0.75";
            downloadBtn.disabled = true;

            const element = document.getElementById('resumeTemplate');
            const opt = {
                margin:       [0.3, 0.3, 0.3, 0.3], 
                filename:     'Jindo_Roy_Resume.pdf',
                image:        { type: 'jpeg', quality: 0.98 },
                html2canvas:  { scale: 2.5, useCORS: true, letterRendering: true },
                jsPDF:        { unit: 'in', format: 'letter', orientation: 'portrait' }
            };

            html2pdf().set(opt).from(element).save().then(() => {
                btnText.textContent = "Download Resume";
                downloadBtn.style.opacity = "1";
                downloadBtn.disabled = false;
            }).catch(err => {
                console.error("PDF generator exception captured:", err);
                btnText.textContent = "Download Failed";
                downloadBtn.style.opacity = "1";
                downloadBtn.disabled = false;
            });
        });

        // Optimized Fluid Scroll Animations Using RequestAnimationFrame
        const scrollBar = document.getElementById('scrollProgressBar');
        const mainHeader = document.getElementById('mainHeader');
        let isScrolling = false;

        window.addEventListener('scroll', () => {
            const winScroll = document.documentElement.scrollTop || document.body.scrollTop;
            
            // Pass to canvas particle engine
            if (window.bgNetwork) {
                window.bgNetwork.handleScrollBoost(winScroll);
            }

            // Throttle UI updates with RAF
            if (!isScrolling) {
                window.requestAnimationFrame(() => {
                    const height = document.documentElement.scrollHeight - document.documentElement.clientHeight;
                    const scrolledPercent = height > 0 ? (winScroll / height) : 0;
                    
                    if (scrollBar) {
                        scrollBar.style.transform = `scaleX(${scrolledPercent})`;
                    }

                    if (mainHeader) {
                        if (winScroll > 30) {
                            mainHeader.classList.add('bg-black/95', 'shadow-xl', 'border-b-[#39FF14]/15');
                            mainHeader.style.paddingTop = '10px';
                            mainHeader.style.paddingBottom = '10px';
                        } else {
                            mainHeader.classList.remove('bg-black/95', 'shadow-xl', 'border-b-[#39FF14]/15');
                            mainHeader.style.paddingTop = '16px';
                            mainHeader.style.paddingBottom = '16px';
                        }
                    }
                    isScrolling = false;
                });
                isScrolling = true;
            }
        }, { passive: true });

        // Responsive element entry viewport spy mapping using IntersectionObserver
        const observerSettings = {
            root: null,
            threshold: 0.05,
            rootMargin: "0px 0px -50px 0px"
        };

        const revealObserver = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('revealed');
                }
            });
        }, observerSettings);

        document.querySelectorAll('.reveal-item').forEach(item => {
            revealObserver.observe(item);
        });

        // Smooth scrolling routing
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                const targetId = this.getAttribute('href');
                if (targetId && targetId !== '#') {
                    try {
                        const targetElement = document.querySelector(targetId);
                        if (targetElement) {
                            e.preventDefault();
                            targetElement.scrollIntoView({
                                behavior: 'smooth'
                            });
                        }
                    } catch (err) {
                        console.warn('Scroll target invalid or missing:', err);
                    }
                }
            });
        });
    </script>
</body>
</html>
