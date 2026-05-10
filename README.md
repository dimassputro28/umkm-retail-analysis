# Dataset: Transaksi Retail UMKM Indonesia
**Proyek 1B — Portofolio Data Analyst**

## Konteks Bisnis
Dataset ini merepresentasikan jaringan UMKM retail multi-kategori yang beroperasi
di 10 kota besar Indonesia selama periode Januari 2023 – Desember 2024.

## File Structure
| File | Rows | Keterangan |
|------|------|------------|
| `transactions_raw.csv` | 5,610 | Data mentah **dengan dirty data** — gunakan ini untuk analisis |
| `transactions_clean_reference.csv` | 5,500 | Referensi data bersih (jangan dibuka sebelum selesai cleaning) |
| `products.csv` | 56 | Katalog produk per kategori |
| `customers.csv` | 1,000 | Profil pelanggan |
| `stores.csv` | 50 | Data toko UMKM per kota |

## Kolom Utama (transactions_raw.csv)
| Kolom | Tipe | Keterangan |
|-------|------|------------|
| order_id | string | ID unik transaksi |
| order_date | string | Tanggal order (ada 4 format berbeda — dirty!) |
| customer_id | string | FK ke customers.csv |
| store_id | string | FK ke stores.csv |
| product_id | string | FK ke products.csv |
| category | string | Kategori produk (ada inkonsistensi casing — dirty!) |
| qty | int | Kuantitas (ada nilai negatif — dirty!) |
| unit_price | float | Harga satuan (ada outlier 10x — dirty!) |
| discount_pct | float | Persentase diskon (ada missing value — dirty!) |
| total_price | float | Total setelah diskon |
| payment_method | string | 12 metode pembayaran lokal (ada missing & casing issues) |
| order_status | string | delivered / cancelled / returned / processing |
| city | string | Kota toko (ada missing value — dirty!) |

## Kategori Produk (8 kategori)
- Fashion & Pakaian
- Makanan & Minuman
- Kecantikan & Perawatan
- Elektronik & Aksesori
- Rumah Tangga
- Perlengkapan Bayi & Anak
- Olahraga & Outdoor
- Kerajinan & Souvenir

## Metode Pembayaran Lokal (12)
GoPay, OVO, Dana, ShopeePay, LinkAja, Transfer BCA, Transfer BRI,
Transfer Mandiri, COD, QRIS, Indomaret, Alfamart

## Dirty Data yang Diinjeksi (untuk latihan cleaning)
| Tipe | Kolom | Estimasi |
|------|-------|----------|
| Missing values | payment_method, discount_pct, city | ~2-5% |
| Duplicate rows | — | ~2% (110 rows) |
| Format tanggal tidak konsisten | order_date | ~3% |
| Inkonsistensi casing | category, payment_method | ~2% |
| Outlier harga | unit_price | ~1% (10x lipat) |
| Nilai qty negatif | qty | ~0.5% |

## Pertanyaan Bisnis (Problem Statement)
1. Kategori produk mana yang paling berkontribusi terhadap revenue dan bagaimana trennya per kuartal?
2. Metode pembayaran digital mana yang paling dominan dan adakah perbedaan preferensi antar kota?
3. Toko mana yang memiliki performa terbaik dan apa karakteristiknya?
4. Bagaimana pola diskon mempengaruhi volume transaksi?
5. Berapa tingkat cancellation & return per kategori dan apa implikasinya?
