# KARSA Executive Work Tracker

Prototype premium/internal workspace for PT Karsa Lifestyle Nusantara.

## Konsep akses

Tidak ada halaman Daftar/Register.

Akun dibuat secara internal. Saat user login, sistem membaca profil:
- `Operasional` → membuat assignment + monitoring lintas divisi.
- `Head Divisi` → hanya melihat pekerjaan di divisinya.
- `Staff` → hanya melihat pekerjaan yang ditugaskan ke akunnya.

Contoh routing:
`Operasional → IT → Vicky Ferdiansyah`

Dengan RLS Supabase, akun Finance/R&D/etc. tidak bisa membaca data IT hanya dengan mengubah URL/front-end.

## Fitur UI

- Splash/loading premium dengan logo Karsa.
- Login animation + secure access.
- Responsive mobile layout.
- Sidebar desktop + mobile drawer.
- Overview dashboard.
- KPI: total, in progress, siap review, terkendala, lewat deadline.
- Attention center.
- Division pulse.
- Work register + search/filter.
- Pekerjaan Saya.
- Update progress/status/kendala/next action.
- Auto transition: 100% + In Progress → Siap Review.
- Assignment desk Operasional.
- Weekly evaluation.
- CSV export.
- Organization/structure page.
- Local preview mode.
- Supabase Auth + PostgreSQL + RLS ready.

## Struktur organisasi yang dipakai

- Director — Andre Rizki Juanda
- General Manager — Johannes Betrand S. Pardosi
- Finance — Head Andreas / Staff Rizqia Febrianoor
- IT — Head Dimas Putra Pratama / Staff Vicky Ferdiansyah
- Operasional — Head Muhammad Hasan Niam / Staff Peter Vincent Kusuma
- R&D — Head Alif / Staff Muslimin & Reja Maulana

## Cara menjalankan preview

Bisa dibuka dengan Live Server / GitHub Pages.

Karena `DEMO_MODE = true`, tombol Preview Mode tersedia tanpa database.

## Cara mengaktifkan database sungguhan

1. Buat project Supabase.
2. Buka SQL Editor.
3. Jalankan `supabase/schema.sql`.
4. Buka Authentication > Users.
5. Buat user satu per satu secara internal. Jangan membuat public sign-up.
6. Masukkan profile masing-masing ke `public.profiles`.
7. Edit `config.js`:
   - SUPABASE_URL = Project URL
   - SUPABASE_KEY = Publishable/anon key
   - DEMO_MODE = false
8. Upload folder ini ke GitHub.
9. Aktifkan GitHub Pages.

Jangan pernah menaruh `service_role` / secret key Supabase di frontend.

## Catatan penting

Prototype ini sengaja memisahkan:
- GitHub Pages = tampilan/static hosting
- Supabase Auth = login
- Supabase PostgreSQL = database
- Supabase RLS = pembatasan akses

Untuk produksi berikutnya, tambahkan:
- akun PIC berbasis `assignee_id` (bukan hanya nama)
- notifikasi deadline
- progress history yang terlihat di detail job
- approval/validasi Ops
- audit log
- attachment file
- realtime update antar akun
- password reset internal
- backup dan kebijakan retensi data
