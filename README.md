# Gudang Garam International — HTML5 Ad Bundle

## Struktur folder

```
dist/
├── index.html          ← Entry point utama
├── style.css           ← Semua CSS
├── script.js           ← Semua JavaScript
└── assets/             ← Letakkan semua file gambar di sini
    ├── Logo_GG.png
    ├── Mur.png
    ├── improved_version.png
    ├── bg-price.png
    ├── bg-price-mobile.png
    ├── price-text.png
    └── perokok_new.png
```

## Cara deploy

1. Copy semua file gambar dari project Laravel (`public/assets/`) ke folder `dist/assets/`
2. Upload seluruh folder `dist/` ke hosting (Netlify, Vercel, S3, atau server sendiri)
3. Pastikan semua file bisa diakses via HTTPS

## DV360 Click Tracker

Click macro `%%CLICK_URL_UNESC%%` sudah ditambahkan di:
- `index.html` — pada kedua `<a>` tag (desktop & mobile) di dalam `.scratch-reveal`
- `script.js` — pada anchor yang dibuat secara dinamis setelah scratch selesai

DV360 akan otomatis mengganti `%%CLICK_URL_UNESC%%` dengan URL tracker mereka saat iklan tayang.

**Contoh hasil saat tayang:**
```
https://ad.doubleclick.net/ddm/trackclk/...https://www.instagram.com/...
```

## Cara kirim ke ad ops team

Opsi A — Upload bundle:
- Zip seluruh folder `dist/` → kirim file `.zip`

Opsi B — Hosted URL (direkomendasikan DV360):
- Deploy ke hosting → kirim URL publik, misal: `https://yourdomain.com/gg-ad/`
- DV360 akan load `index.html` dari URL tersebut sebagai iframe/tag
