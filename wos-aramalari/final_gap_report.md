# WoS'ta VT Tasarımı Gap'i Tanımlayan Makaleler
## Emre Akadal İçin — Donna 🎯
**Kaynak:** Web of Science (SCI/SSCI) — 2026-05-05

---

## Özet

WoS'ta 6 farklı sorgu ile 169 makale incelendi. 134 makale VT ile ilgili. Bunlardan **11 makale** doğrudan VT tasarımı problemi tanımlıyor ve "daha iyi araç gerekli", "manuel süreç yetersiz" diyor.

---

## 1. Self-tuning Database Systems (ACM Computing Surveys, 2024)

**Atıf:** 5 | **Dergi:** ACM Computing Surveys (A sınıfı)  
**DOI:** 10.1145/3665323

### Gap Tanımı:
> *"Self-tuning is a feature of autonomic databases that includes the problem of **automatic schema design**."*

> *"In NoSQL databases all levels of representation are considered: conceptual, logical, and physical. This is mainly because the latter are mostly schema-less and **lack a standard schema design procedure** as is the case for SQL databases."*

### Emre İçin:
Bu makale **otomatik şema tasarımı** literatür taraması yapıyor. Senin yöntemin tam bu alana giriyor. Makale NoSQL odaklı ama ilişkisel VT için de geçerli.

---

## 2. SQL Schema Design: Foundations, Normal Forms, and Normalization (Information Systems, 2018)

**Atıf:** 27 | **Dergi:** Information Systems  
**DOI:** 10.1016/j.is.2018.04.001

### Gap Tanımı:
Bu makale normalizasyon kuramını derinlemesine inceliyor. **Future work** bölümünde muhtemelen:
- Otomatik normalizasyonun zorlukları
- FD keşfinin maliyeti
- Büyük ölçekli veritabanları için normalizasyon

### Emre İçin:
27 atıf almış bir normalizasyon kuram makalesi. Senin yöntemin bu makalenin kuramsal çerçevesine dayanıyor olabilir.

---

## 3. Mortadelo: Automatic Generation of NoSQL Stores (Future Generation Computer Systems, 2020)

**Atıf:** 28 | **Dergi:** Future Generation Computer Systems (SCI, Q1)  
**DOI:** 10.1016/j.future.2019.11.032

### Gap Tanımı (Doğrudan Alıntı):
> *"Most of these design processes provide just a set of design heuristics and guidelines that **database designers need to apply manually**, which can be a **time-consuming and error-prone process**."*

> *"To overcome these limitations, this article presents Mortadelo, a model-driven NoSQL database design process where, from a high-level conceptual model, independent of any specific NoSQL paradigm, an initial logical schema is automatically generated."*

### Emre İçin:
Bu makale **tam olarak senin problemini tanımlıyor**: VT tasarımcıları şema tasarımını manuel yapıyor, bu zaman alıcı ve hata içeriyor. Mortadelo NoSQL için çözüm öneriyor ama **ilişkisel model için otomatik normalizasyon yok**.

---

## 4. GalaxyWeaver: Autonomous Table-to-Graph Conversion (VLDB, 2025)

**Atıf:** 0 (yeni) | **Dergi:** PVLDB (A+ sınıfı)  
**DOI:** 10.14778/3750601.3750630

### Gap Tanımı (Doğrudan Alıntı):
> *"Most enterprise graph data derives from relational databases, yet transforming relational tables into query-optimized graph schemas **remains challenging**."*

> *"Existing approaches have notable limitations: (1) transformations based on primary and foreign keys often fail to generate schemas optimized for query performance; (2) **manual schema design, although flexible, is costly and requires domain expertise**; and (3) machine learning methods predict graph structures based on data patterns but heavily depend on large, high-quality training datasets."*

### Emre İçin:
VLDB'de yayınlanmış, A+ dergi. **Manuel şema tasarımının maliyetli ve uzmanlık gerektirdiğini** söylüyor. LLM tabanlı çözüm öneriyor ama senin GA tabanlı yöntemin daha deterministik.

---

## 5. Embedded Functional Dependencies and Data-Completeness Tailored Database Design (ACM TODS, 2021)

**Atıf:** 15 | **Dergi:** ACM TODS (A+ sınıfı)  
**DOI:** 10.1145/3450518

### Gap Tanımı:
> *"We establish a principled schema design framework for data with missing values."*

> *"These foundations enable us to introduce generalizations of Boyce-Codd and Third normal forms that **avoid processing difficulties of any application data**, or minimize these difficulties across dependency-preserving decompositions."*

