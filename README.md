# Live Zoom Code — Starter (HTML + Tailwind CSS CLI)

Starter kosong untuk live code. Semua styling pakai **Tailwind CSS v4 (CLI)**, semua interaksi pakai **JavaScript murni** tanpa library.

---

## Cara Menjalankan

### 1. Install dependency

```bash
npm install
```

### 2. Jalankan Tailwind CLI (mode watch)

```bash
npm run dev
```

Perintah ini memantau perubahan di `index.html` dan otomatis memperbarui `src/output.css` setiap kali file disimpan.

> Biarkan terminal ini tetap jalan selama ngoding. Jangan ditutup.

Yang dijalankan di balik layar:

```
npx @tailwindcss/cli -i ./src/input.css -o ./src/output.css --watch
```

| Bagian                | Artinya                                          |
| --------------------- | ------------------------------------------------ |
| `-i ./src/input.css`  | File CSS sumber, isinya `@import "tailwindcss"`   |
| `-o ./src/output.css` | File CSS hasil compile, yang dipakai `index.html` |
| `--watch`             | Rebuild otomatis tiap kali file disimpan          |

### 3. Buka halamannya

Buka `index.html` di browser. Paling enak pakai extension **Live Server** di VS Code supaya auto-refresh.

### 4. Build untuk production

```bash
npm run build
```

Sama seperti `dev`, tapi tanpa `--watch` dan hasilnya di-minify.

---

## Struktur Folder

```
live_zoom_code/
├── index.html            # File HTML utama
├── src/
│   ├── input.css         # SUMBER CSS: design token + utility custom
│   └── output.css        # Hasil compile Tailwind — JANGAN diedit, JANGAN di-commit
├── js/
│   └── main.js           # Semua JavaScript
├── assets/
│   ├── images/           # Simpan semua gambar di sini
│   └── icons/            # Simpan semua icon (SVG/PNG) di sini
├── package.json
├── .gitignore
└── README.md
```

> **Penting:** `src/output.css` dibuat otomatis oleh Tailwind. Jangan pernah diedit manual, dan jangan di-commit (sudah masuk `.gitignore`).

---

## Catatan Tailwind v4

Sudah **tidak ada** `tailwind.config.js`. Semua token ditulis sebagai CSS variable di dalam `@theme` pada `src/input.css`:

```css
@theme {
  --color-primary-300: #0093dd; /* -> bg-primary-300, text-primary-300 */
  --text-display-lg: 2.25rem; /* -> text-display-lg */
  --radius-2xl: 1rem; /* -> rounded-2xl */
}
```

Kalau ada kombinasi style yang berulang, bikin utility sendiri:

```css
@utility flex-center {
  display: flex;
  align-items: center;
  justify-content: center;
}
```

---

## Breakpoint

| Ukuran  | Lebar Layar       | Prefix Tailwind         |
| ------- | ----------------- | ----------------------- |
| Mobile  | kurang dari 640px | (default, tanpa prefix) |
| Tablet  | 768px ke atas     | `md:`                   |
| Desktop | 1024px ke atas    | `lg:`                   |

Cara cek: buka Chrome, klik kanan di halaman, pilih **Inspect**, lalu aktifkan **Toggle Device Toolbar**.

---

## Referensi

| Sumber                      | Link                                                   |
| --------------------------- | ------------------------------------------------------ |
| Instalasi Tailwind CLI      | https://tailwindcss.com/docs/installation/tailwind-cli  |
| Dokumentasi Tailwind v4     | https://tailwindcss.com/docs                           |
| Tailwind `@theme`           | https://tailwindcss.com/docs/theme                     |
| Tailwind `@utility`         | https://tailwindcss.com/docs/adding-custom-styles      |
| Chrome DevTools (Responsif) | https://developer.chrome.com/docs/devtools/device-mode |
