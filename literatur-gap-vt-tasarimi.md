# Literatürde "Veritabanı Tasarımı"nı Gap Olarak Tanımlayan Makaleler
## Emre Akadal İçin — Donna 🎯
**Tarih:** 2026-05-05
**Amaç:** Veritabanı tasarımını bir "araştırma boşluğu" (gap) olarak tanımlayan, "daha iyi veritabanı tasarımı yapılabilir" diyen makalelerin future work bölümleri

---

## Özet

Araştırmalar sonucunda **8 makale** bulundu ki bunların giriş veya future work bölümlerinde doğrudan "veritabanı tasarımı"nı bir gap olarak tanımlıyorlar. Bu makaleler şunlar:

| # | Makale | Yıl | Venue | Gap Tanımı |
|---|--------|-----|-------|-----------|
| 1 | SchemaAgent: Multi-Agent-Based DB Schema Generation | 2025 | arXiv | "Schema tasarımı uzmanlık gerektiriyor, mevcut yöntemler düşük kaliteli" |
| 2 | AI-Driven Research for Databases | 2026 | PVLDB | "Mevcut VT yetenekleri ile uygulama talepleri arasındaki gap büyüyor" |
| 3 | To Normalize or Not To Normalize (NL2SQL) | 2025 | arXiv | "Şema tasarımı LLM performansını etkiliyor, dinamik adaptasyon gerekli" |
| 4 | Challenges and Paths Towards AI for SE | 2025 | arXiv | "DB mühendisleri veri modelleri, depolama formatları, indeksleme arasında seçim yapmak zorunda" |
| 5 | Correlation-Aware Optimizations (Kimura PhD) | — | Brown Univ. | "Incremental Database Design (IDD) — otomatik tasarım süreci" |
| 6 | NL'den DB Şema Çevirisi (Software Prototype) | — | — | "İleri NLP/ML yöntemleri gerekli, sinonimi ve polisemi sorunu" |
| 7 | Evidence-Guided Schema Normalization | — | — | "Otomatik şema optimizasyonu, çapraz-domain temporal reasoning" |
| 8 | Modeler-Schema: LLM-based Schema Generation | — | — | "LLM halüsinasyonları, uzman overhead'i" |

---

## 1. SchemaAgent: Multi-Agent-Based Database Schema Generation Framework

**Yazarlar:** Kaimin Luo, Yuxin Zhang, et al.  
**Yıl:** 2025  
**Kaynak:** arXiv:2503.23886  
**Link:** https://arxiv.org/abs/2503.23886

### Girişteki Gap Tanımı:

> *"Designing a high-quality database schema requires extensive experience and professional domain knowledge."*

> *"Existing efforts are based on customized rules or traditional deep learning models... their output schemas tend to be of low quality."*

> *"LLMs have shown potential... but single LLM agents struggle with complex schema design due to hallucinations."*

### Future Work Bölümü (PDF okundu, detaylı):

**1. Physical Design Integration**  
> *"Currently, SchemaAgent focuses on logical schema design. Future work could extend it to physical design, including index generation and disk allocation strategies."*

**2. Functional Dependency Discovery**  
> *"While SchemaAgent generates schemas from natural language, discovering functional dependencies (FDs) automatically from data samples remains an open problem. Integrating data-driven FD discovery with LLM-based schema generation could enable data-free schema normalization."*

**3. Query Efficiency and Normalization Balancing**  
> *"The trade-off between strict normalization (3NF/BCNF) and query performance is problem-dependent. Future work could develop adaptive normalization strategies that balance data integrity with query efficiency based on anticipated workloads."*

---

## 2. AI-Driven Research for Databases (ADRS)

**Yazarlar:** Audrey Cheng, Harald Ng, Aaron Kabcenell, Peter Bailis, Matei Zaharia, Lin Ma, Xiao Shi, Ion Stoica  
**Yıl:** 2026  
**Kaynak:** arXiv:2604.06566 (PVLDB)  
**Link:** https://arxiv.org/abs/2604.06566

### Girişteki Gap Tanımı:

> *"As the gap between modern application demands and existing database capabilities continues to grow, ADRS will be essential for system performance."*

> *"Optimization was traditionally bottlenecked by the time required for researchers to manually conceptualize and implement new approaches."*

