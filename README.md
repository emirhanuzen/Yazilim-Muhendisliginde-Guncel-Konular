# Safety 4.0 Bootcamp – Laboratuvar Föyleri

**Makine:** ABM CNC-D800 CNC Daire Testere Bileme Makinesi

| | |
|---|---|
| **Ad Soyad** | Emirhan Uzen |
| **Öğrenci No** | 230541086 |
| **Grup** | 4-B Gündüz |
| **Tarih** | 23.10.2026 |

Bu depoda Safety 4.0 Bootcamp programının ilk 4 laboratuvar föyü yer alıyor. Hepsi tek bir makine üzerinde doldurulmuştur: **ABM CNC-D800**. Föylerde makinenin fonksiyonel emniyeti (functional safety) ile siber güvenliği (IEC 62443) birlikte ele alınmıştır.

📄 **Föy dosyası:** [`ABM_CNC-D800_Safety40_Lab1-4_Emirhan_Uzen.pdf`](ABM_CNC-D800_Safety40_Lab1-4_Emirhan_Uzen.pdf)

---

## Makine Hakkında

| Özellik | Açıklama |
|---|---|
| Makine | 6 eksenli, tam CNC üst + yüz bileme (Ø100-800 mm testere) |
| Kontrol | ARM işlemcili PLC (MikroC) + TwinCAT 3 PC tabanlı kontrol / HMI |
| Bağlantılar | Motor sıcaklık/akım/tork + şebeke gerilimi izleme, dış veri akışı, bulut telemetri, internete açık uzak servis modülü (7/24 açık) |
| Dosya girişi | Drawworks CAD DXF/DWG yükleme → G-code üretimi |
| Emniyet ekipmanı | Acil durdurma butonu, koruma kabin kapağı kilidi (varsayım: Safety PLC + STO) |

---

## Laboratuvarlar

| # | Laboratuvar | Çıktı | Evidence Pack |
|---|---|---|---|
| 1 | **Safety Architecture** | Safety Function Map | EP 03 Safety Functions |
| 2 | **IEC 62443 Mini Workshop** (Zone & Conduit) | Zone / Conduit Diagram | EP 05 Zone & Conduit |
| 3 | **Threat & Risk + Risk Matrix** | Risk Register | EP 04 Risk Assessment |
| 4 | **Secure Remote Access** | Secure Architecture | EP 02 + EP 06 |

### LAB 1 – Safety Architecture
- **Tehlike:** Yüksek devirli taşlama diski, keskin testere dişleri, 6 eksen arasında ezilme, taş kırılması.
- **Emniyet fonksiyonları:**
  - SF1: Kabin kapağı kilidi (guard locking).
  - SF2: Acil durdurma → STO.
- **Gerekli seviye:** PLr d (Kat. 3).
- **Kritik nokta:** İnternete açık uzak servis modülü → TwinCAT IPC → safety konfigürasyonu.

### LAB 2 – Zone & Conduit
- **Bölgeler:**
  - Z1 Safety
  - Z2 Kontrol
  - Z3 Mühendislik/Dosya
  - Z4 Uzak Erişim DMZ
  - Z5 Kurumsal
- **Geçişler:** C1–C5 arasındaki geçişler ve her birinde yapılacak kontroller.
- **Uzak erişim kararı:**
  - Jump server
  - VPN
  - MFA
  - Kişisel hesap
  - Tam oturum kaydı
  - Varsayılan kapalı

### LAB 3 – Risk Register

| Senaryo | Kapı | Fiziksel sonuç | L × S × E | Öncelik |
|---|---|---|---|---|
| S1 | Uzak servis modülü | Kapak kilidi bypass → uzuv kaybı | 3 × 3 × 2 = **18** | Kritik |
| S2 | CAD/DXF dosya yükleme | Taş kırılması → yaralanma | 2 × 2 × 3 = **12** | Yüksek |
| S3 | Bulut telemetri | E-stop devre dışı → ağır yaralanma | 1 × 3 × 1 = **3** | Düşük → S=3 nedeniyle öne alındı |

### LAB 4 – Secure Remote Access
- **Mevcut yapı:** Doğrudan internet, açık port, paylaşılan parola, düz ağ, kayıt yok.
- **Hedef yapı (5 ilke):**
  1. Kişisel hesap + MFA
  2. VPN
  3. Jump server + tam oturum kaydı
  4. Varsayılan kapalı (operatör onayı, süreli)
  5. Firewall/conduit
- **Safety PLC:** Uzak yoldan erişilemez.
- **Gereksinim:** Emniyet fonksiyonu, kontrol sistemi ve uzak bakım yolundan bağımsız çalışmalıdır.

---

## Depo İçeriği

```
.
├── README.md
└── ABM_CNC-D800_Safety40_Lab1-4_Emirhan_Uzen.pdf
```

---

> ⚠️ Bu föyler bir eğitim çıktısıdır. Resmî denetim, uygunluk değerlendirmesi veya belgelendirme değildir; CE/mevzuat uygunluğu garantisi vermez.
