# Buku Tugas Akhir ITS

![GitHub last commit](https://img.shields.io/github/last-commit/lyfesan/buku-tugas-akhir)
[![repo size](https://img.shields.io/github/repo-size/lyfesan/buku-tugas-akhir)](https://github.com/lyfesan/buku-tugas-akhir)
[![license](https://img.shields.io/github/license/lyfesan/buku-tugas-akhir)](./LICENSE)
[![build status](https://img.shields.io/github/actions/workflow/status/lyfesan/buku-tugas-akhir/ci.yaml?branch=main)](https://github.com/lyfesan/buku-tugas-akhir/actions/workflows/ci.yaml)

Repositori ini berisi dokumen [LaTeX](https://www.latex-project.org/) dari buku tugas akhir yang disesuaikan dengan format yang diberlakukan oleh [Institut Teknologi Sepuluh Nopember](https://www.its.ac.id/) (ITS). Meskipun disusun berdasarkan [SK Rektor ITS No. 280 Tahun 2022](https://www.its.ac.id/pendidikan/wp-content/uploads/sites/112/2022/03/280-SK-Rektor-ttg-Pedoman-Penyusunan-Laporan-Tugas-Akhir-Sarjana-Sarjana-Terapan.pdf), buku tugas akhir ini secara spesifik disesuaikan untuk kebutuhan **Departemen Teknik Informatika**. Penggunaan untuk departemen lain mungkin memerlukan penyesuaian lebih lanjut.


## Fitur

Template ini dirancang untuk memudahkan pengaturan format dalam menyusun Tugas Akhir dengan fitur-fitur berikut:

*   **Format Standar ITS**: Format halaman (A4), margin, font (Times New Roman), dan spasi sudah disesuaikan dengan SK Rektor ITS No. 280 Tahun 2022.
*   **Struktur Modular**: Dokumen dipecah menjadi beberapa file (bab terpisah) untuk memudahkan pengelolaan konten.
*   **Otomatisasi**:
    *   Pembuatan Daftar Isi, Daftar Gambar, dan Daftar Tabel otomatis.
    *   Pembuatan Daftar Pustaka otomatis menggunakan `biblatex` (backend `biber`).
    *   Penomoran bab, sub-bab, gambar, tabel, dan persamaan otomatis.
*   **Package LaTeX Pendukung**:
    *   Dukungan rumus matematika (`amsmath` via `mathtools` dll, standard LaTeX math environment didukung).
    *   Tabel (`nicematrix`, `xltabular`, `longtable`).
    *   Kode program (`listings` dengan pewarnaan syntax).
    *   Gambar (`graphicx`, `float`, `wrapfig`)

## Prasyarat

Untuk menggunakan template ini secara lokal, disarankan menggunakan:

*   **Distribusi LaTeX**: [TeX Live](https://www.tug.org/texlive/) (Windows, Linux, macOS).
    *   Pastikan memilih instalasi **full** agar semua paket tersedia.
*   **Editor (IDE)**: [TeXstudio](https://www.texstudio.org/).
    *   Editor LaTeX yang lengkap dan mudah digunakan.

Pastikan instalasi mendukung **XeLaTeX** dan **Biber**.

> **CATATAN:** Template ini menggunakan **XeLaTeX** untuk mengakses font sistem secara langsung. Hal ini diperlukan agar dokumen dapat menggunakan font **Times New Roman** yang terinstal di sistem operasi, sesuai dengan standar ITS.

**Catatan untuk Pengguna Linux dan macOS:**
Pastikan font **Times New Roman** sudah terinstall di sistem.
*   **Linux**: Install paket `ttf-mscorefonts-installer` (Debian/Ubuntu) atau salin font dari Windows.
*   **macOS**: Font ini biasanya sudah tersedia, namun jika bermasalah, pastikan font bawaan aktif atau install ulang.

Alternatif lain yang dapat digunakan:
*   Distribusi: [MiKTeX](https://miktex.org/).
*   Editor: [Visual Studio Code](https://code.visualstudio.com/) (dengan ekstensi LaTeX) atau [Overleaf](https://www.overleaf.com/) (Online).

## Cara Penggunaan

### Struktur Folder dan File

Berikut adalah penjelasan fungsi dari setiap folder dan file untuk mempermudah pencarian bagian yang perlu diedit:

*   **`main.tex`**: File utama (root) yang menggabungkan seluruh dokumen.
*   **`abstrak/`**: Edit file di sini untuk mengubah isi abstrak.
    *   `abstrak-id.tex`: Abstrak Bahasa Indonesia.
    *   `abstrak-en.tex`: Abstrak Bahasa Inggris.
*   **`bab/`**: Folder utama tempat menulis materi skripsi/tesis.
    *   `1-pendahuluan.tex`: Latar belakang, rumusan masalah, tujuan.
    *   `2-tinjauan-pustaka.tex`: Penelitian terdahulu serta dasar teori.
    *   `3-desain-implementasi.tex`: Metodologi dan perancangan.
    *   `4-pengujian-analisis.tex`: Hasil dan pembahasan.
    *   `5-penutup.tex`: Kesimpulan dan saran.
*   **`pustaka/`**: Pengaturan referensi dan data diri.
    *   `variables.tex`: Isi judul, nama, NRP, dosen pembimbing, dll di sini.
    *   `pustaka.bib`: Database daftar pustaka (format BibTeX).
*   **`lainnya/`**: Halaman pelengkap.
    *   `lembar-pengesahan.tex`: Lembar pengesahan.
    *   `kata-pengantar.tex`: Kata pengantar.
    *   `biografi-penulis.tex`: Biografi singkat penulis.
    *   `pernyataan-keaslian.tex`: Pernyataan orisinalitas karya.
    *   `pernyataan-ai-generatif.tex`: Pernyataan kode etik penggunaan AI generatif (diwajibkan untuk departemen teknik informatika).
*   **`sampul/`**: Desain halaman sampul depan.
*   **`gambar/`**: Letakkan semua file gambar (JPG, PNG, SVG, dll) yang digunakan di laporan di sini.
*   **`program/`**: Jika ingin melampirkan file kode program terpisah.

### Kompilasi (Build)
Karena template ini menggunakan `fontspec` (untuk Times New Roman) dan `biblatex` dengan backend `biber`, urutan kompilasi yang benar adalah:

1.  `xelatex` (Kompilasi awal untuk generate file auxiliary)
2.  `biber` (Memproses daftar pustaka dari file .bcf)
3.  `xelatex` (Memasukkan daftar pustaka ke dokumen)
4.  `xelatex` (Finalisasi referensi silang dan nomor halaman)

**Command Line:**
Jalankan perintah berikut di terminal (pastikan berada di direktori root project):

```bash
xelatex main
biber main
xelatex main
xelatex main
```

Atau jika menggunakan `latexmk` (otomatis):
```bash
latexmk -xelatex main
```

## Snippets dan Contoh Kode

Berikut adalah contoh-contoh kode LaTeX yang sering digunakan dalam template ini.

### 1. Mengisi Data Diri
Buka file `pustaka/variables.tex` dan sesuaikan isinya:

```tex
% Judul dalam Bahasa Indonesia
\newcommand{\tatitle}{Judul Tugas Akhir}
% Nama Penulis
\newcommand{\taauthor}{Nama Lengkap}
% Nomor NRP
\newcommand{\tanrp}{123456789}
```

### 2. Sitasi dan Daftar Pustaka
Pastikan entri referensi sudah ada di file `pustaka/pustaka.bib`.
Contoh entri bibtex:
```bibtex
@article{einstein,
  author = {Albert Einstein},
  title = {Zur Elektrodynamik bewegter Körper},
  journaltitle = {Annalen der Physik},
  year = {1905},
}
```

Cara melakukan sitasi di dalam teks (edit file di folder `bab/`):
```tex
Menurut Einstein \parencite{einstein}, ...  % Output: (Einstein, 1905)
Einstein \textcite{einstein} menyatakan ... % Output: Einstein (1905)
```

### 3. Memasukkan Gambar
Simpan gambar di folder `gambar/`, lalu gunakan kode berikut:

```tex
\begin{figure}[H]
  \centering
  % Ganti 'nama-file.jpg' dengan nama file gambar yang diinginkan
  % scale=0.8 berarti ukuran gambar 80% dari aslinya
  \includegraphics[scale=0.8]{gambar/nama-file.jpg}
  \caption{Keterangan Gambar}
  \label{fig:label-gambar-ini}
\end{figure}

Seperti terlihat pada Gambar \ref{fig:label-gambar-ini} ...
```

### 4. Membuat Tabel
Anda bisa menggunakan `table` biasa atau `nicematrix` untuk tabel yang lebih kompleks.

**Tabel Sederhana:**
```tex
\begin{table}[H]
  \centering
  \caption{Contoh Tabel Sederhana}
  \label{tab:contoh-tabel}
  \begin{tabular}{|c|l|r|} % c=center, l=left, r=right
    \hline
    \textbf{No} & \textbf{Item} & \textbf{Harga} \\ \hline
    1 & Buku Tulis & Rp 5.000 \\ \hline
    2 & Pensil     & Rp 2.000 \\ \hline
  \end{tabular}
\end{table}
```

**Tabel Bersambung (xltabular):**
Gunakan `xltabular` jika tabel sangat panjang dan butuh memotong halaman secara otomatis.

```tex
% Parameter pertama {c} adalah alignment untuk caption (c=center)
% Parameter kedua {l|X} adalah kolom: l=left (lebar pas konten), X=expand (memenuhi sisa lebar tabel)
\begin{xltabular}{\linewidth}{l|X}
  \caption{Contoh Tabel Panjang} \label{tab:panjang} \\
  \hline \textbf{No} & \textbf{Deskripsi Panjang} \\ \hline
  \endfirsthead
  
  \caption*{Lanjutan Tabel \ref{tab:panjang}} \\
  \hline \textbf{No} & \textbf{Deskripsi Panjang} \\ \hline
  \endhead
  
  \hline
  \endfoot

  1 & Ini adalah kolom yang akan otomatis turun baris jika teksnya terlalu panjang melebihi batas margin halaman. \\ \hline
  2 & Baris kedua juga demikian... \\ \hline
\end{xltabular}
```

### 5. Menulis Persamaan Matematika
```tex
\begin{equation}
  \label{eq:rumus-pythagoras}
  a^2 + b^2 = c^2
\end{equation}

Persamaan \ref{eq:rumus-pythagoras} menunjukkan teorema Pythagoras.
```

### 6. Menambahkan Kode Program
Gunakan environment `lstlisting`:

```tex
\begin{lstlisting}[language=Python, caption={Contoh Kode Python}, label={lst:python-code}]
def hello_world():
    print("Hello, ITS!")
\end{lstlisting}
```

## Lisensi

Kode sumber yang ada pada repositori ini dilisensikan di bawah [lisensi MIT](./LICENSE).
