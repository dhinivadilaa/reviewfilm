# 🎬 Review Film

Web aplikasi untuk review dan rating film berbasis Laravel + React (Inertia.js).

## Tech Stack

- **Backend**: Laravel 12, PHP 8.4
- **Frontend**: React 19, TypeScript, Tailwind CSS, Inertia.js
- **Testing**: PestPHP
- **Code Style**: Laravel Pint (PHP), ESLint + Prettier (JS/TS)

## CI/CD Pipeline

Pipeline otomatis berjalan setiap `push` dan `pull_request` ke branch `master` dan `develop`.

| Job | Fungsi |
|-----|--------|
| Code Style Check | Validasi standar kode PHP dengan Laravel Pint |
| Frontend Lint & Type Check | ESLint, TypeScript check, Prettier |
| Unit & Feature Tests | Jalankan semua test dengan PestPHP |
| Build Frontend | Build asset Vite, upload artifact |
| Security Audit | `composer audit` + `npm audit` |
| Merge Gate | Blokir merge ke `master` jika ada job yang gagal |

## Alur Kerja Tim

```
master          ← production, hanya dari develop via PR
develop         ← integrasi semua fitur
feature/xxx     ← branch per fitur per anggota
```

1. Buat branch dari `develop`: `git checkout -b feature/nama-fitur`
2. Kerjakan fitur, commit, push
3. Buat Pull Request ke `develop`
4. Tunggu pipeline ✅ hijau semua
5. Merge ke `develop`

## Setup Lokal

```bash
composer install
cp .env.example .env
php artisan key:generate
php artisan migrate
npm install
npm run dev
```

## Menjalankan Test

```bash
./vendor/bin/pest
```

## Code Style

```bash
# Fix otomatis
./vendor/bin/pint

# Hanya cek (tidak ubah file)
./vendor/bin/pint --test
```
