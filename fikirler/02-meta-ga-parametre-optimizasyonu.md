# Fikir 2: Meta-GA ile Parametre Optimizasyonu ⭐⭐

## Özet

Emre'nin mevcut genetik algoritmasındaki hiperparametreleri (popülasyon boyutu, jenerasyon sayısı, crossover/mutation oranları, fitness function ağırlıkları) otomatik olarak optimize eden bir meta-GA katmanı eklemek.

## Motivasyon

Orijinal çalışmada:
- **Eşit ağırlıklar** kullanılmış: w₁=w₂=w₃=w₄=0.25
- GA parametreleri **elle ayarlanmış**
- **Farklı dataset türleri** için farklı optimal parametreler olabilir
- %72 oranı **arttırılabilir**

> *"We tried various methods to define the best weights, but a global set of weights was not available for all cases."* — Akadal & Satman (2022)

## Temel Soru

> Her dataset türü için en uygun GA parametreleri nedir? Bunu otomatik bulabilir miyiz?

## Metodoloji (DSRM)

### 1. Problem Tanımlama
Mevcut algoritmanın performansı dataset'e göre değişiyor. Elle ayarlanmış parametreler suboptimal olabilir.

### 2. Çözüm Hedefleri
- Dataset özelliklerine göre otomatik parametre seçimi
- %72'yi %85-90 aralığına çıkarmak

### 3. Artifact
**Self-Tuning Normalization Engine** — meta-optimizasyon katmanı

### 4. Tasarım Detayları

#### Meta-GA Yapısı:

```
Üst Seviye GA (Meta-GA)
├── Kromozom: [pop_size, gen_count, crossover_rate, mutation_rate, w1, w2, w3, w4]
├── Fitness: Alt GA'nın başarı oranı (exact match %)
└── Çıktı: Dataset için optimal parametre seti

Alt Seviye GA (Emre'nin Orijinal Algoritması)
├── Kromozom: Veritabanı şeması
├── Fitness: 4 fitness function
└── Çıktı: Normalize edilmiş şema
```

#### Dataset Özellik Vektörü:

| Özellik | Açıklama |
|---------|----------|
| N (kayıt sayısı) | Dataset büyüklüğü |
| A (attribute sayısı) | Sütun sayısı |
| C (kardinalite) | Benzersiz değer oranı |
| R (redundancy) | Tekrar eden kayıt oranı |
| T (veri türü dağılımı) | Numerik/kategorik/tarih oranı |

#### Hyperparameter Tuning Yöntemleri:

1. **Meta-GA:** GA'nın GA ile optimizasyonu
2. **Bayesian Optimization:** Gaussian Process ile efektif arama
3. **Grid Search + Random Search:** Baseline karşılaştırma
4. **Reinforcement Learning:** Parametre seçimini RL ajanına bırakma

### 5. Değerlendirme (FEDS — Purely Technical)

| Ölçüt | Yöntem |
|-------|--------|
| Exact match iyileştirmesi | Orijinal vs. meta-optimize edilmiş |
| Konverjans hızı | Kaç jenerasyonda stabil hale geliyor? |
| Genelleştirilebilirlik | Görülmemiş dataset'lerde performans |
| Parametre adaptasyonu | Farklı dataset türleri için doğruluk |

### 6. İletişim
**Hedef dergi:** Applied Soft Computing, Expert Systems with Applications, Information Sciences

## Beklenen Sonuçlar

- **%72 → %85-90** exact match artışı
- Dataset türüne göre **otomatik parametre önerisi**
- **Performans profili:** Küçük/büyük, sparse/dense dataset'ler için optimal ayarlar

## İnovasyon

- İki seviyeli GA (Meta + Object-level)
- Dataset-aware parametre seçimi
- "No free lunch" prensibine pratik çözüm

## Kaynaklar

- Akadal, E., & Satman, M.H. (2022). A Novel Automatic Relational Database Normalization Method. *Acta Informatica Pragensia*, 11(3), 293-308.
- Bergstra, J., & Bengio, Y. (2012). Random Search for Hyper-Parameter Optimization. *JMLR*, 13, 281-305.
- Snoek, J., et al. (2012). Practical Bayesian Optimization of Machine Learning Algorithms. *NeurIPS*.

---
*Hazırlayan: Donna 🎯*
