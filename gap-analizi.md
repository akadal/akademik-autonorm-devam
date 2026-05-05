# Orijinal Çalışmanın Literatürdeki Gap Analizi

## Orijinal Çalışma

**Akadal, E., & Satman, M.H. (2022).** A Novel Automatic Relational Database Normalization Method. *Acta Informatica Pragensia*, 11(3), 293-308. DOI: 10.18267/j.aip.193

### Temel Katkı:
- FD (Functional Dependency) bilgisi gerektirmeden, sadece ham veri seti ile tam otomatik normalizasyon
- %72 exact match başarı (250 dataset, 2500 simülasyon)
- 4 fitness function ile çok amaçlı optimizasyon
- Binary-coded GA

---

## Literatürdeki Benzer Çalışmalar

| Çalışma | Yıl | Gereksinim | Limitasyon |
|---------|-----|-----------|------------|
| Du & Wery (Micro) | 1999 | FD bilgisi | Kısmen otomatik |
| Dongare et al. (RDBNorma) | 2011 | FD bilgisi | Semi-automatic |
| Yazıcı & Karakaya | 2007 | FD bilgisi | Mathematica bağımlı |
| Bahmani et al. | 2008 | Dependency graph | Kullanıcı girdisi |
| Ahmad et al. | 2014 | Excel + FD | Misidentification risk |
| **Akadal & Satman** | **2022** | **Sadece dataset** | **%72 başarı** |

---

## Tespit Edilen Gap'ler

### 1. Gerçek Dünya Validasyonu Eksikliği ❌
- Sadece sentetik dataset'ler (denormalize edilmiş iyi VT'ler)
- Gerçek legacy VT üzerinde test yok
- Gerçek kurum kullanımı yok

### 2. Performans Optimizasyonu Eksikliği ❌
- GA parametreleri (popülasyon, jenerasyon, crossover, mutation) elle ayarlanmış
- Meta-optimizasyon yok
- Dataset'e özgü parametre adaptasyonu yok

### 3. Açıklanabilirlik (Explainability) Eksikliği ❌
- GA kara kutu
- "Neden bu attribute bu entity'de?" sorusuna cevap yok
- DBA karar desteği yok

### 4. NoSQL Genişlemesi Eksikliği ❌
- Sadece ilişkisel model
- Document, column-family, graph modelleri için yok
- Polyglot persistence desteği yok

### 5. Zaman Serisi / IoT Uygulaması Eksikliği ❌
- Streaming data için adaptasyon yok
- Sensor verileri için şema tasarımı yok

### 6. Veri Kalitesi Entegrasyonu Eksikliği ❌
- Veri temizliği ön adımı yok
- Data quality metrics entegre değil

### 7. Sorgu Performansı Değerlendirmesi Eksikliği ❌
- Normalize edilmiş VT'nin sorgu hızı test edilmemiş
- Storage efficiency ölçülmemiş
- Insert/Update/Delete anomaly riski değerlendirilmemiş

### 8. Blockchain / Merkeziyetsiz VT Eksikliği ❌
- Web3 / DApp veri yönetimi için uygulama yok
- Gas cost-aware tasarım yok
- Immutable veri pattern'leri yok

---

## Gap Önceliklendirme

| Öncelik | Gap | Neden? |
|---------|-----|--------|
| 1 | Gerçek dünya validasyonu | En kritik eksiklik, A sınıfı dergi için şart |
| 2 | Performans optimizasyonu | %72'yi artırma potansiyeli yüksek |
| 3 | Açıklanabilirlik | DBA kabulü için gerekli |
| 4 | Blockchain / Merkeziyetsiz | Emre'nin uzmanlık kesişimi, literature gap büyük |
| 5 | NoSQL genişlemesi | Modern VT ihtiyacı |
| 6 | Sorgu performansı | Pratik değerlendirme |
| 7 | Zaman serisi / IoT | Niche alan |
| 8 | Veri kalitesi | Destekleyici özellik |

---

*Hazırlayan: Donna 🎯*
