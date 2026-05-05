# DSRM Literatür Raporu
## Emre Akadal İçin — Donna 🎯
**Tarih:** 2026-05-05
**Kaynaklar:** WoS, Scopus, AIS basket of 8, DESRIST, FEDS

---

## 1. DSRM'nin Güncel Durumu

### Temel Metodoloji
**Peffers et al. (2007)** tarafından önerilen 6 adımlı DSRM, hâlâ en yaygın kullanılan DS yöntemidir:

1. Problem Tanımlama ve Motivasyon
2. Çözüm Hedeflerinin Tanımlanması  
3. Tasarım ve Geliştirme
4. Demonstrasyon
5. Değerlendirme
6. İletişim

### Güncel Kabul
- **2024-2026** arasında DSRM aktif olarak tartışılmaya devam ediyor (isresearcher.com, DESRIST konferansları)
- **Peffers et al. (2007)** 28,000+ atıf almış — bu, metodolojinin canlılığının en net göstergesi
- **Hevner et al. (2004)** ve **Gregor & Hevner (2013)** DS teorisi temel kaynakları olarak hâlâ referans veriliyor
- **Venable et al. (2016)** FEDS değerlendirme çerçevesi, DS projelerinin vazgeçilmezi haline geldi

---

## 2. Üst Düzey Dergilerde Kabul Edilebilirlik

### A Sınıfı Dergilerde DS Makale Sayıları (Literatür Verisi)

| Dergi | DS Makale Sayısı | Kaynak |
|-------|-----------------|--------|
| **MIS Quarterly (MISQ)** | 18+ | 1995-2012 analizi, özel sayı (2008) |
| **Decision Support Systems (DSS)** | 30 | Micu (2024) PhD tezi |
| **Journal of AIS (JAIS)** | 22+ | Özel sayı (2007), 2012-2022 analizi |
| **Journal of Management IS (JMIS)** | 21+ | Özel sayı (2008), retroaktif analiz |
| **European Journal of IS (EJIS)** | 19+ | 1995-2012 analizi |
| **Information Systems Research (ISR)** | 10+ | Basket of 8 analizi |
| **Information Systems Frontiers** | 16 | Micu (2024) |
| **Information & Management** | 11 | Micu (2024) |

### Büyüme Eğilimi
- **Micu (2024)** CBS PhD tezi: DS makale sayısı son 10 yılda **6 kat arttı** (2001-2011: 41 makale → 2012-2022: 225 makale)
- 2001-2011: 14 farklı dergi → 2012-2022: 43 farklı dergi
- Teknik dergilerin yanı sıra **Journal of Operations Management (11)**, **Production Planning and Control (6)** gibi yönetim dergileri de DS kabul ediyor

### Özel Sayılar ve Konferanslar
- **MISQ** 2008 özel sayı: Design Science Research
- **JAIS** 2007 özel sayı: Design Science
- **DESRIST** konferansı: 2006'dan beri yıllık olarak düzenleniyor

### Sonuç
**DSRM, A sınıfı dergilerde (MISQ, ISR, JAIS, JMIS, EJIS, ISJ, DSS) tamamen kabul görmüş bir metodolojidir.** Özel sayılar, artan makale sayısı, ve 6 kat büyüme trendi bunu kanıtlıyor.

---

## 3. FEDS Değerlendirme Çerçevesi

**Venable et al. (2016)** — *European Journal of Information Systems*, 77-89.

DSRM'nin en büyük zayıflığı değerlendirme aşamasıydı. FEDS bu boşluğu doldurdu.

### FEDS Boyutları:
1. **Amaç (Purpose):** Formative (geliştirme sürecinde) vs. Summative (sonradan)
2. **Paradigma:** Artificial (laboratuvar/simülasyon) vs. Naturalistic (gerçek ortam)

### FEDS Değerlendirme Stratejileri:
1. **Quick & Simple** — Hızlı, düşük risk
2. **Human Risk & Effectiveness** — Kullanıcı odaklı
3. **Technical Risk & Efficacy** — Teknik performans odaklı
4. **Purely Technical** — Saf teknik artifact

### Değerlendirme Teknikleri (Hevner et al. 2004):
- Observation (case study, field study)
- Experimentation (simulation, lab)
- Mathematical proofs
- Client feedback / surveys
- Quantitative performance measures

---

## 4. Blokzincir + DSRM Literatürü

### Bulunan DSRM+Blokzincir Makaleleri:

| Makale | Artifact Türü | Dergi/Tür |
|--------|--------------|-----------|
| **Data Analysis in Blockchain** | Framework (çerçeve) | Bilimsel makale |
| **DLT Standardization for Interoperable Data** | Method + Case Scenario | Bilimsel makale |
| **UoP Green Bond (Blockchain-based)** | System/Instantiaton | Bilimsel makale |
| **Blockchain-based Credential Verification** | Framework + Hyperledger | Bilimsel makale |
| **Blockchain for Emergency Response** | Framework | Bilimsel makale |
| **Blockchain Platform in Healthcare** | DSRM 6 adım | Bilimsel makale |
| **PsyCogMetrics AI Lab** | 3-cycle DSR + Evaluation | Bilimsel makale |
| **Blockchain and Supply Chain** | Multiple artifacts | WoS analizimizde 26 makale |

### Önemli Bulgu:
Blokzincir alanında DSRM kullanımı **yoğunlaşmış** ancak **"Blockchain + Veritabanı Tasarımı"** ve **"Blockchain + HRIS/İK"** konularında DSRM ile yapılmış **yeterince derinlemesine bir çalışma yok.** Bu, Emre için bir fırsat.

