# Fikir 4: NoSQL Modellerine Genişletme ⭐

## Özet

Mevcut algoritmayı ilişkisel modelin dışına çıkarıp NoSQL veritabanları (document, column-family, graph, key-value) için otomatik şema tasarımı yapacak şekilde genişletmek.

## Motivasyon

Modern uygulamalar artık sadece ilişkisel VT kullanmıyor:
- **MongoDB** — Document (JSON/BSON)
- **Cassandra** — Column-family
- **Neo4j** — Graph
- **Redis** — Key-value
- **Amazon DynamoDB** — Document + Key-value hybrid

Ancak **NoSQL şema tasarımı** hâlâ uzmanlık gerektiriyor:
- Embedding vs. Referencing kararı
- Partition key seçimi
- Denormalizasyon stratejisi
- Aggregation pipeline optimizasyonu

> **"Automatic NoSQL Schema Design"** literatürde neredeyse **hiç yok.**

## Literatürdeki Boşluk

| Alan | Çalışma Sayısı (WoS/Scopus) |
|------|----------------------------|
| Otomatik ilişkisel VT tasarımı | ~30 |
| Otomatik NoSQL VT tasarımı | **< 5** |
| GA + NoSQL | **1-2** |

## Metodoloji (DSRM)

### 1. Problem Tanımlama
NoSQL veritabanları şema esnekliği sunuyor ama bu esneklik kötü tasarıma yol açıyor. Performans sorunları, tutarsızlık, ölçeklenebilirlik problemleri.

### 2. Çözüm Hedefleri
- Dataset özelliklerine göre NoSQL modeli seçimi
- Otomatik embedding/referencing kararı
- Partition/cluster key önerisi

### 3. Artifact
**Polyglot Schema Designer** — çok model destekli otomatik şema aracı

### 4. Tasarım Detayları

#### Model Seçimi (Dataset → NoSQL Model):

| Dataset Özelliği | Önerilen Model |
|-----------------|---------------|
| Karmaşık ilişkiler, ağ yapısı | Graph (Neo4j) |
| Yüksek yazma hacmi, zaman serisi | Column-family (Cassandra) |
| Esnek şema, nested veri | Document (MongoDB) |
| Basit key-value, cache | Key-value (Redis) |
| Karmaşık sorgular, transactions | İlişkisel (PostgreSQL) |

#### MongoDB İçin Fitness Function'lar:

```python
# f1: Embedding benefit
# Yüksek birlikte erişim (co-access) = embedding avantajlı
f1 = 1 - (co_access_count / total_query_count)

# f2: Array size risk
# Array çok büyükse → referencing tercih et
f2 = avg_array_size / max_safe_array_size

# f3: Update isolation
# Sık güncellenen alan ayrı dokümanda = referencing
f3 = update_frequency * referencing_benefit

# f4: Query pattern match
# Sık sorgulanan pattern'leri destekleme
f4 = 1 - (supported_patterns / total_patterns)
```

#### Cassandra İçin Partition Key Seçimi:

```python
# f1: Data distribution uniformity
# Eşit dağılım = yüksek parallelism
f1 = 1 - (max_partition_size / avg_partition_size)

# f2: Query support
# Sık sorgulanan WHERE clause'ları partition key'de olmalı
f2 = supported_queries / total_queries

# f3: Hot spot avoidance
# Aşırı sıcak partition'dan kaçınma
f3 = 1 - hot_spot_probability
```

### 5. Değerlendirme (FEDS — Technical Risk & Efficacy)

| Ölçüt | Yöntem |
|-------|--------|
| Sorgu performansı | YBench / YCSB benchmark |
| Depolama verimliliği | Disk kullanımı |
| Ölçeklenebilirlik | Load test, cluster test |
| Şema doğruluğu | Expert review |

### 6. İletişim
**Hedef dergi:** Information Sciences, Future Generation Computer Systems, Journal of Big Data

## Kullanım Senaryoları

### Senaryo 1: E-ticaret (MongoDB)
```
Dataset: Orders, Customers, Products, Categories

İlişkisel şema:
- Orders (OrderID, CustomerID, ProductID, ...)
- Customers (CustomerID, Name, ...)
- Products (ProductID, Name, CategoryID, ...)

NoSQL önerisi:
- orders collection: { _id, customer: { _id, name, address },
                       products: [ { _id, name, price } ],
                       total, status }
- Açıklama: "Siparişler müşteri ve ürünle birlikte sık sorgulanıyor. 
             Embedding %40 daha az join."
```

### Senaryo 2: IoT Sensör (Cassandra)
```
Dataset: SensorID, Timestamp, Location, Temperature, Humidity

Partition key önerisi: (Location, date_bucket)
Clustering key: Timestamp

Açıklama: "Konuma göre sorgu = en sık pattern. 
           Zaman sıralaması = clustering."
```

## Teknoloji Yığını

- **MongoDB:** pymongo
- **Cassandra:** cassandra-driver
- **Neo4j:** neo4j-python-driver
- **Redis:** redis-py
- **Benchmark:** YCSB (Yahoo! Cloud Serving Benchmark)

## İnovasyon

- İlk model-agnostik otomatik NoSQL şema tasarımı
- Dataset-aware model seçimi
- Embedding/referencing karar mekanizması

## Kaynaklar

- Akadal, E., & Satman, M.H. (2022). A Novel Automatic Relational Database Normalization Method. *Acta Informatica Pragensia*, 11(3), 293-308.
- Sadalage, P.J., & Fowler, M. (2012). *NoSQL Distilled*. Addison-Wesley.
- MongoDB Documentation — Schema Design Patterns
- DataStax Documentation — Cassandra Data Modeling

---
*Hazırlayan: Donna 🎯*
