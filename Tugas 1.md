<span style="font-family: 'CMU Serif', monospace; font-size: 18px; color: black;">

<div style="text-align: center;">

---

# Mathematical Software

ARIIQ NABILA
25030630033
MATEMATIKA E

---

## Daftar Isi

[TOC]

<div style="text-align: justify;">

---

## 1. Klasifikasi Software Matematika

Software matematika umumnya dibagi berdasarkan wilayah operasinya: analitik (simbolik), numerik, atau data.

| Kategori | Deskripsi & Kegunaan | Contoh Software |
| :--- | :--- | :--- |
| **Computer Algebra Systems (CAS)** | Memanipulasi variabel secara analitik tanpa pembulatan. Sangat esensial untuk kalkulus, aljabar abstrak, dan teori bilangan. | Mathematica, Maple, SymPy |
| **Komputasi Numerik** | Berbasis aritmatika *floating-point* untuk operasi matriks berskala masif, pemodelan sistem dinamis, dan kalkulasi algoritmik. | MATLAB, SciPy, Julia |
| **Komputasi Statistik** | Fokus pada probabilitas, uji hipotesis, dan manipulasi *dataframe* deret waktu. | R, Pandas/Statsmodels (Python) |
| **Automated Theorem Provers** | Memverifikasi kebenaran logika formal secara ketat. Digunakan untuk membuktikan lema dan teorema tingkat lanjut. | Lean, Coq |
| **Mathematical Typesetting** | Sistem *markup* untuk merender dokumen berstandar akademik dan persamaan kompleks (mis. integral Riemann atau matriks stokastik). | LaTeX, MathJax |

---

## 2. Sejarah Perkembangan Software Matematika

Evolusi Software matematika berjalan beriringan dengan perkembangan arsitektur komputasi, bergerak dari sekadar kalkulator numerik besar menjadi asisten pembuktian logis yang canggih.

*   **Era 1960–1970an (Fondasi Komputasi & CAS Pertama):** Bahasa pemrograman tingkat tinggi seperti FORTRAN mendominasi kalkulasi numerik untuk proyek sains dan militer. Pada akhir 1960-an, proyek MACSYMA di MIT memelopori *Computer Algebra System* (CAS) pertama yang mampu menyelesaikan ekspresi analitik (seperti integral) secara simbolik, bukan sekadar komputasi angka.
*   **Era 1980an (Kelahiran Raksasa Komersial):** Software mulai digunakan untuk penggunaan industri dan akademik. MATLAB (1984) lahir sebagai antarmuka untuk pustaka matriks aljabar linear (LINPACK). Di ranah komputasi simbolik, Maple (1982) dan Wolfram Mathematica (1988) diluncurkan dan segera merajai pasar dengan mesin komputasi teoretis yang sangat tangguh.
*   **Era 1990an (Demokratisasi Statistika & Standar Publikasi):** LaTeX (terutama rilis LaTeX2e pada 1994) memantapkan posisinya sebagai standar absolut untuk penulisan (*typesetting*) matematika di kalangan akademisi. Di bidang data, bahasa R (1993) diciptakan di Universitas Auckland untuk menyediakan alternatif *open-source* bagi Software statistik komersial.
*   **Era 2000an (Revolusi *Open Source* & Kebangkitan Python):** Rilisnya pustaka NumPy (2006) dan SciPy mengubah Python dari bahasa pemrograman umum menjadi raksasa komputasi ilmiah. Pada periode yang sama, proyek SageMath (2005) mulai menyatukan puluhan alat matematika *open-source* dalam satu antarmuka agar bisa bersaing langsung dengan Software komersial yang mahal.
*   **Era 2010an (Komputasi Interaktif & *Cloud*):** Kehadiran Jupyter Notebook mengubah paradigma kerja matematikawan. Format *notebook* ini memungkinkan integrasi blok kode (Python/R/Julia), persamaan matematis, dan visualisasi grafik interaktif dalam satu dokumen hidup (*live document*).
*   **Era 2020an (Integrasi AI & *Automated Theorem Provers*):** *Large Language Models* (LLM) mulai diintegrasikan untuk membantu menerjemahkan ide matematis abstrak menjadi sintaks kode. Selain itu, Software pembuktian teorema berbasis logika formal seperti **Lean** semakin populer di kalangan matematikawan murni (contohnya dalam proyek *Liquid Tensor Experiment*), berfungsi bukan untuk menghitung, melainkan memvalidasi logika pembuktian.

---

## 3. Analisis Data: Ekosistem Python vs R

Dalam konteks pemodelan regresi (*robust regression* / *outlier handling*) dan visualisasi deret waktu, kedua ekosistem ini memiliki filosofi yang bertolak belakang.

