# Kebun — Toko Sayur Segar Online

Website toko sayur online satu halaman (static site) dengan desain premium:
foto produk asli, keranjang belanja fungsional (localStorage), filter kategori,
pencarian live, dan layout responsif penuh — tanpa emoji, semua ikon SVG.

## Struktur

```
index.html      Halaman utama (HTML + CSS + JS dalam satu file)
images/         Foto produk & hero (WebP, 15 file)
404.html        Halaman tidak ditemukan
robots.txt      Aturan crawler + referensi sitemap
sitemap.xml     Daftar URL untuk SEO
dev/            Skrip verifikasi (verify.js, qa2.js) + screenshot — bukan bagian situs
```

## Menjalankan lokal

Tinggal buka `index.html` di browser. Untuk pengembangan dengan server:

```bash
python -m http.server 8137
# buka http://127.0.0.1:8137
```

## Mengedit

- **Produk, harga, kategori** — ubah array `PRODUCTS` dan `CATS` di bagian atas
  `<script>` dalam `index.html`.
- **Foto produk** — taruh file WebP/JPG di `images/` lalu ubah nama file di data produk.
- **Warna & font** — token desain ada di blok `:root` pada `<style>`.

## Verifikasi otomatis

```bash
node dev/verify.js   # 23 cek fungsional (keranjang, filter, cari, checkout, mobile)
node dev/qa2.js      # 20 cek kualitas (kontras WCAG, tinggi kartu, teks terpotong, dll)
```

Keduanya butuh server lokal berjalan (`python -m http.server 8137`) dan Edge
terpasang (dipakai sebagai browser headless via Playwright).

## Deploy

Situs ini statis murni — bisa dihosting di mana saja:

- **GitHub Pages** (yang dipakai saat ini): push ke branch utama, situs live di
  `https://sansaks-jpg.github.io/`. Jangan lupa file `.nojekyll` (sudah ada).
- **Netlify / Vercel / Surge**: drag-and-drop folder ini, atau deploy via CLI.
