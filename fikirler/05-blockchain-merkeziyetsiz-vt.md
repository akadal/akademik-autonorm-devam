# Fikir 5: Blockchain / Merkeziyetsiz VT ⭐⭐⭐

## Özet

Emre'nin iki uzmanlığının kesişimi: **Blockchain + Veritabanı tasarımı.** Merkeziyetsiz veritabanları (BigchainDB, IPFS + SQLite, merkeziyetsiz SQL) için otomatik şema tasarım ilkeleri ve araçları geliştirmek.

## Motivasyon

Web3 / DApp ekosistemi hızla büyüyor:
- **BigchainDB:** MongoDB + blockchain hybrid
- **IPFS + SQLite:** Merkeziyetsiz dosya + lokal sorgu
- **The Graph:** Blockchain verisi indeksleme
- **Ceramic Network:** Merkeziyetsiz veri grafiği
- **Space and Time:** Merkeziyetsiz data warehouse

Ancak **merkeziyetsiz veritabanlarında şema tasarımı** hiç incelenmemiş:
- Veri immutable — update/delete yok, sadece append
- Shard/key distribution blockchain özgü
- Consensus overhead veri yapısını etkiliyor
- Gas cost (blockchain) veri yapısını etkiliyor

> **"Blockchain-based Database Design"** WoS taramamızda **0 makale** çıktı.

## Literatürdeki Boşluk

| Alan | Çalışma Sayısı |
|------|---------------|
| Blockchain + Supply Chain | ~26 |
| Blockchain + Healthcare | ~18 |
| Blockchain + Accounting | ~37 |
| **Blockchain + VT Tasarımı** | **0** |
| **Blockchain + Normalizasyon** | **0** |
| Merkeziyetsiz VT şema tasarımı | **0** |

## Metodoloji (DSRM)

### 1. Problem Tanımlama
Web3 geliştiricileri veri yapısı tasarlarken blockchain özgü kısıtları göz ardı ediyor. Gas cost, immutable veri, consensus gecikmesi — bunlar şema tasarımını etkiliyor ama hiç araştırılmamış.

### 2. Çözüm Hedefleri
- Blockchain özgü kısıtları içeren şema tasarım ilkeleri
- Gas cost-aware normalizasyon
- Immutable veri için append-only şema pattern'leri

### 3. Artifact
**Decentralized Schema Designer (DSD)** — blockchain-aware VT tasarım aracı

### 4. Tasarım Detayları

#### Blockchain Özgü Fitness Function'lar:

```python
# f1: Gas cost minimization
# Her transaction = gas cost. Veri yapısı gas'ı etkiler.
f1 = estimated_gas_cost / max_acceptable_gas

# f2: Immutable data efficiency
# Update/delete yok. History tracking gerekli mi?
f2 = 1 - (redundant_history / total_history)

# f3: Shard/key distribution
# Blockchain üzerinde veri nerede? Shard mantığı.
f3 = distribution_uniformity

# f4: Query decentralization
# Merkeziyetsiz sorgu desteği. The Graph, IPFS index.
f4 = decentralized_query_support

# f5: Consensus latency impact
# Veri yapısı consensus gecikmesini nasıl etkiler?
f5 = 1 - (consensus_rounds / critical_threshold)
```

#### Normalizasyon için Blockchain Kısıtları:

| İlişkisel Kural | Blockchain Uyarlaması |
|----------------|----------------------|
| 1NF (Atomic değerler) | ✅ Aynı — her attribute atomic |
| 2NF (Kısmi bağımlılık yok) | ⚠️ Dikkat — her entity = ayrı transaction |
| 3NF (Transitive bağımlılık yok) | ❌ **Gerekli değil** — denormalize etmek gas cost azaltır |
| BCNF | ❌ **Tavsiye edilmez** — join = fazla gas |

> **Blockchain'de denormalizasyon tercih edilir!** Join'ler cross-contract call = pahalı.

