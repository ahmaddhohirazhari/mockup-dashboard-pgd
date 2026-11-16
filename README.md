# Pegadaian Command Center — Prototipe

Dashboard monitoring realtime jaringan kantor (Pusat, Kanwil, Cabang, Outlet/UPC) dengan 4 tab:
**Peta Jaringan**, **Kinerja KPI**, **Produk**, dan **Risiko**.

> ⚠️ Semua angka adalah **data simulasi** untuk keperluan pitching/prototipe.

## Struktur
- `index.html` — satu file mandiri (peta Indonesia SVG, grafik, data dummy, simulasi realtime). Tanpa dependensi eksternal.
- `vercel.json` — header keamanan + `noindex`.
- `robots.txt` — mencegah indexing mesin pencari.

## Deploy ke Vercel
1. Import repo ini di https://vercel.com/new
2. Framework Preset: **Other** · Build Command: kosong · Output Directory: kosong (root)
3. Deploy → tambahkan domain di **Settings › Domains**

## Menjalankan lokal
Buka `index.html` langsung di browser, atau:
```bash
npx serve .
```

## Integrasi data asli
Ganti fungsi `tick()` (bagian *SIMULASI REALTIME*) dengan stream dari backend, mis.:
```js
const es = new EventSource("/api/realtime/stream");
es.onmessage = e => { const t = JSON.parse(e.data); handleTx(BY[t.officeId], t.produkIdx, t.nilai, t.isEmas); };
```
Data kantor (`O`) dapat diganti dengan response API master kantor.
