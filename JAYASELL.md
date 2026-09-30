<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jaya Sell - Toko Buah & Daging</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', sans-serif;
        }

        :root {
            --hijau: #22c55e;
            --merah: #ef4444;
            --coklat: #92400e;
            --biru: #3b82f6;
            --gelap: #0f172a;
            --abu: #1e293b;
        }

        body {
            background-color: var(--gelap);
            color: #fff;
            line-height: 1.6;
        }

        /* Navbar */
        nav {
            background-color: var(--abu);
            padding: 1rem 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 2px 10px #00000070;
        }

        .logo {
            font-size: 1.6rem;
            font-weight: bold;
            color: var(--hijau);
        }

        .nav-links {
            display: flex;
            gap: 2rem;
        }

        .nav-links a {
            color: #fff;
            text-decoration: none;
            transition: 0.3s;
        }

        .nav-links a:hover {
            color: var(--hijau);
        }

        .cart-btn {
            background: linear-gradient(90deg, var(--hijau), var(--biru));
            border: none;
            color: white;
            padding: 8px 16px;
            border-radius: 8px;
            cursor: pointer;
        }

        /* Hero Section */
        .hero {
            padding: 6rem 5%;
            text-align: center;
            background: radial-gradient(circle at center, #164e63 0%, var(--gelap) 70%);
        }

        .hero h1 {
            font-size: 2.8rem;
            margin-bottom: 1rem;
            color: var(--hijau);
        }

        .hero p {
            max-width: 600px;
            margin: 0 auto 2rem;
            opacity: 0.8;
        }

        .btn-primary {
            background: linear-gradient(90deg, var(--hijau), var(--biru));
            color: white;
            padding: 12px 28px;
            border-radius: 10px;
            border: none;
            font-size: 1rem;
            cursor: pointer;
            transition: 0.3s;
        }

        .btn-primary:hover {
            transform: scale(1.05);
        }

        /* Produk Section */
        .produk-section {
            padding: 4rem 5%;
        }

        .section-title {
            text-align: center;
            font-size: 2rem;
            margin-bottom: 3rem;
        }

        .grid-produk {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 2rem;
        }

        .card-produk {
            background: var(--abu);
            border-radius: 12px;
            overflow: hidden;
            transition: 0.3s;
        }

        .card-produk:hover {
            transform: translateY(-8px);
            box-shadow: 0 8px 20px #00000080;
        }

        .gambar-produk {
            height: 200px;
            background: #333;
            display: flex;
            align-items: center;
            justify-content: center;
            color:#aaa;
        }

        .info-produk {
            padding: 1.2rem;
        }

        .info-produk h3 {
            margin-bottom: 0.5rem;
        }

        .harga {
            color: #facc15;
            font-weight: bold;
            font-size:1.2rem;
            margin-bottom: 0.4rem;
        }

        .stok {
            font-size: 0.9rem;
            opacity: 0.85;
            margin-bottom: 1rem;
        }

        .btn-tambah {
            width: 100%;
            padding: 10px;
            background: linear-gradient(90deg, var(--hijau), var(--biru));
            border: none;
            color:white;
            border-radius: 8px;
            cursor:pointer;
        }
        .btn-tambah:disabled {
            background:#444;
            cursor:not-allowed;
            opacity:0.6;
        }

        /* Keranjang Modal */
        .modal-keranjang {
            position: fixed;
            top:0;
            right:-450px;
            width:420px;
            height:100vh;
            background:#1e293b;
            padding:2rem;
            transition: 0.4s ease;
            z-index: 200;
            box-shadow: -5px 0 20px #000;
            overflow-y:auto;
        }

        .modal-keranjang.open {
            right: 0;
        }

        .keranjang-header {
            display:flex;
            justify-content: space-between;
            align-items:center;
            margin-bottom: 1.5rem;
        }

        .close-cart {
            background: none;
            border:none;
            color:white;
            font-size:1.5rem;
            cursor:pointer;
        }

        .item-keranjang {
            display:flex;
            justify-content: space-between;
            padding:10px 0;
            border-bottom: 1px solid #333;
        }

        .total-harga {
            margin-top: 1.5rem;
            font-size:1.3rem;
            font-weight:bold;
        }

        .btn-checkout {
            width:100%;
            padding:12px;
            margin-top:1rem;
            background:#facc15;
            border:none;
            border-radius:8px;
            font-weight:bold;
            cursor:pointer;
        }

        /* Modal Pembayaran */
        .modal-pembayaran {
            position:fixed;
            top:0;
            left:0;
            width:100%;
            height:100vh;
            background:rgba(0,0,0,0.85);
            z-index:300;
            display:none;
            justify-content:center;
            align-items:center;
            padding:20px;
        }
        .modal-pembayaran.show {
            display:flex;
        }
        .box-pembayaran {
            background:#1e293b;
            padding:2rem;
            border-radius:12px;
            max-width:500px;
            width:100%;
        }
        .box-pembayaran h3 {
            margin-bottom:1rem;
        }
        .qris-img {
            width:100%;
            border-radius:8px;
            margin:1rem 0;
        }
        .step-pembayaran {
            margin:1rem 0;
        }
        .step-pembayaran li {
            margin:0.5rem 0;
        }
        .btn-tutup-pembayaran {
            width:100%;
            padding:12px;
            background:var(--hijau);
            border:none;
            color:white;
            border-radius:8px;
            margin-top:1rem;
            cursor:pointer;
        }

        /* Footer */
        footer {
            background: var(--abu);
            padding: 3rem 5%;
            text-align:center;
            margin-top:4rem;
        }

        /* Responsive HP */
        @media (max-width:768px) {
            .nav-links {
                display:none;
            }
            .modal-keranjang {
                width:100%;
            }
            .hero h1 {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <!-- Navbar -->
    <nav>
        <div class="logo">Jaya Sell</div>
        <div class="nav-links">
            <a href="#beranda">Beranda</a>
            <a href="#produk">Produk</a>
            <a href="#tentang">Tentang</a>
            <a href="#kontak">Kontak</a>
        </div>
        <button class="cart-btn" id="cartButton">🛒 Keranjang</button>
    </nav>

    <!-- Hero -->
    <section class="hero" id="beranda">
        <h1>Jaya Sell</h1>
        <p>Toko buah, daging, coklat & ikan segar, harga terjangkau!</p>
        <button class="btn-primary">Lihat Produk</button>
    </section>

    <!-- Produk -->
    <section class="produk-section" id="produk">
        <h2 class="section-title">Daftar Produk</h2>
        <div class="grid-produk">
            <div class="card-produk">
                <div class="gambar-produk">Gambar Stroberi</div>
                <div class="info-produk">
                    <h3>Stroberi</h3>
                    <div class="harga">Rp 100</div>
                    <div class="stok" data-stok="15">Stok: 15</div>
                    <button class="btn-tambah" data-nama="Stroberi" data-harga="100" data-stok="15">Tambah ke Keranjang</button>
                </div>
            </div>
            <div class="card-produk">
                <div class="gambar-produk">Gambar Daging</div>
                <div class="info-produk">
                    <h3>Daging</h3>
                    <div class="harga">Rp 1.000</div>
                    <div class="stok" data-stok="8">Stok: 8</div>
                    <button class="btn-tambah" data-nama="Daging" data-harga="1000" data-stok="8">Tambah ke Keranjang</button>
                </div>
            </div>
            <div class="card-produk">
                <div class="gambar-produk">Gambar Coklat</div>
                <div class="info-produk">
                    <h3>Coklat</h3>
                    <div class="harga">Rp 3.000</div>
                    <div class="stok" data-stok="10">Stok: 10</div>
                    <button class="btn-tambah" data-nama="Coklat" data-harga="3000" data-stok="10">Tambah ke Keranjang</button>
                </div>
            </div>
            <div class="card-produk">
                <div class="gambar-produk">Gambar Ikan</div>
                <div class="info-produk">
                    <h3>Ikan</h3>
                    <div class="harga">Rp 4.000</div>
                    <div class="stok" data-stok="5">Stok: 5</div>
                    <button class="btn-tambah" data-nama="Ikan" data-harga="4000" data-stok="5">Tambah ke Keranjang</button>
                </div>
            </div>
        </div>
    </section>

    <!-- Modal Keranjang Belanja -->
    <div class="modal-keranjang" id="cartModal">
        <div class="keranjang-header">
            <h2>Keranjang Belanja</h2>
            <button class="close-cart" id="closeCart">✕</button>
        </div>
        <div id="daftarItemKeranjang"></div>
        <div class="total-harga">Total: Rp <span id="totalHarga">0</span></div>
        <button class="btn-checkout" id="btnCheckout">Lanjut Pembayaran</button>
    </div>

    <!-- Modal Pembayaran QRIS -->
    <div class="modal-pembayaran" id="modalPembayaran">
        <div class="box-pembayaran">
            <h3>Metode Pembayaran QRIS</h3>
            <img src="https://ibb.co.com/Gv6pmSCK" alt="QRIS Jaya Sell" class="qris-img">
            <ul class="step-pembayaran">
                <li>1. Buka aplikasi e‑wallet (Gopay, OVO, Dana, ShopeePay)</li>
                <li>2. Pilih menu Scan QRIS</li>
                <li>3. Scan gambar QR di atas</li>
                <li>4. Masukkan jumlah total pembayaran</li>
                <li>5. Selesaikan pembayaran, simpan bukti transfer</li>
                <li>6. Kirim bukti transfer ke kontak kami untuk konfirmasi pesanan</li>
            </ul>
            <button class="btn-tutup-pembayaran" id="btnTutupPembayaran">Tutup</button>
        </div>
    </div>

    <footer>
        <p>&copy; 2026 Jaya Sell - Semua Hak Dilindungi</p>
    </footer>

<script>
    // Data produk dengan stok
    const dataProduk = {
        "Stroberi": {harga:100, stok:15},
        "Daging": {harga:1000, stok:8},
        "Coklat": {harga:3000, stok:10},
        "Ikan": {harga:4000, stok:5}
    };

    const cartModal = document.getElementById("cartModal");
    const cartButton = document.getElementById("cartButton");
    const closeCart = document.getElementById("closeCart");
    const daftarItemKeranjang = document.getElementById("daftarItemKeranjang");
    const totalHargaEl = document.getElementById("totalHarga");
    const btnCheckout = document.getElementById("btnCheckout");
    const modalPembayaran = document.getElementById("modalPembayaran");
    const btnTutupPembayaran = document.getElementById("btnTutupPembayaran");

    let keranjang = [];

    // Buka & Tutup Keranjang
    cartButton.addEventListener('click', ()=>{
        cartModal.classList.add("open");
    })
    closeCart.addEventListener('click', ()=>{
        cartModal.classList.remove("open");
    })

    // Buka modal pembayaran
    btnCheckout.addEventListener('click', ()=>{
        if(keranjang.length === 0){
            alert("Keranjang kamu kosong! Tambahkan produk dulu.");
            return;
        }
        cartModal.classList.remove("open");
        modalPembayaran.classList.add("show");
    })
    btnTutupPembayaran.addEventListener('click', ()=>{
        modalPembayaran.classList.remove("show");
    })

    // Tombol tambah produk ke keranjang
    const tombolTambah = document.querySelectorAll(".btn-tambah");
    tombolTambah.forEach(btn => {
        btn.addEventListener('click', ()=>{
            const nama = btn.dataset.nama;
            const harga = Number(btn.dataset.harga);
            const stokAwal = Number(btn.dataset.stok);

            // Hitung jumlah yang sudah ada di keranjang
            const jumlahDiKeranjang = keranjang.filter(item=>item.nama === nama).length;

            if(jumlahDiKeranjang >= stokAwal){
                alert(`Stok ${nama} sudah habis!`);
                btn.disabled = true;
                return;
            }

            keranjang.push({nama, harga});
            renderKeranjang();
            updateStatusStokTombol();
        })
    })

    // Update tombol jika stok habis
    function updateStatusStokTombol(){
        document.querySelectorAll(".btn-tambah").forEach(btn=>{
            const nama = btn.dataset.nama;
            const stokMax = Number(btn.dataset.stok);
            const jumlahDiKeranjang = keranjang.filter(item=>item.nama === nama).length;
            if(jumlahDiKeranjang >= stokMax){
                btn.disabled = true;
                btn.innerText = "Stok Habis";
            }
        })
    }

    // Render isi keranjang
    function renderKeranjang(){
        daftarItemKeranjang.innerHTML = "";
        let total = 0;
        keranjang.forEach((item, index)=>{
            total += item.harga;
            const divItem = document.createElement("div");
            divItem.className = "item-keranjang";
            divItem.innerHTML = `
                <span>${item.nama}</span>
                <span>Rp ${item.harga.toLocaleString('id-ID')}</span>
            `;
            daftarItemKeranjang.appendChild(divItem);
        })
        totalHargaEl.innerText = total.toLocaleString('id-ID');
    }
</script>
</body>
</html>
