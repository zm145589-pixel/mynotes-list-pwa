# MyNotes PWA Lengkap

Aplikasi catatan PWA dengan backend Node.js bawaan dan database JSON. Tidak membutuhkan `npm install`.

## Jalankan di Windows
1. Ekstrak ZIP.
2. Buka folder `MyNotes-PWA-Lengkap` di VS Code. Pastikan `server.js` terlihat.
3. Buka Terminal > New Terminal.
4. Jalankan `node server.js`.
5. Buka `http://localhost:3000`.

Login admin awal: `admin` / `admin12345`. Segera ganti password admin.

## Deploy online (Railway)
1. Buat repository GitHub baru dan unggah semua isi folder ini (jangan unggah `data.json` yang berisi data pribadi).
2. Di Railway, buat project baru dari repository GitHub tersebut. Railway akan mendeteksi Node.js dan menjalankan `npm start` (package.json tidak punya dependency). Jika diminta, Start Command: `npm start`.
3. Setelah service dibuat, buka Settings/Networking dan pilih Generate Domain agar mendapat URL publik HTTPS.
4. Agar catatan tidak hilang saat restart/deploy, tambahkan Volume pada service dengan Mount Path `/app/data`. Kode otomatis membaca `RAILWAY_VOLUME_MOUNT_PATH` dan menyimpan `data.json` di volume tersebut.
5. Setelah deploy, buka URL publik dan login. Segera ubah password admin awal.

Catatan: ketentuan paket, kredit/trial, dan biaya hosting dapat berubah. Periksa halaman billing platform sebelum mengonfirmasi layanan berbayar. Volume diperlukan untuk menyimpan file JSON secara persisten. Jangan mengandalkan filesystem biasa layanan hosting karena dapat terhapus saat deploy/restart.

## Data dan keamanan
- Data lokal tersimpan di `data.json` di folder proyek.
- Jika memakai Railway Volume, database tersimpan pada volume `/app/data`.
- Backup `data.json` secara berkala. Jangan membagikannya karena berisi data akun dan catatan.
- Password disimpan dalam bentuk hash, bukan teks biasa.
