# Deskripsi Agent Plugin

## Ringkasan

Agent Plugin adalah kumpulan aturan dan panduan teknis untuk membantu AI agent merancang serta membangun aplikasi web full-stack dengan lebih terstruktur. Aturan disusun dalam file `.mdc` dan dikelompokkan berdasarkan domain, sehingga panduan yang relevan dapat digunakan saat mengerjakan bagian tertentu dari sebuah proyek.

Plugin ini ditujukan untuk membantu menghasilkan implementasi yang lebih konsisten, mudah dirawat, memperhatikan keamanan, dan memiliki pengalaman pengguna yang baik. Hasil akhirnya tetap bergantung pada kebutuhan proyek, konteks yang diberikan, pilihan teknologi, serta proses review dan pengujian.

## Cakupan Panduan

- **Frontend:** Next.js, React, TypeScript, UI/UX, aksesibilitas, internasionalisasi, SEO, dan performa.
- **Backend:** desain API, struktur proyek, clean code, dan pengembangan layanan FastAPI.
- **Database:** Prisma, PostgreSQL, Supabase, migrasi, keamanan data, dan optimasi query.
- **Security:** autentikasi, otorisasi, validasi input, pengelolaan rahasia, dan hardening aplikasi.
- **Testing:** unit test, integration test, pengujian komponen, end-to-end, dan isolasi database test.
- **DevOps:** containerization dan otomasi CI/CD.
- **Monitoring:** logging, error handling, health checks, metrics, dan distributed tracing.

## Daftar File Aturan

Gunakan daftar ini untuk memilih file yang perlu ditinjau atau diperbaiki:

### Backend

- [api-design.mdc](backend/api-design.mdc) — desain endpoint REST, format respons, pagination, dan dokumentasi API.
- [clean-code.mdc](backend/clean-code.mdc) — prinsip clean code, SOLID, penamaan, dan contoh TypeScript/Python.
- [fastapi-backend.mdc](backend/fastapi-backend.mdc) — pola implementasi FastAPI, validasi, dependency injection, dan testing.
- [project-structure.mdc](backend/project-structure.mdc) — struktur folder, pemisahan modul, dan konvensi proyek.

### Database

- [database-prisma-supabase.mdc](database/database-prisma-supabase.mdc) — Prisma, PostgreSQL, Supabase RLS, migrasi, dan optimasi query.

### Frontend

- [accessibility-i18n-seo.mdc](frontend/accessibility-i18n-seo.mdc) — aksesibilitas, internasionalisasi, dan SEO.
- [nextjs-react-uiux.mdc](frontend/nextjs-react-uiux.mdc) — arsitektur Next.js/React, komponen, UI/UX, dan validasi data.
- [performance-uiux.mdc](frontend/performance-uiux.mdc) — Core Web Vitals, rendering, caching, dan optimasi performa.

### Security

- [auth-authorization.mdc](security/auth-authorization.mdc) — autentikasi, sesi, token, dan otorisasi berbasis peran.
- [security-hardening.mdc](security/security-hardening.mdc) — validasi input, CSP, CORS, rate limiting, dan hardening aplikasi.

### Testing

- [testing-strategy.mdc](testing/testing-strategy.mdc) — unit, integration, component, dan end-to-end testing.

### DevOps

- [devops-deployment.mdc](devops/devops-deployment.mdc) — Docker, deployment, dan pipeline CI/CD.

### Monitoring

- [error-handling-logging.mdc](monitoring/error-handling-logging.mdc) — penanganan error, structured logging, dan pelacakan error.
- [observability-monitoring.mdc](monitoring/observability-monitoring.mdc) — metrics, tracing, health checks, dan alerting.

## File yang Perlu Diprioritaskan

Temuan berikut berasal dari pemeriksaan isi panduan saat ini. Perbaiki dan selaraskan contoh serta klaim dokumentasinya sebelum menjadikan aturan tersebut standar proyek:

1. **[security-hardening.mdc](security/security-hardening.mdc)** — kebijakan CSP memakai nonce untuk script, tetapi masih mengizinkan `'unsafe-inline'` pada `style-src`. Selaraskan konfigurasi ini dengan klaim tentang strict CSP dan kebutuhan styling stack yang dipakai.
2. **[auth-authorization.mdc](security/auth-authorization.mdc)** — contoh pembuat token TypeScript menyimpan claim `userId`, sedangkan contoh FastAPI mengambil `sub`. Selain itu, middleware Next.js membaca Bearer token dan menaruh identitas pada response headers; samakan pola autentikasi dan cara meneruskan identitas antar contoh.
3. **[api-design.mdc](backend/api-design.mdc) dan [README.md](README.md)** — format respons yang dijelaskan tidak konsisten. README menyebut envelope `{ success, data, error, meta }`, sedangkan panduan API memberi contoh `data`/`pagination` dan objek `error`. Pilih satu kontrak lalu gunakan konsisten.
4. **[nextjs-react-uiux.mdc](frontend/nextjs-react-uiux.mdc), [accessibility-i18n-seo.mdc](frontend/accessibility-i18n-seo.mdc), dan [performance-uiux.mdc](frontend/performance-uiux.mdc)** — aturan UI melarang CSS biasa, tetapi dua panduan lain memberi contoh CSS. Tentukan apakah proyek wajib memakai Tailwind atau boleh menggunakan CSS, lalu selaraskan instruksinya.
5. **[performance-uiux.mdc](frontend/performance-uiux.mdc)** — contoh `items.sort(...)` mengubah array sumber. Gunakan pola non-mutasi seperti `[...items].sort(...)` agar contoh tidak mendorong perubahan state yang tidak disengaja.

## Hasil yang Ditargetkan

Saat aturan yang sesuai digunakan, AI agent diarahkan untuk:

1. Memahami kebutuhan dan struktur proyek sebelum memilih pendekatan implementasi.
2. Mengikuti pola teknologi dan konvensi yang relevan dengan bagian proyek yang sedang dikerjakan.
3. Mempertimbangkan responsivitas, aksesibilitas, keamanan, performa, dan penanganan error.
4. Menambahkan atau menyesuaikan pengujian untuk perilaku penting.
5. Menghasilkan kode dan antarmuka yang lebih terorganisasi serta lebih mudah ditinjau dan dikembangkan.

## Penggunaan

Pilih atau aktifkan file aturan yang sesuai dengan IDE atau AI agent yang digunakan, lalu berikan kebutuhan website secara spesifik. Sertakan informasi seperti tujuan produk, pengguna, fitur utama, referensi visual, stack yang sudah dipakai, batasan teknis, dan kriteria penerimaan agar hasilnya lebih tepat.

Contoh permintaan:

> Buat dashboard inventaris untuk tim operasional. Gunakan stack yang sudah ada di repository, dukung tampilan mobile, sediakan pencarian dan filter, dan sertakan loading, empty, serta error states. Tinjau aksesibilitas dan jalankan test yang relevan.

## Batasan

Plugin ini adalah panduan kerja, bukan jaminan bahwa setiap website akan sempurna atau siap produksi tanpa pemeriksaan. AI agent tetap perlu mengikuti konteks repository dan versi dependency yang benar. Kode yang dihasilkan perlu ditinjau, diuji, dan disesuaikan sebelum digunakan di lingkungan produksi.