[kbase.html](https://github.com/user-attachments/files/29297126/kbase.html)
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kbase — Knowledge Management System</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #2563eb;
            --primary-dark: #1d4ed8;
            --primary-light: #dbeafe;
            --surface: #ffffff;
            --surface-2: #f8fafc;
            --surface-3: #f1f5f9;
            --text: #0f172a;
            --text-secondary: #475569;
            --text-muted: #94a3b8;
            --border: #e2e8f0;
            --shadow-sm: 0 1px 2px 0 rgb(0 0 0 / 0.05);
            --shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
            --shadow-lg: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
            --radius: 12px;
            --radius-sm: 8px;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            font-family: 'Inter', sans-serif;
            background: var(--surface-2);
            color: var(--text);
            line-height: 1.6;
            height: 100vh;
            overflow: hidden;
        }

        /* Layout */
        .app {
            display: grid;
            grid-template-columns: 280px 1fr;
            height: 100vh;
        }

        @media (max-width: 768px) {
            .app {
                grid-template-columns: 1fr;
                grid-template-rows: auto 1fr;
            }
        }

        /* Sidebar */
        .sidebar {
            background: var(--surface);
            border-right: 1px solid var(--border);
            display: flex;
            flex-direction: column;
            padding: 24px 0;
            overflow-y: auto;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 0 24px 24px;
            border-bottom: 1px solid var(--border);
            margin-bottom: 16px;
        }

        .logo-icon {
            width: 40px; height: 40px;
            background: linear-gradient(135deg, var(--primary), var(--primary-dark));
            border-radius: var(--radius-sm);
            display: flex; align-items: center; justify-content: center;
            color: white; font-weight: 700; font-size: 18px;
        }

        .logo-text h1 { font-size: 18px; font-weight: 700; }
        .logo-text p { font-size: 12px; color: var(--text-muted); margin-top: 2px; }

        .nav-section { padding: 0 16px; margin-bottom: 8px; }
        .nav-title {
            font-size: 11px; font-weight: 600; text-transform: uppercase;
            letter-spacing: 0.5px; color: var(--text-muted);
            padding: 0 12px; margin-bottom: 8px;
        }

        .nav-item {
            display: flex; align-items: center; gap: 12px;
            padding: 10px 12px; border-radius: var(--radius-sm);
            cursor: pointer; transition: all 0.2s;
            font-size: 14px; font-weight: 500; color: var(--text-secondary);
            margin-bottom: 2px;
        }

        .nav-item:hover { background: var(--surface-3); color: var(--text); }
        .nav-item.active { background: var(--primary-light); color: var(--primary); }

        .nav-icon { width: 20px; height: 20px; display: flex; align-items: center; justify-content: center; }

        /* Main Content */
        .main {
            display: flex; flex-direction: column;
            overflow: hidden;
        }

        .header {
            background: var(--surface);
            border-bottom: 1px solid var(--border);
            padding: 20px 32px;
            display: flex; align-items: center; justify-content: space-between;
            gap: 24px;
        }

        .search-box {
            flex: 1; max-width: 520px;
            position: relative;
        }

        .search-box input {
            width: 100%; padding: 12px 16px 12px 44px;
            border: 1px solid var(--border); border-radius: var(--radius);
            background: var(--surface-2); font-size: 14px;
            transition: all 0.2s; font-family: inherit;
        }

        .search-box input:focus {
            outline: none; border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
            background: var(--surface);
        }

        .search-icon {
            position: absolute; left: 14px; top: 50%; transform: translateY(-50%);
            color: var(--text-muted);
        }

        .header-actions {
            display: flex; align-items: center; gap: 12px;
        }

        .btn {
            padding: 10px 20px; border-radius: var(--radius);
            font-size: 14px; font-weight: 500; cursor: pointer;
            border: none; transition: all 0.2s; font-family: inherit;
            display: inline-flex; align-items: center; gap: 8px;
        }

        .btn-primary {
            background: var(--primary); color: white;
        }
        .btn-primary:hover { background: var(--primary-dark); }

        .btn-ghost {
            background: transparent; color: var(--text-secondary);
            border: 1px solid var(--border);
        }
        .btn-ghost:hover { background: var(--surface-3); }

        /* Content Area */
        .content {
            flex: 1; overflow-y: auto;
            padding: 32px;
        }

        .content-inner { max-width: 1000px; margin: 0 auto; }

        /* Hero Section */
        .hero {
            background: linear-gradient(135deg, #1e293b, #0f172a);
            color: white; padding: 48px;
            border-radius: var(--radius); margin-bottom: 32px;
            position: relative; overflow: hidden;
        }

        .hero::before {
            content: ''; position: absolute; top: -50%; right: -10%;
            width: 400px; height: 400px;
            background: radial-gradient(circle, rgba(37,99,235,0.3), transparent 70%);
            border-radius: 50%;
        }

        .hero h2 { font-size: 32px; font-weight: 700; margin-bottom: 12px; position: relative; }
        .hero p { font-size: 16px; color: #94a3b8; max-width: 560px; position: relative; }

        /* Quick Stats */
        .stats {
            display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px; margin-bottom: 32px;
        }

        .stat-card {
            background: var(--surface); padding: 24px;
            border-radius: var(--radius); border: 1px solid var(--border);
            transition: box-shadow 0.2s;
        }
        .stat-card:hover { box-shadow: var(--shadow); }
        .stat-card .stat-value { font-size: 28px; font-weight: 700; color: var(--primary); }
        .stat-card .stat-label { font-size: 14px; color: var(--text-secondary); margin-top: 4px; }

        /* Section */
        .section { margin-bottom: 40px; }
        .section-header {
            display: flex; align-items: center; justify-content: space-between;
            margin-bottom: 20px;
        }
        .section-title { font-size: 20px; font-weight: 700; }
        .section-link { font-size: 14px; color: var(--primary); cursor: pointer; }
        .section-link:hover { text-decoration: underline; }

        /* Cards */
        .card-grid {
            display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
        }

        .card {
            background: var(--surface); border: 1px solid var(--border);
            border-radius: var(--radius); padding: 24px;
            transition: all 0.2s; cursor: pointer;
        }
        .card:hover {
            box-shadow: var(--shadow); border-color: var(--primary);
            transform: translateY(-2px);
        }

        .card-icon {
            width: 40px; height: 40px; border-radius: var(--radius-sm);
            background: var(--primary-light); color: var(--primary);
            display: flex; align-items: center; justify-content: center;
            font-size: 18px; margin-bottom: 16px;
        }
        .card-title { font-size: 16px; font-weight: 600; margin-bottom: 6px; }
        .card-desc { font-size: 14px; color: var(--text-secondary); line-height: 1.5; }
        .card-meta { font-size: 12px; color: var(--text-muted); margin-top: 14px; display: flex; gap: 16px; }

        /* FAQ */
        .faq-item {
            background: var(--surface); border: 1px solid var(--border);
            border-radius: var(--radius); margin-bottom: 12px; overflow: hidden;
        }
        .faq-question {
            padding: 20px 24px; display: flex; align-items: center; justify-content: space-between;
            cursor: pointer; font-weight: 600; font-size: 15px;
        }
        .faq-question:hover { background: var(--surface-2); }
        .faq-answer {
            padding: 0 24px; max-height: 0; overflow: hidden;
            transition: max-height 0.3s, padding 0.3s;
            font-size: 14px; color: var(--text-secondary); line-height: 1.7;
        }
        .faq-item.open .faq-answer { padding: 0 24px 20px; max-height: 500px; }
        .faq-chevron { transition: transform 0.3s; color: var(--text-muted); }
        .faq-item.open .faq-chevron { transform: rotate(180deg); }

        /* Article Detail */
        .article-view { display: none; }
        .article-view.active { display: block; animation: fadeIn 0.3s; }

        .breadcrumb {
            display: flex; align-items: center; gap: 8px;
            font-size: 14px; color: var(--text-muted); margin-bottom: 20px;
        }
        .breadcrumb a { color: var(--primary); text-decoration: none; cursor: pointer; }
        .breadcrumb a:hover { text-decoration: underline; }

        .article-body {
            background: var(--surface); border: 1px solid var(--border);
            border-radius: var(--radius); padding: 40px;
        }
        .article-body h1 { font-size: 28px; font-weight: 700; margin-bottom: 8px; }
        .article-body .article-meta { color: var(--text-muted); font-size: 14px; margin-bottom: 32px; }
        .article-body p { margin-bottom: 16px; font-size: 15px; color: var(--text-secondary); }
        .article-body h3 { font-size: 20px; font-weight: 600; margin: 28px 0 12px; }
        .article-body ul { margin-left: 20px; margin-bottom: 16px; color: var(--text-secondary); }
        .article-body li { margin-bottom: 8px; }
        .article-body code {
            background: var(--surface-3); padding: 2px 8px; border-radius: 4px;
            font-size: 13px; font-family: 'Fira Code', monospace;
        }
        .article-body pre {
            background: #1e293b; color: #e2e8f0; padding: 20px;
            border-radius: var(--radius-sm); overflow-x: auto; margin-bottom: 20px;
        }

        @keyframes fadeIn { from { opacity: 0; transform: translateY(8px); } to { opacity: 1; transform: translateY(0); } }

        /* Tag */
        .tag {
            display: inline-block; padding: 4px 12px; border-radius: 999px;
            font-size: 12px; font-weight: 500; background: var(--primary-light);
            color: var(--primary); margin-right: 6px; margin-bottom: 6px;
        }

        /* Mobile Toggle */
        .mobile-toggle {
            display: none; padding: 12px;
            background: none; border: none; cursor: pointer; font-size: 24px;
        }
        @media (max-width: 768px) {
            .mobile-toggle { display: block; }
            .sidebar {
                position: fixed; left: 0; top: 0; width: 280px; height: 100vh;
                z-index: 100; transform: translateX(-100%);
                transition: transform 0.3s;
            }
            .sidebar.open { transform: translateX(0); }
            .overlay {
                display: none; position: fixed; inset: 0; background: rgba(0,0,0,0.5); z-index: 99;
            }
            .overlay.show { display: block; }
            .content { padding: 20px; }
            .header { padding: 16px 20px; }
        }

        /* Search Results */
        .search-results { display: none; }
        .search-results.active { display: block; }
        .result-item {
            background: var(--surface); border: 1px solid var(--border);
            border-radius: var(--radius); padding: 20px; margin-bottom: 12px;
            cursor: pointer; transition: all 0.2s;
        }
        .result-item:hover { border-color: var(--primary); box-shadow: var(--shadow-sm); }
        .result-title { font-weight: 600; color: var(--primary); margin-bottom: 4px; }
        .result-snippet { font-size: 14px; color: var(--text-secondary); }
        .result-category { font-size: 12px; color: var(--text-muted); margin-top: 8px; }

        .hidden { display: none !important; }
    </style>
</head>
<body>
    <div class="overlay" id="overlay"></div>
    <div class="app">
        <!-- Sidebar -->
        <aside class="sidebar" id="sidebar">
            <div class="logo">
                <div class="logo-icon">K</div>
                <div class="logo-text">
                    <h1>Kbase</h1>
                    <p>Knowledge Management</p>
                </div>
            </div>

            <div class="nav-section">
                <div class="nav-title">Menu Utama</div>
                <div class="nav-item active" onclick="showHome()">
                    <span class="nav-icon">🏠</span> Beranda
                </div>
                <div class="nav-item" onclick="showCategory('semua')">
                    <span class="nav-icon">📚</span> Semua Artikel
                </div>
                <div class="nav-item" onclick="showCategory('faq')">
                    <span class="nav-icon">❓</span> FAQ
                </div>
            </div>

            <div class="nav-section">
                <div class="nav-title">Kategori</div>
                <div class="nav-item" onclick="showCategory('onboarding')">
                    <span class="nav-icon">🚀</span> Onboarding
                </div>
                <div class="nav-item" onclick="showCategory('panduan')">
                    <span class="nav-icon">📖</span> Panduan
                </div>
                <div class="nav-item" onclick="showCategory('api')">
                    <span class="nav-icon">🔌</span> API & Integrasi
                </div>
                <div class="nav-item" onclick="showCategory('troubleshooting')">
                    <span class="nav-icon">🔧</span> Troubleshooting
                </div>
                <div class="nav-item" onclick="showCategory('keamanan')">
                    <span class="nav-icon">🔒</span> Keamanan
                </div>
            </div>

            <div class="nav-section">
                <div class="nav-title">Bantuan</div>
                <div class="nav-item" onclick="showCategory('changelog')">
                    <span class="nav-icon">📋</span> Changelog
                </div>
                <div class="nav-item" onclick="showCategory('kontak')">
                    <span class="nav-icon">💬</span> Hubungi Kami
                </div>
            </div>
        </aside>

        <!-- Main -->
        <div class="main">
            <div class="header">
                <button class="mobile-toggle" onclick="toggleSidebar()">☰</button>
                <div class="search-box">
                    <span class="search-icon">🔍</span>
                    <input type="text" id="searchInput" placeholder="Cari artikel, panduan, atau jawaban FAQ..." oninput="handleSearch()">
                </div>
                <div class="header-actions">
                    <button class="btn btn-ghost">Masuk</button>
                    <button class="btn btn-primary">+ Artikel Baru</button>
                </div>
            </div>

            <div class="content" id="contentArea">
                <div class="content-inner">
                    <!-- HOME VIEW -->
                    <div id="homeView">
                        <div class="hero">
                            <h2>Selamat Datang di Kbase</h2>
                            <p>Temukan jawaban, panduan, dan dokumentasi lengkap untuk membantu Anda menggunakan produk kami dengan maksimal.</p>
                        </div>

                        <div class="stats">
                            <div class="stat-card">
                                <div class="stat-value">128</div>
                                <div class="stat-label">Artikel Tersedia</div>
                            </div>
                            <div class="stat-card">
                                <div class="stat-value">45</div>
                                <div class="stat-label">FAQ Terjawab</div>
                            </div>
                            <div class="stat-card">
                                <div class="stat-value">12</div>
                                <div class="stat-label">Topik Kategori</div>
                            </div>
                            <div class="stat-card">
                                <div class="stat-value">2.5k</div>
                                <div class="stat-label">Pengunjung Bulan Ini</div>
                            </div>
                        </div>

                        <div class="section">
                            <div class="section-header">
                                <h3 class="section-title">📚 Artikel Populer</h3>
                                <span class="section-link" onclick="showCategory('semua')">Lihat Semua →</span>
                            </div>
                            <div class="card-grid" id="popularArticles"></div>
                        </div>

                        <div class="section">
                            <div class="section-header">
                                <h3 class="section-title">❓ Pertanyaan yang Sering Diajukan</h3>
                                <span class="section-link" onclick="showCategory('faq')">Lihat Semua FAQ →</span>
                            </div>
                            <div id="faqPreview"></div>
                        </div>
                    </div>

                    <!-- SEARCH RESULTS -->
                    <div class="search-results" id="searchResults">
                        <div class="section-header">
                            <h3 class="section-title">🔍 Hasil Pencarian</h3>
                            <span class="section-link" onclick="clearSearch()">Bersihkan</span>
                        </div>
                        <div id="searchResultsList"></div>
                    </div>

                    <!-- ARTICLE LIST VIEW -->
                    <div class="article-view" id="articleListView">
                        <div class="section-header">
                            <h3 class="section-title" id="articleListTitle">Semua Artikel</h3>
                        </div>
                        <div class="card-grid" id="articleListGrid"></div>
                    </div>

                    <!-- ARTICLE DETAIL VIEW -->
                    <div class="article-view" id="articleDetailView">
                        <div class="breadcrumb">
                            <a onclick="showHome()">Beranda</a>
                            <span>/</span>
                            <a onclick="showCategory('semua')">Artikel</a>
                            <span>/</span>
                            <span id="articleDetailCategory">Panduan</span>
                        </div>
                        <div class="article-body" id="articleDetailContent"></div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // ===== DATA =====
        const articles = [
            {
                id: 1, title: "Memulai dengan Kbase: Panduan Pemula", category: "onboarding",
                desc: "Pelajari dasar-dasar menggunakan Kbase untuk mengelola pengetahuan tim Anda dengan efisien.",
                date: "2 hari lalu", readTime: "5 menit", author: "Tim Kbase",
                content: `<h1>Memulai dengan Kbase: Panduan Pemula</h1>
                <div class="article-meta">Dipublikasikan 2 hari lalu · 5 menit baca</div>
                <p>Selamat datang di Kbase! Panduan ini akan membantu Anda memahami fitur-fitur utama dan mulai mengelola pengetahuan tim Anda.</p>
                <h3>1. Membuat Ruang Kerja Pertama</h3>
                <p>Setelah masuk, buat ruang kerja baru dengan mengklik tombol <strong>+ Ruang Kerja</strong> di dashboard. Beri nama yang deskriptif dan tambahkan anggota tim.</p>
                <h3>2. Menulis Artikel Pertama</h3>
                <p>Klik tombol <strong>Artikel Baru</strong> di sidebar. Gunakan editor kaya untuk menambahkan teks, gambar, video, dan kode.</p>
                <h3>3. Mengatur Kategori</h3>
                <p>Organisasi adalah kunci. Buat kategori untuk mengelompokkan artikel berdasarkan topik, tim, atau proyek.</p>
                <ul>
                    <li>Klik <strong>Pengaturan</strong> → <strong>Kategori</strong></li>
                    <li>Tambah kategori baru</li>
                    <li>Seret artikel ke kategori yang sesuai</li>
                </ul>
                <h3>4. Berbagi dengan Tim</h3>
                <p>Setiap artikel dapat dibagikan melalui link publik atau dibatasi hanya untuk anggota tim tertentu.</p>`
            },
            {
                id: 2, title: "Cara Menggunakan API Kbase", category: "api",
                desc: "Dokumentasi lengkap untuk mengintegrasikan Kbase dengan aplikasi pihak ketiga melalui REST API.",
                date: "1 minggu lalu", readTime: "12 menit", author: "Engineering Team",
                content: `<h1>Cara Menggunakan API Kbase</h1>
                <div class="article-meta">Dipublikasikan 1 minggu lalu · 12 menit baca</div>
                <p>Kbase menyediakan REST API lengkap untuk mengelola artikel, kategori, dan pengguna secara programatis.</p>
                <h3>Autentikasi</h3>
                <p>Semua request API memerlukan API key. Dapatkan API key di halaman <strong>Pengaturan → API</strong>.</p>
                <pre>Authorization: Bearer kb_xxxxxxxxxxxxxxxx</pre>
                <h3>Mengambil Daftar Artikel</h3>
                <pre>GET /api/v1/articles
Content-Type: application/json</pre>
                <h3>Membuat Artikel Baru</h3>
                <pre>POST /api/v1/articles
{
  "title": "Artikel Baru",
  "content": "Konten artikel...",
  "category_id": "cat_123",
  "status": "published"
}</pre>
                <h3>Batas Rate Limit</h3>
                <p>Free tier: 100 request/jam. Pro tier: 10,000 request/jam.</p>`
            },
            {
                id: 3, title: "Mengatur Izin dan Keamanan", category: "keamanan",
                desc: "Pelajari cara mengatur izin pengguna, SSO, dan kebijakan keamanan untuk melindungi data organisasi.",
                date: "3 hari lalu", readTime: "8 menit", author: "Security Team",
                content: `<h1>Mengatur Izin dan Keamanan</h1>
                <div class="article-meta">Dipublikasikan 3 hari lalu · 8 menit baca</div>
                <p>Keamanan data adalah prioritas utama. Kbase menawarkan berbagai fitur kontrol akses untuk melindungi informasi organisasi Anda.</p>
                <h3>Peran Pengguna (Roles)</h3>
                <ul>
                    <li><strong>Admin</strong> — Akses penuh ke semua pengaturan dan artikel</li>
                    <li><strong>Editor</strong> — Dapat membuat, mengedit, dan menghapus artikel</li>
                    <li><strong>Viewer</strong> — Hanya dapat membaca artikel yang diizinkan</li>
                </ul>
                <h3>Single Sign-On (SSO)</h3>
                <p>Integrasikan Kbase dengan provider identitas perusahaan Anda seperti Google Workspace, Microsoft Azure AD, atau Okta.</p>
                <h3>Audit Log</h3>
                <p>Lacak setiap aktivitas pengguna termasuk login, edit, dan hapus artikel melalui menu <strong>Keamanan → Audit Log</strong>.</p>`
            },
            {
                id: 4, title: "Panduan Integrasi dengan Slack", category: "panduan",
                desc: "Hubungkan Kbase dengan Slack untuk notifikasi real-time dan pencarian artikel langsung dari chat.",
                date: "5 hari lalu", readTime: "6 menit", author: "Integration Team",
                content: `<h1>Panduan Integrasi dengan Slack</h1>
                <div class="article-meta">Dipublikasikan 5 hari lalu · 6 menit baca</div>
                <p>Dengan integrasi Slack, tim Anda dapat menerima notifikasi artikel baru dan mencari pengetahuan tanpa meninggalkan chat.</p>
                <h3>Langkah 1: Instal Aplikasi</h3>
                <p>Kunjungi <strong>Pengaturan → Integrasi → Slack</strong> dan klik <strong>Hubungkan</strong>.</p>
                <h3>Langkah 2: Pilih Channel</h3>
                <p>Pilih channel Slack tempat notifikasi akan dikirim. Anda juga dapat menambahkan beberapa channel untuk kategori berbeda.</p>
                <h3>Perintah Slash</h3>
                <ul>
                    <li><code>/kbase cari [kata kunci]</code> — Cari artikel</li>
                    <li><code>/kbase artikel baru</code> — Buat artikel dari Slack</li>
                </ul>`
            },
            {
                id: 5, title: "Mengelola Kategori dan Tag", category: "panduan",
                desc: "Tips dan trik untuk mengorganisasi artikel dengan sistem kategori dan tag yang efektif.",
                date: "1 minggu lalu", readTime: "7 menit", author: "Tim Kbase",
                content: `<h1>Mengelola Kategori dan Tag</h1>
                <div class="article-meta">Dipublikasikan 1 minggu lalu · 7 menit baca</div>
                <p>Struktur yang baik membuat pengetahuan mudah ditemukan. Pelajari strategi terbaik untuk mengorganisasi konten.</p>
                <h3>Best Practices Kategori</h3>
                <ul>
                    <li>Gunakan maksimal 5-7 kategori utama</li>
                    <li>Nama kategori harus jelas dan konsisten</li>
                    <li>Pertimbangkan perspektif pengguna, bukan internal</li>
                </ul>
                <h3>Tag vs Kategori</h3>
                <p><strong>Kategori</strong> untuk struktur besar (Onboarding, API, Troubleshooting). <strong>Tag</strong> untuk detail spesifik (v2.0, urgent, beta).</p>`
            },
            {
                id: 6, title: "Memperbaiki Error Sinkronisasi", category: "troubleshooting",
                desc: "Solusi untuk masalah sinkronisasi data antara Kbase dan integrasi pihak ketiga.",
                date: "2 minggu lalu", readTime: "10 menit", author: "Support Team",
                content: `<h1>Memperbaiki Error Sinkronisasi</h1>
                <div class="article-meta">Dipublikasikan 2 minggu lalu · 10 menit baca</div>
                <p>Jika data tidak sinkron antara Kbase dan integrasi eksternal, ikuti langkah-langkah pemecahan masalah berikut.</p>
                <h3>1. Periksa Status API</h3>
                <p>Kunjungi <a href="#">status.kbase.io</a> untuk memastikan layanan berjalan normal.</p>
                <h3>2. Verifikasi API Key</h3>
                <p>Pastikan API key masih aktif dan belum kedaluwarsa. Generate ulang jika perlu.</p>
                <h3>3. Force Sync</h3>
                <p>Di halaman integrasi, klik tombol <strong>Force Sync</strong> untuk memaksa sinkronisasi manual.</p>
                <h3>4. Hubungi Support</h3>
                <p>Jika masalah berlanjut, kirim log error ke support@kbase.io dengan ID ruang kerja Anda.</p>`
            }
        ];

        const faqs = [
            { q: "Apakah Kbase gratis untuk digunakan?", a: "Kbase menyediakan paket Free selamanya dengan 1 ruang kerja, 3 anggota tim, dan 100 artikel. Paket Pro mulai dari $9/bulan untuk fitur tak terbatas dan integrasi API." },
            { q: "Bagaimana cara mengimpor artikel dari platform lain?", a: "Kbase mendukung impor dari Notion, Confluence, Google Docs, dan Markdown. Masuk ke Pengaturan → Impor/Export, pilih sumber, dan ikuti langkah impor." },
            { q: "Bisakah saya mengatur artikel sebagai pribadi?", a: "Ya. Setiap artikel memiliki pengaturan visibilitas: Publik (siapa saja), Internal (hanya tim), atau Pribadi (hanya Anda)." },
            { q: "Apakah ada aplikasi mobile untuk Kbase?", a: "Ya. Kbase tersedia untuk iOS dan Android. Unduh dari App Store atau Google Play Store untuk mengakses artikel di mana saja." },
            { q: "Berapa batasan ukuran file yang bisa diunggah?", a: "Ukuran maksimal per file adalah 100MB untuk paket Free dan 500MB untuk paket Pro. Total storage tidak dibatasi untuk artikel teks." },
            { q: "Bagaimana cara mengaktifkan SSO untuk tim saya?", a: "SSO tersedia di paket Enterprise. Hubungi tim sales kami untuk mengaktifkan integrasi dengan SAML 2.0 provider seperti Okta, Azure AD, atau Google Workspace." }
        ];

        const categoryNames = {
            onboarding: "Onboarding", panduan: "Panduan", api: "API & Integrasi",
            troubleshooting: "Troubleshooting", keamanan: "Keamanan", changelog: "Changelog",
            kontak: "Hubungi Kami", semua: "Semua Artikel", faq: "FAQ"
        };

        // ===== INIT =====
        function init() {
            renderPopularArticles();
            renderFAQPreview();
        }

        function renderPopularArticles() {
            const grid = document.getElementById('popularArticles');
            grid.innerHTML = articles.slice(0, 3).map(a => `
                <div class="card" onclick="showArticle(${a.id})">
                    <div class="card-icon">📄</div>
                    <div class="card-title">${a.title}</div>
                    <div class="card-desc">${a.desc}</div>
                    <div class="card-meta">
                        <span>${a.readTime}</span>
                        <span>•</span>
                        <span>${a.date}</span>
                    </div>
                </div>
            `).join('');
        }

        function renderFAQPreview() {
            const container = document.getElementById('faqPreview');
            container.innerHTML = faqs.slice(0, 3).map((f, i) => `
                <div class="faq-item ${i === 0 ? 'open' : ''}">
                    <div class="faq-question" onclick="toggleFAQ(this.parentElement)">
                        <span>${f.q}</span>
                        <span class="faq-chevron">▼</span>
                    </div>
                    <div class="faq-answer">${f.a}</div>
                </div>
            `).join('');
        }

        function renderAllFAQ() {
            const container = document.getElementById('faqPreview');
            container.innerHTML = faqs.map((f, i) => `
                <div class="faq-item ${i === 0 ? 'open' : ''}">
                    <div class="faq-question" onclick="toggleFAQ(this.parentElement)">
                        <span>${f.q}</span>
                        <span class="faq-chevron">▼</span>
                    </div>
                    <div class="faq-answer">${f.a}</div>
                </div>
            `).join('');
        }

        function toggleFAQ(el) {
            el.classList.toggle('open');
        }

        // ===== NAVIGATION =====
        function hideAllViews() {
            document.getElementById('homeView').classList.add('hidden');
            document.getElementById('searchResults').classList.remove('active');
            document.getElementById('articleListView').classList.remove('active');
            document.getElementById('articleDetailView').classList.remove('active');
        }

        function showHome() {
            hideAllViews();
            document.getElementById('homeView').classList.remove('hidden');
            document.getElementById('searchInput').value = '';
            updateActiveNav('home');
        }

        function showCategory(cat) {
            hideAllViews();
            document.getElementById('articleListView').classList.add('active');
            document.getElementById('articleListTitle').textContent = categoryNames[cat] || cat;
            document.getElementById('searchInput').value = '';
            updateActiveNav(cat);

            const filtered = cat === 'semua' || cat === 'faq'
                ? articles
                : articles.filter(a => a.category === cat);

            const grid = document.getElementById('articleListGrid');
            if (cat === 'faq') {
                grid.innerHTML = '<div style="grid-column:1/-1">' + faqs.map(f => `
                    <div class="faq-item">
                        <div class="faq-question" onclick="toggleFAQ(this.parentElement)">
                            <span>${f.q}</span>
                            <span class="faq-chevron">▼</span>
                        </div>
                        <div class="faq-answer">${f.a}</div>
                    </div>
                `).join('') + '</div>';
                return;
            }

            grid.innerHTML = filtered.map(a => `
                <div class="card" onclick="showArticle(${a.id})">
                    <div class="card-icon">📄</div>
                    <div class="card-title">${a.title}</div>
                    <div class="card-desc">${a.desc}</div>
                    <div class="card-meta">
                        <span class="tag">${categoryNames[a.category] || a.category}</span>
                        <span>${a.readTime}</span>
                    </div>
                </div>
            `).join('');
        }

        function showArticle(id) {
            const article = articles.find(a => a.id === id);
            if (!article) return;

            hideAllViews();
            document.getElementById('articleDetailView').classList.add('active');
            document.getElementById('articleDetailCategory').textContent = categoryNames[article.category] || article.category;
            document.getElementById('articleDetailContent').innerHTML = article.content;
            document.getElementById('searchInput').value = '';
        }

        function updateActiveNav(cat) {
            document.querySelectorAll('.nav-item').forEach(el => el.classList.remove('active'));
            const navMap = {
                home: 0, semua: 1, faq: 2, onboarding: 3, panduan: 4, api: 5, troubleshooting: 6, keamanan: 7, changelog: 8, kontak: 9
            };
            const idx = navMap[cat];
            if (idx !== undefined) {
                document.querySelectorAll('.nav-item')[idx]?.classList.add('active');
            }
        }

        // ===== SEARCH =====
        function handleSearch() {
            const query = document.getElementById('searchInput').value.toLowerCase().trim();
            if (!query) {
                clearSearch();
                return;
            }

            hideAllViews();
            document.getElementById('searchResults').classList.add('active');

            const results = [];
            articles.forEach(a => {
                if (a.title.toLowerCase().includes(query) || a.desc.toLowerCase().includes(query)) {
                    results.push({ type: 'artikel', ...a });
                }
            });
            faqs.forEach((f, i) => {
                if (f.q.toLowerCase().includes(query) || f.a.toLowerCase().includes(query)) {
                    results.push({ type: 'faq', id: `faq-${i}`, title: f.q, snippet: f.a, category: 'FAQ' });
                }
            });

            const list = document.getElementById('searchResultsList');
            if (results.length === 0) {
                list.innerHTML = '<p style="color:var(--text-muted); text-align:center; padding:40px;">Tidak ada hasil untuk "' + escapeHtml(query) + '"</p>';
                return;
            }

            list.innerHTML = results.map(r => `
                <div class="result-item" onclick="${r.type === 'artikel' ? `showArticle(${r.id})` : `showCategory('faq')`}">
                    <div class="result-title">${highlight(r.title, query)}</div>
                    <div class="result-snippet">${highlight(r.snippet || r.desc, query)}</div>
                    <div class="result-category">${r.category}</div>
                </div>
            `).join('');
        }

        function clearSearch() {
            document.getElementById('searchInput').value = '';
            showHome();
        }

        function highlight(text, query) {
            const re = new RegExp('(' + escapeRegex(query) + ')', 'gi');
            return escapeHtml(text).replace(re, '<mark style="background:#fef08a; border-radius:2px;">$1</mark>');
        }

        function escapeHtml(text) {
            const div = document.createElement('div');
            div.textContent = text;
            return div.innerHTML;
        }

        function escapeRegex(str) {
            return str.replace(/[.*+?^${}()|[\]\\]/g, '\\$&');
        }

        // ===== MOBILE =====
        function toggleSidebar() {
            document.getElementById('sidebar').classList.toggle('open');
            document.getElementById('overlay').classList.toggle('show');
        }

        document.getElementById('overlay').addEventListener('click', () => {
            document.getElementById('sidebar').classList.remove('open');
            document.getElementById('overlay').classList.remove('show');
        });

        // ===== START =====
        init();
    </script>
</body>
</html>
