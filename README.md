<html lang="id" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>VriAcademy - Portal Pembelajaran Matematika Interaktif</title>
    
    <!-- Google Fonts: Plus Jakarta Sans & JetBrains Mono -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;600&family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    
    <!-- KaTeX: penulisan rumus matematika profesional -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.16.9/katex.min.css">
    <script defer src="https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.16.9/katex.min.js"></script>
    <script defer src="https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.16.9/contrib/auto-render.min.js"></script>

    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Lucide Icons CDN -->
    <script src="https://unpkg.com/lucide@latest"></script>

    <!-- Tailwind Configuration -->
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['"Plus Jakarta Sans"', 'sans-serif'],
                        mono: ['"JetBrains Mono"', 'monospace'],
                    },
                    colors: {
                        primary: {
                            50: '#eef2ff',
                            100: '#e0e7ff',
                            500: '#6366f1',
                            600: '#4f46e5',
                            700: '#4338ca',
                            900: '#312e81',
                        },
                        accent: {
                            400: '#fbbf24',
                            500: '#f59e0b',
                            600: '#d97706',
                        }
                    }
                }
            }
        }
    </script>

    <style>
        /* Custom scrollbar & math formula styling */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: transparent;
        }
        ::-webkit-scrollbar-thumb {
            background: #6366f1;
            border-radius: 9999px;
        }
        .math-box {
            font-family: 'JetBrains Mono', monospace;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .animate-fade-in {
            animation: fadeIn 0.3s ease-out forwards;
        }
            .katex { font-size: 1.08em; }
        .katex-display { margin: 0.35em 0; }
        .formula-box .katex-display { text-align: left; }
        .formula-box .katex-display > .katex { text-align: left; }
        .step-line { padding: 1px 0; }
    </style>
</head>
<body class="bg-slate-50 text-slate-800 dark:bg-slate-950 dark:text-slate-100 transition-colors duration-300 antialiased selection:bg-indigo-500 selection:text-white">

    <!-- ================= 1. HEADER & NAVIGASI ================= -->
    <header class="sticky top-0 z-40 w-full backdrop-blur-lg bg-white/85 dark:bg-slate-900/85 border-b border-slate-200 dark:border-slate-800 transition-colors">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-16 md:h-20">
                <!-- Logo -->
                <a href="#" class="flex items-center gap-2.5 group">
                    <div class="w-10 h-10 rounded-xl bg-gradient-to-br from-indigo-600 to-blue-700 flex items-center justify-center text-white shadow-lg shadow-indigo-500/30 group-hover:scale-105 transition-transform">
                        <span class="font-mono font-bold text-xl">∑</span>
                    </div>
                    <div>
                        <span class="font-extrabold text-xl tracking-tight bg-gradient-to-r from-indigo-600 to-blue-600 dark:from-indigo-400 dark:to-cyan-400 bg-clip-text text-transparent">VriAcademy</span>
                        <span class="block text-[10px] font-bold uppercase tracking-widest text-amber-500 -mt-1">SMA Kurikulum Merdeka</span>
                    </div>
                </a>

                <!-- Desktop Navigation -->
                <nav class="hidden md:flex items-center gap-8 font-medium text-sm">
                    <a href="#beranda" class="text-slate-600 dark:text-slate-300 hover:text-indigo-600 dark:hover:text-indigo-400 transition-colors">Beranda</a>
                    <a href="#materi" class="text-slate-600 dark:text-slate-300 hover:text-indigo-600 dark:hover:text-indigo-400 transition-colors">Materi Belajar</a>
                    <a href="#kalkulator" class="text-slate-600 dark:text-slate-300 hover:text-indigo-600 dark:hover:text-indigo-400 transition-colors">Kalkulator Pintar</a>
                    <a href="#kuis" class="text-slate-600 dark:text-slate-300 hover:text-indigo-600 dark:hover:text-indigo-400 transition-colors">Latihan & Kuis</a>
                </nav>

                <!-- Action Buttons (Theme Toggle & Mobile Menu) -->
                <div class="flex items-center gap-3">
                    <button id="theme-toggle" aria-label="Ganti Tema" class="p-2.5 rounded-xl bg-slate-100 dark:bg-slate-800 text-slate-700 dark:text-amber-400 hover:bg-slate-200 dark:hover:bg-slate-700 transition-colors">
                        <i data-lucide="moon" id="theme-icon-dark" class="w-5 h-5 hidden dark:block"></i>
                        <i data-lucide="sun" id="theme-icon-light" class="w-5 h-5 block dark:hidden"></i>
                    </button>

                    <a href="#kuis" class="hidden sm:inline-flex items-center gap-2 px-4 py-2.5 rounded-xl bg-indigo-600 hover:bg-indigo-700 text-white text-sm font-semibold shadow-md shadow-indigo-500/20 transition-all">
                        <i data-lucide="zap" class="w-4 h-4 text-amber-300"></i>
                        Mulai Kuis
                    </a>

                    <!-- Mobile Menu Button -->
                    <button id="mobile-menu-btn" aria-label="Menu Navigasi" class="md:hidden p-2.5 rounded-xl bg-slate-100 dark:bg-slate-800 text-slate-700 dark:text-slate-200">
                        <i data-lucide="menu" class="w-5 h-5"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- Mobile Dropdown Navigation -->
        <div id="mobile-menu" class="hidden md:hidden border-t border-slate-200 dark:border-slate-800 bg-white dark:bg-slate-900 px-4 pt-3 pb-5 space-y-2">
            <a href="#beranda" class="mobile-link block px-3 py-2.5 rounded-lg font-medium hover:bg-indigo-50 dark:hover:bg-slate-800">Beranda</a>
            <a href="#materi" class="mobile-link block px-3 py-2.5 rounded-lg font-medium hover:bg-indigo-50 dark:hover:bg-slate-800">Materi Belajar (Kelas X-XII)</a>
            <a href="#kalkulator" class="mobile-link block px-3 py-2.5 rounded-lg font-medium hover:bg-indigo-50 dark:hover:bg-slate-800">Kalkulator Matematika</a>
            <a href="#kuis" class="mobile-link block px-3 py-2.5 rounded-lg font-medium text-indigo-600 dark:text-indigo-400 font-semibold hover:bg-indigo-50 dark:hover:bg-slate-800">Latihan & Kuis Interaktif</a>
        </div>
    </header>

    <!-- ================= 2. HERO SECTION ================= -->
    <section id="beranda" class="relative overflow-hidden pt-12 pb-20 lg:pt-20 lg:pb-28">
        <!-- Decorative Background Blobs -->
        <div class="absolute top-0 left-1/2 -translate-x-1/2 w-full max-w-7xl h-full pointer-events-none -z-10">
            <div class="absolute top-10 left-10 w-72 h-72 bg-indigo-500/15 dark:bg-indigo-500/10 rounded-full blur-3xl"></div>
            <div class="absolute bottom-10 right-10 w-80 h-80 bg-amber-400/15 dark:bg-amber-500/10 rounded-full blur-3xl"></div>
        </div>

        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid lg:grid-cols-12 gap-12 items-center">
                <!-- Left Copy -->
                <div class="lg:col-span-7 text-center lg:text-left">
                    <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-indigo-50 dark:bg-indigo-950/80 border border-indigo-200 dark:border-indigo-800 text-indigo-700 dark:text-indigo-300 text-xs font-bold mb-6">
                        <span class="w-2 h-2 rounded-full bg-amber-500 animate-ping"></span>
                        Kurikulum Merdeka • Kelas X, XI & XII
                    </div>
                    
                    <h1 class="text-4xl sm:text-5xl lg:text-6xl font-extrabold tracking-tight leading-[1.15] mb-6">
                        Taklukkan Rumus <br class="hidden sm:block">
                        <span class="bg-gradient-to-r from-indigo-600 via-blue-600 to-teal-500 dark:from-indigo-400 dark:via-blue-400 dark:to-teal-300 bg-clip-text text-transparent">Matematika SMA</span>
                        Tanpa Menghafal Mati
                    </h1>
                    
                    <p class="text-base sm:text-lg text-slate-600 dark:text-slate-300 max-w-2xl mx-auto lg:mx-0 mb-8 leading-relaxed">
                        Platform belajar mandiri interaktif yang dirancang khusus untuk siswa SMA. Pahami konsep inti, eksplorasi rumus cepat, gunakan kalkulator otomatis, dan uji pemahamanmu dengan kuis berpembahasan lengkap.
                    </p>

                    <div class="flex flex-col sm:flex-row items-center justify-center lg:justify-start gap-4">
                        <a href="#materi" class="w-full sm:w-auto px-7 py-4 rounded-2xl bg-indigo-600 hover:bg-indigo-700 text-white font-bold shadow-xl shadow-indigo-600/25 flex items-center justify-center gap-2.5 transition-all hover:-translate-y-0.5">
                            <i data-lucide="book-open" class="w-5 h-5"></i>
                            Jelajahi Materi
                        </a>
                        <a href="#kuis" class="w-full sm:w-auto px-7 py-4 rounded-2xl bg-white dark:bg-slate-800 hover:bg-slate-100 dark:hover:bg-slate-700 text-slate-800 dark:text-white font-bold border border-slate-200 dark:border-slate-700 flex items-center justify-center gap-2.5 transition-all">
                            <i data-lucide="award" class="w-5 h-5 text-amber-500"></i>
                            Latihan Soal & Kuis
                        </a>
                    </div>

                    <!-- Quick Stats -->
                    <div class="grid grid-cols-3 gap-4 mt-10 pt-8 border-t border-slate-200/80 dark:border-slate-800 max-w-lg mx-auto lg:mx-0">
                        <div>
                            <p class="text-2xl sm:text-3xl font-extrabold text-indigo-600 dark:text-indigo-400">9 Bab</p>
                            <p class="text-xs sm:text-sm text-slate-500 dark:text-slate-400">Materi Esensial</p>
                        </div>
                        <div>
                            <p class="text-2xl sm:text-3xl font-extrabold text-amber-500">3 Alat</p>
                            <p class="text-xs sm:text-sm text-slate-500 dark:text-slate-400">Kalkulator Instan</p>
                        </div>
                        <div>
                            <p class="text-2xl sm:text-3xl font-extrabold text-teal-600 dark:text-teal-400">100%</p>
                            <p class="text-xs sm:text-sm text-slate-500 dark:text-slate-400">Pembahasan Jelas</p>
                        </div>
                    </div>
                </div>

                <!-- Right Interactive Visual Card -->
                <div class="lg:col-span-5">
                    <div class="relative bg-gradient-to-br from-indigo-900 via-slate-900 to-indigo-950 rounded-3xl p-6 sm:p-8 text-white shadow-2xl border border-indigo-500/30">
                        <div class="flex items-center justify-between mb-6">
                            <div class="flex items-center gap-2">
                                <span class="w-3 h-3 rounded-full bg-rose-500"></span>
                                <span class="w-3 h-3 rounded-full bg-amber-400"></span>
                                <span class="w-3 h-3 rounded-full bg-emerald-500"></span>
                            </div>
                            <span class="text-xs font-mono text-indigo-300 bg-indigo-950/80 px-3 py-1 rounded-full border border-indigo-700/50">Konsep Kunci</span>
                        </div>

                        <div class="space-y-4">
                            <div class="p-4 rounded-2xl bg-white/5 border border-white/10 backdrop-blur-sm">
                                <span class="text-xs uppercase tracking-wider text-amber-400 font-bold">Identitas Trigonometri</span>
                                <p class="font-mono text-lg sm:text-xl font-semibold mt-1 text-cyan-300">sin²(θ) + cos²(θ) = 1</p>
                            </div>

                            <div class="p-4 rounded-2xl bg-white/5 border border-white/10 backdrop-blur-sm">
                                <span class="text-xs uppercase tracking-wider text-amber-400 font-bold">Turunan Fungsi Aljabar</span>
                                <p class="font-mono text-lg sm:text-xl font-semibold mt-1 text-emerald-300">f(x) = a·xⁿ  ⇒  f'(x) = a·n·xⁿ⁻¹</p>
                            </div>

                            <div class="p-4 rounded-2xl bg-white/5 border border-white/10 backdrop-blur-sm">
                                <span class="text-xs uppercase tracking-wider text-amber-400 font-bold">Deret Geometri Tak Hingga</span>
                                <p class="font-mono text-lg sm:text-xl font-semibold mt-1 text-indigo-300">S∞ = a / (1 - r),  |r| &lt; 1</p>
                            </div>
                        </div>

                        <div class="mt-6 pt-4 border-t border-white/10 flex items-center justify-between text-xs text-slate-300">
                            <span>Siap menghadapi UTBK & ASAS?</span>
                            <a href="#kalkulator" class="text-amber-400 hover:underline font-semibold flex items-center gap-1">
                                Coba Kalkulator <i data-lucide="arrow-right" class="w-3.5 h-3.5"></i>
                            </a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- ================= 3. MATERI PEMBELAJARAN (KELAS X, XI, XII) ================= -->
    <section id="materi" class="py-16 sm:py-24 bg-white dark:bg-slate-900/60 border-y border-slate-200/80 dark:border-slate-800">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center max-w-3xl mx-auto mb-12">
                <span class="text-xs font-extrabold uppercase tracking-widest text-indigo-600 dark:text-indigo-400">Kurikulum Merdeka</span>
                <h2 class="text-3xl sm:text-4xl font-extrabold mt-2 mb-4">Materi Pembelajaran Terstruktur</h2>
                <p class="text-slate-600 dark:text-slate-400">Pilih jenjang kelas di bawah ini, lalu klik kartu bab untuk membuka ringkasan rumus inti dan contoh soal beserta pembahasannya.</p>
            </div>

            <!-- Filter Tabs Kelas -->
            <div class="flex flex-wrap justify-center gap-2 sm:gap-3 mb-10" id="grade-tabs">
                <button data-grade="all" class="grade-tab active px-5 py-2.5 rounded-xl font-bold text-sm transition-all bg-indigo-600 text-white shadow-md shadow-indigo-500/25">
                    Semua Kelas
                </button>
                <button data-grade="10" class="grade-tab px-5 py-2.5 rounded-xl font-bold text-sm transition-all bg-slate-100 dark:bg-slate-800 text-slate-700 dark:text-slate-300 hover:bg-slate-200 dark:hover:bg-slate-700">
                    Kelas X (Fase E)
                </button>
                <button data-grade="11" class="grade-tab px-5 py-2.5 rounded-xl font-bold text-sm transition-all bg-slate-100 dark:bg-slate-800 text-slate-700 dark:text-slate-300 hover:bg-slate-200 dark:hover:bg-slate-700">
                    Kelas XI (Fase F)
                </button>
                <button data-grade="12" class="grade-tab px-5 py-2.5 rounded-xl font-bold text-sm transition-all bg-slate-100 dark:bg-slate-800 text-slate-700 dark:text-slate-300 hover:bg-slate-200 dark:hover:bg-slate-700">
                    Kelas XII (Fase F+)
                </button>
            </div>

            <!-- Grid Kartu Materi -->
            <div id="materials-grid" class="grid sm:grid-cols-2 lg:grid-cols-3 gap-6">
                <!-- Cards akan dirender secara dinamis oleh JavaScript -->
            </div>
        </div>
    </section>

    <!-- ================= 4. KALKULATOR & ALAT BANTU INTERAKTIF ================= -->
    <section id="kalkulator" class="py-16 sm:py-24">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center max-w-3xl mx-auto mb-12">
                <span class="text-xs font-extrabold uppercase tracking-widest text-amber-500">Alat Bantu Belajar</span>
                <h2 class="text-3xl sm:text-4xl font-extrabold mt-2 mb-4">Kalkulator Matematika Pintar</h2>
                <p class="text-slate-600 dark:text-slate-400">Verifikasi jawaban tugas sekolahmu secara instan lengkap dengan langkah perhitungannya.</p>
            </div>

            <div class="grid lg:grid-cols-2 gap-8">
                <!-- Kalkulator 1: Persamaan Kuadrat -->
                <div class="bg-white dark:bg-slate-900 rounded-3xl p-6 sm:p-8 border border-slate-200 dark:border-slate-800 shadow-lg">
                    <div class="flex items-center gap-3 mb-4">
                        <div class="w-11 h-11 rounded-2xl bg-indigo-100 dark:bg-indigo-950 text-indigo-600 dark:text-indigo-400 flex items-center justify-center font-mono font-bold text-lg">
                            x²
                        </div>
                        <div>
                            <h3 class="text-xl font-bold">Solver Persamaan Kuadrat</h3>
                            <p class="text-xs text-slate-500 dark:text-slate-400">Bentuk umum: ax² + bx + c = 0</p>
                        </div>
                    </div>

                    <div class="grid grid-cols-3 gap-3 my-6">
                        <div>
                            <label class="block text-xs font-bold mb-1.5 text-slate-600 dark:text-slate-300">Koefisien a</label>
                            <input type="number" id="quad-a" value="1" step="any" class="w-full px-3.5 py-2.5 rounded-xl bg-slate-50 dark:bg-slate-800 border border-slate-300 dark:border-slate-700 font-mono text-center font-semibold focus:outline-none focus:ring-2 focus:ring-indigo-500">
                        </div>
                        <div>
                            <label class="block text-xs font-bold mb-1.5 text-slate-600 dark:text-slate-300">Koefisien b</label>
                            <input type="number" id="quad-b" value="-5" step="any" class="w-full px-3.5 py-2.5 rounded-xl bg-slate-50 dark:bg-slate-800 border border-slate-300 dark:border-slate-700 font-mono text-center font-semibold focus:outline-none focus:ring-2 focus:ring-indigo-500">
                        </div>
                        <div>
                            <label class="block text-xs font-bold mb-1.5 text-slate-600 dark:text-slate-300">Konstanta c</label>
                            <input type="number" id="quad-c" value="6" step="any" class="w-full px-3.5 py-2.5 rounded-xl bg-slate-50 dark:bg-slate-800 border border-slate-300 dark:border-slate-700 font-mono text-center font-semibold focus:outline-none focus:ring-2 focus:ring-indigo-500">
                        </div>
                    </div>

                    <button onclick="calculateQuadratic()" class="w-full py-3 rounded-xl bg-indigo-600 hover:bg-indigo-700 text-white font-bold transition-colors shadow-md shadow-indigo-500/20">
                        Hitung Diskriminan & Akar
                    </button>

                    <!-- Hasil Persamaan Kuadrat -->
                    <div id="quad-result" class="mt-6 p-4 rounded-2xl bg-slate-50 dark:bg-slate-800/80 border border-slate-200 dark:border-slate-700 space-y-2 text-sm">
                        <div class="flex justify-between">
                            <span class="text-slate-500 dark:text-slate-400">Persamaan:</span>
                            <span id="quad-eq-display" class="font-mono font-bold text-indigo-600 dark:text-indigo-400">1x² - 5x + 6 = 0</span>
                        </div>
                        <div class="flex justify-between">
                            <span class="text-slate-500 dark:text-slate-400">Diskriminan (D = b² - 4ac):</span>
                            <span id="quad-disc-display" class="font-mono font-bold">1</span>
                        </div>
                        <div class="flex justify-between">
                            <span class="text-slate-500 dark:text-slate-400">Sifat Akar:</span>
                            <span id="quad-nature-display" class="font-semibold text-emerald-600 dark:text-emerald-400">Dua akar real berbeda</span>
                        </div>
                        <div class="pt-2 border-t border-slate-200 dark:border-slate-700 flex justify-between items-center">
                            <span class="font-bold">Akar-akar (x₁, x₂):</span>
                            <span id="quad-roots-display" class="font-mono font-extrabold text-base text-amber-600 dark:text-amber-400">x₁ = 3, x₂ = 2</span>
                        </div>
                    </div>
                </div>

                <!-- Kalkulator 2: Barisan Aritmatika & Trigonometri -->
                <div class="bg-white dark:bg-slate-900 rounded-3xl p-6 sm:p-8 border border-slate-200 dark:border-slate-800 shadow-lg flex flex-col justify-between">
                    <div>
                        <div class="flex items-center justify-between gap-2 mb-4">
                            <div class="flex items-center gap-3">
                                <div class="w-11 h-11 rounded-2xl bg-amber-100 dark:bg-amber-950 text-amber-600 dark:text-amber-400 flex items-center justify-center font-mono font-bold text-lg">
                                    Un
                                </div>
                                <div>
                                    <h3 class="text-xl font-bold">Barisan & Trigonometri</h3>
                                    <p class="text-xs text-slate-500 dark:text-slate-400">Pilih alat bantu cepat</p>
                                </div>
                            </div>

                            <!-- Mini Switcher -->
                            <div class="flex bg-slate-100 dark:bg-slate-800 p-1 rounded-xl text-xs font-bold">
                                <button id="tool-tab-seq" onclick="switchToolTab('seq')" class="px-3 py-1.5 rounded-lg bg-white dark:bg-slate-700 shadow-sm text-indigo-600 dark:text-indigo-300">Deret</button>
                                <button id="tool-tab-trig" onclick="switchToolTab('trig')" class="px-3 py-1.5 rounded-lg text-slate-500 dark:text-slate-400">Sudut</button>
                            </div>
                        </div>

                        <!-- Panel Barisan Aritmatika -->
                        <div id="tool-panel-seq">
                            <div class="grid grid-cols-3 gap-3 my-6">
                                <div>
                                    <label class="block text-xs font-bold mb-1.5 text-slate-600 dark:text-slate-300">Suku Awal (a)</label>
                                    <input type="number" id="seq-a" value="4" step="any" class="w-full px-3.5 py-2.5 rounded-xl bg-slate-50 dark:bg-slate-800 border border-slate-300 dark:border-slate-700 font-mono text-center font-semibold focus:outline-none focus:ring-2 focus:ring-amber-500">
                                </div>
                                <div>
                                    <label class="block text-xs font-bold mb-1.5 text-slate-600 dark:text-slate-300">Beda (b)</label>
                                    <input type="number" id="seq-b" value="3" step="any" class="w-full px-3.5 py-2.5 rounded-xl bg-slate-50 dark:bg-slate-800 border border-slate-300 dark:border-slate-700 font-mono text-center font-semibold focus:outline-none focus:ring-2 focus:ring-amber-500">
                                </div>
                                <div>
                                    <label class="block text-xs font-bold mb-1.5 text-slate-600 dark:text-slate-300">Suku ke- (n)</label>
                                    <input type="number" id="seq-n" value="10" min="1" max="1000" class="w-full px-3.5 py-2.5 rounded-xl bg-slate-50 dark:bg-slate-800 border border-slate-300 dark:border-slate-700 font-mono text-center font-semibold focus:outline-none focus:ring-2 focus:ring-amber-500">
                                </div>
                            </div>

                            <button onclick="calculateSequence()" class="w-full py-3 rounded-xl bg-amber-500 hover:bg-amber-600 text-slate-950 font-bold transition-colors shadow-md shadow-amber-500/20">
                                Hitung Suku ke-n (Un) & Jumlah (Sn)
                            </button>

                            <div class="mt-6 p-4 rounded-2xl bg-slate-50 dark:bg-slate-800/80 border border-slate-200 dark:border-slate-700 space-y-2 text-sm">
                                <div class="flex justify-between">
                                    <span class="text-slate-500 dark:text-slate-400">Rumus Un = a + (n-1)b:</span>
                                    <span id="seq-un-display" class="font-mono font-extrabold text-indigo-600 dark:text-indigo-400">U₁₀ = 31</span>
                                </div>
                                <div class="flex justify-between">
                                    <span class="text-slate-500 dark:text-slate-400">Jumlah n suku (Sn):</span>
                                    <span id="seq-sn-display" class="font-mono font-extrabold text-teal-600 dark:text-teal-400">S₁₀ = 175</span>
                                </div>
                                <div class="pt-2 border-t border-slate-200 dark:border-slate-700 text-xs text-slate-500 dark:text-slate-400">
                                    <span>5 Suku Pertama: </span>
                                    <span id="seq-preview-display" class="font-mono font-semibold text-slate-700 dark:text-slate-200">4, 7, 10, 13, 16, ...</span>
                                </div>
                            </div>
                        </div>

                        <!-- Panel Kalkulator Trigonometri -->
                        <div id="tool-panel-trig" class="hidden">
                            <div class="my-6">
                                <label class="block text-xs font-bold mb-1.5 text-slate-600 dark:text-slate-300">Masukkan Besar Sudut (Derajat °)</label>
                                <div class="flex gap-2">
                                    <input type="number" id="trig-deg" value="30" step="any" class="w-full px-4 py-2.5 rounded-xl bg-slate-50 dark:bg-slate-800 border border-slate-300 dark:border-slate-700 font-mono font-semibold focus:outline-none focus:ring-2 focus:ring-indigo-500">
                                    <button onclick="calculateTrig()" class="px-6 py-2.5 rounded-xl bg-indigo-600 hover:bg-indigo-700 text-white font-bold transition-colors">Hitung</button>
                                </div>
                                <!-- Preset Sudut Istimewa -->
                                <div class="flex flex-wrap gap-1.5 mt-3">
                                    <span class="text-xs text-slate-400 self-center mr-1">Sudut Istimewa:</span>
                                    <button onclick="setTrigAngle(0)" class="px-2.5 py-1 text-xs font-mono rounded-lg bg-slate-100 dark:bg-slate-800 hover:bg-indigo-100 dark:hover:bg-indigo-900">0°</button>
                                    <button onclick="setTrigAngle(30)" class="px-2.5 py-1 text-xs font-mono rounded-lg bg-slate-100 dark:bg-slate-800 hover:bg-indigo-100 dark:hover:bg-indigo-900">30°</button>
                                    <button onclick="setTrigAngle(45)" class="px-2.5 py-1 text-xs font-mono rounded-lg bg-slate-100 dark:bg-slate-800 hover:bg-indigo-100 dark:hover:bg-indigo-900">45°</button>
                                    <button onclick="setTrigAngle(60)" class="px-2.5 py-1 text-xs font-mono rounded-lg bg-slate-100 dark:bg-slate-800 hover:bg-indigo-100 dark:hover:bg-indigo-900">60°</button>
                                    <button onclick="setTrigAngle(90)" class="px-2.5 py-1 text-xs font-mono rounded-lg bg-slate-100 dark:bg-slate-800 hover:bg-indigo-100 dark:hover:bg-indigo-900">90°</button>
                                </div>
                            </div>

                            <div class="p-4 rounded-2xl bg-slate-50 dark:bg-slate-800/80 border border-slate-200 dark:border-slate-700 grid grid-cols-3 gap-3 text-center">
                                <div class="p-2.5 rounded-xl bg-white dark:bg-slate-900 border border-slate-200 dark:border-slate-700">
                                    <span class="block text-xs text-slate-400">sin(θ)</span>
                                    <span id="trig-sin" class="font-mono font-bold text-indigo-600 dark:text-indigo-400 text-base">0.5</span>
                                </div>
                                <div class="p-2.5 rounded-xl bg-white dark:bg-slate-900 border border-slate-200 dark:border-slate-700">
                                    <span class="block text-xs text-slate-400">cos(θ)</span>
                                    <span id="trig-cos" class="font-mono font-bold text-teal-600 dark:text-teal-400 text-base">0.866</span>
                                </div>
                                <div class="p-2.5 rounded-xl bg-white dark:bg-slate-900 border border-slate-200 dark:border-slate-700">
                                    <span class="block text-xs text-slate-400">tan(θ)</span>
                                    <span id="trig-tan" class="font-mono font-bold text-amber-600 dark:text-amber-400 text-base">0.5774</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- ================= 5. KUIS / LATIHAN SOAL INTERAKTIF ================= -->
    <section id="kuis" class="py-16 sm:py-24 bg-gradient-to-b from-indigo-50/70 to-slate-50 dark:from-slate-900 dark:to-slate-950 border-t border-slate-200 dark:border-slate-800">
        <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-10">
                <span class="text-xs font-extrabold uppercase tracking-widest text-indigo-600 dark:text-indigo-400">Uji Kompetensi</span>
                <h2 class="text-3xl sm:text-4xl font-extrabold mt-2 mb-3">Kuis Matematika SMA Interaktif</h2>
                <p class="text-slate-600 dark:text-slate-400">Selesaikan 6 soal pilihan ganda dari berbagai bab kelas X–XII. Dapatkan umpan balik dan pembahasan langsung setiap nomor!</p>
            </div>

            <!-- Quiz Container Card -->
            <div class="bg-white dark:bg-slate-900 rounded-3xl shadow-xl border border-slate-200 dark:border-slate-800 overflow-hidden">
                
                <!-- Screen 1: Start Quiz -->
                <div id="quiz-start-screen" class="p-8 sm:p-12 text-center">
                    <div class="w-16 h-16 rounded-2xl bg-indigo-100 dark:bg-indigo-950 text-indigo-600 dark:text-indigo-400 flex items-center justify-center mx-auto mb-6">
                        <i data-lucide="brain-circuit" class="w-8 h-8"></i>
                    </div>
                    <h3 class="text-2xl font-bold mb-3">Siap Menguji Kemampuan Berhitungmu?</h3>
                    <p class="text-slate-600 dark:text-slate-400 max-w-md mx-auto mb-6 text-sm leading-relaxed">
                        Kuis ini terdiri dari 6 soal mencakup Eksponen, Trigonometri, Matriks, Barisan Deret, Turunan, dan Peluang.
                    </p>

                    <!-- Opsi Timer -->
                    <div class="flex items-center justify-center gap-3 mb-8">
                        <label class="inline-flex items-center gap-2 cursor-pointer select-none bg-slate-100 dark:bg-slate-800 px-4 py-2.5 rounded-xl border border-slate-200 dark:border-slate-700">
                            <input type="checkbox" id="quiz-timer-toggle" checked class="w-4 h-4 accent-indigo-600 rounded">
                            <span class="text-sm font-semibold">Aktifkan Timer (3 Menit)</span>
                        </label>
                    </div>

                    <button onclick="startQuiz()" class="px-8 py-4 rounded-2xl bg-indigo-600 hover:bg-indigo-700 text-white font-bold text-base shadow-lg shadow-indigo-500/30 transition-all hover:scale-105 inline-flex items-center gap-2">
                        <i data-lucide="play" class="w-5 h-5"></i>
                        Mulai Mengerjakan Sekarang
                    </button>
                </div>

                <!-- Screen 2: Active Question -->
                <div id="quiz-question-screen" class="hidden p-6 sm:p-10">
                    <!-- Top Status Bar -->
                    <div class="flex flex-wrap items-center justify-between gap-4 pb-6 mb-6 border-b border-slate-200 dark:border-slate-800">
                        <div>
                            <span id="quiz-topic-badge" class="text-xs font-bold uppercase tracking-wider px-3 py-1 rounded-full bg-indigo-100 dark:bg-indigo-950 text-indigo-700 dark:text-indigo-300">Bab Materi</span>
                            <p class="text-sm font-bold text-slate-500 dark:text-slate-400 mt-2">
                                Soal <span id="quiz-current-num" class="text-slate-900 dark:text-white">1</span> dari <span id="quiz-total-num">6</span>
                            </p>
                        </div>

                        <div class="flex items-center gap-4">
                            <!-- Timer Display -->
                            <div id="quiz-timer-box" class="flex items-center gap-1.5 px-3.5 py-2 rounded-xl bg-amber-50 dark:bg-amber-950/60 border border-amber-200 dark:border-amber-800 text-amber-700 dark:text-amber-400 font-mono font-bold text-sm">
                                <i data-lucide="timer" class="w-4 h-4"></i>
                                <span id="quiz-timer-text">03:00</span>
                            </div>

                            <!-- Score Badge -->
                            <div class="px-3.5 py-2 rounded-xl bg-slate-100 dark:bg-slate-800 font-bold text-sm">
                                Skor: <span id="quiz-live-score" class="text-indigo-600 dark:text-indigo-400">0</span>
                            </div>
                        </div>
                    </div>

                    <!-- Progress Bar -->
                    <div class="w-full h-2 bg-slate-100 dark:bg-slate-800 rounded-full mb-8 overflow-hidden">
                        <div id="quiz-progress-bar" class="h-full bg-indigo-600 transition-all duration-300" style="width: 16.6%"></div>
                    </div>

                    <!-- Question Text -->
                    <h4 id="quiz-question-text" class="text-lg sm:text-xl font-bold leading-relaxed mb-6">
                        Pertanyaan akan muncul di sini...
                    </h4>

                    <!-- Options Container -->
                    <div id="quiz-options-container" class="space-y-3">
                        <!-- Pilihan jawaban dirender JS -->
                    </div>

                    <!-- Instant Feedback & Explanation Box -->
                    <div id="quiz-feedback-box" class="hidden mt-6 p-5 rounded-2xl border animate-fade-in">
                        <div class="flex items-center gap-2 font-bold text-base mb-1.5" id="quiz-feedback-title">
                            <!-- Status Benar/Salah -->
                        </div>
                        <p id="quiz-feedback-explanation" class="text-sm leading-relaxed text-slate-700 dark:text-slate-300">
                            Pembahasan soal...
                        </p>
                    </div>

                    <!-- Next Button -->
                    <div class="mt-8 flex justify-end">
                        <button id="quiz-next-btn" onclick="nextQuestion()" class="hidden px-6 py-3 rounded-xl bg-indigo-600 hover:bg-indigo-700 text-white font-bold text-sm items-center gap-2 shadow-md">
                            Soal Berikutnya <i data-lucide="arrow-right" class="w-4 h-4"></i>
                        </button>
                    </div>
                </div>

                <!-- Screen 3: Quiz Result -->
                <div id="quiz-result-screen" class="hidden p-8 sm:p-12 text-center animate-fade-in">
                    <div id="result-icon-wrapper" class="w-20 h-20 rounded-3xl bg-amber-100 dark:bg-amber-950 text-amber-500 flex items-center justify-center mx-auto mb-6">
                        <i data-lucide="trophy" class="w-10 h-10"></i>
                    </div>
                    
                    <h3 class="text-2xl sm:text-3xl font-extrabold mb-2">Kuis Selesai!</h3>
                    <p id="result-message" class="text-slate-600 dark:text-slate-400 mb-6">Kerja bagus! Terus tingkatkan latihanmu.</p>

                    <div class="max-w-xs mx-auto p-6 rounded-3xl bg-slate-50 dark:bg-slate-800/80 border border-slate-200 dark:border-slate-700 mb-8">
                        <span class="text-xs font-bold uppercase tracking-wider text-slate-400">Nilai Akhir Kamu</span>
                        <div class="text-5xl font-extrabold text-indigo-600 dark:text-indigo-400 my-2" id="result-final-score">100</div>
                        <p class="text-xs font-semibold text-slate-500 dark:text-slate-400">
                            Benar <span id="result-correct-count" class="text-emerald-600 dark:text-emerald-400 font-bold">6</span> dari <span id="result-total-count">6</span> soal
                        </p>
                    </div>

                    <div class="flex flex-col sm:flex-row justify-center gap-3">
                        <button onclick="startQuiz()" class="px-6 py-3.5 rounded-xl bg-indigo-600 hover:bg-indigo-700 text-white font-bold text-sm inline-flex items-center justify-center gap-2">
                            <i data-lucide="rotate-ccw" class="w-4 h-4"></i>
                            Ulangi Kuis
                        </button>
                        <a href="#materi" class="px-6 py-3.5 rounded-xl bg-slate-100 dark:bg-slate-800 hover:bg-slate-200 dark:hover:bg-slate-700 font-bold text-sm inline-flex items-center justify-center gap-2">
                            Pelajari Kembali Materi
                        </a>
                    </div>
                </div>

            </div>
        </div>
    </section>

    <!-- ================= 6. FOOTER INFORMATIF ================= -->
    <footer class="bg-slate-900 text-slate-300 pt-16 pb-10 border-t border-slate-800">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid md:grid-cols-12 gap-10 pb-12 border-b border-slate-800">
                <!-- Brand Info -->
                <div class="md:col-span-5">
                    <div class="flex items-center gap-2.5 mb-4">
                        <div class="w-9 h-9 rounded-xl bg-indigo-600 flex items-center justify-center text-white font-mono font-bold text-lg">∑</div>
                        <span class="font-extrabold text-xl text-white">VriAcademy</span>
                    </div>
                    <p class="text-sm text-slate-400 leading-relaxed max-w-sm">
                        Portal edukasi Matematika SMA berbasis web interaktif untuk membantu siswa memahami konsep Kelas X, XI, dan XII Kurikulum Merdeka secara visual dan praktis.
                    </p>
                </div>

                <!-- Navigasi Cepat -->
                <div class="md:col-span-3">
                    <h4 class="text-white font-bold text-sm uppercase tracking-wider mb-4">Navigasi Cepat</h4>
                    <ul class="space-y-2.5 text-sm text-slate-400">
                        <li><a href="#beranda" class="hover:text-amber-400 transition-colors">Beranda</a></li>
                        <li><a href="#materi" class="hover:text-amber-400 transition-colors">Materi Kelas X - XII</a></li>
                        <li><a href="#kalkulator" class="hover:text-amber-400 transition-colors">Kalkulator Persamaan Kuadrat</a></li>
                        <li><a href="#kuis" class="hover:text-amber-400 transition-colors">Latihan Soal & Kuis</a></li>
                    </ul>
                </div>

                <!-- Topik Populer -->
                <div class="md:col-span-4">
                    <h4 class="text-white font-bold text-sm uppercase tracking-wider mb-4">Topik Unggulan</h4>
                    <div class="flex flex-wrap gap-2 text-xs">
                        <span class="px-3 py-1.5 rounded-lg bg-slate-800 text-slate-300">Eksponen & Logaritma</span>
                        <span class="px-3 py-1.5 rounded-lg bg-slate-800 text-slate-300">Trigonometri</span>
                        <span class="px-3 py-1.5 rounded-lg bg-slate-800 text-slate-300">Matriks</span>
                        <span class="px-3 py-1.5 rounded-lg bg-slate-800 text-slate-300">Kalkulus Turunan</span>
                        <span class="px-3 py-1.5 rounded-lg bg-slate-800 text-slate-300">Integral</span>
                        <span class="px-3 py-1.5 rounded-lg bg-slate-800 text-slate-300">Kaidah Pencacahan</span>
                    </div>
                </div>
            </div>

            <div class="pt-8 flex flex-col sm:flex-row items-center justify-between gap-4 text-xs text-slate-500">
                <p>&copy; 2026 VriAcademy Indonesia. Dibuat untuk kemajuan pendidikan matematika.</p>
                <p>Mendukung Pembelajaran Mandiri & Persiapan SNBT/UTBK.</p>
            </div>
        </div>
    </footer>

    <!-- ================= MODAL POPUP DETAIL MATERI ================= -->
    <div id="material-modal" class="fixed inset-0 z-50 hidden items-center justify-center p-4 bg-slate-950/70 backdrop-blur-sm">
        <div class="bg-white dark:bg-slate-900 w-full max-w-2xl max-h-[90vh] rounded-3xl shadow-2xl border border-slate-200 dark:border-slate-800 overflow-hidden flex flex-col animate-fade-in">
            <!-- Modal Header -->
            <div class="px-6 py-5 bg-gradient-to-r from-indigo-600 to-blue-700 text-white flex items-center justify-between">
                <div>
                    <span id="modal-grade-badge" class="text-[11px] font-bold uppercase tracking-wider px-2.5 py-0.5 rounded-full bg-white/20">Kelas X</span>
                    <h3 id="modal-title" class="text-xl sm:text-2xl font-extrabold mt-1">Judul Materi</h3>
                </div>
                <button onclick="closeMaterialModal()" aria-label="Tutup Modal" class="p-2 rounded-xl bg-white/10 hover:bg-white/20 text-white transition-colors">
                    <i data-lucide="x" class="w-5 h-5"></i>
                </button>
            </div>

            <!-- Modal Body (Scrollable) -->
            <div class="p-6 overflow-y-auto space-y-6 text-sm sm:text-base">
                <!-- Konsep Inti -->
                <div>
                    <h4 class="font-bold text-indigo-600 dark:text-indigo-400 flex items-center gap-2 mb-2">
                        <i data-lucide="lightbulb" class="w-4 h-4"></i> Konsep Dasar
                    </h4>
                    <p id="modal-concept" class="text-slate-600 dark:text-slate-300 leading-relaxed"></p>
                </div>

                <!-- Rumus Penting -->
                <div>
                    <h4 class="font-bold text-amber-600 dark:text-amber-400 flex items-center gap-2 mb-2.5">
                        <i data-lucide="function-square" class="w-4 h-4"></i> Rumus & Sifat Penting
                    </h4>
                    <div id="modal-formulas" class="space-y-2 bg-slate-50 dark:bg-slate-800/90 p-4 rounded-2xl border border-slate-200 dark:border-slate-700 text-sm sm:text-base">
                        <!-- Rumus dirender JS -->
                    </div>
                </div>

                <!-- Contoh Soal & Pembahasan -->
                <div>
                    <h4 class="font-bold text-teal-600 dark:text-teal-400 flex items-center gap-2 mb-2.5">
                        <i data-lucide="check-circle-2" class="w-4 h-4"></i> Contoh Soal & Pembahasan
                    </h4>
                    <div id="modal-examples" class="space-y-4"></div>
                </div>
            </div>

            <!-- Modal Footer -->
            <div class="px-6 py-4 bg-slate-50 dark:bg-slate-800/60 border-t border-slate-200 dark:border-slate-800 flex justify-end">
                <button onclick="closeMaterialModal()" class="px-5 py-2.5 rounded-xl bg-indigo-600 hover:bg-indigo-700 text-white font-bold text-sm transition-colors">
                    Mengerti, Tutup
                </button>
            </div>
        </div>
    </div>

    <!-- ================= JAVASCRIPT INTERAKTIF ================= -->
    <script>
        // 1. DATA MATERI PEMBELAJARAN SMA (KELAS X, XI, XII)
        const materialsData = (() => {
            const r = String.raw;
            const C = ['indigo', 'amber', 'teal'];
            const mk = (id, grade, title, icon, summary, concept, formulas, examples) => ({
                id, grade, gradeLabel: 'Kelas ' + {10: 'X', 11: 'XI', 12: 'XII'}[grade], title, icon,
                color: C[(id - 1) % 3], summary, concept, formulas,
                examples: examples.map(([q, a]) => ({q, a}))
            });
            return [
            mk(1, "10", "Eksponen & Logaritma", "superscript",
                "Memahami bilangan berpangkat bulat/pecahan, fungsi eksponensial, serta inversnya yaitu logaritma.",
                r`Eksponen adalah perkalian berulang suatu bilangan dengan dirinya sendiri. Logaritma adalah operasi invers dari perpangkatan yang digunakan untuk mencari besar pangkat.`,
                [r`a^m \times a^n = a^{m+n} \qquad \dfrac{a^m}{a^n} = a^{m-n}`,
                 r`(a^m)^n = a^{mn} \qquad a^{-n} = \dfrac{1}{a^n}`,
                 r`{}^{a}\!\log b = c \iff a^c = b \quad (a \gt 0,\ a \neq 1,\ b \gt 0)`,
                 r`{}^{a}\!\log (xy) = {}^{a}\!\log x + {}^{a}\!\log y`,
                 r`{}^{a}\!\log \dfrac{x}{y} = {}^{a}\!\log x - {}^{a}\!\log y`,
                 r`{}^{a}\!\log x^n = n \cdot {}^{a}\!\log x`],
                [[r`Tentukan nilai dari $\,{}^{2}\!\log 16 + {}^{2}\!\log 8 - {}^{2}\!\log 4$!`,
                  [r`Gunakan sifat penjumlahan dan pengurangan logaritma:`, r`$= {}^{2}\!\log \dfrac{16 \times 8}{4}$`, r`$= {}^{2}\!\log \dfrac{128}{4} = {}^{2}\!\log 32$`, r`Karena $2^5 = 32$, maka hasilnya $\mathbf{5}$.`]],
                 [r`Sederhanakan $\dfrac{2^3 \times 2^4}{2^5}$!`,
                  [r`$= 2^{3+4-5}$`, r`$= 2^2 = \mathbf{4}$`]]]),
            mk(2, "10", "Barisan & Deret", "list-ordered",
                "Pola bilangan aritmetika dengan selisih tetap dan pola geometri dengan rasio perkalian tetap.",
                r`Barisan bilangan adalah urutan bilangan dengan aturan tertentu. Jika selisih antarsuku tetap disebut barisan aritmetika; jika perbandingan (rasio) antarsuku tetap disebut barisan geometri.`,
                [r`\text{Aritmetika: } U_n = a + (n-1)b`,
                 r`S_n = \dfrac{n}{2}\,\bigl(2a + (n-1)b\bigr)`,
                 r`\text{Geometri: } U_n = a \cdot r^{\,n-1}`,
                 r`S_n = \dfrac{a(r^n - 1)}{r - 1} \quad (r \gt 1)`,
                 r`S_\infty = \dfrac{a}{1 - r} \quad (|r| \lt 1)`],
                [[r`Diketahui barisan aritmetika $3, 7, 11, 15, \dots$ Tentukan suku ke-20!`,
                  [r`Diketahui $a = 3$, $b = 7 - 3 = 4$, $n = 20$.`, r`$U_{20} = a + (20-1)\,b$`, r`$U_{20} = 3 + 19(4) = 3 + 76 = \mathbf{79}$`]],
                 [r`Tentukan suku ke-5 barisan geometri $2, 6, 18, \dots$!`,
                  [r`$a = 2$, $\ r = \dfrac{6}{2} = 3$`, r`$U_5 = a \cdot r^4 = 2 \cdot 3^4 = 2 \cdot 81 = \mathbf{162}$`]]]),
            mk(3, "10", "Trigonometri Dasar", "triangle",
                "Perbandingan sisi pada segitiga siku-siku (sin, cos, tan) serta nilai sudut istimewa.",
                r`Trigonometri mempelajari hubungan antara sudut dan panjang sisi segitiga. Pada segitiga siku-siku berlaku perbandingan sisi depan, samping, dan miring (de-mi, sa-mi, de-sa).`,
                [r`\sin\theta = \dfrac{\text{depan}}{\text{miring}} \qquad \cos\theta = \dfrac{\text{samping}}{\text{miring}}`,
                 r`\tan\theta = \dfrac{\text{depan}}{\text{samping}} = \dfrac{\sin\theta}{\cos\theta}`,
                 r`\sin^2\theta + \cos^2\theta = 1`,
                 r`\sin 30^\circ = \tfrac12,\ \ \sin 45^\circ = \tfrac{\sqrt2}{2},\ \ \sin 60^\circ = \tfrac{\sqrt3}{2}`],
                [[r`Sebuah tangga sepanjang $6$ m bersandar pada dinding dengan sudut elevasi $60^\circ$ terhadap lantai. Berapa tinggi ujung tangga dari lantai?`,
                  [r`Tinggi = sisi depan sudut $60^\circ$; panjang tangga = sisi miring.`, r`$\sin 60^\circ = \dfrac{t}{6}$`, r`$\dfrac{1}{2}\sqrt3 = \dfrac{t}{6}$`, r`$t = 6 \times \dfrac12\sqrt3 = \mathbf{3\sqrt3}\ \text{m}$`]],
                 [r`Pada segitiga siku-siku, sisi depan $\theta$ = $3$ dan sisi samping = $4$. Tentukan $\sin\theta$, $\cos\theta$, $\tan\theta$!`,
                  [r`Miring $= \sqrt{3^2 + 4^2} = 5$`, r`$\sin\theta = \dfrac35,\quad \cos\theta = \dfrac45,\quad \tan\theta = \dfrac34$`]]]),
            mk(4, "11", "Matriks & Transformasi", "grid",
                "Operasi penjumlahan, perkalian matriks, determinan, invers matriks ordo 2×2, dan transformasi geometri.",
                r`Matriks adalah susunan bilangan berbentuk persegi panjang yang diatur menurut baris dan kolom. Matriks persegi ordo $2\times2$ memiliki determinan dan (jika tidak singular) invers.`,
                [r`A = \begin{pmatrix} a & b \\ c & d \end{pmatrix}`,
                 r`\det(A) = |A| = ad - bc`,
                 r`A^{-1} = \dfrac{1}{ad - bc}\begin{pmatrix} d & -b \\ -c & a \end{pmatrix}`,
                 r`\text{Matriks singular (tak punya invers): } \det(A) = 0`],
                [[r`Tentukan determinan dari $P = \begin{pmatrix} 4 & 3 \\ 2 & 5 \end{pmatrix}$!`,
                  [r`$\det(P) = (4 \times 5) - (3 \times 2)$`, r`$\det(P) = 20 - 6 = \mathbf{14}$`]],
                 [r`Tentukan invers dari $A = \begin{pmatrix} 2 & 3 \\ 1 & 4 \end{pmatrix}$!`,
                  [r`$\det(A) = 2\cdot4 - 3\cdot1 = 5$`, r`$A^{-1} = \dfrac15\begin{pmatrix} 4 & -3 \\ -1 & 2 \end{pmatrix}$`]]]),
            mk(5, "11", "Komposisi & Invers Fungsi", "repeat",
                "Penggabungan dua fungsi f(g(x)) serta menentukan fungsi kebalikan f⁻¹(x).",
                r`Fungsi komposisi $(f\circ g)(x)$ berarti memasukkan $g(x)$ ke dalam variabel $x$ milik $f(x)$. Fungsi invers adalah pemetaan kebalikan dari daerah hasil ke daerah asal.`,
                [r`(f \circ g)(x) = f\bigl(g(x)\bigr)`,
                 r`(g \circ f)(x) = g\bigl(f(x)\bigr)`,
                 r`y = f(x) \iff x = f^{-1}(y)`,
                 r`f(x) = \dfrac{ax+b}{cx+d} \ \Rightarrow\ f^{-1}(x) = \dfrac{-dx+b}{cx-a}`],
                [[r`Diketahui $f(x) = 2x + 3$ dan $g(x) = x - 4$. Tentukan $(f\circ g)(5)$!`,
                  [r`Langkah 1: $g(5) = 5 - 4 = 1$`, r`Langkah 2: $f(1) = 2(1) + 3 = 5$`, r`Jadi $(f\circ g)(5) = \mathbf{5}$.`]],
                 [r`Jika $f(x) = 2x + 3$, tentukan $f^{-1}(x)$!`,
                  [r`Misal $y = 2x + 3$`, r`$x = \dfrac{y - 3}{2}$`, r`$f^{-1}(x) = \dfrac{x - 3}{2}$`]]]),
            mk(6, "11", "Limit Fungsi Aljabar", "trending-up",
                "Pendekatan nilai suatu fungsi saat variabel x mendekati titik tertentu tanpa harus menyentuhnya.",
                r`Limit fungsi mencari nilai pendekatan $f(x)$ saat $x$ mendekati $c$. Jika substitusi langsung menghasilkan bentuk tak tentu $\frac{0}{0}$, gunakan pemfaktoran atau perkalian sekawan.`,
                [r`\lim_{x \to c} k = k`,
                 r`\lim_{x \to c}\bigl[f(x) \pm g(x)\bigr] = \lim_{x \to c} f(x) \pm \lim_{x \to c} g(x)`,
                 r`\dfrac{0}{0}\ \Rightarrow\ \text{faktorkan pembilang dan penyebut}`,
                 r`\lim_{x \to \infty} \dfrac{ax^n + \cdots}{bx^n + \cdots} = \dfrac{a}{b}`],
                [[r`Hitung $\displaystyle\lim_{x \to 2} \dfrac{x^2 - 4}{x - 2}$!`,
                  [r`Substitusi $x = 2$ menghasilkan $\frac00$ (tak tentu).`, r`Faktorkan: $x^2 - 4 = (x-2)(x+2)$`, r`$\displaystyle\lim_{x \to 2} (x + 2) = 2 + 2 = \mathbf{4}$`]],
                 [r`Hitung $\displaystyle\lim_{x \to \infty} \dfrac{3x^2 + 2x}{x^2 - 5}$!`,
                  [r`Pangkat tertinggi pembilang dan penyebut sama ($x^2$).`, r`Hasil = perbandingan koefisien $= \dfrac{3}{1} = \mathbf{3}$`]]]),
            mk(7, "12", "Turunan Fungsi (Diferensial)", "activity",
                "Laju perubahan sesaat suatu fungsi, gradien garis singgung kurva, serta nilai maksimum dan minimum.",
                r`Turunan pertama $f'(x)$ mengukur seberapa cepat nilai fungsi berubah terhadap perubahan $x$. Sangat berguna untuk optimasi nilai maksimum/minimum.`,
                [r`f(x) = a x^n \ \Rightarrow\ f'(x) = a\,n\,x^{n-1}`,
                 r`(u \cdot v)' = u'v + uv'`,
                 r`\left(\dfrac{u}{v}\right)' = \dfrac{u'v - uv'}{v^2}`,
                 r`\text{Titik stasioner: } f'(x) = 0`],
                [[r`Tentukan turunan pertama dari $f(x) = 3x^4 - 5x^2 + 7x - 9$!`,
                  [r`$f'(x) = 3(4)x^{3} - 5(2)x^{1} + 7 - 0$`, r`$f'(x) = \mathbf{12x^3 - 10x + 7}$`]],
                 [r`Tentukan $f'(x)$ jika $f(x) = (2x+1)(x^2-3)$!`,
                  [r`$u = 2x+1 \Rightarrow u' = 2$;  $v = x^2-3 \Rightarrow v' = 2x$`, r`$f'(x) = 2(x^2-3) + (2x+1)(2x)$`, r`$= 2x^2 - 6 + 4x^2 + 2x = \mathbf{6x^2 + 2x - 6}$`]]]),
            mk(8, "12", "Integral Tak Tentu & Tentu", "sigma",
                "Antiturunan suatu fungsi aljabar serta penerapannya dalam menghitung luas daerah di bawah kurva.",
                r`Integral adalah operasi kebalikan dari turunan (antidiferensial). Integral tak tentu selalu disertai konstanta $+C$, sedangkan integral tentu memiliki batas atas dan bawah.`,
                [r`\int a x^n\,dx = \dfrac{a}{n+1}\,x^{n+1} + C \quad (n \neq -1)`,
                 r`\int k\,dx = kx + C`,
                 r`\int_a^b f(x)\,dx = F(b) - F(a)`],
                [[r`Tentukan hasil dari $\displaystyle\int (6x^2 + 4x - 3)\,dx$!`,
                  [r`$= \dfrac{6}{3}x^3 + \dfrac{4}{2}x^2 - 3x + C$`, r`$= \mathbf{2x^3 + 2x^2 - 3x + C}$`]],
                 [r`Hitung $\displaystyle\int_1^3 (2x + 1)\,dx$!`,
                  [r`$= \bigl[x^2 + x\bigr]_1^3$`, r`$= (9 + 3) - (1 + 1) = \mathbf{10}$`]]]),
            mk(9, "12", "Kaidah Pencacahan & Peluang", "dice-5",
                "Aturan perkalian, permutasi (memperhatikan urutan), kombinasi (tanpa urutan), dan peluang kejadian.",
                r`Kaidah pencacahan menghitung banyaknya cara menyusun objek. Permutasi memperhatikan urutan ($AB \neq BA$), sedangkan kombinasi mengabaikan urutan ($AB = BA$).`,
                [r`P(n, r) = \dfrac{n!}{(n-r)!}`,
                 r`C(n, r) = \dfrac{n!}{r!\,(n-r)!}`,
                 r`P(A) = \dfrac{n(A)}{n(S)}`,
                 r`F_h = P(A) \times \text{banyak percobaan}`],
                [[r`Dari $7$ siswa akan dipilih $3$ pengurus inti (Ketua, Sekretaris, Bendahara). Berapa susunan yang mungkin?`,
                  [r`Jabatan berbeda, urutan diperhatikan (permutasi):`, r`$P(7,3) = \dfrac{7!}{(7-3)!} = \dfrac{7!}{4!}$`, r`$= 7 \times 6 \times 5 = \mathbf{210}$ cara`]],
                 [r`Dari $6$ pria dan $4$ wanita dipilih $3$ orang terdiri atas $2$ pria dan $1$ wanita. Berapa cara?`,
                  [r`$C(6,2) \times C(4,1)$`, r`$= 15 \times 4 = \mathbf{60}$ cara`]]]),
            mk(10, "10", "Persamaan & Fungsi Kuadrat", "spline",
                "Akar-akar persamaan kuadrat, diskriminan, jumlah-hasil kali akar, dan titik puncak parabola.",
                r`Persamaan kuadrat berbentuk $ax^2 + bx + c = 0$ ($a \neq 0$). Akarnya dicari dengan pemfaktoran, melengkapkan kuadrat, atau rumus abc. Grafik fungsi kuadrat berupa parabola dengan titik puncak sebagai nilai maksimum/minimum.`,
                [r`D = b^2 - 4ac`,
                 r`D \gt 0:\ \text{dua akar real berbeda};\quad D = 0:\ \text{akar kembar};\quad D \lt 0:\ \text{tak real}`,
                 r`x_{1,2} = \dfrac{-b \pm \sqrt{D}}{2a}`,
                 r`x_1 + x_2 = -\dfrac{b}{a} \qquad x_1 \cdot x_2 = \dfrac{c}{a}`,
                 r`\text{Titik puncak: } \left(-\dfrac{b}{2a},\ -\dfrac{D}{4a}\right)`],
                [[r`Tentukan akar-akar dari $x^2 - 5x + 6 = 0$!`,
                  [r`Faktorkan: $(x-2)(x-3) = 0$`, r`Maka $x = 2$ atau $x = 3$.`]],
                 [r`Tentukan titik puncak $f(x) = x^2 - 6x + 5$!`,
                  [r`$a = 1,\ b = -6,\ c = 5$`, r`$x_p = -\dfrac{b}{2a} = \dfrac{6}{2} = 3$`, r`$y_p = f(3) = 9 - 18 + 5 = -4$`, r`Titik puncak $= (3, -4)$, minimum karena $a \gt 0$.`]]]),
            mk(11, "10", "Sistem Persamaan & Pertidaksamaan", "scale",
                "Menyelesaikan SPLDV dengan eliminasi-substitusi dan pertidaksamaan nilai mutlak.",
                r`Sistem persamaan linear dua variabel (SPLDV) diselesaikan dengan eliminasi atau substitusi. Nilai mutlak $|x|$ menyatakan jarak $x$ ke $0$, sehingga pertidaksamaannya diubah menjadi pertidaksamaan rentang.`,
                [r`|x| \lt a \iff -a \lt x \lt a`,
                 r`|x| \gt a \iff x \lt -a \ \text{atau}\ x \gt a`,
                 r`\text{Dikali/dibagi bilangan negatif} \Rightarrow \text{tanda pertidaksamaan dibalik}`],
                [[r`Selesaikan $2x + y = 7$ dan $x - y = 2$!`,
                  [r`Jumlahkan kedua persamaan: $3x = 9 \Rightarrow x = 3$`, r`Substitusi: $3 - y = 2 \Rightarrow y = 1$`, r`$HP = \{(3, 1)\}$`]],
                 [r`Tentukan penyelesaian $|2x - 1| \lt 5$!`,
                  [r`$-5 \lt 2x - 1 \lt 5$`, r`$-4 \lt 2x \lt 6$`, r`$\mathbf{-2 \lt x \lt 3}$`]]]),
            mk(12, "10", "Statistika Data Tunggal", "bar-chart-3",
                "Ukuran pemusatan (mean, median, modus), kuartil, dan ukuran penyebaran data.",
                r`Statistika mengolah dan menyajikan data. Ukuran pemusatan menunjukkan nilai tengah data, sedangkan ragam dan simpangan baku menunjukkan seberapa menyebar data dari rata-ratanya.`,
                [r`\bar{x} = \dfrac{\sum x_i}{n}`,
                 r`s^2 = \dfrac{\sum (x_i - \bar{x})^2}{n} \qquad s = \sqrt{s^2}`,
                 r`\text{Median: nilai tengah data terurut}`,
                 r`\text{Jangkauan antarkuartil: } Q_3 - Q_1`],
                [[r`Tentukan mean, median, dan modus dari data $4, 6, 8, 8, 9$!`,
                  [r`Mean $= \dfrac{4+6+8+8+9}{5} = \dfrac{35}{5} = 7$`, r`Median (data ke-3) $= 8$`, r`Modus $= 8$`]],
                 [r`Tentukan simpangan baku data $2, 4, 4, 4, 5, 5, 7, 9$!`,
                  [r`Mean $= \dfrac{40}{8} = 5$`, r`$\sum (x_i - 5)^2 = 9+1+1+1+0+0+4+16 = 32$`, r`$s^2 = \dfrac{32}{8} = 4 \ \Rightarrow\ s = \sqrt4 = \mathbf{2}$`]]]),
            mk(13, "11", "Vektor", "move-up-right",
                "Besaran berarah: panjang vektor, operasi, perkalian skalar (dot), dan sudut antar vektor.",
                r`Vektor adalah besaran yang memiliki besar dan arah, dinyatakan dengan komponen $(x, y, z)$. Perkalian titik (dot product) menghasilkan skalar dan dipakai untuk mencari sudut serta proyeksi.`,
                [r`|\vec a| = \sqrt{a_1^2 + a_2^2 + a_3^2}`,
                 r`\vec a \cdot \vec b = a_1 b_1 + a_2 b_2 + a_3 b_3 = |\vec a||\vec b|\cos\theta`,
                 r`\cos\theta = \dfrac{\vec a \cdot \vec b}{|\vec a|\,|\vec b|}`,
                 r`\vec a \perp \vec b \iff \vec a \cdot \vec b = 0`,
                 r`\text{Proyeksi skalar } \vec a \text{ pada } \vec b = \dfrac{\vec a \cdot \vec b}{|\vec b|}`],
                [[r`Tentukan panjang vektor $\vec a = (2, 1, -2)$!`,
                  [r`$|\vec a| = \sqrt{2^2 + 1^2 + (-2)^2} = \sqrt{9} = \mathbf{3}$`]],
                 [r`Tunjukkan $\vec a = (3, 4)$ dan $\vec b = (4, -3)$ saling tegak lurus!`,
                  [r`$\vec a \cdot \vec b = 3\cdot4 + 4\cdot(-3) = 12 - 12 = 0$`, r`Karena hasil kali titik $= 0$, maka $\vec a \perp \vec b$.`]]]),
            mk(14, "11", "Polinomial (Suku Banyak)", "variable",
                "Teorema sisa, teorema faktor, dan pembagian suku banyak.",
                r`Polinomial adalah bentuk aljabar berderajat $n$: $f(x) = a_n x^n + \cdots + a_1 x + a_0$. Pembagian dapat dipercepat dengan teorema sisa dan teorema faktor tanpa pembagian panjang.`,
                [r`f(x) = (x - k)\,H(x) + S \quad \text{dengan } S = f(k)`,
                 r`\text{Teorema sisa: sisa } f(x) : (x-k) = f(k)`,
                 r`\text{Teorema faktor: } (x-k) \text{ faktor } f(x) \iff f(k) = 0`,
                 r`\text{Akar rasional: } \pm\dfrac{\text{faktor } a_0}{\text{faktor } a_n}`],
                [[r`Tentukan sisa pembagian $f(x) = x^3 - 2x^2 + x - 5$ oleh $(x - 2)$!`,
                  [r`Sisa $= f(2) = 8 - 8 + 2 - 5 = \mathbf{-3}$`]],
                 [r`Faktorkan $f(x) = x^3 - 6x^2 + 11x - 6$!`,
                  [r`$f(1) = 1 - 6 + 11 - 6 = 0 \Rightarrow (x-1)$ faktor.`, r`Hasil bagi: $x^2 - 5x + 6 = (x-2)(x-3)$`, r`$f(x) = \mathbf{(x-1)(x-2)(x-3)}$`]]]),
            mk(15, "11", "Trigonometri Lanjut", "waves",
                "Identitas trigonometri, rumus jumlah/selisih sudut, dan sudut rangkap.",
                r`Rumus jumlah-selisih dan sudut rangkap memungkinkan kita menghitung nilai trigonometri sudut non-istimewa (seperti $75^\circ$ atau $15^\circ$) dengan menguraikannya menjadi sudut istimewa.`,
                [r`\sin^2\theta + \cos^2\theta = 1 \qquad 1 + \tan^2\theta = \sec^2\theta`,
                 r`\sin(A \pm B) = \sin A\cos B \pm \cos A\sin B`,
                 r`\cos(A \pm B) = \cos A\cos B \mp \sin A\sin B`,
                 r`\sin 2A = 2\sin A\cos A`,
                 r`\cos 2A = \cos^2 A - \sin^2 A = 1 - 2\sin^2 A = 2\cos^2 A - 1`],
                [[r`Tentukan nilai $\sin 75^\circ$!`,
                  [r`$\sin 75^\circ = \sin(45^\circ + 30^\circ)$`, r`$= \sin45^\circ\cos30^\circ + \cos45^\circ\sin30^\circ$`, r`$= \dfrac{\sqrt2}{2}\cdot\dfrac{\sqrt3}{2} + \dfrac{\sqrt2}{2}\cdot\dfrac12$`, r`$= \dfrac{\sqrt6 + \sqrt2}{4}$`]],
                 [r`Jika $\sin A = \dfrac35$ ($A$ lancip), tentukan $\sin 2A$!`,
                  [r`$\cos A = \dfrac45$ (segitiga 3-4-5)`, r`$\sin 2A = 2\sin A\cos A = 2\cdot\dfrac35\cdot\dfrac45 = \dfrac{24}{25}$`]]]),
            mk(16, "12", "Aplikasi Turunan", "line-chart",
                "Fungsi naik/turun, titik stasioner, nilai maksimum-minimum, dan masalah optimasi.",
                r`Turunan pertama menunjukkan kemiringan grafik. Titik stasioner terjadi saat $f'(x) = 0$; uji turunan kedua menentukan apakah titiknya maksimum atau minimum. Konsep ini dipakai untuk masalah optimasi.`,
                [r`f'(x) \gt 0 \Rightarrow \text{naik} \qquad f'(x) \lt 0 \Rightarrow \text{turun}`,
                 r`\text{Titik stasioner: } f'(x) = 0`,
                 r`f''(x) \lt 0 \Rightarrow \text{maksimum} \qquad f''(x) \gt 0 \Rightarrow \text{minimum}`,
                 r`\text{Garis singgung di } x = a:\ \ y - f(a) = f'(a)(x - a)`],
                [[r`Tentukan titik stasioner dan jenisnya untuk $f(x) = x^3 - 3x^2 + 2$!`,
                  [r`$f'(x) = 3x^2 - 6x = 3x(x-2) = 0 \Rightarrow x = 0$ atau $x = 2$`, r`$f''(x) = 6x - 6$`, r`$x = 0$: $f'' = -6 \lt 0$ → maksimum, $f(0) = 2$`, r`$x = 2$: $f'' = 6 \gt 0$ → minimum, $f(2) = -2$`]],
                 [r`Persegi panjang berkeliling $40$ cm. Tentukan luas maksimumnya!`,
                  [r`$p + l = 20 \Rightarrow l = 20 - p$`, r`$L(p) = p(20 - p) = 20p - p^2$`, r`$L'(p) = 20 - 2p = 0 \Rightarrow p = 10,\ l = 10$`, r`Luas maksimum $= \mathbf{100}\ \text{cm}^2$`]]]),
            mk(17, "12", "Luas & Volume dengan Integral", "shapes",
                "Menghitung luas daerah di bawah kurva, di antara dua kurva, dan volume benda putar.",
                r`Integral tentu dapat ditafsirkan sebagai luas daerah di bawah kurva. Jika daerah diputar mengelilingi sumbu-$x$, terbentuk benda putar yang volumenya dihitung dengan integral kuadrat fungsi.`,
                [r`L = \int_a^b f(x)\,dx`,
                 r`L = \int_a^b \bigl[f(x) - g(x)\bigr]\,dx \quad (f \geq g)`,
                 r`V = \pi \int_a^b \bigl[f(x)\bigr]^2\,dx`],
                [[r`Hitung luas daerah di bawah $y = x^2$ dari $x = 0$ sampai $x = 3$!`,
                  [r`$L = \displaystyle\int_0^3 x^2\,dx = \left[\dfrac{x^3}{3}\right]_0^3$`, r`$= \dfrac{27}{3} - 0 = \mathbf{9}$ satuan luas`]],
                 [r`Hitung volume benda putar dari $y = x$, $0 \leq x \leq 2$, diputar mengelilingi sumbu-$x$!`,
                  [r`$V = \pi\displaystyle\int_0^2 x^2\,dx = \pi\left[\dfrac{x^3}{3}\right]_0^2$`, r`$= \dfrac{8\pi}{3}$ satuan volume (kerucut)`]]]),
            mk(18, "12", "Peluang Bersyarat & Binomial", "dices",
                "Peluang kejadian bersyarat, kejadian saling bebas, dan distribusi binomial.",
                r`Peluang bersyarat adalah peluang $A$ jika $B$ sudah terjadi. Percobaan Bernoulli yang diulang $n$ kali dengan peluang sukses tetap $p$ mengikuti distribusi binomial.`,
                [r`P(A \mid B) = \dfrac{P(A \cap B)}{P(B)}`,
                 r`\text{Saling bebas: } P(A \cap B) = P(A)\cdot P(B)`,
                 r`P(X = k) = C(n,k)\,p^k\,q^{\,n-k} \quad (q = 1 - p)`,
                 r`\mu = n\,p`],
                [[r`Kotak berisi $5$ bola merah dan $3$ biru. Diambil $2$ bola berturut-turut tanpa pengembalian. Berapa peluang keduanya merah?`,
                  [r`$P(M_1) = \dfrac58,\quad P(M_2 \mid M_1) = \dfrac47$`, r`$P = \dfrac58 \times \dfrac47 = \dfrac{20}{56} = \dfrac{5}{14}$`]],
                 [r`Sebuah koin dilempar $3$ kali. Berapa peluang muncul tepat $2$ angka?`,
                  [r`$n = 3,\ k = 2,\ p = \dfrac12$`, r`$P = C(3,2)\left(\dfrac12\right)^2\left(\dfrac12\right)^1 = 3 \times \dfrac18 = \dfrac38$`]]])
            ].sort((a, b) => a.grade - b.grade || a.id - b.id);
        })();

        // 2. DATA KUIS INTERAKTIF
        const quizQuestions = [
            {
                topic: "Eksponen & Logaritma (Kelas X)",
                question: "Nilai dari ³log 27 + ³log 9 - ³log 3 adalah ...",
                options: ["3", "4", "5", "6"],
                correctIndex: 1,
                explanation: "³log 27 = 3 (karena 3³ = 27), ³log 9 = 2 (karena 3² = 9), dan ³log 3 = 1. Maka 3 + 2 - 1 = 4."
            },
            {
                topic: "Trigonometri (Kelas X)",
                question: "Jika diketahui sin α = 3/5 dan α adalah sudut lancip, maka nilai dari cos α adalah ...",
                options: ["4/5", "3/4", "5/4", "2/5"],
                correctIndex: 0,
                explanation: "Gunakan tripel Pythagoras: sisi depan = 3, sisi miring = 5, maka sisi samping = √(5² - 3²) = √16 = 4. Jadi cos α = samping/miring = 4/5."
            },
            {
                topic: "Matriks (Kelas XI)",
                question: "Diketahui matriks A = [5  2 ; 7  3]. Nilai determinan matriks A adalah ...",
                options: ["-1", "1", "15", "29"],
                correctIndex: 1,
                explanation: "det(A) = (5 × 3) - (2 × 7) = 15 - 14 = 1."
            },
            {
                topic: "Barisan & Deret (Kelas X/XI)",
                question: "Jumlah deret geometri tak hingga dari 8 + 4 + 2 + 1 + ... adalah ...",
                options: ["12", "15", "16", "24"],
                correctIndex: 2,
                explanation: "Suku pertama a = 8, rasio r = 4/8 = 1/2. Rumus S∞ = a / (1 - r) = 8 / (1 - 1/2) = 8 / (1/2) = 16."
            },
            {
                topic: "Turunan Fungsi (Kelas XII)",
                question: "Turunan pertama dari fungsi f(x) = 2x³ - 4x² + 5x - 8 adalah ...",
                options: [
                    "6x² - 8x + 5",
                    "6x² - 4x + 5",
                    "5x² - 8x + 5",
                    "6x³ - 8x² + 5x"
                ],
                correctIndex: 0,
                explanation: "f'(x) = 2(3)x² - 4(2)x¹ + 5(1)x⁰ - 0 = 6x² - 8x + 5."
            },
            {
                topic: "Peluang (Kelas XII)",
                question: "Dua buah dadu dilempar undi bersama-sama satu kali. Peluang munculnya mata dadu berjumlah 7 adalah ...",
                options: ["1/12", "1/9", "1/6", "7/36"],
                correctIndex: 2,
                explanation: "Ruang sampel dua dadu n(S) = 36. Pasangan berjumlah 7 ada 6 yaitu: (1,6), (2,5), (3,4), (4,3), (5,2), (6,1). Peluang = 6/36 = 1/6."
            }
        ];

        // 3. INISIALISASI TEMA (DARK/LIGHT MODE) & MENU MOBILE
        const htmlEl = document.documentElement;
        const themeToggleBtn = document.getElementById('theme-toggle');

        // Cek preferensi tersimpan
        if (localStorage.getItem('mathverse-theme') === 'dark' || 
            (!localStorage.getItem('mathverse-theme') && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
            htmlEl.classList.add('dark');
        }

        themeToggleBtn.addEventListener('click', () => {
            htmlEl.classList.toggle('dark');
            localStorage.setItem('mathverse-theme', htmlEl.classList.contains('dark') ? 'dark' : 'light');
        });

        // Mobile Menu Toggle
        const mobileMenuBtn = document.getElementById('mobile-menu-btn');
        const mobileMenu = document.getElementById('mobile-menu');
        mobileMenuBtn.addEventListener('click', () => {
            mobileMenu.classList.toggle('hidden');
        });
        document.querySelectorAll('.mobile-link').forEach(link => {
            link.addEventListener('click', () => mobileMenu.classList.add('hidden'));
        });

        // 4. RENDER MATERI & FILTER KELAS
        const materialsGrid = document.getElementById('materials-grid');
        const gradeTabs = document.querySelectorAll('.grade-tab');

        function renderMaterials(filterGrade = 'all') {
            materialsGrid.innerHTML = '';
            const filtered = filterGrade === 'all' 
                ? materialsData 
                : materialsData.filter(item => item.grade === filterGrade);

            filtered.forEach(item => {
                const badgeColors = {
                    indigo: 'bg-indigo-100 text-indigo-700 dark:bg-indigo-950 dark:text-indigo-300',
                    amber: 'bg-amber-100 text-amber-700 dark:bg-amber-950 dark:text-amber-300',
                    teal: 'bg-teal-100 text-teal-700 dark:bg-teal-950 dark:text-teal-300'
                };

                const card = document.createElement('div');
                card.className = 'group bg-slate-50 dark:bg-slate-900 rounded-3xl p-6 border border-slate-200 dark:border-slate-800 hover:border-indigo-500 dark:hover:border-indigo-500 shadow-sm hover:shadow-xl transition-all duration-300 cursor-pointer flex flex-col justify-between animate-fade-in';
                card.onclick = () => openMaterialModal(item.id);

                card.innerHTML = `
                    <div>
                        <div class="flex items-center justify-between mb-4">
                            <span class="text-xs font-extrabold px-3 py-1 rounded-full ${badgeColors[item.color]}">${item.gradeLabel}</span>
                            <div class="w-10 h-10 rounded-xl bg-white dark:bg-slate-800 border border-slate-200 dark:border-slate-700 flex items-center justify-center text-indigo-600 dark:text-indigo-400 group-hover:scale-110 transition-transform">
                                <i data-lucide="${item.icon}" class="w-5 h-5"></i>
                            </div>
                        </div>
                        <h3 class="text-xl font-bold mb-2 group-hover:text-indigo-600 dark:group-hover:text-indigo-400 transition-colors">${item.title}</h3>
                        <p class="text-sm text-slate-600 dark:text-slate-400 leading-relaxed mb-6">${item.summary}</p>
                    </div>
                    <div class="pt-4 border-t border-slate-200/80 dark:border-slate-800 flex items-center justify-between text-sm font-bold text-indigo-600 dark:text-indigo-400">
                        <span>Buka Rumus & Contoh</span>
                        <i data-lucide="arrow-up-right" class="w-4 h-4 group-hover:translate-x-0.5 group-hover:-translate-y-0.5 transition-transform"></i>
                    </div>
                `;
                materialsGrid.appendChild(card);
            });

            lucide.createIcons();
        }

        // Event Listener Tab Kelas
        gradeTabs.forEach(tab => {
            tab.addEventListener('click', () => {
                gradeTabs.forEach(t => {
                    t.classList.remove('bg-indigo-600', 'text-white', 'shadow-md', 'shadow-indigo-500/25');
                    t.classList.add('bg-slate-100', 'dark:bg-slate-800', 'text-slate-700', 'dark:text-slate-300');
                });
                tab.classList.remove('bg-slate-100', 'dark:bg-slate-800', 'text-slate-700', 'dark:text-slate-300');
                tab.classList.add('bg-indigo-600', 'text-white', 'shadow-md', 'shadow-indigo-500/25');

                renderMaterials(tab.dataset.grade);
            });
        });

        // 5. MODAL DETAIL MATERI
        const materialModal = document.getElementById('material-modal');

        function openMaterialModal(id) {
            const item = materialsData.find(m => m.id === id);
            if (!item) return;

            document.getElementById('modal-grade-badge').textContent = item.gradeLabel;
            document.getElementById('modal-title').textContent = item.title;
            document.getElementById('modal-concept').innerHTML = item.concept;
            document.getElementById('modal-examples').innerHTML = item.examples.map((ex, i) => `
                <div class="p-4 rounded-2xl bg-indigo-50/70 dark:bg-indigo-950/40 border border-indigo-100 dark:border-indigo-900/60 space-y-3">
                    <div>
                        <span class="text-xs font-bold uppercase text-indigo-600 dark:text-indigo-400">Contoh Soal ${i + 1}:</span>
                        <p class="font-semibold text-slate-800 dark:text-slate-100 mt-1 leading-relaxed">${ex.q}</p>
                    </div>
                    <div class="pt-2 border-t border-indigo-200/60 dark:border-indigo-800/60">
                        <span class="text-xs font-bold uppercase text-teal-600 dark:text-teal-400">Pembahasan:</span>
                        <div class="text-slate-700 dark:text-slate-300 mt-1 leading-loose">${ex.a.map(l => `<div class="step-line">${l}</div>`).join('')}</div>
                    </div>
                </div>`).join('');

            document.getElementById('modal-formulas').innerHTML = item.formulas.map(f =>
                `<div class="formula-box px-4 py-2 rounded-xl bg-white dark:bg-slate-900 border border-slate-200/80 dark:border-slate-700 text-indigo-700 dark:text-indigo-300 overflow-x-auto">$$${f}$$</div>`
            ).join('');

            if (window.renderMathInElement) {
                renderMathInElement(materialModal, {
                    delimiters: [{left: '$$', right: '$$', display: true}, {left: '$', right: '$', display: false}],
                    throwOnError: false
                });
            }
            materialModal.querySelector('.overflow-y-auto').scrollTop = 0;

            materialModal.classList.remove('hidden');
            materialModal.classList.add('flex');
            document.body.style.overflow = 'hidden';
        }

        function closeMaterialModal() {
            materialModal.classList.add('hidden');
            materialModal.classList.remove('flex');
            document.body.style.overflow = '';
        }

        materialModal.addEventListener('click', (e) => {
            if (e.target === materialModal) closeMaterialModal();
        });

        // 6. KALKULATOR INTERAKTIF
        function calculateQuadratic() {
            const a = parseFloat(document.getElementById('quad-a').value);
            const b = parseFloat(document.getElementById('quad-b').value);
            const c = parseFloat(document.getElementById('quad-c').value);

            if (isNaN(a) || isNaN(b) || isNaN(c)) return;
            if (a === 0) {
                document.getElementById('quad-eq-display').textContent = "Bukan persamaan kuadrat (a ≠ 0)";
                document.getElementById('quad-disc-display').textContent = "-";
                document.getElementById('quad-nature-display').textContent = "Koefisien a tidak boleh 0";
                document.getElementById('quad-roots-display').textContent = "-";
                return;
            }

            const signB = b >= 0 ? `+ ${b}` : `- ${Math.abs(b)}`;
            const signC = c >= 0 ? `+ ${c}` : `- ${Math.abs(c)}`;
            document.getElementById('quad-eq-display').textContent = `${a}x² ${signB}x ${signC} = 0`;

            const D = (b * b) - (4 * a * c);
            document.getElementById('quad-disc-display').textContent = Number(D.toFixed(4));

            const natureEl = document.getElementById('quad-nature-display');
            const rootsEl = document.getElementById('quad-roots-display');

            if (D > 0) {
                const x1 = (-b + Math.sqrt(D)) / (2 * a);
                const x2 = (-b - Math.sqrt(D)) / (2 * a);
                natureEl.textContent = "Dua akar real berbeda (D > 0)";
                natureEl.className = "font-semibold text-emerald-600 dark:text-emerald-400";
                rootsEl.textContent = `x₁ = ${Number(x1.toFixed(3))}, x₂ = ${Number(x2.toFixed(3))}`;
            } else if (D === 0) {
                const x = -b / (2 * a);
                natureEl.textContent = "Dua akar real kembar (D = 0)";
                natureEl.className = "font-semibold text-amber-600 dark:text-amber-400";
                rootsEl.textContent = `x₁ = x₂ = ${Number(x.toFixed(3))}`;
            } else {
                const realPart = (-b / (2 * a)).toFixed(2);
                const imagPart = (Math.sqrt(Math.abs(D)) / (2 * a)).toFixed(2);
                natureEl.textContent = "Akar imajiner / tidak real (D < 0)";
                natureEl.className = "font-semibold text-rose-600 dark:text-rose-400";
                rootsEl.textContent = `${realPart} ± ${imagPart}i`;
            }
        }

        function switchToolTab(tab) {
            const seqPanel = document.getElementById('tool-panel-seq');
            const trigPanel = document.getElementById('tool-panel-trig');
            const seqBtn = document.getElementById('tool-tab-seq');
            const trigBtn = document.getElementById('tool-tab-trig');

            if (tab === 'seq') {
                seqPanel.classList.remove('hidden');
                trigPanel.classList.add('hidden');
                seqBtn.className = "px-3 py-1.5 rounded-lg bg-white dark:bg-slate-700 shadow-sm text-indigo-600 dark:text-indigo-300";
                trigBtn.className = "px-3 py-1.5 rounded-lg text-slate-500 dark:text-slate-400";
            } else {
                seqPanel.classList.add('hidden');
                trigPanel.classList.remove('hidden');
                trigBtn.className = "px-3 py-1.5 rounded-lg bg-white dark:bg-slate-700 shadow-sm text-indigo-600 dark:text-indigo-300";
                seqBtn.className = "px-3 py-1.5 rounded-lg text-slate-500 dark:text-slate-400";
            }
        }

        function calculateSequence() {
            const a = parseFloat(document.getElementById('seq-a').value) || 0;
            const b = parseFloat(document.getElementById('seq-b').value) || 0;
            const n = parseInt(document.getElementById('seq-n').value) || 1;

            const un = a + (n - 1) * b;
            const sn = (n / 2) * (a + un);

            document.getElementById('seq-un-display').textContent = `U${n} = ${Number(un.toFixed(2))}`;
            document.getElementById('seq-sn-display').textContent = `S${n} = ${Number(sn.toFixed(2))}`;

            const preview = [];
            for (let i = 0; i < 5; i++) {
                preview.push(Number((a + i * b).toFixed(2)));
            }
            document.getElementById('seq-preview-display').textContent = preview.join(', ') + ', ...';
        }

        function setTrigAngle(deg) {
            document.getElementById('trig-deg').value = deg;
            calculateTrig();
        }

        function calculateTrig() {
            const deg = parseFloat(document.getElementById('trig-deg').value) || 0;
            const rad = deg * (Math.PI / 180);

            const sinVal = Math.sin(rad);
            const cosVal = Math.cos(rad);
            
            document.getElementById('trig-sin').textContent = Math.abs(sinVal) < 1e-10 ? '0' : Number(sinVal.toFixed(4));
            document.getElementById('trig-cos').textContent = Math.abs(cosVal) < 1e-10 ? '0' : Number(cosVal.toFixed(4));

            if (Math.abs(cosVal) < 1e-10) {
                document.getElementById('trig-tan').textContent = 'Tak Terdefinisi';
            } else {
                const tanVal = Math.tan(rad);
                document.getElementById('trig-tan').textContent = Math.abs(tanVal) < 1e-10 ? '0' : Number(tanVal.toFixed(4));
            }
        }

        // 7. LOGIKA KUIS INTERAKTIF
        let currentQuizIdx = 0;
        let correctAnswersCount = 0;
        let hasAnsweredCurrent = false;
        let quizTimerInterval = null;
        let timeLeftSeconds = 180;

        function startQuiz() {
            currentQuizIdx = 0;
            correctAnswersCount = 0;
            hasAnsweredCurrent = false;
            clearInterval(quizTimerInterval);

            document.getElementById('quiz-start-screen').classList.add('hidden');
            document.getElementById('quiz-result-screen').classList.add('hidden');
            document.getElementById('quiz-question-screen').classList.remove('hidden');

            document.getElementById('quiz-total-num').textContent = quizQuestions.length;
            document.getElementById('quiz-live-score').textContent = '0';

            const useTimer = document.getElementById('quiz-timer-toggle').checked;
            const timerBox = document.getElementById('quiz-timer-box');
            
            if (useTimer) {
                timerBox.classList.remove('hidden');
                timeLeftSeconds = 180; // 3 Menit
                updateTimerDisplay();
                quizTimerInterval = setInterval(() => {
                    timeLeftSeconds--;
                    updateTimerDisplay();
                    if (timeLeftSeconds <= 0) {
                        clearInterval(quizTimerInterval);
                        finishQuiz(true);
                    }
                }, 1000);
            } else {
                timerBox.classList.add('hidden');
            }

            renderQuestion();
        }

        function updateTimerDisplay() {
            const mins = Math.floor(timeLeftSeconds / 60).toString().padStart(2, '0');
            const secs = (timeLeftSeconds % 60).toString().padStart(2, '0');
            document.getElementById('quiz-timer-text').textContent = `${mins}:${secs}`;
        }

        function renderQuestion() {
            hasAnsweredCurrent = false;
            const q = quizQuestions[currentQuizIdx];

            document.getElementById('quiz-topic-badge').textContent = q.topic;
            document.getElementById('quiz-current-num').textContent = currentQuizIdx + 1;
            document.getElementById('quiz-question-text').textContent = q.question;

            const progress = ((currentQuizIdx + 1) / quizQuestions.length) * 100;
            document.getElementById('quiz-progress-bar').style.width = `${progress}%`;

            // Sembunyikan feedback & tombol next
            const feedbackBox = document.getElementById('quiz-feedback-box');
            feedbackBox.classList.add('hidden');
            const nextBtn = document.getElementById('quiz-next-btn');
            nextBtn.classList.add('hidden');
            nextBtn.classList.remove('inline-flex');

            // Render Opsi
            const optionsContainer = document.getElementById('quiz-options-container');
            optionsContainer.innerHTML = '';
            const letters = ['A', 'B', 'C', 'D'];

            q.options.forEach((optText, idx) => {
                const btn = document.createElement('button');
                btn.className = 'quiz-option-btn w-full text-left p-4 rounded-2xl border-2 border-slate-200 dark:border-slate-800 hover:border-indigo-500 dark:hover:border-indigo-500 bg-slate-50/50 dark:bg-slate-800/40 font-medium flex items-center gap-3.5 transition-all';
                btn.onclick = () => selectAnswer(idx);

                btn.innerHTML = `
                    <span class="w-8 h-8 rounded-xl bg-white dark:bg-slate-800 border border-slate-300 dark:border-slate-700 flex items-center justify-center font-bold text-sm shrink-0">${letters[idx]}</span>
                    <span>${optText}</span>
                `;
                optionsContainer.appendChild(btn);
            });
        }

        function selectAnswer(selectedIdx) {
            if (hasAnsweredCurrent) return;
            hasAnsweredCurrent = true;

            const q = quizQuestions[currentQuizIdx];
            const isCorrect = selectedIdx === q.correctIndex;
            const optionBtns = document.querySelectorAll('.quiz-option-btn');

            optionBtns.forEach((btn, idx) => {
                btn.disabled = true;
                btn.classList.remove('hover:border-indigo-500');

                if (idx === q.correctIndex) {
                    btn.classList.remove('border-slate-200', 'dark:border-slate-800');
                    btn.classList.add('border-emerald-500', 'bg-emerald-50', 'dark:bg-emerald-950/50', 'text-emerald-900', 'dark:text-emerald-100');
                } else if (idx === selectedIdx && !isCorrect) {
                    btn.classList.remove('border-slate-200', 'dark:border-slate-800');
                    btn.classList.add('border-rose-500', 'bg-rose-50', 'dark:bg-rose-950/50', 'text-rose-900', 'dark:text-rose-100');
                }
            });

            if (isCorrect) {
                correctAnswersCount++;
                const liveScore = Math.round((correctAnswersCount / quizQuestions.length) * 100);
                document.getElementById('quiz-live-score').textContent = liveScore;
            }

            // Tampilkan Umpan Balik
            const feedbackBox = document.getElementById('quiz-feedback-box');
            const feedbackTitle = document.getElementById('quiz-feedback-title');
            const feedbackExp = document.getElementById('quiz-feedback-explanation');

            feedbackBox.classList.remove('hidden', 'bg-emerald-50', 'border-emerald-200', 'dark:bg-emerald-950/40', 'dark:border-emerald-800', 'bg-rose-50', 'border-rose-200', 'dark:bg-rose-950/40', 'dark:border-rose-800');

            if (isCorrect) {
                feedbackBox.classList.add('bg-emerald-50', 'border-emerald-200', 'dark:bg-emerald-950/40', 'dark:border-emerald-800');
                feedbackTitle.innerHTML = `<i data-lucide="check-circle" class="w-5 h-5 text-emerald-600"></i> <span class="text-emerald-700 dark:text-emerald-400">Jawaban Benar!</span>`;
            } else {
                feedbackBox.classList.add('bg-rose-50', 'border-rose-200', 'dark:bg-rose-950/40', 'dark:border-rose-800');
                feedbackTitle.innerHTML = `<i data-lucide="x-circle" class="w-5 h-5 text-rose-600"></i> <span class="text-rose-700 dark:text-rose-400">Kurang Tepat!</span>`;
            }

            feedbackExp.textContent = q.explanation;
            lucide.createIcons();

            const nextBtn = document.getElementById('quiz-next-btn');
            nextBtn.innerHTML = currentQuizIdx === quizQuestions.length - 1 
                ? `Lihat Hasil Akhir <i data-lucide="award" class="w-4 h-4"></i>` 
                : `Soal Berikutnya <i data-lucide="arrow-right" class="w-4 h-4"></i>`;
            nextBtn.classList.remove('hidden');
            nextBtn.classList.add('inline-flex');
            lucide.createIcons();
        }

        function nextQuestion() {
            if (currentQuizIdx < quizQuestions.length - 1) {
                currentQuizIdx++;
                renderQuestion();
            } else {
                finishQuiz(false);
            }
        }

        function finishQuiz(isTimeout) {
            clearInterval(quizTimerInterval);
            document.getElementById('quiz-question-screen').classList.add('hidden');
            document.getElementById('quiz-result-screen').classList.remove('hidden');

            const finalScore = Math.round((correctAnswersCount / quizQuestions.length) * 100);
            document.getElementById('result-final-score').textContent = finalScore;
            document.getElementById('result-correct-count').textContent = correctAnswersCount;
            document.getElementById('result-total-count').textContent = quizQuestions.length;

            const msgEl = document.getElementById('result-message');
            if (isTimeout) {
                msgEl.textContent = "Waktu habis! Berikut adalah hasil pengerjaanmu.";
            } else if (finalScore >= 80) {
                msgEl.textContent = "Luar biasa! Pemahaman konsep Matematika SMA kamu sangat kuat.";
            } else if (finalScore >= 50) {
                msgEl.textContent = "Cukup baik! Pelajari kembali beberapa rumus di bagian materi untuk hasil maksimal.";
            } else {
                msgEl.textContent = "Jangan menyerah! Baca ringkasan rumus & contoh soal di atas, lalu coba lagi.";
            }
        }

        // Inisialisasi awal saat halaman dimuat
        window.addEventListener('DOMContentLoaded', () => {
            renderMaterials('all');
            calculateQuadratic();
            calculateSequence();
            calculateTrig();
            lucide.createIcons();
        });
    </script>
</body>
</html>
