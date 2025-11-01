# 🔐 Firmware ve Yazılım Açıkları — Anomali Senaryosu

Bu senaryo, elektrikli araç şarj istasyonlarında firmware (gömülü yazılım) güncellemeleri sırasında
oluşabilecek güvenlik zafiyetlerini incelemekte ve bu zafiyetlere karşı geliştirilen
**yapay zekâ tabanlı tespit sisteminin** etkinliğini analiz etmektedir.

---

## 🔍 SWOT Analizi

### 🟩 Strengths (Güçlü Yönler)
- Yapay zekâ tabanlı anomali tespit sistemi  
- Dijital imzalı firmware yapısı (certificate-based validation)  
- Merkezi güncelleme ve dağıtım kontrolü  
- Ayrıntılı loglama ve izleme mekanizması  

### 🟥 Weaknesses (Zayıf Yönler)
- Sertifika yaşam döngüsü yönetiminin karmaşıklığı  
- Güncellemelerde gecikme veya senkronizasyon sorunları  
- Eski donanımların uyumsuzluk riski  
- Yanlış pozitif (false positive) tespit olasılığı  

### 🟦 Opportunities (Fırsatlar)
- ISO 15118, OCPP 2.0 ve ISO 27001 gibi uluslararası güvenlik standartlarına tam uyumluluk  
- Sertifikalı ürün farkı ve kurumsal güven imajı  
- Yapay zekâ ile otonom öğrenme ve sürekli iyileştirme potansiyeli  
- Yasal regülasyonlara (KVKK, NIS2) uyum avantajı  

### 🟨 Threats (Tehditler)
- Zero-day (bilinmeyen) güvenlik açıkları  
- Tedarik zinciri (supply-chain) saldırıları  
- Firmware reverse engineering (tersine mühendislik) girişimleri  
- İç tehditler ve yetkili kötüye kullanımı (insider attacks)  

---

## ⚙️ Anomali Senaryosu: **İmzalanmamış Firmware Manipülasyonu**

### 🎯 Amaç
İmzalanmamış, değiştirilmiş veya sürümü düşürülmüş firmware dosyalarının
yapay zekâ destekli sistem tarafından tespit edilip,
otomatik olarak engellenmesini sağlamaktır.

### 🧩 Senaryo Akışı
1. **Normal Durum:**  
   Şarj istasyonu yalnızca doğrulanmış ve dijital imzalı firmware dosyalarını kabul eder.  
   (signature_valid=True, hash_match=True)

2. **Saldırı Durumu:**  
   Saldırgan, imzasız veya eski bir firmware dosyasını
   merkezi güncelleme sunucusu üzerinden sisteme iletir.  
   (signature_valid=False, hash_match=False, downgrade=True)

3. **Sistemin Tepkisi:**  
   - Yapay zekâ modeli anomaliyi tanımlar ve uyarı üretir.  
   - Güncelleme işlemi 30 saniye içinde durdurulur.  
   - İlgili istasyon karantina (quarantine) moduna alınır.  
   - SOC (Security Operations Center) sistemine olay bildirimi yapılır.  

### 📏 Ölçüm Kriterleri
- 100 test senaryosundan **en az %95 doğrulukla tespit**  
- Ortalama tespit süresi: **< 30 saniye**  
- Yanlış pozitif oranı: **≤ %5**

---

## 🎯 İlgili Proje Hedefleri

| Hedef | Açıklama |
|-------|-----------|
| **Hedef 1** | Anomali Tespit Sisteminin ≥%95 doğrulukla geliştirilmesi |
| **Hedef 3** | Veri manipülasyonunun gerçek zamanlı olarak ≥%90 doğrulukla saptanması |
| **Hedef 4** | Gerçek zamanlı izleme ve otomatik müdahale süresinin ≤30 saniye olması |

---

## 🧠 Sonuç

Firmware açıkları, şarj istasyonları için **kritik güvenlik riskleri** taşır.
Bu senaryo, yapay zekâ destekli bir sistemin bu tür tehditleri
gerçek zamanlı olarak tespit edip müdahale edebilme kabiliyetini ölçmeyi hedefler.

Geliştirilen çözüm, sahte veya imzasız güncellemeleri 30 saniyeden kısa sürede algılayarak  
otomatik izolasyon sağlar ve **ISO 15118**, **ISO 27001** gibi güvenlik standartlarına
uyumlu bir güvenlik mimarisi oluşturur.

---

📅 **Fırat Üniversitesi — Bilgi Sistemleri ve Güvenliği Dersi (2025 Güz Dönemi)**  
👩‍💻 **Hazırlayan:** Sena Köse  
🔗 **Proje Kapsamı:** Yapay zekâ tabanlı şarj istasyonu güvenlik sistemi