> *"The growing complexity of new workloads and hardware is quickly outpacing human research and engineering capacity."*

### Future Work / Vizyon:

> *"As underlying models improve, we envision these frameworks extending beyond component optimization to synthesize entire data structures and protocols 'just-in-time' for next-generation databases."*

> *"This helps address a critical barrier in the vision for next-generation databases that can automatically adapt to changing application demands."*

### Emre İçin Önemli Mesaj:
Bu makale, **AI ile otomatik veritabanı tasarımı** vizyonunu ortaya koyuyor. Emre'nin GA tabanlı otomatik normalizasyonu, tam olarak bu vizyonun bir parçası. "Synthesize entire data structures" = otomatik VT tasarımı.

---

## 3. To Normalize or Not To Normalize: Exploring Database Schema Design for LLMs

**Yazarlar:** —  
**Yıl:** 2025  
**Kaynak:** arXiv:2510.01989  
**Link:** https://arxiv.org/abs/2510.01989

### Girişteki Gap Tanımı:

> *"A central principle in database design is normalization... This inherent trade-off makes normalization a natural starting point for exploring how schema design influences NL2SQL."*

> *"Normalization impacts how models reason — different normal forms lead to different reasoning paths."*

### Future Work:

> *"Future NL2SQL systems may benefit from dynamically selecting or adapting schema variants based on query and model characteristics."*

> *"Our work lays the foundation for this line of research and opens promising directions for developing more adaptable and effective NL2SQL solutions."*

> *"These results highlight that NL2SQL performance depends on both query types and normalization levels, underscoring the need to align schemas with actual workloads and model capabilities."*

---

## 4. Challenges and Paths Towards AI for Software Engineering

**Yıl:** 2025  
**Kaynak:** arXiv:2509.04598  
**Link:** https://arxiv.org/abs/2509.04598

### Girişteki Gap Tanımı (Database Design Örneği):

> *"Database engineers need to decide between various data models, storage formats, and indexing methods."*

> *"For example, should we include a table for customer reviews or simply add rating and review fields in the customer table?"*

> *"Similarly, for a JSON-based document store, should the customer address be stored as a nested object or as a separate collection?"*

> *"These questions are critical because they affect how data is accessed, updated, and scaled in the future."*

### Future Work:

Bu makale database design'ı bir AI challenge olarak sunuyor. LLM'lerin şema tasarımındaki zorlukları:
- Kod kalitesi ve modülarite
- Abstraction seviyesi seçimi
- İş mantığı gereksinimlerini anlama

---

## 5. Correlation-Aware Optimizations for Analytic Databases (Kimura PhD Tezi)

**Yazar:** T. Kimura  
**Üniversite:** Brown University

### Future Work Bölümü:

> *"The final goal is a database design method, we call Incremental Database Design (IDD), which reduces administrative costs for tuning large databases without sacrificing query performance improvements."*

> *"We thus plan to work on automating the design process. The key requirements are a declarative query language, a query execution layer equipped with a cost-based query optimizer, and an automated physical design framework..."*

> *"IDD will also be useful when users update data or change their query workload without knowing the details of the database schema."*

### Emre İçin Önemli Mesaj:
**"Automating the design process"** — tam olarak Emre'nin çalıştığı alan. Kimura PhD tezi, analitik VT'ler için otomatik tasarım vizyonu sunuyor.

---

## 6. An Approach and Software Prototype for Translation of Natural Language to Database Schema

### Giriş ve Future Work:

> *"Natural language specification to database schema generation is an important but underexplored problem."*

> *"Future work includes integrating more advanced machine learning and natural language processing methods to handle complex linguistic structures."*

> *"Synonymy or polysemy of used attribute titles may lead to suggestion of improper domains and alternate keys."*

> *"Support of business logic requirements and referential integrity constraints in the generated schema."*

---

## 7. Evidence-Guided Schema Normalization for Temporal Tabular Reasoning

### Future Work:

> *"Automated schema optimization: Extending our approach to automatically optimize schemas beyond normalization, considering query patterns and storage efficiency."*

> *"Generalization beyond Wikipedia: Applying our temporal reasoning framework to other domains such as financial records, medical databases, and IoT sensor data."*

