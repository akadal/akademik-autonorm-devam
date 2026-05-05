# Fikir 1: Gerçek VT Denormalize → Normalize ⭐⭐⭐

## Özet

İyi tasarlanmış gerçek dünya veritabanlarını (Sakila, Northwind, Employees vb.) bilerek denormalize edip, Emre'nin otomatik normalizasyon algoritmasıyla tekrar normalize ederek gerçek dünya validasyonu sağlamak.

## Motivasyon

Orijinal çalışmada 250 dataset **senteik olarak üretildi** — 50 iyi VT'den 5 varyasyon. Gerçek dünyada ise:
- Legacy sistemler kötü tasarlanmış
- Hızlı geliştirme denormalizasyona yol açıyor
- Modernize edilmesi gereken binlerce VT var
- Otomatik normalizasyon pratik bir ihtiyaç

## Metodoloji (DSRM)

### 1. Problem Tanımlama
Legacy veritabanları kötü tasarlanmış. Manuel normalize etmek uzmanlık gerektiriyor ve maliyetli.

### 2. Çözüm Hedefleri
- Denormalize VT'yi algoritmaya ver
- Otomatik normalize şema üret
- Orijinal şema ile karşılaştır

### 3. Artifact
Geliştirilmiş GA tabanlı normalizasyon aracı + gerçek VT adaptörü

### 4. Demonstrasyon
- Sakila, Employees, StackOverflow dump üzerinde test
- Denormalize → Normalize süreci

### 5. Değerlendirme (FEDS — Technical Risk & Efficacy)

| Ölçüt | Yöntem |
|-------|--------|
| Exact match oranı | Şema karşılaştırması |
| Normal form uygunluğu | 1NF, 2NF, 3NF, BCNF kontrolü |
| Sorgu performansı | Before/after benchmark |
| Depolama verimliliği | Disk kullanımı karşılaştırması |
| Anomali riski | Insert/Update/Delete anomaly testi |

### 6. İletişim
**Hedef dergi:** Expert Systems with Applications (IF: ~8.5), DSS, Information & Management

## Kullanılacak Veritabanları

| VT | Kaynak | Açıklama |
|-----|--------|----------|
| Sakila | MySQL Official | Film kiralama benchmark'ı |
| Employees | MySQL Official | Büyük İK şeması |
| Northwind | Microsoft | Klasik e-ticaret |
| AdventureWorks | Microsoft | Modern ERP |
| StackOverflow Dump | Archive.org | Gerçek sosyal veri |
| Chinook | SQLite | Müzik dijital |
| Pagila | PostgreSQL | Sakila portu |
| Dell DVD Store | Dell | E-ticaret benchmark |

## Denormalizasyon Stratejisi

Her VT için şu denormalizasyon teknikleri uygulanacak:

1. **Tablo birleştirme** — 1:1 ve 1:N ilişkilerini tek tabloda toplama
2. **Redundancy ekleme** — Foreign key yerine tüm veriyi kopyalama
3. **Attribute tekrarı** — Çok-değerli attribute'ları CSV olarak tek sütunda tutma
4. **JSON/XML sütunları** — Yapılandırılmış veriyi tek sütunda tutma (PostgreSQL jsonb gibi)

## Beklenen Sonuçlar

- %72 oranını gerçek VT'lerde teyit veya iyileştirme
- Sorgu performansı kazancı ölçümü
- Depolama verimliliği analizi
- Gerçek dünya kullanılabilirlik kanıtı

## Kaynaklar

- Akadal, E., & Satman, M.H. (2022). A Novel Automatic Relational Database Normalization Method. *Acta Informatica Pragensia*, 11(3), 293-308.
- TPC-C / TPC-H benchmark şemaları
- MySQL Documentation — Sample Databases

---
*Hazırlayan: Donna 🎯*
