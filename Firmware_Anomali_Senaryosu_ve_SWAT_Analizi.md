# Firmware ve Yazılım Açıkları — SWAT Analizi ve Anomali Senaryosu

## 🔍 SWAT Analizi

### Strengths (Güçlü Yönler)
- Yapay zekâ tabanlı tespit sistemi
- Dijital imzalı firmware altyapısı
- Merkezi güncelleme yönetimi
- Kapsamlı log kayıt sistemi

### Weaknesses (Zayıf Yönler)
- Sertifika yönetimi karmaşıklığı
- Gecikmeli güncellemeler
- Eski donanım uyumsuzlukları
- Yanlış pozitif riski

### Opportunities (Fırsatlar)
- Uluslararası güvenlik standartlarına uyum (ISO 15118, OCPP, ISO 27001)
- Sertifikalı ürün farkı ve marka itibarı
- Yapay zekâ destekli otonom öğrenme kapasitesi
- Regülasyonlara tam uyum (NIS2, KVKK)

### Threats (Tehditler)
- Zero-day açıklar
- Tedarik zinciri saldırıları
- Firmware reverse engineering
- İç tehditler (insider attacks)

---

## ⚙️ Anomali Senaryosu: İmzalanmamış Firmware Manipülasyonu

### Amaç
İmzalanmamış veya değiştirilmiş firmware güncellemelerinin yapay zekâ destekli sistem tarafından tespit edilmesi ve saldırının otomatik engellenmesi.

### Senaryo Adımları
1. **Normal Durum:**  
   Şarj istasyonu yalnızca doğrulanmış imzalı firmware’leri yükler.  
   (signature_valid=True, hash_match=True)

2. **Saldırı Durumu:**  
   Saldırgan, farklı imzalı veya eski bir firmware gönderir.  
   (signature_valid=False, hash_match=False, downgrade=True)

3. **Sistemin Tepkisi:**  
   - AI modeli anomalili davranışı tespit eder  
   - Sistem 30 saniye içinde güncellemeyi durdurur  
   - İstasyon quarantine moduna alınır  
   - SOC uyarısı oluşturulur

### Ölçüm Kriteri
- 100 anomali senaryosundan **en az %95’i doğru tespit edilmeli**
- Ortalama tespit süresi: **< 30 saniye**
- Yanlış pozitif oranı: **≤ %5**

---

## 🎯 İlgili Proje Hedefleri
| Hedef | Açıklama |
|-------|-----------|
| **Hedef 1** | Anomali Tespit Sisteminin %95 doğrulukla geliştirilmesi |
| **Hedef 3** | Veri manipülasyonunun tespiti (%90 doğruluk) |
| **Hedef 4** | Gerçek zamanlı izleme ve otomatik müdahale (≤30s) |

---

## 🧠 Sonuç
Firmware güvenlik açıkları, şarj istasyonları için en kritik tehditlerden biridir. Bu senaryo, AI tabanlı tespit sisteminin bu tür saldırılara karşı etkinliğini ölçmeyi hedefler. Sistem, sahte güncellemeleri 30 saniyeden kısa sürede fark edip otomatik izolasyon gerçekleştirerek güvenlik standartlarıyla (ISO 15118, ISO 27001) uyumlu hale gelir.
