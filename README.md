# Gudang Garam International — HTML5 Ad Bundle

## Struktur folder

```
creative/
├── index.html              ← Entry point utama
├── style.css               ← Semua CSS
├── script.embedded.js      ← Semua JavaScript (embedded/bundled)
└── assets/
    ├── Logo_GG.png
    ├── Mur.png
    ├── Mur.webp
    ├── improved_version.png
    ├── bg_improved.png
    ├── bg-price.png
    ├── bg-price-mobile.png
    ├── bg_harga.png
    ├── price-text.png
    ├── perokok_new.png
    ├── perokok_new.jpeg
    ├── Harga_new.png
    └── Harga_new.jpeg
```

## Alur iklan

1. Iklan tampil dengan animasi masuk
2. User menggosok area scratch card
3. Setelah area tergosok cukup → reveal animasi harga tampil
4. Redirect otomatis ke Instagram via `window.clickTag`

## DV360 Click Tag

Project ini menggunakan standar `clickTag` untuk HTML5 zip upload ke DV360.

**Definisi variabel** (di `<head>` `index.html`):
```html
<script type="text/javascript">
    var clickTag = "https://www.instagram.com/priapunyaselera.official?igsh=MTFodjFzb29lZ3MxYw==";
</script>
```

**Redirect setelah scratch selesai** (di `script.embedded.js`):
```js
window.location.href = window.clickTag;
```

DV360 akan otomatis **override** nilai `clickTag` saat iklan tayang, sehingga URL tujuan bisa diganti dari dashboard kampanye tanpa perlu upload ulang.

> **Catatan:** Redirect menggunakan `window.location.href` (bukan `window.open`) agar tidak diblokir popup blocker browser, karena redirect dipicu otomatis via `setTimeout` setelah animasi scratch selesai — bukan dari klik langsung user.

## Cara kirim ke DV360

**Upload sebagai ZIP (HTML5 creative):**
1. Zip seluruh isi folder `creative/` (pastikan `index.html` ada di root zip, bukan di subfolder)
2. Upload ke DV360 → **New Creative → HTML5**
3. DV360 akan otomatis mengenali dan override `clickTag`

**Hosted URL:**
1. Deploy ke hosting (Netlify, Vercel, S3, dll.) → pastikan HTTPS
2. Kirim URL publik ke ad ops, contoh: `https://yourdomain.com/gg-ad/`