### A. Arsitektur dan Manipulasi Data
*   **R (Tidyverse):** Menggunakan filosofi *Grammar of Data Manipulation* fungsional dengan operator *pipe* (`%>%` atau `|>` ). Manipulasi data dibaca secara sekuensial dan deskriptif.
*   **Python (Pandas):** Berbasis *Object-Oriented Programming* (OOP) yang diwariskan dari NumPy. Pemanggilan metode sering kali bersarang (*chained methods*), sangat tangguh dalam mengeksekusi operasi pada matriks berukuran besar.

### B. Pendekatan Pemodelan
*   **R:** Adalah standar emas akademis untuk **inferensi statistik**. Fungsi bawaan dengan mudah menghasilkan tabel statistik terperinci (uji-t, p-value, interval kepercayaan). Model *robust* untuk menangani *outlier* tertanam kuat pada paket seperti `MASS`.
*   **Python:** Memiliki dua pilar (Statsmodels untuk inferensi dan Scikit-Learn untuk ML). Keunggulan mutlak Python adalah kemampuannya menjembatani regresi statistik klasik dengan arsitektur **Machine Learning** di dalam satu alur kerja yang sama.

### C. Visualisasi Deret Waktu (Time Series)
*   **R (`ggplot2` + `lubridate`):** Sempurna untuk infografis dan visualisasi siap publikasi (*Grammar of Graphics*).
*   **Python (`Matplotlib` + `DatetimeIndex`):** Superior dalam pergeseran waktu (*lagging*), rata-rata bergerak (*rolling mean*), serta pembangunan visualisasi komputasional (seperti *3D surface plot*).

---

## 4. Euler Math Toolbox (EMT)

EMT adalah sistem **hibrida** yang efisien dan unik, dirancang oleh René Grothmann (1988). EMT menjembatani kesenjangan antara komputasi angka murni dan manipulasi rumus.

### Fitur Kunci
1.  **Arsitektur Ganda:** Menggabungkan *engine* numerik mirip MATLAB (ditulis dalam C/C++) dengan *engine* simbolik **Maxima** (CAS klasik yang sangat kuat).
2.  **Aritmatika Interval (*Interval Arithmetic*):** Fitur krusial untuk mencegah kesalahan pembulatan *floating-point*. EMT melacak batas atas dan batas bawah perhitungan untuk memastikan hasil eksak selalu berada di dalam rentang tersebut.
3.  **Buku Kerja Interaktif:** Menyediakan antarmuka berbasis *notebook* tempat kode, plot 3D, dan deskripsi berformat Markdown/LaTeX dapat dijalankan secara bersamaan.
4.  **Keringanan Ekstrem:** Memiliki kompilator C internal (Tiny C) dan integrasi skrip Python asli, semuanya dalam satu paket instalasi kecil tanpa memerlukan dependensi besar.

### Pro dan Kontra EMT
*   **Pro:** Sangat cepat, ukuran kecil, integrasi aljabar dan numerik berjalan mulus, *open-source*.
*   **Kontra:** Hanya dirancang murni untuk Windows (membutuhkan perantara di OS lain), antarmuka grafis (GUI) klasik, dan basis komunitas yang relatif kecil jika dibandingkan dengan raksasa seperti Python atau R.

---

## 5. Software Matematika Berdasarkan Domain Spesifik

Selain analisis data dan CAS umum, komputasi matematis memiliki spesialisasi tinggi yang melayani berbagai cabang keilmuan mutakhir:

### A. Kriptografi & Teori Bilangan (Cryptography)
*   **PARI/GP:** Sistem aljabar komputer yang dirancang khusus untuk komputasi teoretis secara presisi dalam teori bilangan (faktorisasi, fungsi L, kurva eliptik) yang menjadi jantung kriptografi modern.
*   **Magma:** Software komersial raksasa untuk aljabar abstrak, teori Galois, dan kriptografi. Sangat berkuasa dalam memecahkan masalah struktur diskrit.
*   **SageMath:** Ekosistem *open-source* berbasis Python yang memiliki modul kriptografi bawaan sangat komprehensif, mengintegrasikan PARI/GP dan Singular di balik layar.

### B. Asisten Pembuktian (Proof Assistants)
*   **Lean:** Sangat dominan saat ini (terutama Lean 4) untuk memformalkan matematika kompleks. Memiliki pustaka raksasa *mathlib* yang dikembangkan secara gotong royong oleh matematikawan murni.
*   **Coq:** Asisten bukti berbasis Kalkulus Konstruksi Induktif (*Calculus of Inductive Constructions*), historis karena perannya dalam pembuktian Teorema Empat Warna.
*   **Isabelle/HOL:** Banyak digunakan untuk verifikasi sistem kritis (perangkat keras/Software) serta memformalkan cabang-cabang matematika terapan dan analisis.

