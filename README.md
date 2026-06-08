# Klasifikasi Kepadatan Lalu Lintas — CNN MobileNetV2

Implementasi model **Convolutional Neural Network (CNN)** dengan arsitektur **MobileNetV2** dan **Transfer Learning** untuk mengklasifikasi kepadatan lalu lintas menjadi tiga kelas: **Lancar**, **Sedang**, dan **Padat**. Dilengkapi landing page interaktif dengan inference langsung di browser menggunakan **TensorFlow.js**.

> Tugas Besar Machine Learning — Semester Genap 2025/2026
> Politeknik Negeri Indramayu — Prodi D4 Sistem Informasi Kota Cerdas

---

## Fitur Utama

- **Klasifikasi 3 kelas** — Lancar, Sedang, Padat berdasarkan citra visual jalan
- **Transfer Learning** — MobileNetV2 pre-trained ImageNet, di-fine-tune pada dataset traffic density
- **Inference di Browser** — Model TF.js berjalan sepenuhnya di client-side, tanpa server
- **Upload Gambar & Video** — Prediksi real-time untuk gambar statis maupun video
- **Progressive Web Ready** — Landing page responsif, optimasi untuk mobile & desktop

## Performa Model

| Metric | Value |
|--------|-------|
| **Accuracy** | 77.60% |
| **Precision** | 77.49% (weighted) |
| **Recall** | 77.60% (weighted) |
| **F1-Score** | 77.50% (weighted) |
| **Parameters** | 2.4M |
| **Input Shape** | 224 × 224 × 3 |

### Classification Report

| Kelas | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| Lancar | 80.00% | 75.00% | 77.42% | 64 |
| Sedang | 67.19% | 67.19% | 67.19% | 64 |
| Padat | 85.29% | 90.62% | 87.88% | 64 |

## Tech Stack

| Layer | Technology |
|-------|------------|
| **Model** | CNN MobileNetV2, TensorFlow/Keras, Transfer Learning (ImageNet) |
| **Frontend** | Astro 6, Tailwind CSS 4, TensorFlow.js 4 |
| **Deployment** | Vercel (Static) |
| **Tools** | Google Colab, Python 3, Matplotlib, Seaborn |

## Dataset

Dataset citra kondisi jalan dengan **2,396 gambar** yang diklasifikasikan ke dalam 3 kelas:

| Kelas | Jumlah | Persentase |
|-------|--------|------------|
| Lancar | 936 | 46.8% |
| Sedang | 688 | 34.4% |
| Padat | 378 | 18.9% |

**Pembagian data:**
- Training: 2,002 citra (84%)
- Validation: 202 citra (8%)
- Testing: 192 citra (8%)

**Augmentasi data:** Rotation ±15°, Shift 10%, Horizontal Flip, Zoom 10%

**Penanganan imbalanced class:** Class weighting pada training

## Project Structure

```
landing-page/
├── public/
│   ├── model/
│   │   ├── model.json          # TF.js graph model
│   │   └── group1-shard*.bin   # Model weights (3 shards, ~9.5MB)
│   ├── macet.jpg               # Sample image
│   └── favicon.svg             # Cpu icon favicon
├── src/
│   ├── components/
│   │   ├── Navbar.astro        # Fixed navigation bar
│   │   ├── Hero.astro          # Hero section + mock prediction card
│   │   ├── About.astro         # Problem & solution overview
│   │   ├── Dataset.astro       # Dataset distribution & split
│   │   ├── Results.astro       # Metrics, classification report, confusion matrix
│   │   ├── Demo.astro          # Interactive demo (image + video upload)
│   │   ├── Team.astro          # Team members
│   │   └── Footer.astro        # Footer with navigation
│   ├── layouts/
│   │   └── Layout.astro        # Base HTML layout
│   ├── pages/
│   │   └── index.astro         # Main page with scroll reveal & counter animation
│   └── styles/
│       └── global.css          # Global styles, glass morphism, animations
├── Implementasi_CNN_TrafficDensity_FINAL.ipynb  # Google Colab notebook
└── package.json
```

## Getting Started

```bash
# Clone repository
git clone https://github.com/daryibrahim6/traffic-density-cnn.git
cd traffic-density-cnn/landing-page

# Install dependencies
npm install

# Start dev server
npm run dev

# Build for production
npm run build
```

Landing page akan tersedia di `http://localhost:4321`.

## How It Works

1. **Input** — User upload gambar atau video kondisi jalan
2. **Preprocessing** — Resize 224×224, normalisasi `(pixel / 127.5) - 1.0` (MobileNetV2 standard)
3. **Inference** — Model MobileNetV2 + classifier dijalankan via TensorFlow.js di browser
4. **Output** — Prediksi kelas (Lancar/Sedang/Padat) beserta confidence score per kelas

> Seluruh inference dilakukan di browser. Tidak ada data yang dikirim ke server.

## Tim (Kelompok 3)

| Nama | NIM | Peran |
|------|-----|-------|
| Dary Ibrahim Akram | 2307088 | Machine Learning |
| Bunga Purwaningsih | 2307086 | Data Preprocessing |
| Chairani Nayu Nainggolan | 2307087 | Visualization & Evaluation |
| Muhammad Rijal Marzuq | 2307097 | Frontend Development |

## License

Proyek ini dibuat untuk keperluan akademik — Tugas Besar Machine Learning Semester Genap 2025/2026.