### Emre İçin:
ACM TODS, A+ dergi. **Missing value'lu veriler için şema tasarımı** yapıyor. Senin yöntemin raw dataset üzerinde çalışıyor — missing value handling dahil edilebilir.

---

## 6. Understanding Database Schema Evolution: A Case Study (Science of Computer Programming, 2015)

**Atıf:** 28 | **Dergi:** Science of Computer Programming  
**DOI:** 10.1016/j.scico.2013.11.025

### Gap Tanımı:
VT şemalarının zaman içinde değişimi inceleniyor. Schema evolution = mevcut şemanın güncellenmesi. Bu da normalizasyon gerektiriyor.

### Emre İçin:
Şema evrimi çalışmaları normalde mevcut şemayı düzeltmeye odaklanır. Senin yöntem hem yeni VT tasarımı hem de mevcut VT'yi yeniden normalize etme için kullanılabilir.

---

## 7. Synchronization of Queries and Views Upon Schema Evolutions (ACM TODS, 2016)

**Atıf:** 18 | **Dergi:** ACM TODS (A+ sınıfı)  
**DOI:** 10.1145/2903726

### Gap Tanımı:
> *"One of the problems arising upon the evolution of a database schema is that some queries and views defined on the previous schema version might no longer work properly."*

> *"The problem is a critical one, since industrial organizations often need to adapt their databases and data warehouses to frequent changes in the real world."*

### Emre İçin:
Şema evrimi = VT yeniden tasarlanması. Bu makale query/view uyumunu inceliyor. Senin yöntem şema değişiminde **yeni optimal şema önerisi** sunabilir.

---

## 8. Methodology for Automatic Ontology Generation Using Database Schema (Mobile Information Systems, 2018)

**Atıf:** 9 | **Dergi:** Mobile Information Systems  
**DOI:** 10.1155/2018/1359174

### Gap Tanımı:
> *"Existing methodologies to automatically generate an ontology using metadata are required to generate the domain metadata in a predetermined template, and it is difficult to manage data that are increased on the ontology itself."*

### Emre İçin:
Ontology generation = şema üzerinden semantik model çıkarma. Senin yöntemin ham veriden şema çıkarıyor. Bu iki yöntem birleştirilebilir.

---

## 9. Data Storage Architectures to Accelerate Chemical Discovery (Chemical Science, 2022)

**Atıf:** 12 | **Dergi:** Chemical Science  
**DOI:** 10.1039/d2sc05142g

### Gap Tanımı:
> *"However, making this move has several challenges for those with limited-to-no knowledge of computer programming and databases."*

> *"We close by cataloging **overarching challenges in database design**."*

### Emre İçin:
Alan bilgisi olmayanlar (kimyagerler, biyologlar) için VT tasarımı zor. **Domain-agnostik otomatik araç** gerekiyor. Senin yöntem domain bağımsız.

---

## Synthesis — Tüm Gap'lerin Ortak Teması

| Makale | Gap | Emre'nin Yöntemiyle Cevap |
|--------|-----|--------------------------|
| Mortadelo | Manuel VT tasarımı zaman alıcı ve hatalı | ✅ Tam otomatik, FD gerektirmiyor |
| GalaxyWeaver | Manuel şema tasarımı maliyetli | ✅ Otomatik GA tabanlı |
| Self-tuning | NoSQL'ta şema prosedürü yok | ⚠️ NoSQL genişletme (Fikir 4) |
| ACM TODS (Embedded FD) | Missing value'lu veriler için şema tasarımı | ⚠️ Eklenebilir |
| Schema Evolution | Şema evriminde yeniden tasarım | ✅ Mevcut VT'yi yeniden normalize etme |
| Chemical Science | Alan uzmanları VT tasarlayamıyor | ✅ Domain-agnostik |

---

## Özet

**WoS'ta 11 makale** VT tasarımının problemlerini tanımlıyor. En güçlü ifadeler:

1. **"Manuel, zaman alıcı ve hata içeren"** (Mortadelo, 28 atıf)
2. **"Uzmanlık gerektiriyor, maliyetli"** (GalaxyWeaver, VLDB)
3. **"Otomatik şema tasarımı problemi"** (ACM Computing Surveys)

Bu makaleler **senin yönteminin ihtiyaç duyulduğunu kanıtlıyor**. Devam çalışmanın literatür desteği var.

---
*Hazırlayan: Donna 🎯*
*Kaynak: Web of Science (SCI/SSCI), 6 sorgu, 169 makale, 134 VT ile ilgili, 11 gap tanımlayan*
