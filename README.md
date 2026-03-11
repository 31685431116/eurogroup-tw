<!DOCTYPE html>
<html lang="zh-TW">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title data-lang-key="title">歐洲好物團購站 - EuroGroup TW</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;500;700&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css">
  <style>
    :root {
      --primary: #2c5282;
      --accent: #c9a96e;
      --success: #4a8c59;
      --dark: #1a202c;
      --light: #f7fafc;
      --gray: #edf2f7;
      --bg-gradient: linear-gradient(135deg, #f7fafc 0%, #edf2f7 100%);
    }
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body { font-family: 'Inter', sans-serif; background: var(--bg-gradient); color: var(--dark); line-height: 1.7; }
    header { background: linear-gradient(135deg, var(--dark) 0%, var(--primary) 100%); color: white; text-align: center; padding: 6rem 1rem 4rem; position: relative; }
    h1 { font-family: 'Playfair Display', serif; font-size: 3.5rem; margin-bottom: 0.8rem; }
    .tagline { font-size: 1.2rem; opacity: 0.9; max-width: 700px; margin: 0 auto; }
    .header-right { position: absolute; top: 1.5rem; right: 1rem; display: flex; align-items: center; gap: 1rem; z-index: 10; }
    .cart-icon { background: rgba(255,255,255,0.15); backdrop-filter: blur(10px); color: white; padding: 0.6rem 1.2rem; border-radius: 50px; cursor: pointer; font-weight: 500; transition: all 0.2s ease; }
    .cart-icon:hover { background: rgba(255,255,255,0.3); transform: translateY(-2px); }
    .lang-switcher select { background: rgba(255,255,255,0.15); backdrop-filter: blur(10px); color: white; border: 1px solid rgba(255,255,255,0.3); padding: 0.6rem 1rem; border-radius: 50px; font-size: 0.95rem; cursor: pointer; min-width: 120px; }
    .container { max-width: 1200px; margin: 0 auto; padding: 1rem; }
    .section-title { font-family: 'Playfair Display', serif; text-align: center; font-size: 2.5rem; margin: 3rem 0 2rem; color: var(--dark); }
    .product-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 2rem; }
    .product-card { background: white; border-radius: 20px; overflow: hidden; box-shadow: 0 8px 25px rgba(0,0,0,0.08); transition: transform 0.2s ease; }
    .product-card:hover { transform: translateY(-8px); }
    .product-img { width: 100%; height: 320px; object-fit: cover; transition: transform 0.3s ease; loading: lazy; }
    .product-card:hover .product-img { transform: scale(1.03); }
    .product-body { padding: 1.5rem; text-align: center; }
    .product-title { font-family: 'Playfair Display', serif; font-size: 1.6rem; margin-bottom: 0.8rem; color: var(--dark); }
    .price { font-size: 1.8rem; font-weight: 700; color: var(--accent); margin: 0.4rem 0; }
    .original-price { text-decoration: line-through; color: #999; font-size: 1.2rem; margin-left: 0.8rem; }
    .group-info { background: rgba(201,169,110,0.1); padding: 0.8rem; border-radius: 10px; margin: 1rem 0; font-weight: 500; color: var(--primary); }
    button { background: var(--accent); color: white; border: none; padding: 0.8rem 2rem; font-size: 1rem; border-radius: 50px; cursor: pointer; transition: all 0.2s ease; font-weight: 500; }
    button:hover { background: #b38c50; transform: translateY(-2px); }
    footer { background: var(--dark); color: white; text-align: center; padding: 3rem 1rem; margin-top: 4rem; font-size: 0.9rem; }
    .modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.6); justify-content: center; align-items: center; z-index: 1000; }
    .modal-content { background: white; padding: 2rem; border-radius: 20px; max-width: 600px; width: 90%; max-height: 80vh; overflow-y: auto; position: relative; }
    .close { position: absolute; top: 10px; right: 15px; font-size: 2rem; cursor: pointer; color: #555; }
    .cart-list { margin: 1rem 0; }
    .cart-item { display: flex; justify-content: space-between; align-items: center; padding: 0.8rem 0; border-bottom: 1px solid #eee; }
    .cart-item button { background: #ff4444; color: white; border: none; padding: 0.4rem 0.8rem; border-radius: 50%; cursor: pointer; font-size: 1.2rem; }
    .cart-total { font-weight: bold; margin-top: 1rem; text-align: right; font-size: 1.3rem; }
    .contact-section { background: white; border-radius: 20px; padding: 2rem; box-shadow: 0 8px 25px rgba(0,0,0,0.08); text-align: center; margin: 3rem 0; }
    .contact-icons a { margin: 0 1.5rem; font-size: 2.5rem; color: var(--primary); text-decoration: none; transition: color 0.3s; }
    .contact-icons a:hover { color: var(--accent); }
    #chat-btn { position: fixed; bottom: 30px; right: 30px; background: #00c300; color: white; width: 70px; height: 70px; border-radius: 50%; font-size: 2.2rem; display: flex; align-items: center; justify-content: center; box-shadow: 0 6px 20px rgba(0,195,0,0.4); cursor: pointer; z-index: 999; transition: all 0.3s; }
    #chat-btn:hover { transform: scale(1.1); }
    #chat-window { display: none; position: fixed; bottom: 110px; right: 20px; width: 340px; height: 440px; background: white; border-radius: 20px; box-shadow: 0 15px 50px rgba(0,0,0,0.25); overflow: hidden; z-index: 999; }
    #chat-header { background: #00c300; color: white; padding: 1.2rem; text-align: center; font-weight: 600; }
    #chat-body { padding: 1.2rem; height: calc(100% - 130px); overflow-y: auto; }
    #chat-input { width: 100%; padding: 1rem; border: none; border-top: 1px solid #ddd; font-size: 1rem; }
    .chat-msg { margin: 1rem 0; padding: 1rem 1.2rem; border-radius: 18px; max-width: 80%; }
    .user-msg { background: var(--primary); color: white; margin-left: auto; }
    .bot-msg { background: #f1f1f1; color: #333; }
  </style>
</head>
<body>

  <header>
    <h1 data-lang-key="title">歐洲好物團購站</h1>
    <p class="tagline" data-lang-key="tagline">臺灣直送正品歐洲精品 • 多人團購越買越便宜 • 直播開箱看實品</p>

    <div class="header-right">
      <div class="lang-switcher">
        <select id="langSelect" onchange="changeLanguage(this.value)">
          <option value="zh-TW">繁體中文</option>
          <option value="zh-CN">简体中文</option>
          <option value="en">English</option>
          <option value="th">ภาษาไทย</option>
          <option value="id">Bahasa Indonesia</option>
        </select>
      </div>
      <div class="cart-icon" onclick="showCartModal()">
        <span data-lang-key="cart">購物車</span> (<span id="cart-count">0</span>)
      </div>
    </div>
  </header>

  <div class="container">
    <h2 class="section-title" data-lang-key="hot_products">精選歐洲團購蜂蜜</h2>
    <div class="product-grid">
      <div class="product-card">
        <img loading="lazy" src="https://i.imgur.com/y4rRLmo.jpg" alt="Melvita 250g" class="product-img">
        <div class="product-body">
          <h3 class="product-title" data-lang-key="melvita_250">Melvita Weide- en Veld Bloemen Honing 250g</h3>
          <p style="font-size: 0.9rem; color: #555;" data-lang-key="melvita_250_desc">Lacht & Fijn • 歐洲花蜜 • 天然擠壓瓶 • 無添加</p>
          <div class="price">NT$ 199 <span class="original-price">NT$ 320</span></div>
          <div class="group-info" id="group-m1">目前 8 / 25 人參與 • 再 17 人享 20% OFF！</div>
          <button onclick="addToCart('Melvita Weide- en Veld Bloemen Honing 250g', 199)">加入團購</button>
        </div>
      </div>

      <div class="product-card">
        <img loading="lazy" src="https://i.imgur.com/UW0vKPa.jpg" alt="Melvita 365g" class="product-img">
        <div class="product-body">
          <h3 class="product-title" data-lang-key="melvita_365">Melvita Biologische Bloemen Honing 365g (有機)</h3>
          <p style="font-size: 0.9rem; color: #555;" data-lang-key="melvita_365_desc">Rijk & Intens • 歐盟有機認證 • 純天然 • 擠壓瓶</p>
          <div class="price">NT$ 329 <span class="original-price">NT$ 420</span></div>
          <div class="group-info" id="group-m2">目前 6 / 35 人參與 • 再 29 人享 25% OFF！</div>
          <button onclick="addToCart('Melvita Biologische Bloemen Honing 365g', 329)">加入團購</button>
        </div>
      </div>

      <div class="product-card">
        <img loading="lazy" src="https://i.imgur.com/RKvrV5L.jpg" alt="1de Beste 320g" class="product-img">
        <div class="product-body">
          <h3 class="product-title" data-lang-key="honey_1de">荷蘭 1de Beste Bloemen Honing 花蜜 320g</h3>
          <p style="font-size: 0.9rem; color: #555;" data-lang-key="honey_1de_desc">Vloeibare • 純正荷蘭混合花蜜 • 每15g 48 kcal / 每100g 320 kcal • 天然無添加</p>
          <div class="price">NT$ 249 <span class="original-price">NT$ 320</span></div>
          <div class="group-info" id="group-m3">目前 12 / 30 人參與 • 再 18 人享 25% OFF！</div>
          <button onclick="addToCart('荷蘭 1de Beste Bloemen Honing 320g', 249)">加入團購</button>
        </div>
      </div>
    </div>

    <div class="contact-section">
      <h2 data-lang-key="contact_us">聯絡我們</h2>
      <p data-lang-key="contact_desc">有任何問題？歡迎隨時聯繫！</p>
      <div class="contact-icons">
        <a href="mailto:service@eurogrouptw.com"><i class="fas fa-envelope"></i> service@eurogrouptw.com</a>
        <a href="tel:+886912345678"><i class="fas fa-phone"></i> +886 912 345 678</a>
        <a href="https://line.me/ti/p/@eurogrouptw" target="_blank"><i class="fab fa-line"></i> LINE: @eurogrouptw</a>
      </div>
    </div>
  </div>

  <!-- 購物車 Modal -->
  <div id="cartModal" class="modal">
    <div class="modal-content">
      <span class="close" onclick="closeCartModal()">×</span>
      <h2 data-lang-key="cart_title">購物車</h2>
      <div id="cartList" class="cart-list"></div>
      <div id="cartTotal" class="cart-total" data-lang-key="cart_total_prefix">總計: NT$ 0</div>
      <button onclick="checkout()" style="width:100%; margin-top:1rem; background:var(--success);" data-lang-key="checkout_button">結帳</button>
      <button onclick="clearCart()" style="width:100%; margin-top:0.5rem; background:#999;" data-lang-key="clear_cart_button">清空購物車</button>
    </div>
  </div>

  <!-- 小幫手按鈕與視窗 -->
  <div id="chat-btn" onclick="toggleChat()">💬</div>
  <div id="chat-window">
    <div id="chat-header" data-lang-key="chat_header">線上小幫手 <span onclick="toggleChat()" style="float:right; cursor:pointer; font-size:1.5rem;">×</span></div>
    <div id="chat-body">
      <div class="chat-msg bot-msg" data-lang-key="chat_welcome">您好！我是歐洲好物團購站的小幫手～有什麼可以幫您的嗎？</div>
    </div>
    <input type="text" id="chat-input" placeholder="輸入訊息..." onkeypress="if(event.key === 'Enter') sendChat();">
  </div>

  <footer>
    <p data-lang-key="footer">© 2026 歐洲好物團購站 • 正品保證 • 客服 LINE: @eurogrouptw</p>
  </footer>

  <script>
    // 多語言字典（完整整合版）
    const translations = {
      "zh-TW": {
        title: "歐洲好物團購站",
        tagline: "臺灣直送正品歐洲精品 • 多人團購越買越便宜 • 直播開箱看實品",
        cart: "購物車",
        cart_title: "購物車",
        cart_total_prefix: "總計: ",
        checkout_button: "結帳",
        clear_cart_button: "清空購物車",
        hot_products: "精選歐洲團購蜂蜜",
        melvita_250: "Melvita Weide- en Veld Bloemen Honing 250g",
        melvita_250_desc: "Lacht & Fijn • 歐洲花蜜 • 天然擠壓瓶 • 無添加",
        melvita_365: "Melvita Biologische Bloemen Honing 365g (有機)",
        melvita_365_desc: "Rijk & Intens • 歐盟有機認證 • 純天然 • 擠壓瓶",
        honey_1de: "荷蘭 1de Beste Bloemen Honing 花蜜 320g",
        honey_1de_desc: "Vloeibare • 純正荷蘭混合花蜜 • 每15g 48 kcal / 每100g 320 kcal • 天然無添加",
        add_cart: "加入團購",
        contact_us: "聯絡我們",
        contact_desc: "有任何問題？歡迎隨時聯繫！",
        chat_header: "線上小幫手",
        chat_welcome: "您好！我是歐洲好物團購站的小幫手～有什麼可以幫您的嗎？",
        footer: "© 2026 歐洲好物團購站 • 正品保證 • 客服 LINE: @eurogrouptw"
      },
      "zh-CN": {
        title: "欧洲好物团购站",
        tagline: "台湾直送正品欧洲精品 • 多人团购越买越便宜 • 直播开箱看实品",
        cart: "购物车",
        cart_title: "购物车",
        cart_total_prefix: "总计: ",
        checkout_button: "结账",
        clear_cart_button: "清空购物车",
        hot_products: "精选欧洲团购蜂蜜",
        melvita_250: "Melvita Weide- en Veld Bloemen Honing 250g",
        melvita_250_desc: "Lacht & Fijn • 欧洲花蜜 • 天然挤压瓶 • 无添加",
        melvita_365: "Melvita Biologische Bloemen Honing 365g (有机)",
        melvita_365_desc: "Rijk & Intens • 欧盟有机认证 • 纯天然 • 挤压瓶",
        honey_1de: "荷兰 1de Beste Bloemen Honing 花蜜 320g",
        honey_1de_desc: "Vloeibare • 纯正荷兰混合花蜜 • 每15g 48 kcal / 每100g 320 kcal • 天然无添加",
        add_cart: "加入团购",
        contact_us: "联系我们",
        contact_desc: "有任何问题？欢迎随时联系！",
        chat_header: "在线小助手",
        chat_welcome: "您好！我是欧洲好物团购站的小助手～有什么可以帮您的吗？",
        footer: "© 2026 欧洲好物团购站 • 正品保证 • 客服 LINE: @eurogrouptw"
      },
      "en": {
        title: "EuroGroup TW",
        tagline: "Taiwan Direct Authentic European Products • Group Buy Cheaper • Live Unboxing",
        cart: "Cart",
        cart_title: "Cart",
        cart_total_prefix: "Total: ",
        checkout_button: "Checkout",
        clear_cart_button: "Clear Cart",
        hot_products: "Selected European Group Buy Honey",
        melvita_250: "Melvita Weide- en Veld Flower Honey 250g",
        melvita_250_desc: "Lacht & Fijn • European Flower Honey • Natural Squeeze Bottle • No Additives",
        melvita_365: "Melvita Organic Flower Honey 365g",
        melvita_365_desc: "Rijk & Intens • EU Organic Certified • Pure Natural • Squeeze Bottle",
        honey_1de: "Dutch 1de Beste Flower Honey 320g",
        honey_1de_desc: "Vloeibare • Pure Dutch Mixed Flower Honey • 48 kcal/15g • 320 kcal/100g • Natural No Additives",
        add_cart: "Add to Cart",
        contact_us: "Contact Us",
        contact_desc: "Any questions? Feel free to contact us!",
        chat_header: "Online Assistant",
        chat_welcome: "Hello! I'm the assistant of EuroGroup TW ~ How can I help you?",
        footer: "© 2026 EuroGroup TW • Genuine Guarantee • LINE Support: @eurogrouptw"
      },
      "th": {
        title: "สถานที่ซื้อกลุ่มผลิตภัณฑ์ดีจากยุโรป",
        tagline: "ส่งตรงจากไต้หวันสินค้าดีจากยุโรปแท้ • ซื้อกลุ่มยิ่งมากยิ่งถูก • ถ่ายทอดสดเปิดกล่องดูของจริง",
        cart: "รถเข็น",
        cart_title: "รถเข็น",
        cart_total_prefix: "รวมทั้งสิ้น: ",
        checkout_button: "ชำระเงิน",
        clear_cart_button: "ล้างรถเข็น",
        hot_products: "น้ำผึ้งเลือกสรรจากยุโรปสำหรับซื้อกลุ่ม",
        melvita_250: "Melvita Weide- en Veld Bloemen Honing 250g",
        melvita_250_desc: "Lacht & Fijn • น้ำผึ้งดอกไม้จากยุโรป • ขวดบีบธรรมชาติ • ไม่มีสารเติมแต่ง",
        melvita_365: "Melvita Biologische Bloemen Honing 365g (ออร์แกนิก)",
        melvita_365_desc: "Rijk & Intens • 認證ออร์แกนิก EU • ธรรมชาติบริสุทธิ์ • ขวดบีบ",
        honey_1de: "น้ำผึ้งดอกไม้ 1de Beste จากเนเธอร์แลนด์ 320g",
        honey_1de_desc: "Vloeibare • น้ำผึ้งดอกไม้ผสมบริสุทธิ์จากเนเธอร์แลนด์ • 48 kcal/15g • 320 kcal/100g • ธรรมชาติไม่เติมสาร",
        add_cart: "เพิ่มลงตะกร้า",
        contact_us: "ติดต่อเรา",
        contact_desc: "มีคำถามอะไรไหม? ยินดีติดต่อได้ตลอดเวลา!",
        chat_header: "ผู้ช่วยออนไลน์",
        chat_welcome: "สวัสดีครับ/ค่ะ! ผม/ดิฉันเป็นผู้ช่วยของสถานที่ซื้อกลุ่มผลิตภัณฑ์ดีจากยุโรป มีอะไรให้ช่วยไหมครับ/คะ?",
        footer: "© 2026 สถานที่ซื้อกลุ่มผลิตภัณฑ์ดีจากยุโรป • ประกันสินค้าของแท้ • LINE บริการลูกค้า: @eurogrouptw"
      },
      "id": {
        title: "EuroGroup TW - Pembelian Kelompok Eropa",
        tagline: "Pengiriman Langsung dari Taiwan Produk Asli Eropa • Pembelian Kelompok Makin Murah • Live Unboxing",
        cart: "Keranjang",
        cart_title: "Keranjang",
        cart_total_prefix: "Total: ",
        checkout_button: "Checkout",
        clear_cart_button: "Kosongkan Keranjang",
        hot_products: "Madu Eropa Terpilih untuk Pembelian Kelompok",
        melvita_250: "Melvita Weide- en Veld Bloemen Honing 250g",
        melvita_250_desc: "Lacht & Fijn • Madu Bunga Eropa • Botol Tekan Alami • Tanpa Tambahan",
        melvita_365: "Melvita Biologische Bloemen Honing 365g (Organik)",
        melvita_365_desc: "Rijk & Intens • Sertifikasi Organik UE • Alami Murni • Botol Tekan",
        honey_1de: "Madu Bunga 1de Beste Belanda 320g",
        honey_1de_desc: "Vloeibare • Madu Bunga Campuran Belanda Murni • 48 kcal/15g • 320 kcal/100g • Alami Tanpa Tambahan",
        add_cart: "Tambah ke Keranjang",
        contact_us: "Hubungi Kami",
        contact_desc: "Ada pertanyaan? Silakan hubungi kapan saja!",
        chat_header: "Asisten Online",
        chat_welcome: "Halo! Saya asisten dari EuroGroup TW ~ Ada yang bisa saya bantu?",
        footer: "© 2026 EuroGroup TW • Jaminan Asli • Layanan Pelanggan LINE: @eurogrouptw"
      }
    };

    let currentLang = localStorage.getItem('lang') || 'zh-TW';
    let cart = JSON.parse(localStorage.getItem('cart')) || [];

    function changeLanguage(lang) {
      currentLang = lang;
      localStorage.setItem('lang', lang);
      document.querySelectorAll('[data-lang-key]').forEach(el => {
        const key = el.getAttribute('data-lang-key');
        if (translations[lang] && translations[lang][key]) {
          if (key === 'cart_total_prefix') {
            // 只更新前綴，保留數字部分
            const currentTotal = document.getElementById('cartTotal').textContent.split(': ')[1] || 'NT$ 0';
            document.getElementById('cartTotal').textContent = translations[lang][key] + currentTotal;
          } else {
            el.textContent = translations[lang][key];
          }
        }
      });
      document.documentElement.lang = lang;
    }

    function addToCart(name, price) {
      cart.push({ name, price });
      localStorage.setItem('cart', JSON.stringify(cart));
      updateCartCount();
      alert(`已加入購物車！${name} - NT$ ${price}`);
    }

    function updateCartCount() {
      document.getElementById('cart-count').textContent = cart.length;
    }

    function showCartModal() {
      if (cart.length === 0) {
        alert(translations[currentLang]?.cart_empty || '購物車是空的');
        return;
      }
      const list = document.getElementById('cartList');
      list.innerHTML = '';
      let total = 0;
      cart.forEach((item, index) => {
        const div = document.createElement('div');
        div.className = 'cart-item';
        div.innerHTML = `
          <span>${item.name} - NT$ ${item.price}</span>
          <button onclick="removeFromCart(${index})" style="background:#ff4444; color:white; border:none; padding:0.4rem 0.8rem; border-radius:50%; cursor:pointer;">×</button>
        `;
        list.appendChild(div);
        total += item.price;
      });
      const totalPrefix = translations[currentLang]?.cart_total_prefix || '總計: ';
      document.getElementById('cartTotal').textContent = totalPrefix + `NT$ ${total}`;
      document.getElementById('cartModal').style.display = 'flex';
    }

    function removeFromCart(index) {
      cart.splice(index, 1);
      localStorage.setItem('cart', JSON.stringify(cart));
      updateCartCount();
      showCartModal();
    }

    function closeCartModal() {
      document.getElementById('cartModal').style.display = 'none';
    }

    function clearCart() {
      if (confirm(translations[currentLang]?.confirm_clear || '確定清空購物車？')) {
        cart = [];
        localStorage.setItem('cart', JSON.stringify(cart));
        updateCartCount();
        closeCartModal();
      }
    }

    function checkout() {
      if (cart.length === 0) return;
      let total = cart.reduce((sum, item) => sum + item.price, 0);
      alert((translations[currentLang]?.checkout_thanks || '感謝購買！我們會盡快處理您的訂單～') + `\n${translations[currentLang]?.cart_total_prefix || '總金額：'}NT$ ${total}`);
      cart = [];
      localStorage.setItem('cart', JSON.stringify(cart));
      updateCartCount();
      closeCartModal();
    }

    function toggleChat() {
      const win = document.getElementById('chat-window');
      win.style.display = win.style.display === 'block' ? 'none' : 'block';
    }

    function sendChat() {
      const input = document.getElementById('chat-input');
      const msg = input.value.trim();
      if (!msg) return;
      const body = document.getElementById('chat-body');
      body.innerHTML += `<div class="chat-msg user-msg">${msg}</div>`;
      setTimeout(() => {
        let reply = translations[currentLang]?.chat_reply || '收到您的訊息！我們會盡快回覆～';
        body.innerHTML += `<div class="chat-msg bot-msg">${reply}</div>`;
        body.scrollTop = body.scrollHeight;
      }, 800);
      input.value = '';
      body.scrollTop = body.scrollHeight;
    }

    window.addEventListener('load', () => {
      document.getElementById('langSelect').value = currentLang;
      changeLanguage(currentLang);
      updateCartCount();
    });
  </script>
</body>
</html>
