# akademik-autonorm-devam

**Emre Akadal'ın Otomatik Veritabanı Normalizasyonu Çalışmasının Devamı**

Bu repo, Emre Akadal'ın 2022 yılında Acta Informatica Pragensia'da yayınlanan ["A Novel Automatic Relational Database Normalization Method"](https://doi.org/10.18267/j.aip.193) makalesinin devam çalışmalarına ait fikirleri, planları ve literatür notlarını içerir.

## 📄 Orijinal Çalışma

- **Başlık:** A Novel Automatic Relational Database Normalization Method
- **Yazarlar:** Emre Akadal, Mehmet Hakan Satman
- **Dergi:** Acta Informatica Pragensia, 11(3), 293-308
- **Yıl:** 2022
- **DOI:** [10.18267/j.aip.193](https://doi.org/10.18267/j.aip.193)
- **Temel Katkı:** FD (Functional Dependency) bilgisi gerektirmeden, sadece ham veri seti ile tam otomatik ilişkisel veritabanı normalizasyonu. %72 exact match başarı.

## 🎯 Bu Repoda Neler Var?

| Dosya | Açıklama |
|-------|----------|
| [`README.md`](README.md) | Bu dosya — proje özeti |
| [`fikirler/`](fikirler/) | 6 devam çalışma fikri ve detayları |
| [`gap-analizi.md`](gap-analizi.md) | Orijinal çalışmanın literatürdeki boşlukları (gap'ler) |
| [`DSRM-FEDS-raporu.md`](DSRM-FEDS-raporu.md) | Design Science Research Methodology + FEDS değerlendirme çerçevesi raporu |
| [`wos-aramalari/`](wos-aramalari/) | Web of Science sistematik tarama sonuçları ve JSON verileri |

## 💡 Devam Çalışma Fikirleri

1. **[Gerçek VT Denormalize → Normalize](fikirler/01-gercek-vt-denormalize-normalize.md)** ⭐⭐⭐
   - Legacy veritabanlarını denormalize edip algoritmayla normalize etme
   - Gerçek dünya validasyonu, sorgu performansı testi

2. **[Meta-GA ile Parametre Optimizasyonu](fikirler/02-meta-ga-parametre-optimizasyonu.md)** ⭐⭐
   - GA'nın kendi hiperparametrelerini optimize eden üst katman
   - %72 başarıyı artırma potansiyeli

3. **[Açıklanabilirlik (XAI) Entegrasyonu](fikirler/03-aciklanabilirlik-xai.md)** ⭐⭐
   - "Bu attribute neden bu entity'de?" sorusuna yanıt
   - DBA eğitimi ve karar destek sistemi

4. **[NoSQL Modellerine Genişletme](fikirler/04-nosql-genisletme.md)** ⭐
   - MongoDB, Cassandra, Neo4j için otomatik şema tasarımı
   - "Automatic NoSQL Schema Design" alanı neredeyse boş

5. **[Blockchain / Merkeziyetsiz VT](fikirler/05-blockchain-merkeziyetsiz-vt.md)** ⭐⭐⭐
   - İki uzmanlığın kesişimi: Blockchain + Veritabanı tasarımı
   - Web3 / DApp geliştiricileri için araç

6. **[Missing Value ile VT Tasarımı](fikirler/06-missing-value-vt-tasarimi.md)** ⭐⭐⭐
   - 5. fitness function: Missing value robustness
   - WoS'ta ACM TODS (2021, 15 atıf) tarafından tanımlanan gap
   - NULL değerlerin yayılmasını önleyen otomatik şema tasarımı

## 🔬 Metodoloji

Tüm devam çalışmaları **Design Science Research Methodology (DSRM)** ile kurgulanacak ve **FEDS (Framework for Evaluation in Design Science Research)** çerçevesiyle değerlendirilecektir.

| DSRM Adımı | İçerik |
|-----------|--------|
| 1. Problem Tanımlama | Literatürdeki gap ve gerçek dünya sorunları |
| 2. Çözüm Hedefleri | Artifact (method/framework/tool) tanımı |
| 3. Tasarım & Geliştirme | Algoritma/araç geliştirme |
| 4. Demonstrasyon | Prototip ve uygulama |
| 5. Değerlendirme | FEDS: Artificial/Naturalistic + Formative/Summative |
| 6. İletişim | A sınıfı dergi / konferans yayını |

## 🛠️ Teknoloji Yığını (Planlanan)

- **Dil:** Python 3.10+
- **GA Kütüphaneleri:** DEAP, PyGAD
- **Veritabanları:** PostgreSQL, MySQL, SQLite, MongoDB
- **XAI:** SHAP, LIME
- **Benchmark:** TPC-C, TPC-H, Dell DVD Store

## 👤 Hakkında

**Emre Akadal**  
Doçent, İstanbul Üniversitesi İktisat Fakültesi  
Yönetim Bilişim Sistemleri Bölümü  
İstanbul BTC Genel Koordinatörü  
[avesis.istanbul.edu.tr/emre.akadal](https://avesis.istanbul.edu.tr/emre.akadal)

---
*Bu repo akademik araştırma amaçlıdır. Tüm içerik Emre Akadal'ın fikri mülkiyetindedir.*
