## Baozi Downloader V3

Baozi Downloader V3 adalah web tool berbasis HTML + JavaScript untuk mengambil gambar dari chapter terbaru baozimh, lalu mengunduhnya dalam bentuk ZIP.

## Fitur utama:

- Mengambil semua gambar dari halaman chapter
- Auto deteksi dan crop banner (atas / bawah)
- Download semua gambar dalam 1 file ZIP
- Fallback mode (upload HTML jika fetch gagal)



## Cara Menggunakan

1. Buka file "index.html"
2. Masukkan URL chapter: `https://www.twmanga.com/...`
3. Klik Fetch Links
4. Setelah link muncul, klik Download Process
5. File ZIP akan otomatis terunduh
 > Bisa juga diupload ke pihak ketiga seperti `Netlify`


## Konfigurasi Proxy (WAJIB)

  Di dalam file "index.html", terdapat 2 bagian berikut:

   `"YOUR_PROXY1" dan "YOUR_PROXY2"`
    Ganti "YOUR_PROXY1" dan "YOUR_PROXY2" dengan URL proxy milikmu.

## Requirement Proxy

Proxy yang digunakan HARUS menambahkan header berikut saat request:

   - `referer`
   - `app-id`
   - `device-code`
   - `device-id`
   - `user-agent`
   - `app-version`

 # Contoh Format Proxy

   Endpoint proxy harus bisa menerima parameter:

     `https://your-proxy.com/?url=https://target-url`

   Contoh penggunaan dalam kode:

     const proxyUrl = `${PROXY}?url=${encodeURIComponent(url)}`;


# Catatan Penting

- Tanpa proxy yang sesuai, request akan gagal (403 / blocked)
- Beberapa chapter mungkin membutuhkan fallback (upload HTML)
- Banner detection menggunakan metode hash, tidak 100% akurat tapi cukup efektif
- Kecepatan download tergantung proxy yang digunakan


Fallback Mode

Jika gagal fetch:

1. Buka halaman chapter di browser
2. Tekan Ctrl + S (Save as HTML)
3. Upload file tersebut ke tool
4. Sistem akan mengekstrak link gambar dari file HTML


# Teknologi

- Vanilla JavaScript
- JSZip (untuk ZIP download)
- Canvas API (untuk crop & hash)
- HTML5 + CSS3
