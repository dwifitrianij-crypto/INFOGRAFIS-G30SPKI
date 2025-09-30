<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>G30S/PKI - Gen Z Edition</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            overflow-x: hidden;
        }

        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
        }

        .hero {
            text-align: center;
            padding: 60px 20px;
            color: white;
            animation: fadeInDown 1s ease;
        }

        .hero h1 {
            font-size: 3em;
            margin-bottom: 20px;
            text-shadow: 3px 3px 6px rgba(0,0,0,0.3);
            animation: glow 2s ease-in-out infinite alternate;
        }

        @keyframes glow {
            from { text-shadow: 0 0 20px #fff, 0 0 30px #ff0080; }
            to { text-shadow: 0 0 30px #fff, 0 0 40px #ff0080; }
        }

        .subtitle {
            font-size: 1.3em;
            opacity: 0;
            animation: fadeIn 1s ease 0.5s forwards;
        }

        .timeline {
            position: relative;
            padding: 40px 0;
        }

        .timeline::before {
            content: '';
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
            width: 4px;
            height: 100%;
            background: linear-gradient(to bottom, #ff6b6b, #4ecdc4);
            animation: lineGrow 2s ease;
        }

        @keyframes lineGrow {
            from { height: 0; }
            to { height: 100%; }
        }

        .timeline-item {
            margin: 40px 0;
            position: relative;
            opacity: 0;
            animation: slideIn 0.8s ease forwards;
        }

        .timeline-item:nth-child(1) { animation-delay: 0.2s; }
        .timeline-item:nth-child(2) { animation-delay: 0.4s; }
        .timeline-item:nth-child(3) { animation-delay: 0.6s; }
        .timeline-item:nth-child(4) { animation-delay: 0.8s; }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .card {
            background: white;
            border-radius: 20px;
            padding: 30px;
            margin: 20px 0;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .card:hover {
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 20px 40px rgba(0,0,0,0.3);
        }

        .card h2 {
            color: #667eea;
            margin-bottom: 15px;
            font-size: 1.8em;
        }

        .card-emoji {
            font-size: 3em;
            display: block;
            margin-bottom: 15px;
            animation: bounce 2s infinite;
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }

        .hero-list {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin: 30px 0;
        }

        .hero-card {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            color: white;
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            transform: rotateY(0deg);
            transition: all 0.6s ease;
        }

        .hero-card:hover {
            transform: rotateY(180deg);
        }

        .fact-box {
            background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%);
            border-left: 5px solid #ff6b6b;
            padding: 20px;
            margin: 15px 0;
            border-radius: 10px;
            animation: pulse 3s infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.02); }
        }

        .quote-box {
            background: linear-gradient(135deg, #a8edea 0%, #fed6e3 100%);
            padding: 30px;
            border-radius: 20px;
            margin: 30px 0;
            font-style: italic;
            font-size: 1.3em;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .quote-box::before {
            content: '"';
            font-size: 8em;
            position: absolute;
            top: -20px;
            left: 20px;
            color: rgba(255,255,255,0.5);
        }

        .action-btn {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 15px 40px;
            border: none;
            border-radius: 50px;
            font-size: 1.2em;
            cursor: pointer;
            margin: 10px;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }

        .action-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.3);
        }

        .floating-emoji {
            position: fixed;
            font-size: 2em;
            animation: float 6s ease-in-out infinite;
            pointer-events: none;
            z-index: 1000;
        }

        @keyframes float {
            0%, 100% {
                transform: translateY(0) rotate(0deg);
            }
            25% {
                transform: translateY(-30px) rotate(5deg);
            }
            50% {
                transform: translateY(-60px) rotate(-5deg);
            }
            75% {
                transform: translateY(-30px) rotate(5deg);
            }
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 20px;
            margin: 30px 0;
        }

        .stat-card {
            background: white;
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .stat-number {
            font-size: 3em;
            font-weight: bold;
            color: #667eea;
            animation: countUp 2s ease;
        }

        @keyframes countUp {
            from { opacity: 0; transform: scale(0); }
            to { opacity: 1; transform: scale(1); }
        }

        .hashtags {
            text-align: center;
            padding: 30px;
            color: white;
            font-size: 1.2em;
        }

        .hashtags span {
            display: inline-block;
            margin: 5px 10px;
            animation: fadeIn 1s ease forwards;
            opacity: 0;
        }

        .hashtags span:nth-child(1) { animation-delay: 0.2s; }
        .hashtags span:nth-child(2) { animation-delay: 0.4s; }
        .hashtags span:nth-child(3) { animation-delay: 0.6s; }
        .hashtags span:nth-child(4) { animation-delay: 0.8s; }

        @keyframes fadeIn {
            to { opacity: 1; }
        }

        @keyframes fadeInDown {
            from {
                opacity: 0;
                transform: translateY(-50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .scroll-indicator {
            text-align: center;
            color: white;
            font-size: 1.2em;
            margin: 20px 0;
            animation: bounce 2s infinite;
        }
    </style>
</head>
<body>
    <div class="floating-emoji" style="top: 10%; left: 10%;">🇮🇩</div>
    <div class="floating-emoji" style="top: 20%; right: 15%; animation-delay: 1s;">🕊️</div>
    <div class="floating-emoji" style="bottom: 15%; left: 20%; animation-delay: 2s;">📚</div>
    <div class="floating-emoji" style="bottom: 25%; right: 10%; animation-delay: 3s;">✨</div>

    <div class="hero">
        <h1>G30S/PKI</h1>
        <p class="subtitle">Fakta Kelam yang Gak Boleh Dilupakan 🔥</p>
        <div class="scroll-indicator">👇 Scroll ke bawah untuk lanjut 👇</div>
    </div>

    <div class="container">
        <div class="card">
            <span class="card-emoji">📅</span>
            <h2>Apa Sih G30S/PKI?</h2>
            <p>Gerakan 30 September adalah peristiwa berdarah yang terjadi pada <strong>30 September - 1 Oktober 1965</strong>. Malam itu, 7 perwira tinggi TNI AD diculik dan dibunuh secara tragis.</p>
        </div>

        <div class="card">
            <span class="card-emoji">⏰</span>
            <h2>Timeline Singkat</h2>
            <div class="timeline">
                <div class="timeline-item">
                    <div class="fact-box">
                        <strong>Malam 30 Sept 1965 (23:00)</strong><br>
                        Sekelompok pasukan mulai menculik para jenderal dari rumah mereka
                    </div>
                </div>
                <div class="timeline-item">
                    <div class="fact-box">
                        <strong>Dini Hari 1 Okt 1965</strong><br>
                        6 jenderal dibunuh dan jasadnya dibuang ke Lubang Buaya
                    </div>
                </div>
                <div class="timeline-item">
                    <div class="fact-box">
                        <strong>Siang 1 Okt 1965</strong><br>
                        Soeharto mengambil alih kepemimpinan TNI AD
                    </div>
                </div>
                <div class="timeline-item">
                    <div class="fact-box">
                        <strong>4 Okt 1965</strong><br>
                        Jenazah para pahlawan ditemukan
                    </div>
                </div>
            </div>
        </div>

        <div class="card">
            <span class="card-emoji">🦸</span>
            <h2>Para Pahlawan Revolusi</h2>
            <div class="stats-grid">
                <div class="stat-card">
                    <div class="stat-number">7</div>
                    <p>Pahlawan Gugur</p>
                </div>
                <div class="stat-card">
                    <div class="stat-number">1</div>
                    <p>Jenderal Selamat</p>
                </div>
                <div class="stat-card">
                    <div class="stat-number">1</div>
                    <p>Putri Pahlawan Gugur</p>
                </div>
            </div>
            <div class="hero-list">
                <div class="hero-card">Letjen Ahmad Yani</div>
                <div class="hero-card">Mayjen R. Suprapto</div>
                <div class="hero-card">Mayjen M.T. Haryono</div>
                <div class="hero-card">Mayjen S. Parman</div>
                <div class="hero-card">Brigjen D.I. Panjaitan</div>
                <div class="hero-card">Brigjen Sutoyo</div>
                <div class="hero-card">Lettu Pierre Tendean</div>
            </div>
        </div>

        <div class="card">
            <span class="card-emoji">💡</span>
            <h2>Kenapa Ini Penting Banget?</h2>
            <div class="fact-box">✅ Menghargai pengorbanan para pahlawan</div>
            <div class="fact-box">✅ Belajar dari kesalahan sejarah</div>
            <div class="fact-box">✅ Memahami fondasi Indonesia modern</div>
            <div class="fact-box">✅ Menjaga persatuan dan kesatuan bangsa</div>
        </div>

        <div class="card">
            <span class="card-emoji">🔥</span>
            <h2>Fun Facts</h2>
            <div class="fact-box">
                <strong>#1</strong> - Penculikan dilakukan tengah malam dengan dalih "melindungi Presiden"
            </div>
            <div class="fact-box">
                <strong>#2</strong> - Lubang Buaya kini jadi museum untuk mengenang para pahlawan
            </div>
            <div class="fact-box">
                <strong>#3</strong> - Sampai sekarang masih ada perdebatan siapa dalang sebenarnya
            </div>
            <div class="fact-box">
                <strong>#4</strong> - Setiap 1 Oktober diperingati sebagai Hari Kesaktian Pancasila
            </div>
        </div>

        <div class="quote-box">
            Bangsa yang besar adalah bangsa yang menghargai jasa pahlawannya
        </div>

        <div class="quote-box">
            "Jas Merah: Jangan Sekali-kali Melupakan Sejarah" - Ir. Soekarno
        </div>

        <div class="card">
            <span class="card-emoji">🎯</span>
            <h2>Pelajaran untuk Gen Z</h2>
            <div class="fact-box">📱 <strong>Cek Fakta</strong> - Jangan mudah percaya provokasi atau hoax</div>
            <div class="fact-box">🤝 <strong>Persatuan</strong> - Jangan biarkan perbedaan memecah belah kita</div>
            <div class="fact-box">⭐ <strong>Pancasila</strong> - Ideologi negara yang harus dijaga bersama</div>
            <div class="fact-box">🧠 <strong>Critical Thinking</strong> - Belajar sejarah dari berbagai sudut pandang</div>
        </div>

        <div class="card" style="text-align: center;">
            <span class="card-emoji">✊</span>
            <h2>Yang Bisa Kita Lakukan</h2>
            <button class="action-btn" onclick="alert('Kunjungi Monumen Pancasila Sakti di Jakarta Timur!')">📍 Kunjungi Museum</button>
            <button class="action-btn" onclick="alert('Baca buku sejarah dari perpustakaan atau online!')">📚 Baca Buku Sejarah</button>
            <button class="action-btn" onclick="alert('Share konten edukasi ini ke teman-temanmu!')">📲 Share ke Teman</button>
            <button class="action-btn" onclick="alert('Mari jaga persatuan Indonesia di dunia nyata dan digital!')">🇮🇩 Jaga Persatuan</button>
        </div>

        <div class="hashtags">
            <span>#BelajarSejarah</span>
            <span>#G30SPKI</span>
            <span>#PahlawanRevolusi</span>
            <span>#GenZPeduli</span>
            <span>#PancasilaSakti</span>
        </div>

        <div class="card" style="background: linear-gradient(135deg, #ffeaa7 0%, #fdcb6e 100%);">
            <h2 style="color: #d63031;">⚠️ Disclaimer</h2>
            <p>Materi ini dibuat untuk edukasi berdasarkan sumber-sumber terpercaya. G30S/PKI adalah peristiwa kompleks dengan berbagai perspektif historis. Penting untuk membaca dari berbagai sumber dan berpikir kritis.</p>
        </div>
    </div>

    <script>
        // Add smooth scroll animation
        document.addEventListener('DOMContentLoaded', function() {
            const cards = document.querySelectorAll('.card');
            
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.style.opacity = '1';
                        entry.target.style.transform = 'translateY(0)';
                    }
                });
            }, { threshold: 0.1 });

            cards.forEach(card => {
                card.style.opacity = '0';
                card.style.transform = 'translateY(50px)';
                card.style.transition = 'all 0.6s ease';
                observer.observe(card);
            });
        });

        // Interactive hero cards flip
        const heroCards = document.querySelectorAll('.hero-card');
        heroCards.forEach(card => {
            card.addEventListener('click', function() {
                this.style.transform = this.style.transform === 'rotateY(180deg)' ? 'rotateY(0deg)' : 'rotateY(180deg)';
            });
        });
    </script>
</body>
</html>