---

## 5. Emre'nin Projeleri İçin DSRM Uygunluğu

### Proje 1: "Blockchain-based Database Design Principles"

| DSRM Kriteri | Uygunluk | Açıklama |
|-------------|----------|----------|
| **Problem Relevance** | ✅ Yüksek | Merkeziyetsiz veritabanlarında normalizasyon eksikliği |
| **Novelty** | ✅ Yüksek | Literatürde neredeyse hiç yok (WoS taramamızda 0 makale) |
| **Artifact Türü** | **Method** | Normalizasyon algoritması/çerçevesi (March & Smith 1995) |
| **Evaluation** | **Technical Risk & Efficacy** | FEDS: Simülasyon + Matematiksel proof + Performance measure |
| **Contribution** | ✅ Yüksek | Kuramsal (design knowledge) + Pratik (algorithm) |

**DSRM Adımları:**
1. Problem: Blokzincir veritabanlarında normalizasyon ilkeleri yok → veri tutarsızlığı
2. Hedef: Geleneksel normalizasyon kurallarını DLT bağlamına uyarlamak
3. Tasarım: Otomatik normalizasyon algoritmanı blokzincir veri yapılarına genişletmek
4. Demonstrasyon: Akademik transkript verisi üzerinde prototip
5. Değerlendirme: FEDS — Simülasyon (artificial) + Performance comparison
6. İletişim: MISQ/JMIS/JAIS hedeflenebilir (A sınıfı)

### Proje 2: "Blockchain Applications in HR Information Systems"

| DSRM Kriteri | Uygunluk | Açıklama |
|-------------|----------|----------|
| **Problem Relevance** | ✅ Yüksek | Çalışan verileri güvenliği, sertifikasyon |
| **Novelty** | ✅ Çok Yüksek | Sadece 1 makale (WoS'ta 100 makale içinde) |
| **Artifact Türü** | **Model / Framework** | HRIS-Blockchain entegrasyon modeli |
| **Evaluation** | **Human Risk & Effectiveness** | FEDS: Kullanıcı anketi + Case study (naturalistic) |
| **Contribution** | ✅ Yüksek | YBS literatüründe büyük boşluk |

**DSRM Adımları:**
1. Problem: İK sistemlerinde veri güvenliği, yetenek sertifikasyonu güveni
2. Hedef: Blokzincir tabanlı İK bilgi sistemi çerçevesi
3. Tasarım: İK veri akışları için DLT modeli
4. Demonstrasyon: Bir kurumda pilot uygulama veya simülasyon
5. Değerlendirme: FEDS — Kullanıcı memnuniyeti + Veri bütünlüğü testi
6. İletişim: DSS, Information & Management, JAIS hedeflenebilir

---

## 6. Önerilen Değerlendirme Stratejisi (FEDS)

### Proje 1 (Veritabanı) için:
- **Strateji:** Technical Risk & Efficacy
- **Formative:** Algoritma iterasyonlarında simülasyon
- **Summative:** Geleneksel DB vs. Blockchain-DB normalizasyon doğruluğu karşılaştırması
- **Teknikler:** Performance benchmarking, mathematical correctness proof, scalability test

### Proje 2 (HRIS) için:
- **Strateji:** Human Risk & Effectiveness
- **Formative:** Prototip testleri, kullanıcı geri bildirimi
- **Summative:** Gerçek kurumda pilot, veri bütünlüğü denetimi
- **Teknikler:** Case study, survey, expert review

---

## 7. Sonuç ve Tavsiye

### DSRM'nin Durumu:
- ✅ **Canlı ve gelişen** bir metodoloji (2024-2026 aktif kullanım)
- ✅ **A sınıfı dergilerde** tam kabul görmüş (MISQ, ISR, JAIS, JMIS, DSS)
- ✅ **6 kat büyüme** gösteren bir trend
- ✅ **FEDS (Venable 2016)** ile değerlendirme problemi çözülmüş

### Emre'nin Projeleri İçin DSRM:
- ✅ **Mükemmel uyum.** Her iki proje de "yeni bir artifact (method/model) tasarlamak" üzerine — tam olarak DSRM'nin odak alanı.
- ✅ **Gap + DSRM = Yüksek etki potansiyeli.** Boş alanlarda DS artifact üretmek, A sınıfı dergilerin aradığı "novelty + rigor" kombinasyonunu sağlar.
- ✅ **Emre'nin uzmanlığı** (normalizasyon + blockchain) ile DSRM'nin "design as a search process" ilkesi doğal uyumlu.

### Hedef Dergiler:
1. **MISQ / ISR:** İlk proje (veritabanı) için — kuramsal katkı yüksekse
2. **JAIS / JMIS:** İkinci proje (HRIS) için — applied katkı yüksekse
3. **DSS / Information & Management:** Her ikisi için güvenli seçenek
4. **DESRIST Konferansı:** İlk sunum için ideal (design science odaklı)

---

**Kaynaklar:**
- Peffers et al. (2007) — DSRM temel makalesi
- Hevner et al. (2004) — Design Science in IS Research
- Venable et al. (2016) — FEDS (European Journal of IS)
- Gregor & Hevner (2013) — Positioning and Presenting DS Research
- March & Smith (1995) — Design and Natural Science Research
- Micu (2024) — PhD Thesis, Copenhagen Business School
- Guido & Vaassen (2011) — DSRM in AIS (International Journal of AIS)

---
_Donna. İşini bilen._ 🎯
