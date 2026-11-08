# Swarm Free Mint — Dashboard Publik

Dashboard publik hasil vetting swarm free-mint BSC. Data nyata dari log sweep,
diperbarui tiap 3 jam. Bukan saran investasi.

**Live site (setelah deploy):** `https://<username>.github.io/swarm-free-mint/`

## Isi

- `index.html` — halaman dashboard, satu file mandiri (CSS inline, font sistem,
  tanpa dependensi JS eksternal, tanpa build step).
- `data.json` — semua angka di halaman, dalam format mesin-terbaca, beserta
  `generated_at` dan daftar file log sweep sumber.
- `.github/workflows/pages.yml` — GitHub Actions yang men-deploy repo ini ke
  GitHub Pages setiap push ke `main`.

## Data

Sumber: log sweep swarm di `workspace/goals/free-nft-mint/hidden_files/`:

- `sweep-2026-11-08-0900.md` (sweep 12, 09:00–09:35 WIB — terbaru)
- `sweep-2026-11-08-0600.md` (sweep 11)
- `sweep-2026-11-08-0300.md` (sweep 10)
- `sweep-2026-11-08-0000.md` (sweep 9)
- `sweep-2026-11-07-2100.md` (sweep 8, baseline total 12)

Angka utama (8 Nov 2026): 14 kandidat baru lolos di sweep 12, total lolos aktif
~62, 55 baru lolos 00:00–09:00 WIB, 2 turun status, 8 gugur. Semua 14 kandidat
baru butuh Agent ID (gas saja, BSC). Pasar secondary terverifikasi: 0 untuk
semua kandidat.

Catatan rekonsiliasi: Analis menghitung 52 − 4 keluar + 14 baru = ~62,
sedangkan Koordinator hanya mengonfirmasi 2 keluar (Pumpkinfarm, NULLRAID),
jadi 64 bila hanya keduanya. Komposisi baseline pasti ditugaskan ke sweep 13.

## Cara update

Setelah tiap sweep selesai:

1. Perbarui `data.json` (angka, tabel kandidat, deadline, `generated_at`).
2. Perbarui bagian yang sama di `index.html` — halaman ini sengaja statis,
   jadi kedua file harus diubah bersamaan.
3. Commit dan push ke `main`. Workflow Pages men-deploy otomatis.

## Yang TIDAK ada di situs ini

- Tidak ada tombol mint, tidak ada wallet connect, tidak ada transaksi.
  Eksekutor swarm terkunci: **PREVIEW ONLY • NO MINT**.
- Tidak ada harga, profit, atau win rate. Swarm ini memvettng mint gratis,
  bukan trading.
- Tidak ada data privat: tidak ada alamat wallet pengguna, saldo, nama,
  atau informasi pribadi apa pun. Alamat kontrak yang tampil adalah data
  on-chain publik.

## Disclaimer

Data nyata sweep 9–12. Bukan saran investasi. Lolos vetting bukan berarti aman
— semua 14 kontrak baru punya fungsi owner `withdraw()` / `setMintOpen()` /
`setRoyalty()` yang masih aktif. Tidak ada pasar secondary terverifikasi untuk
satu pun kandidat. Angka supply berubah seiring mint berlangsung; cek ulang
on-chain sebelum bertindak.