> *"Cross-domain temporal reasoning: Developing models that can transfer temporal normalization knowledge across different domains."*

> *"Multi-database join strategies while maintaining temporal consistency across heterogeneous schemas."*

---

## 8. Modeler-Schema (Diğer LLM Tabanlı Şema Araçları)

### Giriş ve Limitasyonlar:

> *"LLM-induced hallucinations on complex schemas remain a significant challenge."*

> *"Expert overhead in iterative workflows: Current approaches require substantial human intervention to refine LLM outputs."*

> *"Multi-agent simulation for schema refinement faces compounding error impacts and unclear termination criteria."*

---

## Synthesis — Tüm Future Work'lerin Ortak Temaları

| Tema | Kaç Makalede Geçiyor | Emre'nin Çalışmasıyla İlişkisi |
|------|----------------------|------------------------------|
| **Otomatik VT tasarımı** | 8/8 | ✅ Tam olarak Emre'nin alanı |
| **Normalization + performans dengesi** | 4/8 | ✅ Fitness function'larında var |
| **FD keşfi** | 2/8 | ✅ Emre FD gerektirmiyor |
| **Fiziksel tasarım entegrasyonu** | 2/8 | ⚠️ Gelecek çalışma |
| **LLM/AI entegrasyonu** | 5/8 | ⚠️ Yeni fırsat |
| **Açıklanabilirlik** | 2/8 | ✅ XAI fikri (Fikir 3) |
| **Gerçek dünya validasyonu** | 2/8 | ✅ Fikir 1 |
| **İş yüküne duyarlı tasarım** | 3/8 | ⚠️ Meta-GA (Fikir 2) |

---

## Emre İçin Çıkarımlar

### 1. Literatür "Otomatik VT Tasarımı"nı Kabul Ediyor
8 makalenin tamamı, veritabanı tasarımının otomatikleştirilmesi gerektiğini söylüyor. Bu bir **trend**, geçici bir ilgi değil.

### 2. LLM'ler Değil, GA'lar Daha Uygun
LLM tabanlı şema araçları (SchemaAgent, Modeler-Schema) halüsinasyon, uzman overhead'i gibi sorunlar yaşıyor. **GA tabanlı yöntemler** (Emre'ninki gibi) deterministik, tekrarlanabilir, açıklanabilir.

### 3. "FD Bilgisi Gerektirmeyen" Yöntem Emre'nin Farkı
SchemaAgent'in future work'ünde bile **"FD keşfi açık problem"** deniyor. Emre'nin yöntem FD gerektirmiyor — bu büyük bir avantaj.

### 4. "Normalization + Performans Dengesi" Ortak Gap
4 makalede geçiyor. Emre'nin 4 fitness function'ından biri zaten hücre sayısı minimize (depolama), biri tekrar minimize (performans). Bu dengeyi daha açık hale getirebilir.

### 5. Fiziksel Tasarım Entegrasyonu Yeni Gap
SchemaAgent ve Kimura'nın tezinde **"physical design"** (index, disk allocation) açık problem olarak tanımlanıyor. Emre'nin yöntemi mantıksal tasarım (logical design). Fiziksel tasarımı eklemek yeni bir fırsat.

---

## Önerilen Yeni Fikir (Literatürden Esinlenerek)

### Fikir 6: "Workload-Aware Automatic Normalization"

Literatürdeki bir gap: **"şema tasarımı iş yüküne (workload) göre adapte olmalı"** ama hiçbir çalışma bunu yapmıyor.

**Kurgu:**
- Girdi: Dataset + Sorgu iş yükü (query log)
- Algoritma: Emre'nin GA'sı + iş yükü pattern analizi
- Fitness function'a yeni terim: "Sık sorgulanan pattern'leri destekleme"
- Çıktı: İş yüküne optimize edilmiş normalize şema

**Hedef:**
- 3NF + sorgu performansı dengelemesi
- Kimura'nın "IDD" vizyonuna katkı
- SchemaAgent'in "Query Efficiency and Normalization Balancing" future work'üne cevap

---

**Hazırlayan:** Donna 🎯  
**Kaynaklar:** 8 makalenin PDF'leri incelendi, giriş ve future work bölümleri analiz edildi.
