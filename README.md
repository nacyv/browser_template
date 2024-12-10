# Browser Template

Browser Template adalah proyek template untuk membuat aplikasi browser Android sederhana. Template ini dirancang agar mudah digunakan, dimodifikasi, dan dapat digunakan kembali (reusable) untuk mengembangkan aplikasi browser sesuai kebutuhan.

---
## Fitur

- WebView yang mendukung pengaturan tingkat lanjut (JavaScript, DOM Storage, File Access).

- Progress Bar untuk menampilkan status loading halaman web.

- Input URL yang responsif dengan dukungan pengisian otomatis.

Mudah dimodifikasi dengan struktur kode yang bersih dan terorganisir.

---
## Persyaratan Sistem

Android: Versi minimal 5.0 (Lollipop).

IDE: Android Studio.

Bahasa Pemrograman: Java.

---
## Cara Menggunakan

1. Clone repository ini ke perangkat Anda:

```bash
git clone https://github.com/nacyv/browser_template.git
```

2. Buka proyek ini di Android Studio.

3. Lakukan sinkronisasi dependensi (sync Gradle).

4. Jalankan aplikasi di perangkat atau emulator Anda.


---
## Struktur Proyek

MainActivity.java: Logika utama aplikasi browser.

res/layout: Layout aplikasi yang terdiri dari WebView, ProgressBar, dan elemen UI lainnya.

res/values: Berisi tema, warna, dan string yang dapat disesuaikan.

AndroidManifest.xml: File konfigurasi utama untuk aplikasi Android.

---
## Fungsi Utama

### WebView

   Menggunakan WebViewClient untuk menangani loading halaman web.
   Mendukung fitur JavaScript, DOM Storage, dan zoom.
   Proses loading halaman ditampilkan melalui ProgressBar.


### Input URL

   Mendukung input URL dengan fitur pencarian otomatis.
   Dapat digunakan untuk menavigasi ke halaman web baru.


### Pengelolaan Memori

   Mengimplementasikan pengelolaan memori yang baik untuk mencegah memory leak pada WebView.
   WebView dihancurkan sepenuhnya di lifecycle onDestroy().

---
## Contoh Kode

### Menjalankan WebView

```java
webview.loadUrl("https://www.google.com");
```

### Mengatur Progress Bar

```java
webview.setWebChromeClient(new WebChromeClient() {
    @Override
    public void onProgressChanged(WebView view, int newProgress) {
        progressbar.setProgress(newProgress);
    }
});
```

### Mengatasi Memory Leak

```java
@Override
protected void onDestroy() {
    if (webview != null) {
        webview.stopLoading();
        webview.loadUrl("about:blank");
        webview.setWebViewClient(null);
        webview.setWebChromeClient(null);
        webview.removeAllViews();
        webview.destroy();
    }
    super.onDestroy();
}
```

---
## Kontribusi

   Kontribusi untuk memperbaiki atau menambahkan fitur baru sangat diterima! Silakan buat pull request atau laporkan masalah di bagian Issues.

---
## Lisensi

   Proyek ini dilisensikan di bawah lisensi MIT. Lihat file LICENSE untuk informasi lebih lanjut.