### C. Geometri Dinamis & Diskrit (Geometry)
*   **GeoGebra:** Standar industri absolut untuk pendidikan dan eksplorasi, menyatukan geometri dinamis, aljabar, kalkulus, dan statistik dalam satu kanvas interaktif.
*   **Polymake:** Spesialis untuk riset dalam geometri diskrit dan polihedral (kombinatorika politop, kompleks simplisial), perpotongan kuat antara aljabar linear dan topologi.
*   **Cinderella:** Selain untuk geometri dinamis, sangat kuat mensimulasikan geometri non-Euclidean (hiperbolik/fraktal) dan fisika mekanik.

### D. Analisis Numerik Lanjut (Numerical Analysis)
*   **FEniCS:** *Platform* komputasi mutakhir untuk memecahkan Persamaan Diferensial Parsial (PDE) menggunakan Finite Element Method (FEM). Inti dari analisis struktur mekanis dan fluida.
*   **Scilab & GNU Octave:** Keduanya adalah saudara kandung *open-source* dari MATLAB, sangat mumpuni untuk simulasi numerik murni, pemrosesan sinyal, dan sintesis sistem kontrol.
*   **Julia:** Meskipun berupa bahasa pemrograman, ini adalah standar modern bagi penganalisis numerik. Menawarkan eksekusi JIT (*Just-In-Time*) secepat C/Fortran namun dengan sintaks level-tinggi seperti Python.

### E. Matematika Musik & Audio (Musical Computing)
*   **OpenMusic:** Bahasa pemrograman visual berbasis LISP untuk komposisi berbantuan komputer. Komposer dapat merancang kurva matematis yang mendikte struktur harmonik atau ritme algoritmis.
*   **SuperCollider & Sonic Pi:** *Live-coding* lingkungan komputasi audio di mana algoritma dan persamaan matematika digunakan secara langsung untuk mensintesis gelombang suara kompleks dan tekstur musik.

### F. Fisika Matematis (Physics)
*   **COMSOL Multiphysics:** Pemodelan elemen hingga industri untuk memecahkan masalah fisika tergandeng (misal: merangkai simulasi termal, elektromagnetik, dan mekanik sekaligus).
*   **Geant4:** Pustaka C++ buatan CERN yang menggunakan metode *Monte Carlo* untuk mensimulasikan lintasan partikel melintasi materi (fisika nuklir dan radiasi ruang angkasa).
*   **FeynCalc (Mathematica Add-on):** Alat komputasi khusus untuk mengevaluasi secara analitik diagram Feynman dan kinematika dalam fisika partikel teoretis.

### G. Biomatematika & Sistem Dinamis (Biomathematics)
*   **XPPAUT:** *Software* andalan untuk mensimulasikan, menganalisis stabilitas, dan memvisualisasikan sistem persamaan diferensial. Sangat esensial dalam neurosains komputasional (mis. model neuron Hodgkin-Huxley).
*   **COPASI:** Software khusus untuk memodelkan dan mengkalibrasi dinamika jaringan biokimia serta kinetika enzim biologis menggunakan pendekatan persamaan stokastik maupun deterministik.

### H. Kimia Matematis & Komputasional (Mathematical Chemistry)
*   **Gaussian:** Alat komputasi raksasa untuk memecahkan persamaan Schrödinger secara numerik (kimia kuantum) demi memprediksi struktur geometri dan tingkat energi molekul.
*   **GROMACS:** Mesin super efisien untuk simulasi dinamika molekuler, merender ribuan persamaan gerak mekanika klasik Newtonian untuk sistem biomolekuler (protein, lipid).

### I. Ekonomi Matematis & Ekonometrika (Mathematical Economics)
*   **Dynare:** Paket ekstensi MATLAB/Octave yang mendominasi riset makroekonomi untuk mensimulasikan model *Dynamic Stochastic General Equilibrium* (DSGE).
*   **GAMS (General Algebraic Modeling System):** Sistem pemodelan tinggi khusus untuk optimasi matematis diskrit/kontinu dan teori permainan ekuilibrium dalam riset ekonomi/operasional.
*   **Stata & EViews:** Industri ekonometrika terapan berfokus kuat di sini. Sangat kuat untuk analisis panel data, deret waktu ekonomi (*cointegration*, ARCH/GARCH), dan pemodelan kausalitas preskriptif.

---

Dokumen ini disusun dengan bantuan Gemini AI dengan _prompt_ sebagai berikut.

1. Carikan berbagai mathematical software, klasifikasinya, kegunaannya, perbandingan pro-kontranya, sejarah perkembangannya, kemutakhirannya, kompleksitasnya, dan sebagainya secara komprehensif beserta tabel dan lain-lain.
2. Bagaimana fitur, kelebihan, dan kekurangan Euler Math Toolbox?
3. Bagaimana sejarah perkembangan software matematika? (tidak harus spesifik, tetapi komprehensif)
4. Selain untuk analisis data, coba carikan mathematical software yang berfungsi di ranah cryptography, proof assistants, geometry, numerical analysis, musical, physics, biomathematics, mathematical chemistry, dan mathematical economics.

---

</div>
</div>
</span><span style="font-family: 'CMU Serif', monospace; font-size: 20px; color: black;">