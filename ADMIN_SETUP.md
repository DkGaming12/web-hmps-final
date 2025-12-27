# Admin Menu (Decap/Netlify CMS)

Project ini web statis (tanpa build). Supaya posting “Kegiatan/Berita HMPS” tidak perlu ngoding manual, kita pakai **Decap CMS (Netlify CMS)** yang mengedit file JSON: `data/posts.json`.

## Cara akses
- Buka: `/admin/` (contoh: `https://domain-kamu.netlify.app/admin/`)
- Admin akan mengelola daftar posting di `data/posts.json`

## Role: Admin Dev vs Admin
Karena web ini statis, kontrol “akses semuanya” paling aman & simpel dilakukan lewat **Netlify Dashboard**:
- **Admin Dev**: akun Netlify *owner/maintainer* situs → bisa akses semuanya (setting, deploy, Identity, Git Gateway, dll).
- **Admin**: user Netlify Identity yang diundang → fokus tambah/edit posting lewat `/admin/`.

Catatan: di CMS sendiri, Admin Dev & Admin sama-sama bisa edit posting (sesuai kebutuhan). Akses fitur “semua” (setting situs, undang user, dll) tetap hanya Admin Dev di Dashboard Netlify.

## Setup di Netlify (wajib sekali)
1. Netlify Dashboard → Site settings → **Identity** → Enable
2. Identity → **Registration**: pilih invite-only (disarankan)
3. Identity → **Services** → Enable **Git Gateway**
4. Identity → **Users**: Invite email Admin

Setelah itu, Admin bisa login di `/admin/`.

## Struktur posting
File: `data/posts.json`
- `id`: unik (dipakai untuk link `post.html?id=...`)
- `title`: judul
- `date`: format `YYYY-MM-DD`
- `excerpt`: ringkasan
- `image`: optional (bisa upload via CMS)
- `url`: optional (kalau mau link ke halaman lama seperti `pkd.html`)
- `content`: optional (Markdown, akan dirender di `post.html`)
- `published`: true/false

## Cara membuat posting baru
- Masuk `/admin/`
- Buka **Posting Kegiatan → Daftar Posting**
- Klik **Add** di list Posts
- Isi minimal: `id`, `title`, `date`, `excerpt`, `published=true`
- Pilih salah satu:
  - Isi `content` (Markdown) → otomatis tampil di `post.html?id=...`
  - Atau isi `url` → tombol “Baca Selengkapnya” akan menuju link itu

