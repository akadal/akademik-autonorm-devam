# Fikir 6: Missing Value ile VT Tasarımı — 5. Fitness Function ⭐⭐⭐

## Özet

Emre'nin mevcut 4 fitness function'una **5. bir fitness function** eklemek: **Missing Value Handling**. WoS'ta bulunan ACM TODS (2021, 15 atıf) makalesi, "missing value'lu veriler için şema tasarımı" gap'ini tanımlıyor. Emre'nin yöntemi ham veri üzerinde çalışıyor — bu özelliği eklemek doğal bir genişletme.

## Motivasyon

WoS'ta bulunan makale:
- **"Embedded Functional Dependencies and Data-Completeness Tailored Database Design"** (ACM TODS, 2021, 15 atıf)
- **Gap:** *"We establish a principled schema design framework for data with missing values."*
- **Gap:** *"These foundations enable us to introduce generalizations of Boyce-Codd and Third normal forms that avoid processing difficulties of any application data."*

Gerçek dünya verilerinde **missing value** yaygın:
- Anket verilerinde cevapsız sorular
- IoT sensör verilerinde bağlantı kesintileri
- Finansal verilerde raporlama gecikmeleri
- Sağlık verilerinde eksik ölçümler

## Mevcut 4 Fitness Function

| # | Fitness Function | Amaç |
|---|----------------|------|
| f1 | Hücre sayısı minimize | Depolama verimliliği |
| f2 | Tekrar eden kayıt sayısı minimize | Redundancy azaltma |
| f3 | Entity sayısı minimize | Basitlik |
| f4 | Numerik entity sayısı minimize | Veri tipi optimizasyonu |

## Önerilen 5. Fitness Function: Missing Value Robustness

```python
# f5: Missing value dayanıklılığı
# Amaç: Missing value'lu attribute'ları ayrı entity'lere yerleştirerek
# tutarsızlığı minimize etmek

f5 = missing_value_penalty

# Formülasyon:
# Her attribute için missing value oranı hesapla
# Missing value oranı yüksek attribute'ları ayrı entity'lere ayır
# Böylece NULL değerlerin ana tabloda yayılması önlenir

missing_ratio(attr) = count(NULL) / count(total_records)

# Eğer missing_ratio > threshold (örn: 0.3):
#   → Attribute'u ayrı entity'ye taşı (optional relationship)
# Eğer missing_ratio < threshold:
#   → Attribute'u ana entity'de tut (mandatory relationship)

f5 = sum(missing_ratio(attr) * entity_size_penalty)
```

## Örnek Senaryo

```
Dataset: Müşteri Bilgileri
┌─────────────┬──────────┬─────────────┬─────────────┬────────────┐
│ CustomerID  │ Name     │ Phone       │ Address     │ Income     │
├─────────────┼──────────┼─────────────┼─────────────┼────────────┤
│ 1           │ Ali      │ 5551234     │ İstanbul    │ 50000      │
│ 2           │ Veli     │ NULL        │ NULL        │ 45000      │
│ 3           │ Ayşe     │ 5555678     │ NULL        │ NULL       │
│ 4           │ Fatma    │ NULL        │ Ankara      │ 60000      │
└─────────────┴──────────┴─────────────┴─────────────┴────────────┘

Missing Value Oranları:
- Name:     0%  → Ana entity'de (Customers)
- Phone:    50% → Ayrı entity (CustomerPhones) — optional 1:1
- Address:  50% → Ayrı entity (CustomerAddresses) — optional 1:1
- Income:   25% → Ana entity'de (threshold = 30% altında)

Önerilen Şema:
Customers(CustomerID, Name, Income)
CustomerPhones(CustomerID, Phone) — CustomerID = PK + FK
CustomerAddresses(CustomerID, Address) — CustomerID = PK + FK

Avantaj:
- Customers tablosunda NULL yok (veya çok az)
- Sorgular: Customers = hızlı, CustomerPhones = sadece ihtiyaç olduğunda
- Veri kalitesi artar
```

## DSRM ile Kurgu

### 1. Problem Tanımlama
WoS'ta (ACM TODS, 2021) missing value'lu veriler için şema tasarımı gap'i tanımlanmış. Mevcut normalizasyon teorisi NULL değerleri varsaymıyor.

### 2. Çözüm Hedefleri
- Missing value oranına göre otomatik entity ayrımı
- NULL yayılımını minimize eden şema tasarımı

### 3. Artifact
**Genişletilmiş GA:** 5 fitness function'lu otomatik normalizasyon aracı

### 4. Demonstrasyon
- Gerçek dataset'ler üzerinde (Kaggle, UCI) missing value oranları analizi
- Before/after karşılaştırması

### 5. Değerlendirme (FEDS — Technical Risk & Efficacy)

| Ölçüt | Yöntem |
|-------|--------|
| NULL oranı azalması | Ana entity'deki NULL yüzdesi |
| Sorgu performansı | JOIN maliyeti vs. NULL filtre maliyeti |
| Depolama verimliliği | Sparse matrix vs. ayrı entity |
| Veri kalitesi | Completeness metric (ISO 25012) |

### 6. İletişim
**Hedef dergi:** Information Systems, Expert Systems with Applications, DSS

## Farklı Missing Value Pattern'leri

| Pattern | Açıklama | Şema Önerisi |
|---------|----------|-------------|
| **MCAR** (Missing Completely at Random) | Rastgele eksik | Genel threshold kullan |
| **MAR** (Missing at Random) | Başka değişkene bağlı | Bağımlılık analizi ekle |
| **MNAR** (Missing Not at Random) | Sistematik eksik | Domain knowledge gerekli |
| **Yapısal eksik** | Soru cevapsız kalmış | Ayrı entity (zorunlu değil) |
| **Zaman serisi eksik** | Sensör arızası | Interpolasyon + entity |

## Teknoloji

- **Missing value tespiti:** pandas `.isnull()`
- **Oran hesaplama:** `.isnull().mean()`
- **GA entegrasyonu:** f5 fitness function olarak ekleme
- **Threshold optimizasyonu:** Meta-GA ile optimal threshold bulma

## Kaynaklar (WoS)

- **ACM TODS (2021):** "Embedded Functional Dependencies and Data-completeness Tailored Database Design" — DOI: 10.1145/3450518
- **Akadal & Satman (2022):** Orijinal 4 fitness function
- **ISO 25012:** Data Quality model

---

**Hazırlayan:** Donna 🎯  
**Tarih:** 2026-05-05  
**Kaynak:** WoS (SCI/SSCI) taraması
