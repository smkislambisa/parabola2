# AbdUmar Lab Maya — Gerak Parabola

Laboratorium virtual Fisika SMA kelas X–XI. Website statis, responsif, dan dapat dipublikasikan menggunakan GitHub Pages. Tidak membutuhkan backend atau proses build.

## Fitur
- Materi konsep gerak parabola dan persamaan fisika.
- Simulasi interaktif: kecepatan awal, sudut elevasi, ketinggian awal, dan gravitasi.
- Preset gravitasi Bumi, Bulan, Mars, dan Jupiter.
- Animasi lintasan, titik puncak, vektor kecepatan, dan metrik eksperimen.
- Penyimpanan data percobaan di `localStorage`.
- Grafik jangkauan, ekspor CSV.
- LKPD digital, penyimpanan jawaban lokal, dan cetak/Simpan PDF melalui browser.
- Kuis formatif lima soal dengan umpan balik.
- Responsif untuk desktop, tablet, dan ponsel.

## Menjalankan secara lokal
Cara paling sederhana: buka `index.html` di browser modern. Untuk pengalaman yang konsisten, jalankan server lokal, misalnya ekstensi Live Server di VS Code.

## Deploy ke GitHub Pages
1. Buat repository baru, misalnya `abdumar-lab-maya`.
2. Unggah seluruh isi folder proyek ke root repository.
3. Buka **Settings → Pages**.
4. Pada **Build and deployment**, pilih **Deploy from a branch**.
5. Pilih branch `main` dan folder `/ (root)`, lalu Save.
6. Setelah deployment selesai, buka URL Pages yang ditampilkan GitHub.

Alternatif: workflow GitHub Actions sudah disertakan di `.github/workflows/pages.yml`. Pilih **GitHub Actions** sebagai source pada Settings → Pages.

## Custom domain
1. Pastikan domain sudah dimiliki dan DNS dapat dikelola.
2. Di repository, buka **Settings → Pages → Custom domain**, masukkan domain yang sebenarnya, lalu Save. GitHub akan membuat file `CNAME` untuk deployment branch.
3. Atur DNS pada penyedia domain:
   - Untuk subdomain seperti `lab.domainanda.id`: `CNAME` host `lab` → `USERNAME.github.io`.
   - Untuk apex domain seperti `domainanda.id`: gunakan A record GitHub Pages `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`. AAAA record IPv6 tersedia di dokumentasi GitHub.
4. Jangan membuat wildcard DNS. Aktifkan **Enforce HTTPS** setelah sertifikat tersedia.
5. Ganti `USERNAME` dengan username GitHub pemilik repository. Jangan menebak domain sebelum domain final ditetapkan.

Dokumentasi resmi: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site

## Penyimpanan dan privasi
Semua hasil eksperimen dan jawaban LKPD disimpan di browser perangkat yang digunakan (`localStorage`). Data tidak otomatis tersinkronisasi antarperangkat, tidak dikirim ke guru, dan dapat hilang jika data situs/browser dihapus. Ekspor CSV dan cetak PDF disediakan untuk pencadangan manual.

## Asumsi ilmiah
Model 2D ideal, gravitasi konstan, hambatan udara diabaikan. Sumbu vertikal positif ke atas. Waktu pendaratan adalah akar positif persamaan `y(t)=0`, sehingga peluncuran dari ketinggian awal nonnol juga dihitung.

## Catatan pengembangan
Warna identitas menggunakan dasar navy-biru-putih dengan aksen merah muda dan ungu elegan. Untuk penggunaan kelas skala sekolah dengan pengumpulan tugas terpusat, tambahkan backend dan autentikasi pada tahap terpisah.

## Tahap 2 — Advanced Physics Simulation

Pembaruan ini mempertahankan struktur Tahap 1 dan menambahkan:

- Integrasi numerik Runge–Kutta orde 4 (RK4) untuk gerak proyektil.
- Hambatan udara kuadratik opsional dengan parameter efektif `k` (`a_drag = -k |v| v`).
- Vektor kecepatan dan percepatan yang berubah mengikuti waktu simulasi.
- Telemetri posisi, komponen kecepatan, kelajuan, dan percepatan secara real-time.
- Grafik x-t, y-t, vx-t, dan vy-t yang tersinkron dengan animasi.
- Perbandingan lintasan beberapa sudut peluncuran.
- Mode eksperimen bebas dan eksperimen terbimbing.
- Pengaturan kecepatan animasi 0,5× hingga 4×.

### Catatan model fisika

Simulasi menggunakan satuan SI. Model hambatan udara memakai percepatan `a_drag = -k |v| v`; `k` merupakan parameter efektif untuk eksplorasi pembelajaran, bukan nilai koefisien drag universal. Untuk eksperimen kuantitatif benda nyata, nilai tersebut perlu dikalibrasi berdasarkan massa, luas penampang, densitas fluida, dan koefisien drag benda.

### Menjalankan lokal

Buka `index.html` melalui browser modern. Tidak ada backend, database, build step, atau dependensi eksternal yang wajib dipasang. Untuk hasil terbaik, gunakan server lokal sederhana atau GitHub Pages.
