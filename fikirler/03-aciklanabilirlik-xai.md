# Fikir 3: Açıklanabilirlik (XAI) Entegrasyonu ⭐⭐

## Özet

Genetik algoritmanın "kara kutu" yapısını kırarak, ürettiği veritabanı şemasının neden öyle olduğunu açıklayan bir modül eklemek. "Bu attribute neden bu entity'de?" sorusuna yanıt verebilmek.

## Motivasyon

Orijinal çalışmada GA kara kutu:
- Kromozomlar binary-coded
- Fitness function'lar minimize ediliyor
- **Ama neden bu entity yapısı?**
- DBA'lar algoritmanın kararına güvenmek istiyor — açıklama şart

> *"The solution can be treated as a relational database design suggestion."* — Akadal & Satman (2022)

> *"Suggestion" kelimesi, DBA'nın onaylayıp onaylamayacağına işaret ediyor. Onay için açıklama gerekli.*

## Literatürdeki Boşluk

| Alan | Çalışma Sayısı |
|------|---------------|
| Otomatik normalizasyon | ~20 |
| **Açıklanabilir otomatik normalizasyon** | **0** |
| XAI + veritabanı tasarımı | ~5 (genel) |

## Metodoloji (DSRM)

### 1. Problem Tanımlama
GA kara kutu. Kararlar açıklanamıyor. DBA'lar ve öğrenciler neden sorusuna yanıt bulamıyor.

### 2. Çözüm Hedefleri
- Her attribute için entity seçim nedenini açıklamak
- Normalizasyon kararlarını görselleştirmek
- Eğitim aracı olarak kullanılabilmek

### 3. Artifact
**Explainable Normalization Engine** — açıklama + görselleştirme modülü

### 4. Tasarım Detayları

#### Açıklama Yöntemleri:

**1. Feature Importance (SHAP/LIME)**

```
Attribute: "CustomerName" → Entity: "Customers"
SHAP Değeri: +0.72 (yüksek)
Açıklama: "Bu attribute, 1NF ihlali riskini %85 azaltıyor. 
          Tekrar eden değerler CustomerID ile gruplanıyor."
```

**2. Fitness Function Katkısı**

| Attribute | Entity | f1 (Hücre) | f2 (Tekrar) | f3 (Entity) | f4 (Numerik) | Toplam |
|-----------|--------|-----------|------------|------------|-------------|--------|
| CustomerName | Customers | -0.15 | -0.42 | +0.08 | 0.00 | **-0.49** ✅ |
| CustomerName | Orders | +0.23 | +0.38 | -0.05 | 0.00 | **+0.56** ❌ |

**3. Kural Tabanlı Açıklama**

```
Kural: "Eğer attribute'ın kardinalitesi düşükse ve başka entity'de 
        primary key olarak kullanılıyorsa → ayrı entity'ye taşı"

Örnek: "Country" attribute'u:
- Kardinalite: 15 (düşük)
- Orders tablosunda 5000 tekrar
- Ayrı "Countries" entity'sine taşınmış
- Açıklama: "Düşük kardinalite + yüksek tekrar = redundancy azaltma"
```

**4. Görselleştirme**

- Entity-Attribute ilişki grafiği
- Fitness improvement kıvrımı
- Normal form adım adım ilerleme şeması

### 5. Değerlendirme (FEDS — Human Risk & Effectiveness)

| Ölçüt | Yöntem |
|-------|--------|
| Açıklama kalitesi | DBA'larla anket (5'li Likert) |
| Eğitim etkinliği | Öğrenci ön/son test |
| Karar destek | Açıklama var/yok karşılaştırması |
| Açıklama doğruluğu | Fitness function katkısı doğrulama |

### 6. İletişim
**Hedef dergi:** JAIS (Journal of AIS), Computers & Education, Information & Management

## Kullanım Senaryoları

### Senaryo 1: DBA Karar Destek
```
Girdi: Legacy VT şeması
Çıktı: Önerilen yeni şema + her attribute için açıklama
DBA: "Hmm, Orders tablosundan CustomerName'i çıkarmış. 
      Neden? → Açıklama: Redundancy %32 azaltma."
DBA kararı: ✅ Onayla / ❌ Reddet (nedeniyle birlikte)
```

### Senaryo 2: Öğrenci Eğitimi
```
Öğrenci: Normalizasyon ödevi verilmiş
Sistem: Öğrencinin şemasını değerlendiriyor + açıklama üretiyor
Öğrenci: "Ben neden 2NF'de kaldım?"
Sistem: "SiparişTarihi, MüşteriID'ye fonksiyonel bağımlı. 
         Ayrı entity'ye taşımalısın."
```

## Teknoloji Yığını

- **SHAP:** `shap` Python kütüphanesi
- **LIME:** `lime` Python kütüphanesi
- **Görselleştirme:** D3.js, Plotly, Graphviz
- **Örnek tabanlı açıklama:** Case-based reasoning

## İnovasyon

- İlk açıklanabilir otomatik normalizasyon sistemi
- Fitness function'ların anlamsal çevirisi
- DBA-AI işbirliği modeli

## Kaynaklar

- Akadal, E., & Satman, M.H. (2022). A Novel Automatic Relational Database Normalization Method. *Acta Informatica Pragensia*, 11(3), 293-308.
- Lundberg, S.M., & Lee, S.I. (2017). A Unified Approach to Interpreting Model Predictions. *NeurIPS*.
- Ribeiro, M.T., et al. (2016). "Why Should I Trust You?": Explaining the Predictions of Any Classifier. *KDD*.
- Arrieta, A.B., et al. (2020). Explainable Artificial Intelligence (XAI): Concepts, Taxonomies, Opportunities and Challenges. *Information Fusion*, 58, 82-115.

---
*Hazırlayan: Donna 🎯*