#### Append-Only Şema Pattern'leri:

```json
// İlişkisel: Customers (CustomerID, Name, Address)
// Blockchain: Her update = yeni kayıt

{
  "customer_history": [
    { "block": 10001, "name": "Ali", "address": "İstanbul" },
    { "block": 10500, "name": "Ali", "address": "Ankara" },
    { "block": 11000, "name": "Ali Veli", "address": "Ankara" }
  ],
  "current_snapshot": { "name": "Ali Veli", "address": "Ankara" }
}
```

### 5. Değerlendirme (FEDS — Technical Risk & Efficacy)

| Ölçüt | Yöntem |
|-------|--------|
| Gas cost | Ethereum testnet (Sepolia) üzerinde ölçüm |
| Sorgu performansı | The Graph vs. doğrudan blockchain |
| Veri bütünlüğü | Immutable kanıtı (hash chain) |
| Ölçeklenebilirlik | Farklı ağlarda test (Ethereum, Polygon, Solana) |

### 6. İletişim
**Hedef dergi:** MISQ (kuramsal katkı yüksekse), JAIS, Information & Management, Expert Systems with Applications

**Hedef konferans:** DESRIST (Design Science odaklı), ICIS (en üst seviye)

## Kullanım Senaryoları

### Senaryo 1: DApp E-ticaret (Solidity + IPFS)
```
Girdi: Ürün, Sipariş, Müşteri dataset'leri

Blockchain önerisi:
- products (on-chain): { productID, price, stock }
- product_details (IPFS): { description, images, metadata }
- orders (on-chain): { orderID, productIDs[], amounts[], total }
- customer_history (append-only): her update = yeni block

Açıklama: "Fiyat/stok on-chain (güven). Detaylar IPFS (ucuz depolama). 
           Append-only = audit trail."
```

### Senaryo 2: Merkeziyetsiz Kimlik (DID)
```
Dataset: Kullanıcı kimlik bilgileri, sertifikalar, yetkiler

Blockchain önerisi:
- did_registry (on-chain): { did, public_key, status }
- credentials (IPFS + hash on-chain): { credential_hash, issuer, type }
- credential_history (append-only): her yeni sertifika = yeni kayıt

Açıklama: "Kimlik anahtarı on-chain (immutability). 
           Sertifikalar IPFS (büyük veri). 
           Hash on-chain = doğrulama."
```

## Teknoloji Yığını

- **Ethereum:** web3.py, Hardhat
- **IPFS:** ipfs-http-client
- **BigchainDB:** bigchaindb-driver
- **The Graph:** subgraph geliştirme
- **Testnet:** Sepolia, Mumbai (Polygon)

## İnovasyon

- **İlk blockchain-aware normalizasyon kuramı**
- Gas cost-aware şema tasarımı
- Append-only pattern kataloğu
- "Blockchain'te neden denormalize?" — ilk akademik cevap

## Akademik Etki Potansiyeli

| Kriter | Değer |
|--------|-------|
| Novelty | Çok yüksek (literatürde 0 makale) |
| Pratik Relevance | Web3 geliştiricileri için kritik |
| Interdisciplinary | Blockchain + VT + YBS |
| Emre'nin Uzmanlığı | İki alanı birleştiriyor |

## Kaynaklar

- Akadal, E., & Satman, M.H. (2022). A Novel Automatic Relational Database Normalization Method. *Acta Informatica Pragensia*, 11(3), 293-308.
- McConaghy, M., et al. (2016). BigchainDB: A Scalable Blockchain Database. *Whitepaper*.
- Benet, J. (2014). IPFS - Content Addressed, Versioned, P2P File System. *arXiv*.
- Wüst, K., & Gervais, A. (2018). Do you need a Blockchain? *Crypto Valley Conference*.
- Zheng, Z., et al. (2017). An Overview of Blockchain Technology: Architecture, Consensus, and Future Trends. *IEEE BigData*.

---
*Hazırlayan: Donna 🎯*
