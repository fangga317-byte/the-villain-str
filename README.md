# VILLAIN X BUG Panel — Next.js + Supabase + Vercel

## Fitur
- Login dan registrasi dengan Supabase Auth
- Dashboard dan katalog produk
- Pemesanan dan riwayat pesanan
- Halaman pembayaran dengan poster QRIS yang disertakan
- Admin dapat menambah produk dan mengubah status pesanan
- Desain responsif dengan background gambar pengguna

## 1. Buat database
1. Buat project di https://supabase.com
2. Buka SQL Editor, jalankan seluruh isi `supabase.sql`.
3. Di Authentication > URL Configuration, isi Site URL dengan URL Vercel setelah deploy. Tambahkan URL preview/development yang diperlukan ke Redirect URLs.

## 2. Jalankan lokal
1. Salin `.env.example` menjadi `.env.local`.
2. Isi `NEXT_PUBLIC_SUPABASE_URL` dan `NEXT_PUBLIC_SUPABASE_ANON_KEY` dari Project Settings > API.
3. Jalankan `npm install` lalu `npm run dev`.

## 3. Deploy ke Vercel
1. Upload project ini ke repositori GitHub.
2. Di Vercel pilih Add New > Project dan impor repositori.
3. Tambahkan dua Environment Variables dari `.env.local` di Vercel Project Settings > Environment Variables.
4. Deploy.

## 4. Jadikan akun sebagai admin
1. Daftar akun melalui aplikasi.
2. Di Supabase SQL Editor jalankan (ganti alamat email):
   `update public.profiles set role = 'admin' where email = 'email-kamu@example.com';`
3. Logout lalu login kembali.

## Catatan pembayaran & keamanan
- Gambar QRIS berasal dari pengguna dan belum diverifikasi. Pastikan QRIS benar-benar milikmu/berizin dan cek nama penerima sebelum menerima pembayaran.
- Pembayaran belum diverifikasi otomatis. Pengguna menandai sudah bayar; admin harus memeriksa pembayaran secara manual sebelum mengubah status pesanan.
- Aplikasi memakai Row Level Security (RLS). Jangan pernah menaruh service-role key di frontend atau di repositori.
