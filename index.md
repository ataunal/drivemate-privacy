<!DOCTYPE html>
<html lang="tr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>DriveMate — Gizlilik Politikası</title>
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }
    body {
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
      background: #0d0d0d;
      color: #e0e0e0;
      line-height: 1.75;
      padding: 24px 16px 60px;
    }
    .container { max-width: 720px; margin: 0 auto; }
    h1 { font-size: 2rem; color: #ffffff; margin-bottom: 8px; }
    .subtitle { color: #888; font-size: 0.9rem; margin-bottom: 40px; }
    h2 {
      font-size: 1.15rem;
      color: #f0c040;
      margin: 36px 0 12px;
      padding-bottom: 6px;
      border-bottom: 1px solid #2a2a2a;
    }
    p { margin-bottom: 12px; color: #ccc; }
    ul { padding-left: 20px; margin-bottom: 12px; }
    li { margin-bottom: 6px; color: #ccc; }
    strong { color: #fff; }
    a { color: #f0c040; text-decoration: none; }
    a:hover { text-decoration: underline; }
    .badge {
      display: inline-block;
      background: #1a1a1a;
      border: 1px solid #333;
      border-radius: 6px;
      padding: 2px 10px;
      font-size: 0.8rem;
      color: #888;
      margin-bottom: 4px;
    }
    table { width: 100%; border-collapse: collapse; margin-bottom: 16px; }
    th, td { text-align: left; padding: 10px 12px; border-bottom: 1px solid #222; font-size: 0.9rem; }
    th { color: #f0c040; font-weight: 600; background: #161616; }
    td { color: #ccc; }
  </style>
</head>
<body>
<div class="container">

  <h1>🚗 DriveMate</h1>
  <p class="subtitle">Gizlilik Politikası — Son güncelleme: Nisan 2026</p>

  <p>
    DriveMate, Türkiye'deki sürücülere hız kamerası uyarıları sunan bir mobil uygulamadır.
    Bu politika; hangi verileri topladığımızı, neden topladığımızı, nasıl sakladığımızı ve
    haklarınızı açıkça ortaya koymaktadır. <strong>6698 sayılı Kişisel Verilerin Korunması Kanunu (KVKK)</strong>
    kapsamındaki yükümlülüklerimize bu politika çerçevesinde uyuyoruz.
  </p>

  <h2>1. Toplanan Veriler ve Amaçları</h2>

  <table>
    <thead>
      <tr>
        <th>Veri</th>
        <th>Amaç</th>
        <th>Saklama</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><strong>Gerçek zamanlı konum</strong></td>
        <td>Yakındaki hız kameralarını göstermek, sesli uyarı vermek</td>
        <td>Cihazda işlenir, sunucuya gönderilmez</td>
      </tr>
      <tr>
        <td><strong>Anonim kullanıcı kimliği (UUID)</strong></td>
        <td>Rapor takibi, oy sistemi, premium durumu</td>
        <td>Cihaz + Firebase Firestore</td>
      </tr>
      <tr>
        <td><strong>Seyyar radar raporları</strong></td>
        <td>Topluluk kamera veritabanını oluşturmak</td>
        <td>Firestore — 2 saat sonra otomatik silinir</td>
      </tr>
      <tr>
        <td><strong>Güvenilirlik skoru</strong></td>
        <td>Rapor kalitesini değerlendirmek</td>
        <td>Firestore (kullanıcı profilinde)</td>
      </tr>
      <tr>
        <td><strong>Premium durumu</strong></td>
        <td>Reklam gösterimi kararı</td>
        <td>Firestore + Adapty</td>
      </tr>
      <tr>
        <td><strong>Reklam tanımlayıcı (IDFA/GAID)</strong></td>
        <td>Google AdMob üzerinden banner reklam göstermek (yalnızca ücretsiz kullanıcılar)</td>
        <td>Google'ın gizlilik politikasına tabidir</td>
      </tr>
    </tbody>
  </table>

  <p>
    <strong>Konum geçmişi kaydedilmez.</strong> Uygulama yalnızca anlık konumunuzu kullanır;
    güzergah, varış noktası veya geçmiş sürüş verileri saklanmaz.
  </p>

  <h2>2. Anonim Kimlik Sistemi</h2>
  <p>
    DriveMate, hesap oluşturmanızı <strong>gerektirmez</strong>. Uygulamayı ilk açtığınızda
    cihazınızda rastgele bir UUID (evrensel benzersiz kimlik) oluşturulur. Bu kimlik:
  </p>
  <ul>
    <li>Ad, e-posta veya telefon numarasıyla ilişkilendirilmez.</li>
    <li>Yalnızca raporlarınızı ve premium durumunuzu tanımlamak için kullanılır.</li>
    <li>Firebase Anonymous Authentication ile eşleştirilir — kimlik doğrulama gerekliliği olmaksızın Firestore'a güvenli yazım sağlar.</li>
    <li>Hesap silme işlemiyle tamamen imha edilir ve yerine yeni bir UUID oluşturulur.</li>
  </ul>

  <h2>3. Hesap Silme</h2>
  <p>
    Uygulama içinden (<strong>Ayarlar → Hesabı Sil</strong>) hesabınızı tamamen silebilirsiniz.
    Bu işlem:
  </p>
  <ul>
    <li>Firebase Firestore'daki kullanıcı profilinizi siler.</li>
    <li>Sizinle ilişkili tüm seyyar radar raporlarını siler.</li>
    <li>Firebase Authentication anonim oturumunuzu kapatır ve siler.</li>
    <li>Cihazınızdaki UUID'yi temizler.</li>
    <li>Adapty'deki abonelik profilinizin bağlantısını keser.</li>
  </ul>
  <p>
    İşlem tamamlandıktan sonra uygulama taze bir anonim kimlikle çalışmaya devam eder.
    <strong>Bu işlem geri alınamaz.</strong> Aktif bir premium aboneliğiniz varsa App Store üzerinden
    aboneliğinizi yönetebilirsiniz; hesap silme aboneliği otomatik iptal etmez.
  </p>

  <h2>4. Üçüncü Taraf Servisler</h2>
  <p>DriveMate aşağıdaki üçüncü taraf hizmetleri kullanmaktadır:</p>
  <ul>
    <li>
      <strong>Google Firebase (Firestore &amp; Authentication)</strong> — Veri depolama ve anonim kimlik doğrulama.
      <a href="https://firebase.google.com/support/privacy" target="_blank" rel="noopener">Firebase Gizlilik Politikası →</a>
    </li>
    <li>
      <strong>Google AdMob</strong> — Ücretsiz kullanıcılara banner reklam gösterimi. Reklam kişiselleştirme tercihleriniz işletim sistemi düzeyinde yönetilebilir.
      <a href="https://policies.google.com/privacy" target="_blank" rel="noopener">Google Gizlilik Politikası →</a>
    </li>
    <li>
      <strong>Adapty</strong> — Abonelik yönetimi ve satın alma doğrulaması. Ödeme bilgileri Adapty veya uygulama tarafından saklanmaz; doğrudan App Store / Google Play üzerinden işlenir.
      <a href="https://adapty.io/privacy" target="_blank" rel="noopener">Adapty Gizlilik Politikası →</a>
    </li>
    <li>
      <strong>Apple App Store / Google Play</strong> — Abonelik işlemleri. Platform gizlilik politikaları geçerlidir.
    </li>
    <li>
      <strong>OpenStreetMap / Overpass API</strong> — Sabit hız kamerası veritabanı. Konum veriniz bu API'ye gönderilmez; sorgular sunucu tarafında yapılır ve önbelleğe alınır.
    </li>
  </ul>

  <h2>5. Veri Güvenliği</h2>
  <p>
    Firestore'a yazılan tüm veriler Firebase güvenlik kuralları ile korunmaktadır; yalnızca
    ilgili UUID kimliğiyle erişilebilir. Uygulama, başka kullanıcıların profillerine veya
    raporlarına erişemez. İnternet bağlantıları HTTPS/TLS ile şifrelenmektedir.
  </p>

  <h2>6. Çocukların Gizliliği</h2>
  <p>
    DriveMate 13 yaşın altındaki çocuklara yönelik değildir. Bu yaş grubundan bilerek
    kişisel veri toplamıyoruz. Böyle bir durumun farkına varırsak ilgili verileri derhal sileriz.
  </p>

  <h2>7. KVKK Kapsamındaki Haklarınız</h2>
  <p>6698 sayılı Kanun uyarınca aşağıdaki haklara sahipsiniz:</p>
  <ul>
    <li>Verilerinizin işlenip işlenmediğini öğrenme</li>
    <li>İşlenen veriler hakkında bilgi talep etme</li>
    <li>Verilerin silinmesini veya yok edilmesini isteme (<em>uygulama içi "Hesabı Sil" butonu bu hakkı anında kullanmanızı sağlar</em>)</li>
    <li>Verilerin yanlış işlendiğini düşünüyorsanız itiraz etme</li>
  </ul>
  <p>
    Talepleriniz için: <a href="mailto:ataaunall@gmail.com">ataaunall@gmail.com</a>
  </p>

  <h2>8. Politika Güncellemeleri</h2>
  <p>
    Bu politika önemli değişiklikler olduğunda güncellenir. Güncel sürüm her zaman bu sayfada
    yayımlanır. Uygulamayı kullanmaya devam etmeniz, güncel politikayı kabul ettiğiniz
    anlamına gelir.
  </p>

  <h2>9. İletişim</h2>
  <p>
    Gizlilik ile ilgili sorularınız için:<br />
    <a href="mailto:ataaunall@gmail.com">ataaunall@gmail.com</a>
  </p>

</div>
</body>
</html>
