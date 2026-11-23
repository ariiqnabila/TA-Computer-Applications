# EMT untuk Komputasi Aljabar
Selamat datang di notebook EMT (Euler Math Toolbox) untuk Komputasi Aljabar! Melalui notebook ini,
Anda akan mempelajari cara menggunakan EMT untuk memecahkan berbagai persoalan aljabar.


Agar pembelajaran lebih optimal, ikuti langkah-langkah berikut: - Bacalah setiap penjelasan pada
notebook ini dengan saksama. - Praktikkan langsung contoh-contoh perintah yang ada dengan menekan
tombol ENTER pada setiap baris perintah (arahkan kursor ke baris terkait). - Jangan ragu untuk
memodifikasi perintah yang ada; amati perbedaannya dan tambahkan catatan Anda sendiri. - Sisipkan
baris baru untuk berlatih mengerjakan soal dari dokumen eksternal, lalu beri catatan pada hasilnya. -
Biasakan menyertakan teks soal sebelum penyelesaian (menggunakan format LaTeX). - Gunakan format
LaTeX untuk menampilkan hasil perhitungan eksak atau simbolik agar lebih rapi dan profesional[cite:
5].


## Contoh Dasar Penggunaan EMT

Berikut adalah contoh penyederhanaan bentuk aljabar:


$$6x^{-3}y^5\times -7x^2y^{-9}$$\>$&6\*x^(-3)\*y^5\*-7\*x^2\*y^(-9)


$$-\frac{42}{x\,y^4}$$Dan ini adalah contoh penjabaran (ekspansi) aljabar:


$$(6x^{-3}+y^5)(-7x^2-y^{-9})$$\>$&showev('expand((6\*x^(-3)+y^5)\*(-7\*x^2-y^(-9))))


$${\it expand}\left(\left(-7\,x^2-\frac{1}{y^9}\right)\,\left(\frac{6  }{x^3}+y^5\right)\right)=-\frac{42}{x}-\frac{6}{x^3\,y^9}-\frac{1}{y  ^4}-7\,x^2\,y^5$$## Baris Perintah (The Command Line)

Baris perintah (command line) pada EMT dapat memuat satu atau lebih instruksi. Anda dapat memisahkan
beberapa perintah dengan tanda koma "," atau titik koma ";". Penggunaan titik koma (;) di akhir
perintah akan mengeksekusi perhitungan tanpa mencetak hasilnya di layar, sedangkan tanda koma boleh
diabaikan pada perintah terakhir.


Contoh berikut akan melakukan perhitungan matematika dan mencetak hasilnya, sekaligus menunjukkan
cara mendefinisikan variabel:


\>r:=2; h:=4; pi\*r^2\*h/3


          16.76 

Perintah dalam satu baris harus dipisahkan oleh spasi. Pada contoh di bawah ini, EMT akan mencetak
kedua hasil secara berurutan.


\>pi\*2\*r\*h, %+2\*pi\*r\*h // Ingat tanda % menyatakan hasil perhitungan terakhir sebelumnya


          50.27 
         100.53 

Eksekusi baris perintah bergantung pada urutan Anda menekan tombol ENTER. Oleh karena itu, variabel
akan diperbarui setiap kali Anda mengeksekusi baris yang mendefinisikannya ulang.


\>x := 1;

\>x := cos(x) // nilai cosinus (x dalam radian)


           0.54 

\>x := cos(x)


           0.86 

Untuk menyambung perintah ke baris berikutnya, gunakan tanda "..." (tiga titik). Baris-baris yang
tersambung ini akan selalu dieksekusi bersamaan.


\>x := 1.5; ...  
\>   x := (x+2/x)/2, x := (x+2/x)/2, x := (x+2/x)/2, 


           1.42 
           1.41 
           1.41 

Fitur "..." ini sangat berguna untuk merapikan perintah yang panjang. Tips: Tekan Ctrl+Return untuk
memecah baris pada posisi kursor, atau Ctrl+Backspace untuk menggabungkan baris kembali.


Untuk menyembunyikan (fold) perintah multi-baris, tekan Ctrl+L. Baris berikutnya hanya akan terlihat
jika Anda menaruh fokus pada blok tersebut. Anda juga dapat menyembunyikan satu blok multi-baris
dengan mengawali baris pertamanya menggunakan "%+ ".


\>%+ x=4+5; ...  
\>    // Baris ini tidak akan terlihat setelah kursor keluar dari baris ini


Jika baris diawali dengan tanda %%, baris tersebut akan sepenuhnya disembunyikan.


          81.00 

EMT juga mendukung fitur perulangan (loops) secara langsung di baris perintah, asalkan dapat ditulis
dalam satu kesatuan baris atau multi-baris.


\>x=1; for i=1 to 5; x := (x+2/x)/2, end; // menghitung akar 2


           1.50 
           1.42 
           1.41 
           1.41 
           1.41 

Penulisan perulangan dalam bentuk multi-baris sangat disarankan untuk keterbacaan, asalkan diakhiri
dengan " ...".


\>x := 1.5; // komentar ditulis di sini sebelum ...  
\>   repeat xnew:=(x+2/x)/2; until xnew~=x; ...  
\>      x := xnew; ...  
\>   end; ...  
\>   x,


           1.41 

Pengkondisian logika (if-then) juga dapat diterapkan.


\>if E^pi\>pi^E; then "Tentu saja!", endif;


    Tentu saja!

Saat mengeksekusi perhitungan, posisi kursor dapat berada di mana saja pada baris tersebut. Gunakan
tombol panah atas/bawah untuk berpindah antar baris perintah secara cepat.


EMT memiliki fitur penyorotan (highlighting) otomatis. Saat memindahkan kursor, pasangan tanda kurung
akan ditandai untuk memudahkan pembacaan fungsi bersarang. Perhatikan juga baris status (status line)
di bawah jendela yang menampilkan bantuan argumen untuk fungsi yang sedang diketik.


\>sqrt(sin(10°)/cos(20°))


           0.43 

Gunakan tombol F1 untuk membuka jendela Bantuan (Help). Anda bisa mencari informasi fungsi secara
mendetail di sana. Mengklik ganda (double click) pada sebuah nama perintah di baris perintah akan
otomatis membuka panduan untuk perintah tersebut. Coba klik ganda pada fungsi exp di bawah ini[cite:
5].


\>exp(log(2.5))


           2.50 

Anda juga dapat melakukan Copy (Ctrl-C) dan Paste (Ctrl-V). Blok bagian fungsi atau kurung yang
tersorot menggunakan kursor mouse atau kombinasi tombol Shift + Panah.


## Sintaks Dasar (Basic Syntax)

EMT mengenali fungsi matematika standar. Fungsi trigonometri secara default beroperasi dalam satuan
radian. Untuk menggunakan derajat, tambahkan simbol derajat (tekan F7) atau manfaatkan fungsi rad(x).
Fungsi akar kuadrat menggunakan perintah sqrt() atau bentuk eksponen x^(1/2).


Gunakan ":=" atau "=" untuk mendefinisikan (assign) variabel. Penggunaan ":=" lebih direkomendasikan
demi kejelasan kode. Spasi diabaikan dalam perhitungan, tetapi sangat dianjurkan agar kode lebih
rapi.


\>g:=9.81; t:=2.5; 1/2\*g\*t^2


          30.66 

Karena EMT menggunakan sintaks pemrograman terstruktur, ekspresi kompleks seperti berikut:


$$e^2 \cdot \left( \frac{1}{3+4 \log(0.6)}+\frac{1}{7} \right)$$Harus ditulis dengan penempatan tanda kurung yang akurat dan tanda "/" untuk pembagian. Ingat bahwa
konstanta bilangan natural (Euler) direpresentasikan dengan huruf E kapital.


\>E^2\*(1/(3+4\*log(0.6))+1/7)


           8.78 

Evaluasi pecahan bersusun seperti:


$$\left(\frac{\frac17 + \frac18 + 2}{\frac13 + \frac12}\right)^2 \pi$$Juga memerlukan pembungkusan tanda kurung yang tepat. Konstanta pi ditulis secara eksplisit sebagai
"pi".


\>((1/7 + 1/8 + 2) / (1/3 + 1/2))^2 \* pi


          23.27 

Hasil perhitungan numerik di EMT ditampilkan dalam tipe data floating point (titik mengambang) dengan
akurasi 12 digit secara default. Anda dapat menggunakan tanda % untuk memanggil hasil perhitungan
terakhir, dan menambahkan fungsi khusus untuk mengubah tampilannya (misalnya ke bentuk pecahan).


\>1/3+1/7, fraction %


           0.48 
    10/21

Saat menulis ekspresi yang memuat banyak fungsi dan operator, jangan ragu untuk menggunakan tanda
kurung tambahan jika Anda ragu mengenai preseden operator (urutan prioritas operasi matematika). EMT
akan memandu Anda melalui sorotan kurung saat mengetik.


\>(cos(pi/4)+1)^3\*(sin(pi/4)+1)^2


          14.50 

Beberapa operator matematika yang didukung EMT antara lain:


 +, - (Penjumlahan dan pengurangan)  
 *, / (Perkalian dan pembagian)  
 . (Perkalian matriks / dot product)  
 ^ atau ** (Perpangkatan)  
 ! (Faktorial)  

Daftar fungsi matematika standar:  sin, cos, tan, atan, asin, acos, rad, deg


 log (berlaku sebagai ln), exp, log10, sqrt, logbase


 bin, logbin, logfac, mod, floor, ceil, round, abs, sign


 conj, re, im, arg, real, complex


 beta, betai, gamma, complexgamma, dll.


\>ln(E^2), arctan(tan(0.5))


           2.00 
           0.50 

\>sin(30°)


           0.50 

Pemahaman hierarki eksekusi sangat penting. EMT memproses pangkat beruntun seperti 2^3^4 secara unik.
Pastikan Anda mengapitnya dengan tanda kurung agar kalkulasinya sesuai dengan yang Anda inginkan
(contoh: (2^3)^4 sangat berbeda dengan 2^(3^4)).


\>2^3^4, (2^3)^4, 2^(3^4)


    2417851639229258349412352.00 
        4096.00 
    2417851639229258349412352.00 

## Bilangan Real (Real Numbers)

Basis data utama EMT adalah bilangan real dengan akurasi 16 digit desimal, format standar IEEE.


\>longest 1/3


         0.3333333333333333 

Bilangan disimpan menggunakan 8 byte memori.


\>printdual(1/3)


    1.0101010101010101010101010101010101010101010101010101*2^-2

\>printhex(1/3)


    5.5555555555554*16^-1

## String (Teks)

Deklarasi teks (string) selalu diawali dan diakhiri dengan tanda kutip dua "...".


\>"Sebuah string bisa berisi apa saja."


    Sebuah string bisa berisi apa saja.

Gunakan operator "+" atau "|" untuk menggabungkan string. Angka akan otomatis dikonversi menjadi teks
saat disambungkan dengan string.


\>"Luas lingkaran dengan jari-jari " + 2 + " cm adalah " + pi\*4 + " cm^2."


    Luas lingkaran dengan jari-jari 2 cm adalah 12.5663706144 cm^2.

Fungsi print() menawarkan kontrol tampilan ekstra, termasuk pembatasan digit desimal dan jarak antar
angka (padding).


\>"Rasio Emas (Golden Ratio) : " + print((1+sqrt(5))/2,5,0)


    Rasio Emas (Golden Ratio) : 1.61803

Output fungsi dapat disembunyikan dari layar melalui indikator khusus "none" (berguna dalam rutinitas
pemrograman).


\>none


Evaluasi dapat dilakukan secara langsung dengan merujuk ekspresi teks, yang akan mengonversi teks
numerik menjadi bilangan real yang dapat dikalkulasi.


\>"1234.5"()


        1234.50 

Gunakan tanda kurung siku [...] untuk membuat array (vektor) kumpulan teks.


\>v:=["affe","charlie","bravo"]


    affe
    charlie
    bravo

Vektor string juga dapat disatukan layaknya teks biasa menggunakan operator |.


\>w:=[none]; w|v|v


    affe
    charlie
    bravo
    affe
    charlie
    bravo

EMT mendukung format teks UTF-8 Unicode, yang dipanggil menggunakan awalan u"..." dikombinasikan
dengan kode entitas HTML standar.


\>u"&alpha; = " + 45 + u"&deg;" // pdfLaTeX mungkin gagal menampilkan secara benar


    Î± = 45Â°

I


Entitas HTML juga dapat dituliskan secara langsung dalam baris komentar sebagai alternatif cepat
untuk pencetakan simbol matematika.


Konversi string unicode menjadi angka kode array didukung melalui perintah strtochar(), sementara
perintah chartoutf() mengubah nilai kode array kembali menjadi string Unicode.


\>v=strtochar(u"&Auml; adalah huruf Jerman")


    Real 1 x 21 matrix
    
         196.00       32.00       97.00      100.00       97.00      108.00       97.00     ...

\>v[1]=strtochar(u"&Uuml;")[1]; chartoutf(v)


    Ãœ adalah huruf Jerman

Penerjemahan parameter variabel berisi entitas kode menjadi simbol didukung menggunakan fungsi utf()
atau secara langsung.


\>s="Kita memiliki &alpha;=&beta;."; utf(s) // pdfLaTeX mungkin gagal menampilkan secara benar


    Kita memiliki Î±=Î².

\>u"&#196;hnliches"


    Ã„hnliches

## Nilai Boolean

Representasi logika dasar adalah nilai numerik 1 (benar/true) dan 0 (salah/false). Evaluasi berlaku
baik untuk data bilangan maupun teks string.


\>2<1, "apel"<"pisang"


           0.00 
           1.00 

Mirip dengan sintaks pemrograman keluarga bahasa C, operator logika gabungan mencakup &amp;&amp; (AND) dan ||
(OR).


\>2<E && E<3


           1.00 

Operator ini juga berskala matriks dan memproses array elemen per elemen.


\>(1:10)\>5, nonzeros(%)


    Real 1 x 10 matrix
    
           0.00        0.00        0.00        0.00        0.00        1.00        1.00     ...
           6.00        7.00        8.00        9.00       10.00 

Perintah nonzeros() secara cerdas merujuk elemen matriks berdasarkan nilai logika (bukan berdasarkan
indeks posisi). Pada contoh di bawah, ia memilih rentang anggota array N yang memiliki nilai
isprime(N)=1.


\>N=2|3:2:99 // N berisi elemen 2 dan bilangan2 ganjil dari 3 s.d. 99


    Real 1 x 50 matrix
    
           2.00        3.00        5.00        7.00        9.00       11.00       13.00     ...

\>N[nonzeros(isprime(N))] //pilih anggota2 N yang prima


    Real 1 x 25 matrix
    
           2.00        3.00        5.00        7.00       11.00       13.00       17.00     ...

## Format Output

Format tampilan standar (default format) EMT adalah 12 digit (menggunakan defformat).


\>defformat; pi


    3.14159265359

Format IEEE menyimpan data menggunakan sekitar 16 digit presisi desimal ganda (double precision).
Panggil semua digit kalkulasi ini secara eksplisit menggunakan longestformat atau operator singkat
longest.


\>longest pi


          3.141592653589793 

\>printhex(pi)


    3.243F6A8885A30*16^0

Modifikasi pengaturan jumlah digit menggunakan perintah format().


\>format(12,5); 1/3, pi, sin(1)


        0.33333 
        3.14159 
        0.84147 

\>format(12); 1/3


         0.333333333333 

Untuk penampilan array angka acak, pengaturan singkat seperti shortestformat, shortformat, dan
longformat tersedia.


\>shortestformat; random(3,8)


      0.52   0.51   0.84   0.61   0.37   0.36   0.93   0.85 
      0.76   0.17   0.87   0.98  0.091   0.96   0.39   0.34 
      0.77   0.86   0.84   0.66   0.74   0.95   0.35  0.048 

Skalar secara global diformat pada presisi (12), atau dapat dikustomisasi dengan setscalarformat(x).


\>setscalarformat(5); pi


    3.1416

\>longestformat; pi


    3.141592653589793

Referensi opsi format output EMT meliputi: shortestformat, shortformat, longformat, longestformat,
format(panjang,digit), goodformat(panjang), fracformat(panjang), dan defformat. Akurasi selalu 16
angka di balik layar, perubahan ini murni visualisasi di layar Anda.


\>longestformat; pi,


    3.141592653589793

\>format(10,5); pi


      3.14159 

\>defformat; // default


Terapkan perlakuan format khusus per ekspresi (bukan mengubah opsi umum) dengan menambahkan nama
format sebelum fungsi.


\>longest pi^2/2


          4.934802200544679 

\>fraction 1+1/2+1/3+1/4


    25/12

Karena semua proses floating point EMT dilakukan dalam format biner, pergeseran angka presisi rendah
bisa muncul pada skala hitungan sub-desimal 1e-16 (akibat akumulasi rounding-off error standar IEEE).


\>longest 0.1+0.1+0.1+0.1+0.1+0.1+0.1+0.1+0.1+0.1-1


     -1.110223024625157e-16 

EMT akan mereduksi sisa kecil ini sebagai 0 murni pada format umum demi efisiensi baca.


\>0.1+0.1+0.1+0.1+0.1+0.1+0.1+0.1+0.1+0.1-1


    0

# Ekspresi

Nilai string bisa dialihfungsikan sebagai memori yang menampung rumus perhitungan matematika
(ekspresi). Ekspresi bisa dipanggil dengan operator penutup (), mengikuti fungsi preseden. Sangat
disarankan menamai ekspresi dengan awalan "f", seperti fx atau fxy.


\>r:=2; fx:="pi\*r^2"; longest fx()


          12.56637061435917 

Substitusi sementara nilai pada ekspresi juga bisa dilakukan dengan parameter penugasan, seperti
a=-1.


\>fx:="a\*sin(x)^2"; fx(5,a=-1)


    -0.919535764538

Penting: Sebuah ekspresi selalu mereferensi pada nilai parameter/variabel tingkat global. Ini perlu
dipertimbangkan matang saat memanggil ekspresi berulang-ulang di dalam fungsi tertutup (lokal) guna
menghindari inkonsistensi keluaran komputasi.


\>at:=4; function f(expr,x,at) := expr(x); ...  
\>   f("at\*x^2",3,5) // menghitung 4\*3^2 bukan 5\*3^2


    36

Agar parameter internal digunakan dan menimpa variabel global, pastikan fungsi dipanggil menggunakan
struktur at=nama_parameter.


\>at:=4; function f(expr,x,a) := expr(x,at=a); ...  
\>   f("at\*x^2",3,5)


    45

\>at:=4; function f(expr,x) := expr(x); ...  
\>   f({{"at\*x^2",at=5}},3)


    45

Untuk ekspresi bernilai x, pengaplikasian layaknya sebuah fungsi standar adalah cara paling lazim.


Jangan menggunakan definisi nama yang identik secara berurutan untuk fungsi simbolik global dan
fungsi, untuk menjaga integritas komputasi.


\>f &= 5\*x;

\>function f(x) := 6\*x;

\>f(2)


    12

Ekspresi yang akan dievaluasi simbolik dinamai dengan konvensi fx atau fxy.


\>fx &= diff(x^x,x); $&fx


$$x^{x}\,\left(1+\log x\right)$$Bentuk bebas penginputan argumen di luar x atau y dicapai dengan memberikan header definisi parameter
menggunakan pola "@(variabel)".


\>"@(a,b) a^2+b^2", %(4,5)


    @(a,b) a^2+b^2
    41

Pemanggilan formula ini pada sebuah fungsi secara konsisten menghemat alokasi pengkodean berulang.


\>fx &= x^3-a\*x;  ...  
\>   a=1.2; fx(0.5)


    -0.475

\>fx(0.5,a=1.1)


    -0.425

# Matematika Simbolik dengan Maxima

Integrasi canggih EMT melibatkan peranti aljabar komputer (CAS) bernama Maxima. Anda mengaktifkan
perintah khusus Maxima dengan menambahkan lambang ampersand "&amp;" di depan persamaan.


Salah satu kekuatan utama Maxima adalah aritmatika bilangan bulat tak terhingga untuk memproses angka
berukuran ekstrem secara presisi tanpa hambatan digit IEEE.


\>$&44!


$$2658271574788448768043625811014615890319638528000000000$$Dengan presisi tersebut, operasi binomial eksak dimungkinkan. latex: C(44,10) = \frac{44!}{34! \cdot
10!}


\>$& 44!/(34!\*10!) // nilai C(44,10)


$$2481256778$$Tentu, EMT juga memfasilitasi panggilan langsung fungsi built-in numeriknya yang efisien.


\>$binomial(44,10) //menghitung C(44,10) menggunakan fungsi binomial()


$$2481256778$$Anda bisa memanipulasi bentuk umum fungsi tanpa menentukan angka tetap terlebih dahulu: latex:
C(x,3)=\frac{x!}{(x-3)!3!}=\frac{(x-2)(x-1)x}{6}


\>$binomial(x,3) // C(x,3)


$$\frac{\left(-2+x\right)\,\left(-1+x\right)\,x}{6}$$Ketika tiba saatnya untuk mensubstitusi x menjadi nilai konkret, panggil kata hubung "with".


\>$&binomial(x,3) with x=10 // substitusi x=10 ke C(x,3)


$$120$$Awalan ganda "$&amp;" atau sekadar awalan "$" akan mengirimkan perintah untuk mencetak output simbolik
melalui interpretasi tipografi LaTeX (dengan prasyarat Anda telah menginstal distribusi LaTeX)[cite:
5].


\>$(3+x)/(x^2+1)


$$\frac{3+x}{1+x^2}$$Rantai ekspresi kompleks EMT memungkinkan pendefinisian memori Maxima secara simultan melalui bungkus
string kutip "&amp;"..."" (meskipun untuk prosedur panjang hal ini kurang disarankan).


\>&"v := 5; v^2"


    
                                                     25
    

Hasil manipulasi polinomial Maxima bisa dipanggil menggunakan token operator %.


\>$&expand((1+x)^4), $&factor(diff(%,x)) // diff: turunan, factor: faktor


$$4\,\left(1+x\right)^3$$![images/Tugas%202-015.png](images/Tugas%202-015.png)

Operator pendefinisian "&amp;=" digunakan khusus untuk merekam fungsi ke dalam memori matriks simbolik
Maxima.


\>fx &= (x+1)/(x^4+1); $&fx


$$\frac{1+x}{1+x^4}$$\>$&factor(diff(fx,x))


$$\frac{1-4\,x^3-3\,x^4}{\left(1+x^4\right)^2}$$Untuk programmer berpengalaman, akses kode native (asli) sintaks Maxima dapat dilakukan dengan
menulis dua (::) atau tiga usap titik dua (:::). Format mode native langsung dieksekusi Maxima tanpa
transisi EMT.


\>&factor(20!)


    
                                             2432902008176640000
    

\>::: factor(10!)


    
                                                  8  4  2
                                                 2  3  5  7
    

\>:: factor(20!)


    
                                           18  8  4  2
                                          2   3  5  7  11 13 17 19
    

\>::: av:g$ av^2;


    
                                                      2
                                                     g
    

\>fx &= x^3\*exp(x), $fx


    
                                                     3  x
                                                    x  E
    

$$x^3\,e^{x}$$Evaluasi di sisi Maxima yang dipengaruhi parameter simbolik EMT ditangani secara halus.


\>&(fx with x=5), $%, &float(%)


    
                                                        5
                                                   125 E
    

$$125\,e^5$$    
                                              18551.64488782208
    

\>fx(5)


    18551.6448878

Fungsi eksklusif perata kalkulasi (float) pada argumen Maxima mereduksi hasil besar berjenis rasional
atau transendental ke ukuran yang bisa ditampilkan EMT secara kasat mata.


\>&(fx with x=10)-(fx with x=5), &float(%)


    
                                                    5         10
                                             - 125 E  + 1000 E
    
    
                                             2.20079141499189e+7
    

\>$factor(diff(fx,x,2))


$$x\,\left(6+6\,x+x^2\right)\,e^{x}$$Jika Anda menginginkan ekstraksi string LaTeX untuk dokumentasi, panggil perintah tex(fx).


\>tex(fx)


    x^3\,e^{x}

Variasi simbolik dan numerik saling bersinggungan secara transparan di EMT.


\>fx(0.5)


    0.206090158838

\>$&fx with x=1/2


$$\frac{\sqrt{e}}{8}$$\>$&fx with x=1+t


$$\left(1+t\right)^3\,e^{1+t}$$Perintah krusial, solve(), ditujukan untuk memecahkan persamaan berdasarkan target nol, serta
mengeluarkan kumpulan vektor dari keseluruhan akarnya.


\>$&solve(x^2+x=4,x)


$$\left[ x=\frac{-1-\sqrt{17}}{2} , x=\frac{-1+\sqrt{17}}{2} \right] $$Eksekusi solver secara numerik wajib memberikan titik estimasi awal (initial guess values), serta
dapat dideklarasikan dengan parameter target konstan y=....


\>solve("x^2+x",1,y=4)


    1.56155281281

Pemanggilan array jawaban solve bisa diekstrak per posisinya agar menunjang proses algoritma
beruntun.


\>sol &= solve(x^2+2\*x=4,x); $&sol, sol(), $&float(sol)


$$\left[ x=-1-\sqrt{5} , x=-1+\sqrt{5} \right] $$    [-3.23607,  1.23607]

$$\left[ x=-3.23606797749979 , x=1.23606797749979 \right] $$\>$&solve(x^2+x=1,x), x2 &= x with %[2]; $&x2


$$\frac{-1+\sqrt{5}}{2}$$![images/Tugas%202-027.png](images/Tugas%202-027.png)

Sistem Persamaan Linear (SPL) bisa diselesaikan dengan melemparkan kombinasi vektor persamaan.


\>sol &= solve([x+y=3,x^2+y^2=5],[x,y]); $&sol, $&x\*y with sol[1]


$$2$$![images/Tugas%202-029.png](images/Tugas%202-029.png)

Penanda tambahan (flag modifier) disisipkan dengan token ganjil "|" sebagai pengganti perintah
pembungkus "ev()". Ini memungkinkan penerapan perintah sekunder Maxima seperti "ratsimp" di tahap
evaluasi terakhir.


\>$& diff((x^3-1)/(x+1),x) //turunan bentuk pecahan


$$\frac{1-x^3}{\left(1+x\right)^2}+\frac{3\,x^2}{1+x}$$\>$& diff((x^3-1)/(x+1),x) | ratsimp //menyederhanakan pecahan


$$\frac{1+3\,x^2+2\,x^3}{1+2\,x+x^2}$$\>$&factor(%)


$$\frac{1+3\,x^2+2\,x^3}{\left(1+x\right)^2}$$# Mendefinisikan Fungsi

Pembuatan program kustom di EMT diwujudkan melalui pendeklarasian perintah awalan "function". Anda
bisa menetapkan identitas kalkulasi f(x) secara konstan dengan deklarasi titik dua dan sama dengan
":=" untuk komputasi numerik biasa.


\>function f(x) := x\*sqrt(x^2+1)

\>f(2)


    4.472135955

Berkat sifat matriks EMT, input skala larik berurutan langsung tervektorisasi dengan fungsi tersebut.


\>f(0:0.1:1)


    [0,  0.100499,  0.203961,  0.313209,  0.430813,  0.559017,  0.699714,  0.854459,  1.0245,  1.21083,
    1.41421]

\>solve("f",1,y=1)


    0.786151377757

Hati-hatilah dalam memberi nama fungsi agar tidak berbenturan dengan perintah sistem internal. Jika
terpaksa menimpa (overwrite), gunakan tag awalan "overwrite" dan perhatikan dampaknya secara teliti.


\>function overwrite sin (x) := \_sin(x°) // mendefinisikan ulang sinus dalam derajat

\>sin(45)


    0.707106781187

\>forget sin; sin(pi/4)


    0.707106781187

## Parameter Default

Fungsi numerik yang didesain dapat membawa parameter inisial yang terisi otomatis.


\>function f(x,a=1) := a\*x^2

\>f(4)


    16

\>f(4,5)


    80

\>f(4,a=1)


    16

\>function f(x) := a\*x^2

\>a=6; f(2)


    24

\>f(2,a:=5)


    20

Berbeda dengan ":=", tanda deklarasi "&amp;=" meneruskan fungsi yang Anda tulis murni ke sisi analitik
Maxima. Hasilnya adalah formula yang dapat beroperasi melintasi dua koridor program.


\>function g(x) &= x^3-x\*exp(-x); $&g(x)


$$x^3-x\,e^ {- x }$$\>$&diff(g(x),x), $&% with x=4/3


$$\frac{16}{3}+\frac{e^ {- \frac{4}{3} }}{3}$$![images/Tugas%202-035.png](images/Tugas%202-035.png)

\>g(5+g(1))


    178.635099908

\>function G(x) &= factor(integrate(g(x),x)); $&G(c) // integrate: mengintegralkan


$$\frac{e^ {- c }\,\left(4+4\,c+c^4\,e^{c}\right)}{4}$$\>solve(&g(x),0.5)


    0.703467422498

\>solve(&g,0.5)


    0.703467422498

\>function P(x,n) &= (2\*x-1)^n; $&P(x,n)


$$\left(-1+2\,x\right)^{n}$$\>function Q(x,n) &= (x+2)^n; $&Q(x,n)


$$\left(2+x\right)^{n}$$\>$&P(x,4), $&expand(%)


$$1-8\,x+24\,x^2-32\,x^3+16\,x^4$$![images/Tugas%202-040.png](images/Tugas%202-040.png)

\>P(3,4)


    625

\>$&P(x,4)+ Q(x,3), $&expand(%)


$$9+4\,x+30\,x^2-31\,x^3+16\,x^4$$![images/Tugas%202-042.png](images/Tugas%202-042.png)

\>$&P(x,4)-Q(x,3), $&expand(%), $&factor(%)


$$-7-20\,x+18\,x^2-33\,x^3+16\,x^4$$![images/Tugas%202-044.png](images/Tugas%202-044.png)

![images/Tugas%202-045.png](images/Tugas%202-045.png)

\>$&P(x,4)\*Q(x,3), $&expand(%), $&factor(%)


$$\left(2+x\right)^3\,\left(-1+2\,x\right)^4$$![images/Tugas%202-047.png](images/Tugas%202-047.png)

![images/Tugas%202-048.png](images/Tugas%202-048.png)

\>$&P(x,4)/Q(x,1), $&expand(%), $&factor(%)


$$\frac{\left(-1+2\,x\right)^4}{2+x}$$![images/Tugas%202-050.png](images/Tugas%202-050.png)

![images/Tugas%202-051.png](images/Tugas%202-051.png)

\>function f(x) &= x^3-x; $&f(x)


$$-x+x^3$$\>$&integrate(f(x),x)


$$-\frac{x^2}{2}+\frac{x^4}{4}$$Evaluasi parameter kalkulus seperti pengintegral tentu secara natural mensyaratkan pemanfaatan "=:"
berhubung limit dan interval skalar bersifat numerik.


Peningkatan skalar fungsi diizinkan melalui tambahan awalan "map" saat menginisialisasi perulangan
pada keseluruhan matriks elemen. Fungsi akan dipaksa mengeksekusi satu elemen demi satu.


\>function map f(x) := integrate("x^x",1,x)

\>f(0:0.5:2)


    [-0.783431,  -0.410816,  0,  0.676863,  2.05045]

\>function mylog (x,base=10) := ln(x)/ln(base);

\>mylog(100), mylog(2^6.7,2)


    2
    6.7

\>mylog(E^2,base=E)


    2

\>function f([a,b]) &= a^2+b^2-a\*b+b; $&f(a,b), $&f(x,y)


$$x^2+y-x\,y+y^2$$![images/Tugas%202-055.png](images/Tugas%202-055.png)

\>v=[3,4]; f(v)


    17

Adapun bentuk deklarasi ketat "&amp;&amp;=" akan mengunci fungsi sebatas koridor komputasi analitik murni.


\>function lapl(expr,x,y) &&= diff(expr,x,2)+diff(expr,y,2)//turunan parsial kedua


    
                                     diff(expr, x, 2) + diff(expr, y, 2)
    

\>$&realpart((x+I\*y)^4), $&lapl(%,x,y)


$$0$$![images/Tugas%202-057.png](images/Tugas%202-057.png)

\>function f(x,y) &= factor(lapl((x+y^2)^5,x,y)); $&f(x,y)


$$10\,\left(x+y^2\right)^3\,\left(2+x+9\,y^2\right)$$Ringkasan definisi fungsi:


* 
&amp;= untuk fungsi numerik hibrida (simbolik/numerik).

* 
:= untuk fungsi kalkulasi numerik murni.

* 
&amp;&amp;= untuk perlindungan kalkulasi simbolik ketat di Maxima.


# Menyelesaikan Persamaan dan Ekspresi

Untuk pencarian akar numerik (aproksimasi titik balik potong nol x=0), metode Secant dijalankan
otomatis saat Anda memanggil fungsi standar solve(persamaan, dugaan_awal).


\>solve("x^2-2",1)


    1.41421356237

\>$&solve(x^2=2,x)


$$\left[ x=-\sqrt{2} , x=\sqrt{2} \right] $$\>$&solve(x^2-2,x)


$$\left[ x=-\sqrt{2} , x=\sqrt{2} \right] $$\>$&solve(a\*x^2+b\*x+c=0,x)


$$\left[ x=\frac{-b-\sqrt{b^2-4\,a\,c}}{2\,a} , x=\frac{-b+\sqrt{b^2-  4\,a\,c}}{2\,a} \right] $$\>$&solve([a\*x+b\*y=c,d\*x+e\*y=f],[x,y])


$$\left[ \left[ x=-\frac{c\,e}{b\,\left(-5+d\right)-a\,e} , y=\frac{c  \,\left(-5+d\right)}{b\,\left(-5+d\right)-a\,e} \right]  \right] $$\>px &= 4\*x^8+x^7-x^4-x; $&px


$$-x-x^4+x^7+4\,x^8$$\>solve(px,1,y=2), px(%)


    0.966715594851
    2

\>sol &= solve(x^2-x-1,x); $&sol


$$\left[ x=\frac{1-\sqrt{5}}{2} , x=\frac{1+\sqrt{5}}{2} \right] $$\>longest sol()


        -0.6180339887498949       1.618033988749895 

\>$&x^2 with sol[1], $&expand(x^2-x-1 with sol[2])


$$0$$![images/Tugas%202-066.png](images/Tugas%202-066.png)

\>$&solve([x+y=2,x^3+2\*y+x=4],[x,y])


$$\left[ \left[ x=-1 , y=3 \right]  , \left[ x=1 , y=1 \right]  ,   \left[ x=0 , y=2 \right]  \right] $$\>function f(x,a) := x^a-a^x;


Alternatif mempassing parameter skalar (di luar variabel utama) dalam baris ekspresi persamaan bisa
melalui pembungkus tag ganda list {{ }} atau dengan tanda hubung penugasan titik koma.


\>solve({{"f",3}},2,y=0.1)


    2.54116291558

\>solve({{"x^a-a^x",a=3}},2,y=0.1)


    2.54116291558

# Menyelesaikan Pertidaksamaan

EMT mengandalkan pustaka Maxima, "fourier_elim", untuk memetakan domain pertidaksamaan dengan
kepastian logis tingkat tinggi. Modul ini wajib diinisialisasi melalui sintaks load() agar terbuka
untuk memproses serangkaian matriks logika.


\>&load(fourier\_elim)


    
            C:/Program Files/Euler x64/maxima/share/maxima/5.35.1/share/fourier_elim/fourier_elim.lisp
    

\>$&fourier\_elim([x^2 - 1\>0],[x]) // x^2-1 \> 0


$$\left[ 1<x \right] \lor \left[ x<-1 \right] $$\>$&fourier\_elim([x^2 - 1<0],[x]) // x^2-1 < 0


$$\left[ -1<x , x<1 \right] $$\>$&fourier\_elim([x^2 - 1 # 0],[x]) // x^-1 <\> 0


$$\left[ -1<x , x<1 \right] \lor \left[ 1<x \right] \lor \left[ x<-1   \right] $$\>$&fourier\_elim([x # 6],[x])


$$\left[ x<6 \right] \lor \left[ 6<x \right] $$\>$&fourier\_elim([x < 1, x \> 1],[x]) // tidak memiliki penyelesaian


$${\it emptyset}$$\>$&fourier\_elim([minf < x, x < inf],[x]) // solusinya R


$${\it universalset}$$\>$&fourier\_elim([x^3 - 1 \> 0],[x])


$$\left[ 1<x , 1+x+x^2>0 \right] \lor \left[ x<1 , -1-x-x^2>0   \right] $$\>$&fourier\_elim([cos(x) < 1/2],[x]) // ??? gagal


$$\left[ 1-2\,\cos x>0 \right] $$\>$&fourier\_elim([y-x < 5, x - y < 7, 10 < y],[x,y]) // sistem pertidaksamaan


$$\left[ -5+y<x , 10<y \right] $$\>$&fourier\_elim([y-x < 5, x - y < 7, 10 < y],[y,x])


$$\left[ 10<y , y<5+x , 5<x \right] $$\>$&fourier\_elim((x + y < 5) and (x - y \>8),[x,y])


$$\left[ 8+y<x \right] $$\>$&fourier\_elim(((x + y < 5) and x < 1) or  (x - y \>8),[x,y])


$$\left[ 8+y<x \right] \lor \left[ x<{\it min}\left(1 , 5-y\right)   \right] $$\>&fourier\_elim([max(x,y) \> 6, x # 8, abs(y-1) \> 12],[x,y])


    
                     [6 &lt; x, y &lt; - 11] or [x = y, 13 &lt; y] or [13 &lt; y] or [y &lt; x, 13 &lt; y]
    

\>$&fourier\_elim([(x+6)/(x-9) <= 6],[x])


$${\it universalset}$$# Bahasa Matriks di EMT

Pemisahan indeks matriks sangat penting: tanda koma memisahkan penambahan kolom matriks, sementara
titik koma mencetak iterasi bergeser ke baris bawah matriks.


\>A=[1,2;3,4]


                1             2 
                3             4 

\>b=[3;4]


                3 
                4 

\>b' // transpose b


    [3,  4]

\>inv(A) //invers A


               -2             1 
              1.5          -0.5 

Operator perkalian mutlak dari kaidah determinan dot-cross matriks secara eksplisit diwakili karakter
titik "."


\>A.b //perkalian matriks


               11 
               25 

\>A.inv(A)


                1             0 
                0             1 

Penting: Perkalian skalar elemen-per-elemen secara linier selalu digandeng token bintang "*"[cite:
5].


\>A.A


                7            10 
               15            22 

\>A^2 //perpangkatan elemen2 A


                1             4 
                9            16 

\>A.A.A


               37            54 
               81           118 

\>power(A,3) //perpangkatan matriks


               37            54 
               81           118 

\>A/A //pembagian elemen-elemen matriks yang seletak


                1             1 
                1             1 

\>A/b //pembagian elemen2 A oleh elemen2 b kolom demi kolom (karena b vektor kolom)


         0.333333      0.666667 
             0.75             1 

\>A\\b // hasilkali invers A dan b, A^(-1)b 


               -2 
              2.5 

\>inv(A).b


               -2 
              2.5 

\>A\\A   //A^(-1)A


                1             0 
                0             1 

\>inv(A).A


                1             0 
                0             1 

\>A\*A //perkalian elemen-elemen matriks seletak


                1             4 
                9            16 

Perkalian ini (*) bukanlah dot cross, array merata hanya dikalikan ke pasangannya sendiri.


\>b^2 // perpangkatan elemen-elemen matriks/vektor


                9 
               16 

Array berukuran lebih pendek secara otomatis menyesuaikan skalabilitas sebaran matriks induknya agar
tercapai hitungan yang simetris dan proporsional.


\>2\*A


                2             4 
                6             8 

\>[1,2]\*A


                1             4 
                3             8 

\>A\*[2,3]


                2             6 
                6            12 

\>dup([1,2],2) // dup: menduplikasi/menggandakan vektor [1,2] sebanyak 2 kali (baris)


                1             2 
                1             2 

\>A\*dup([1,2],2) 


                1             4 
                3             8 

Pembentukan pola grid hitungan array kombinasi ini sering dijumpai dalam membangun kontur dasar
kalkulus multi varian 3 dimensi.


\>(1:5)\*(1:5)' // hasilkali elemen-elemen vektor baris dan vektor kolom


                1             2             3             4             5 
                2             4             6             8            10 
                3             6             9            12            15 
                4             8            12            16            20 
                5            10            15            20            25 

\>(1:5).(1:5)' // hasilkali vektor baris dan vektor kolom


    55

\>sum((1:5)\*(1:5)) // sama hasilnya


    55

Pengecekan logika logika boolean untuk serangkaian vektor diizinkan berkat skalabilitas komparator
array sum() atau mnonzeros().


\>(1:10)<6 // menguji elemen-elemen yang kurang dari 6


    [1,  1,  1,  1,  1,  0,  0,  0,  0,  0]

\>sum((1:10)<6) // banyak elemen yang kurang dari 6


    5

\>t=(1:10)^2; t==25 //menguji elemen2 t yang sama dengan 25 (hanya ada 1)


    [0,  0,  0,  0,  1,  0,  0,  0,  0,  0]

\>nonzeros(t\>50) //indeks elemen2 t yang lebih besar daripada 50


    [8,  9,  10]

\>t[nonzeros(t\>50)] //elemen2 t yang lebih besar daripada 50


    [64,  81,  100]

Contoh matematis: Mencari bilangan berpangkat di range tertentu dengan operasi sisa bagi.


\>t=1:1000; nonzeros(mod(t^2,11)==5 && mod(t^2,13)==3)


    [4,  48,  95,  139,  147,  191,  238,  282,  290,  334,  381,  425,  433,  477,  524,  568,  576,
    620,  667,  711,  719,  763,  810,  854,  862,  906,  953,  997]

Operasi filter juga dapat diterapkan di matriks yang kompleks.


\>t=1:1000; length(nonzeros(isprime(t^2+1)))


    112

\>seed(2); A=random(3,4)


         0.765761      0.401188      0.406347      0.267829 
          0.13673      0.390567      0.495975      0.952814 
         0.548138      0.006085      0.444255      0.539246 

\>k=mnonzeros(A<0.4) //indeks elemen2 A yang kurang dari 0,4


                1             4 
                2             1 
                2             2 
                3             2 

\>mset(A,k,0) //mengganti elemen2 suatu matriks pada indeks tertentu


         0.765761      0.401188      0.406347             0 
                0             0      0.495975      0.952814 
         0.548138             0      0.444255      0.539246 

\>mset(A,k,-random(size(A)))


         0.765761      0.401188      0.406347     -0.126917 
        -0.122404     -0.691673      0.495975      0.952814 
         0.548138     -0.483902      0.444255      0.539246 

\>mget(A,k)


    [0.267829,  0.13673,  0.390567,  0.006085]

\>ex=extrema(A)


         0.267829             4      0.765761             1 
          0.13673             1      0.952814             4 
         0.006085             2      0.548138             1 

\>ex[,3]'


    [0.765761,  0.952814,  0.548138]

\>max(A)'


    [0.765761,  0.952814,  0.548138]

\>j=(1:rows(A))'|ex[,4], mget(-A,j)


                1             1 
                2             4 
                3             1 
    [-0.765761,  -0.952814,  -0.548138]

# Fungsi Membangun Matriks Tingkat Lanjut

Matriks parsial dapat ditumpuk berdampingan, dan sistem akan menginjeksi pengisi nilai nol otomatis
bila panjang susunannya asimetris.


\>v=1:3; v\_v


                1             2             3 
                1             2             3 

\>A=random(3,4); A|v'


         0.032444     0.0534171      0.595713      0.564454             1 
          0.83916      0.175552      0.396988       0.83514             2 
        0.0257573      0.658585      0.629832      0.770895             3 

\>A|1


         0.032444     0.0534171      0.595713      0.564454             1 
          0.83916      0.175552      0.396988       0.83514             1 
        0.0257573      0.658585      0.629832      0.770895             1 

\>[v;v]


                1             2             3 
                1             2             3 

\>[v',v']


                1             1 
                2             2 
                3             3 

\>"[x,x^2]"(v')


                1             1 
                2             4 
                3             9 

\>C=zeros(2,4); rows(C), cols(C), size(C), length(C)


    2
    4
    [2,  4]
    4

\>length(2:10)


    9

\>ones(2,2)


                1             1 
                1             1 

\>ones(5)\*6


    [6,  6,  6,  6,  6]

\>random(2,2)


          0.66566      0.831835 
            0.977      0.544258 

\>redim(1:9,3,3) // menyusun elemen2 1, 2, 3, ..., 9 ke bentuk matriks 3x3


                1             2             3 
                4             5             6 
                7             8             9 

\>function rep(v,n) := redim(dup(v,n),1,n\*cols(v))

\>rep(1:3,5)


    [1,  2,  3,  1,  2,  3,  1,  2,  3,  1,  2,  3,  1,  2,  3]

\>multdup(1:3,5), multdup(1:3,[2,3,2])


    [1,  1,  1,  1,  1,  2,  2,  2,  2,  2,  3,  3,  3,  3,  3]
    [1,  1,  2,  2,  2,  3,  3]

\>flipx(1:5) //membalik elemen2 vektor baris


    [5,  4,  3,  2,  1]

\>rotleft(1:5) // memutar elemen2 vektor baris


    [2,  3,  4,  5,  1]

\>drop(10:20,3)


    [10,  11,  13,  14,  15,  16,  17,  18,  19,  20]

\>v=primes(50), i=indexof(v,10:20), drop(v,i)


    [2,  3,  5,  7,  11,  13,  17,  19,  23,  29,  31,  37,  41,  43,  47]
    [0,  5,  0,  6,  0,  0,  0,  7,  0,  8,  0]
    [2,  3,  5,  7,  23,  29,  31,  37,  41,  43,  47]

\>drop(1:10,shuffle([0,0,5,5,7,12,12]))


    [1,  2,  3,  4,  6,  8,  9,  10]

\>A=id(5) // matriks identitas 5x5


                1             0             0             0             0 
                0             1             0             0             0 
                0             0             1             0             0 
                0             0             0             1             0 
                0             0             0             0             1 

\>setdiag(A,-1,1:4) //mengganti diagonal di bawah diagonal utama


                1             0             0             0             0 
                1             1             0             0             0 
                0             2             1             0             0 
                0             0             3             1             0 
                0             0             0             4             1 

\>function tridiag (n,a,b,c) := setdiag(setdiag(b\*id(n),1,c),-1,a); ...  
\>   tridiag(5,1,2,3)


                2             3             0             0             0 
                1             2             3             0             0 
                0             1             2             3             0 
                0             0             1             2             3 
                0             0             0             1             2 

\>A=redim(1:9,3,3)


                1             2             3 
                4             5             6 
                7             8             9 

\>d=getdiag(A,0)


    [1,  5,  9]

\>fraction A/d'


            1         2         3 
          4/5         1       6/5 
          7/9       8/9         1 

# Skalabilitas dan Vektorisasi

Pengaplikasian fungsi tunggal pada array mendatangkan hasil iteratif tanpa kode berbelit berkat
skalabilitas otomatis fungsi vektor EMT.


\>sqrt(1:3)


    [1,  1.41421,  1.73205]

\>x=1:0.01:5; y=log(x)/x^2; // terlalu panjang untuk ditampikan

\>t=-1:0.1:1; s=t^3-t


    [0,  0.171,  0.288,  0.357,  0.384,  0.375,  0.336,  0.273,  0.192,  0.099,  0,  -0.099,  -0.192,
    -0.273,  -0.336,  -0.375,  -0.384,  -0.357,  -0.288,  -0.171,  0]

\>shortest (1:5)\*(1:5)'


         1      2      3      4      5 
         2      4      6      8     10 
         3      6      9     12     15 
         4      8     12     16     20 
         5     10     15     20     25 

\>(1:5).(1:5)'


    55

\>[1,2,3,4]


    [1,  2,  3,  4]

\>v:=[1,2]; v.v', %^2


    5
    25

\>v=1:4; v'


                1 
                2 
                3 
                4 

\>A=[1,2,3,4;5,6,7,8]; A.v'


               30 
               70 

\>v'.v


                1             2             3             4 
                2             4             6             8 
                3             6             9            12 
                4             8            12            16 

\>v.v'


    30

\>norm(v)^2


    30

Aturan vektorisasi merangkum beberapa hukum baku di EMT:


* 
Fungsi skalar jika dieksekusi di vektor akan meniru iterasi parsial loop. - Operator yang berada di
* tengah persilangan dua matriks senama merujuk fungsi per pasangan. - Bila benturan antar elemen
* berskala dimensi asing muncul, sistem mencoba menggandakannya sebisa mungkin, sampai proporsi setara
* terhimpun secara natural..


\>[1,2,3]^2


    [1,  4,  9]

\>v:=[1,2,3]; v\*v'


                1             2             3 
                2             4             6 
                3             6             9 

\>v.v'


    14

\>v\*v, sum(v\*v), cumsum(v\*v)


    [1,  4,  9]
    14
    [1,  5,  14]

\>1:4, 1:2:10


    [1,  2,  3,  4]
    [1,  3,  5,  7,  9]

\>[1,2,3]|[4,5], [1,2,3]\_1


    [1,  2,  3,  4,  5]
                1             2             3 
                1             1             1 

\>A:=[1,2,3;4,5,6;7,8,9]; A[2,3]


    6

\>v:=[2,4,6,8]; v[3], A[3]


    6
    [7,  8,  9]

\>v[1:2], A[:,2]


    [2,  4]
                2 
                5 
                8 

\>A[,2:3]


                2             3 
                5             6 
                8             9 

\>A{4}


    4

\>redim(A,1,prod(size(A))), flatten(A)


    [1,  2,  3,  4,  5,  6,  7,  8,  9]
    [1,  2,  3,  4,  5,  6,  7,  8,  9]

\>defformat; w=0; w=w'; deg(w)


    0

\>M = deg(w)|w|cos(w)|sin(w)


    [0,  0,  1,  0]

\>function map f(x) := integrate("x^x",1,x)

\>f([1:5])


    [0,  2.05045,  13.7251,  113.336,  1241.03]

# Mengekstraksi Elemen pada Matriks

\>A=[1,2,3;4,5,6;7,8,9], A[2,2]


                1             2             3 
                4             5             6 
                7             8             9 
    5

\>A[2]


    [4,  5,  6]

\>v=1:3; v[2]


    2

\>A[2,]


    [4,  5,  6]

\>A[[1,2]]


                1             2             3 
                4             5             6 

\>A[[3,2,1]]


                7             8             9 
                4             5             6 
                1             2             3 

\>A[1:3,2:3]


                2             3 
                5             6 
                8             9 

\>A[:,3]


                3 
                6 
                9 

\>A[,2:3]


                2             3 
                5             6 
                8             9 

\>A[-1]


    [7,  8,  9]

\>A[1,1]=4


                4             2             3 
                4             5             6 
                7             8             9 

\>A[1]=[-1,-1,-1]


               -1            -1            -1 
                4             5             6 
                7             8             9 

\>A[1:2,1:2]=[5,6;7,8]


                5             6            -1 
                7             8             6 
                7             8             9 

\>A[1:2,1:2]=0


                0             0            -1 
                0             0             6 
                7             8             9 

# Mengurutkan dan Mengacak Array (Sorting and Shuffling)

sort() difungsikan untuk mereorganisasi baris vektor terkecil hingga ke terbesar secara menaik
(ascending).


\>sort([5,6,4,8,1,9])


    [1,  4,  5,  6,  8,  9]

Sebaliknya, peranti acak shuffle() akan mengaduk isi array murni secara acak.


\>v=shuffle(1:10)


    [4,  5,  10,  6,  8,  9,  1,  7,  2,  3]

\>{vs,ind}=sort(v); v[ind]


    [1,  2,  3,  4,  5,  6,  7,  8,  9,  10]

\>s=["a","d","e","a","aa","e"]


    a
    d
    e
    a
    aa
    e

\>{ss,ind}=sort(s); ss


    a
    a
    aa
    d
    e
    e

\>ind


    [4,  1,  5,  2,  6,  3]

\>intrandom(1,10,10), unique(%)


    [4,  4,  9,  2,  6,  5,  10,  6,  5,  1]
    [1,  2,  4,  5,  6,  9,  10]

\>unique(s)


    a
    aa
    d
    e

# Pemanfaatan EMT dalam Aljabar Linear Terapan

Pemecahan algoritma matriks terinversi Ax=b merupakan bagian dari sistem komputasi nativ EMT.


\>A=[1,2;3,4]; b=[5;6]; A\\b


               -4 
              4.5 

\>A=normal(200,200); b=sum(A); longest totalmax(abs(inv(A).b-1))


      8.790745908981989e-13 

\>A=[1,2,3;4,5,6;7,8,9]


                1             2             3 
                4             5             6 
                7             8             9 

\>det(A)


    0

# Matriks Simbolik

\>A &= [a,1,1;1,a,1;1,1,a]; $A


$$\begin{pmatrix}a & 1 & 1 \\ 1 & a & 1 \\ 1 & 1 & a \\ \end{pmatrix}$$\>$&det(A), $&factor(%)


$$\left(-1+a\right)^2\,\left(2+a\right)$$![images/Tugas%202-083.png](images/Tugas%202-083.png)

\>$&invert(A) with a=0


$$\begin{pmatrix}-\frac{1}{2} & \frac{1}{2} & \frac{1}{2} \\ \frac{1  }{2} & -\frac{1}{2} & \frac{1}{2} \\ \frac{1}{2} & \frac{1}{2} & -  \frac{1}{2} \\ \end{pmatrix}$$\>A &= [1,a;b,2]; $A


$$\begin{pmatrix}1 & a \\ b & 2 \\ \end{pmatrix}$$\>$&det(A-x\*ident(2)), $&solve(%,x)


$$\left[ x=\frac{3-\sqrt{1+4\,a\,b}}{2} , x=\frac{3+\sqrt{1+4\,a\,b}  }{2} \right] $$![images/Tugas%202-087.png](images/Tugas%202-087.png)

\>$&eigenvalues([a,1;1,a])


$$\left[ \left[ -1+a , 1+a \right]  , \left[ 1 , 1 \right]  \right] $$\>$&eigenvectors([a,1;1,a]), &%[2][1][1]


$$\left[ \left[ \left[ -1+a , 1+a \right]  , \left[ 1 , 1 \right]    \right]  , \left[ \left[ \left[ 1 , -1 \right]  \right]  , \left[   \left[ 1 , 1 \right]  \right]  \right]  \right] $$    
                                                  [1, - 1]
    

\>A(a=4,b=5)


                1             4 
                5             2 

\>$&A[1]


$$\left[ 1 , a \right] $$\>&A[1,1]:=t+1; $&A


$$\begin{pmatrix}1+t & a \\ b & 2 \\ \end{pmatrix}$$\>v &= makelist(1/(i+j),i,1,3); $v


$$\left[ \frac{1}{1+j} , \frac{1}{2+j} , \frac{1}{3+j} \right] $$\>B &:= [1,2;3,4]; $B, $&invert(B)


$$\begin{pmatrix}-2 & 1 \\ \frac{3}{2} & -\frac{1}{2} \\   \end{pmatrix}$$![images/Tugas%202-094.png](images/Tugas%202-094.png)

\>$&invert(B)()


               -2             1 
              1.5          -0.5 

\>longest B.xinv(B)


                          1                       0 
                          0                       1 

\>A=[1,2,3;4,5,6;7,8,9]; real(eigenvalues(A))


    [16.1168,  -1.11684,  0]

\>$&eigenvalues(@A)


$$\left[ \left[ \frac{15-3\,\sqrt{33}}{2} , \frac{15+3\,\sqrt{33}}{2}   , 0 \right]  , \left[ 1 , 1 , 1 \right]  \right] $$# Nilai Numerik dalam Ekspresi Simbolik

\>A &:= [1,pi;4,5]


                1       3.14159 
                4             5 

\>$&A


$$\begin{pmatrix}1 & \frac{1146408}{364913} \\ 4 & 5 \\ \end{pmatrix}$$\>mxmset(A); $&A


$$\begin{pmatrix}1 & 3.141592653589793 \\ 4 & 5 \\ \end{pmatrix}$$\>$&bfloat(sqrt(2)), $&float(sqrt(2))


$$1.414213562373095$$![images/Tugas%202-099.png](images/Tugas%202-099.png)

\>&fpprec:=100; &bfloat(pi)


    
             3.14159265358979323846264338327950288419716939937510582097494459230781640628620899862803482\
    5342117068b0
    

\>B:=[1,pi;3,4]; $&det(@B)


$$-5.424777960769379$$# Studi Kasus: Perhitungan Suku Bunga

Untuk memvisualisasikan bagaimana EMT sangat efektif menyelesaikan dilema analisis riil, mari
berlatih pada perhitungan investasi dan suku bunga. Anggaplah Anda menyimpan dana utama sebesar
$5.000.


\>K=5000


    5000

Dengan rasio tambahan bunga konstan sebesar 3% setiap setahunnya.


\>K\*1.03


    5150

\>K+K\*3%


    5150

Demi mempermudah sistem perhitungan matematis majemuk, kita cukup meringkas pengalinya sebagai
variabel tunggal q = 1,03.


\>q=1+3%, K\*q


    1.03
    5150

Untuk jangka waktu proyeksi pelunasan/pertumbuhan 10 tahun ke depan, kalkulasi logaritmik geometri
sederhana bisa langsung dipanggil.


\>K\*q^10


    6719.58189672

\>format(12,2); K\*q^10


        6719.58 

\>"Berawal dari " + K + "$ Anda mendapatkan " + round(K\*q^10,2) + "$."


    Berawal dari 5000$ Anda mendapatkan 6719.58$.

Pemanfaatan vektor secara horizontal seketika akan menampilkan lintasan proyeksi berurutan dari
rentang tahun pertama hingga kesepuluh.


\>K\*q^(0:10)


    Real 1 x 11 matrix
    
        5000.00     5150.00     5304.50     5463.64     5627.54     5796.37     5970.26     ...

\>short 0:10


    [0,  1,  2,  3,  4,  5,  6,  7,  8,  9,  10]

\>short q^(0:10)


    [1,  1.03,  1.0609,  1.0927,  1.1255,  1.1593,  1.1941,  1.2299,  1.2668,  1.3048,  1.3439]

\>VK=K\*q^(0:10);

\>function oneyear (K) := round(K\*q,2)

\>longest oneyear(1234.57), longest 1234.57\*q


                    1271.61 
                  1271.6071 

Perintah iterate() terbukti sangat ampuh. Proses loop tahun demi tahun direduksi menjadi hanya
sepenggal sintaks memutar algoritma secara progresif.


\>VKr=iterate("oneyear",5000,10)


    Real 1 x 11 matrix
    
        5000.00     5150.00     5304.50     5463.64     5627.55     5796.38     5970.27     ...

\>VKr'


        5000.00 
        5150.00 
        5304.50 
        5463.64 
        5627.55 
        5796.38 
        5970.27 
        6149.38 
        6333.86 
        6523.88 
        6719.60 

\>VKr[2], VKr[1:3]


        5150.00 
        5000.00     5150.00     5304.50 

\>VKr[-1], VK[-1]


        6719.60 
        6719.58 

# Analisis Kritis Pembayaran Suku Bunga

Saat kita memodifikasi kasus suku bunga dengan injeksi (penambahan R) berkala di atas suku bunga
geometri.


\>function onepay (K) := K\*q+R

\>R=200; iterate("onepay",5000,10)


    Real 1 x 11 matrix
    
        5000.00     5350.00     5710.50     6081.82     6464.27     6858.20     7263.94     ...

Tapi bagaimana jika Anda menarik sebagian uang Anda (R minus), berakibat arus negatif secara
perlahan?


\>R=-200; iterate("onepay",5000,10)


    Real 1 x 11 matrix
    
        5000.00     4950.00     4898.50     4845.45     4790.82     4734.54     4676.58     ...

\>VKR=iterate("onepay",5000,50)


    Real 1 x 51 matrix
    
        5000.00     4950.00     4898.50     4845.45     4790.82     4734.54     4676.58     ...

\>min(nonzeros(VKR<0))


          48.00 

Menggunakan metode iterasi dan matriks array, kita bisa mengecek di titik batas iterasi keberapa
dompet digital akan berakhir menembus nol.


\>{x,n}=iterate("onepay",5000,till="x<0"); x, n,


         -19.83 
          47.00 

\>function f(K,R,P,n) := iterate("x\*(1+P/100)+R",K,n;P,R)[-1]

\>f(5000,-200,3,47)


         -19.83 

\>solve("f(5000,-200,x,50)",3)


           3.15 

\>solve("f(5000,x,3,20)",-200)


        -336.08 

## Transformasi Solusi Secara Simbolik

Kasus perbankan di atas dapat diekstrak rumus murninya oleh sistem simbolik.


\>function op(K) &= K\*q+R; $&op(K)


$$q\,K+R$$\>$&op(op(op(op(K)))), $&expand(%)


$$q^4\,K+R+q\,R+q^2\,R+q^3\,R$$![images/Tugas%202-103.png](images/Tugas%202-103.png)

Maxima mampu mengenali formulasi turunan deret ukur: latex: K_n = q^n K + R (1+q+\ldots+q^{n-1}) =
q^n K + \frac{q^n-1}{q-1} R


\>&sum(q^k,k,0,n-1); $& % = ev(%,simpsum)


$$\sum_{k=0}^{-1+n}{q^{k}}=\frac{-1+q^{n}}{-1+q}$$\>function fs(K,R,P,n) &= (1+P/100)^n\*K + ((1+P/100)^n-1)/(P/100)\*R; $&fs(K,R,P,n)


$$K\,\left(1+\frac{P}{100}\right)^{n}+\frac{100\,\left(-1+\left(1+  \frac{P}{100}\right)^{n}\right)\,R}{P}$$\>longest f(5000,-200,3,47), longest fs(5000,-200,3,47)


         -19.82504734650985 
         -19.82504734652684 

\>solve("fs(5000,-330,3,x)",30)


          20.51 

\>equ &= fs(K,R,P,n)=Kn; $&equ


$$K\,\left(1+\frac{P}{100}\right)^{n}+\frac{100\,\left(-1+\left(1+  \frac{P}{100}\right)^{n}\right)\,R}{P}={\it Kn}$$\>equ &= (equ with P=100\*i); $&equ


$$\left(1+i\right)^{n}\,K+\frac{\left(-1+\left(1+i\right)^{n}\right)  \,R}{i}={\it Kn}$$\>$&solve(equ,R)


$$\left[ R=\frac{i\,{\it Kn}-i\,\left(1+i\right)^{n}\,K}{-1+\left(1+i  \right)^{n}} \right] $$\>$&limit(R(5000,0,x,10),x,0)


$$\lim_{x\rightarrow 0}{R\left(5000 , 0 , x , 10\right)}$$\>fn &= solve(equ,n) | ratsimp; $&fn


$$\left[ n=\frac{\log \left(i\,{\it Kn}+R\right)-\log \left(i\,K+R  \right)}{\log \left(1+i\right)} \right] $$## Merangkum Operasi Aljabar Standar

$expand(ekspresi) : Mengekspansi persamaan.


$factor(ekspresi) : Memfaktorkan persamaan persekutuan/kuadratik.


$ratsimp(ekspresi) : Mensimplifikasi pecahan silang berbelit.


\>$expand((x+y)^3)


$$x^3+3\,x^2\,y+3\,x\,y^2+y^3$$Ekspansi bentuk (x+y)^3 dijabarkan menjadi deret binomial utuh.


\>$factor(x^3 - 6\*x^2 + 11\*x - 6)


$$\left(-3+x\right)\,\left(-2+x\right)\,\left(-1+x\right)$$Polinomial tingkat tinggi yang nampak acak langsung diekstrak akar akarnya.


\>$ratsimp((x^2 - 1) / (x - 1))


$$1+x$$Fraksional rasional direduksi memotong pembilang vs penyebut sejenis.


## Kalkulus Fundamental (Limit, Turunan, Integral)

\>$limit((2\*x^2 - 5) / (3\*x^2 + x), x, inf)


$$\frac{2}{3}$$Perhitungan fungsi pergerakan asimtotik asimtot dipecahkan pada ambang tidak terbatas limit inf.


\>$diff(sin(x)\*cos(x), x)


$$\cos ^2x-\sin ^2x$$Turunan persamaan kalkulus kompleks diselesaikan mengikuti aturan produk bersarang (product rule).


\>$integrate(x^2 \* exp(x), x, 0, 1)


$$-2+e$$Integral Tentu dengan penentuan batas wilayah luasan (area boundary constraint).


\>$(2\*x3\*y+z-7)+(4\*x-2\*y-z+8)+(-3\*x+7-2\*z-4)


$$4-2\,\left(a+b\,i\right)+x-2\,y+2\,{\it x_3}\,y$$\>$integrate((2\*x3\*y+z-7)+(4\*x-2\*y-z+8)+(-3\*x+7-2\*z-4), x)


$$4\,x-2\,\left(a+b\,i\right)\,x+\frac{x^2}{2}-2\,x\,y+2\,x\,  {\it x_3}\,y$$\>$powerdisp: true;


Mode powerdisp membalik penyusunan matriks deret dari basis kuadrat terkecil menanjak (ascending).


\>$%


$$\mathbf{true}$$\>$powerdisp: false;

\>$hasil : integrate((2\*x3\*y+z-7)+(4\*x-2\*y-z+8)+(-3\*x+7-2\*z-4), x)


$$2\,x\,{\it x_3}\,y-2\,x\,y+\frac{x^2}{2}-2\,\left(b\,i+a\right)\,x+  4\,x$$## Menyelesaikan Polinomial Kustom Sendiri

\>$ev(%+1, inf);

\>function f(x) &= x^3 - 3\*x^2 + 5


    
                                                 3      2
                                                x  - 3 x  + 5
    

\>$p(x) = x^3 - 3\*x^2 + 5


$$p\left(x\right)=x^3-3\,x^2+5$$\>function f(x) &= x^3 - 3\*x^2 + 5


    
                                                 3      2
                                                x  - 3 x  + 5
    

\>::cfdisrep([1,0,1,2,1,3,1,4])


    
                                                        1
                                        1 + -------------------------
                                                          1
                                            0 + ---------------------
                                                            1
                                                1 + -----------------
                                                              1
                                                    2 + -------------
                                                                1
                                                        1 + ---------
                                                                  1
                                                            3 + -----
                                                                    1
                                                                1 + -
                                                                    4
    

\>::cfdisrep([3000/1,2,2,2])


    
                                                         1
                                              3000 + ---------
                                                           1
                                                     2 + -----
                                                             1
                                                         2 + -
                                                             2
    

\>$fib(1), $fib(3), $fib(6), $fib(24), $fib(79)


$$14472334024676221$$![images/Tugas%202-123.png](images/Tugas%202-123.png)

![images/Tugas%202-124.png](images/Tugas%202-124.png)

![images/Tugas%202-125.png](images/Tugas%202-125.png)

![images/Tugas%202-126.png](images/Tugas%202-126.png)

\>$fibtophi(fib(n))


$$\frac{{\it \%phi}^{n}-\left(1-{\it \%phi}\right)^{n}}{2\,  {\it \%phi}-1}$$## Relasi Interlocking (Fungsi Komposisi/Invers)

\>function f(x) &= sqrt(2\*x+5); $'f(x)=f(x)


$$f\left(x\right)=\sqrt{2\,x+5}$$\>function g(x) &= sqrt(2^x+1); $'g(x)=g(x)


$$g\left(x\right)=\sqrt{2^{x}+1}$$\>g(f(3))


           3.31 

\>$f(a)


$$\sqrt{2\,a+5}$$\>$f(9999999991)


$$\sqrt{19999999987}$$## Operasi Bentuk Pangkat Tingkat Lanjut

\>$(a^x)^y|radexpandall


$$\left(a^{x}\right)^{y}$$## Menyederhanakan Basis dan Logaritma

\>logbase(16,2)


           4.00 

\>&logexpand:all; $log(a^x\*b^y)


$$\log b\,y+\log a\,x$$\>$logcontract(log(x)+log(y))


$$\log y+\log x$$\>:: logcontract(log(x)+log(y))


    
                                                  log(x y)
    

\>logbase(3^5,2)


           7.92 

\>&solve(logbase(2\*x^2-x,3)=1,x)


    
                                                     2
                                         [logbase(2 x  - x, 3) = 1]
    

\>$solve(log(2\*x^2-x)/log(3)=1,x)


$$\left[ x=\frac{3}{2} , x=-1 \right] $$\>$solve(log(2\*x^2-6\*x-7)/log(2)=log(2\*x^2-6\*x-7)/log(3),x)


$$\left[ x=4 , x=-1 \right] $$\>$log(2\*x^2-6\*x-7)/log(2) with x=4


$$0$$Pastikan berhati-hati, perintah logbase() dikhususkan memroses kalkulasi di ranah komputasi numerik
murni.


\>$solve(logbase(2\*x^2+5\*x-10,5)=logbase(x^2-2\*x+18,5),x)


$$\left[ {\it logbase}\left(x^2-2\,x+18 , 5\right)={\it logbase}  \left(2\,x^2+5\,x-10 , 5\right) \right] $$\>$solve(x^2-2\*x+18=2\*x^2+5\*x-10,x)


$$\left[ x=\frac{-\sqrt{161}-7}{2} , x=\frac{\sqrt{161}-7}{2}   \right] $$\>$solve(log(2\*x^2+5\*x-10)/log(5)=log(x^2-2\*x+18)/log(5),x)


$$\left[ \log \left(x^2-2\,x+18\right)=\log \left(2\,x^2+5\,x-10  \right) \right] $$\>$solve(log(2\*x^2+5\*x-10)/(x^2-2\*x+18)=0,x)


$$\left[ x=\frac{-\sqrt{113}-5}{4} , x=\frac{\sqrt{113}-5}{4}   \right] $$\>$solve(log(2\*x^2-2\*x+20)/(x^2+6\*x+5),x)


$$\left[ x=\frac{1-\sqrt{37}\,i}{2} , x=\frac{\sqrt{37}\,i+1}{2}   \right] $$\>$y=pi/4


$$y=\frac{\pi}{4}$$## Konversi Geometri Hiperbolik

\>$'sinh(x)=exponentialize(sinh(x))


$$\sinh x=\frac{e^{x}-e^ {- x }}{2}$$\>$'cosh(x)=exponentialize(cosh(x))


$$\cosh x=\frac{e^{x}+e^ {- x }}{2}$$\>$'tanh(x)=exponentialize(tanh(x))


$$\tanh x=\frac{e^{x}-e^ {- x }}{e^{x}+e^ {- x }}$$\>$'cosh(x)^2-sinh(x)=trigsimp(cosh(x)^2-sinh(x))


$$\cosh ^2x-\sinh x=\cosh ^2x-\sinh x$$\>$'sin(x+y)=trigexpand(sin(x+y))


$$\sin \left(y+x\right)=\cos x\,\sin y+\sin x\,\cos y$$\>&assume(x\>0, x<2\*pi); &halfangles:true; $sin(x/2), $sinh(x/2)


$$\frac{\sqrt{\cosh x-1}}{\sqrt{2}}$$![images/Tugas%202-150.png](images/Tugas%202-150.png)

\>$-sin(x)^2+3\*cos(x)^2+x=trigreduce(-sin(x)^2+3\*cos(x)^2+x)


$$-\sin ^2x+3\,\cos ^2x+x=\frac{\cos \left(2\,x\right)}{2}+3\,\left(  \frac{\cos \left(2\,x\right)}{2}+\frac{1}{2}\right)+x-\frac{1}{2}$$trigreduce() ditugaskan menjembatani ekspansi perpotongan/pengkuadratan formula cos sin menjadi
formula linier lipat ganda tunggal.


\>$'sin(x)^2+sin(x)\*cos(x)+cos(x)^2=...  
\>   trigreduce(sin(x)^2+sin(x)\*cos(x)+cos(x)^2)|radcan


$$\sin ^2x+\cos x\,\sin x+\cos ^2x=\frac{\sin \left(2\,x\right)+2}{2}$$trigrat() berperan mensimplifikasinya kembali ke quasi-linier.


\>a&=trigrat(rhs(%)); $a


$$\frac{\sin \left(2\,x\right)+2}{2}$$## Visualisasi Bilangan Imajiner Complex

\>sqrt(complex(-1))


                 0.00+1.00i 

\>-3i


                -0.00-3.00i 

\>$i // simbolik, i sebagai variabel


$$i$$\>$2+%i, $2+I // menggunakan i sebagai bilangan imajiner pada operasi simbolik

\>z=1+2\*I


                 1.00+2.00i 

\>re(z)


           1.00 

\>im(z)


           2.00 

\>conj(z)


                 1.00-2.00i 

\>$z:a+b\*i, $conjugate(z)


$$b\,i+a$$![images/Tugas%202-156.png](images/Tugas%202-156.png)

\>abs(z), arg(z) // abs() absolute/modulus arg() sudut


           2.24 
           1.11 

\>$z, $abs(z), $r=cabs(z), $carg(z)


$${\rm atan2}\left(0 , b\,i+a\right)$$![images/Tugas%202-158.png](images/Tugas%202-158.png)

![images/Tugas%202-159.png](images/Tugas%202-159.png)

![images/Tugas%202-160.png](images/Tugas%202-160.png)

\>$'1+sqrt(2)\*I=polarform(1+sqrt(2)\*I)


$$\sqrt{2}\,i+1=\sqrt{3}\,e^{i\,\arctan \sqrt{2}}$$\>$'cos(z)=radcan(demoivre(polarform(cos(z))))


$$\cos \left(b\,i+a\right)=\cos \left(b\,i+a\right)$$## Sistem Perpotongan Kurva (Akar Transendental)

\>function f(x)&=x\*sin(x)-3\*cos(x); $'f(x)=f(x)


$$f\left(x\right)=x\,\sin x-3\,\cos x$$\>plot2d("f(x)-1", -2\*pi, 2\*pi):


![images/Tugas%202-164.png](images/Tugas%202-164.png)

\>plot3d("f(x)-1", -2\*pi, 2\*pi, \>contour, \>hue, angle=pi):


![images/Tugas%202-165.png](images/Tugas%202-165.png)

\>x2=solve("x\*sin(x)-3\*cos(x)-1",3,5)


           3.62 

\>$solve(f(x)-1,x)


$$\left[ x=\frac{3\,\cos x+1}{\sin x} \right] $$\>&load(to\_poly\_solve)


    Error in:
    &amp;load(to_poly_solve) ...
                        ^

\>&load(trigtools)


    
            C:/Program Files/Euler x64/maxima/share/maxima/5.35.1/share/contrib/trigtools/trigtools.mac
    

\>::example(solve)


    
    (I526) solve(asin(cos(3*x))*(f(x)-1),x)
    
    solve: using arc-trig functions to get a solution.
    Some solutions will be lost.
                                              pi      3 cos(x) + 1
                                         [x = --, x = ------------]
                                              6          sin(x)
    (I527) ev(solve(5^f(x) = 125,f(x)),solveradcan)
                                                             log(125)
    (%o527)                           [x sin(x) - 3 cos(x) = --------]
                                                              log(5)
    (I528) [4*x^2-y^2 = 12,x*y-x = 2]
                                            2    2
    (%o528)                             [4 x  - y  = 12, x y - x = 2]
    (I529) solve(%,[x,y])
    (%o529) [[x = 2, y = 2], [x = 0.5202594388652008 I - 0.1331240357358706, 
    y = 0.07678378523787788 - 3.608003221870287 I], [x = - 0.5202594388652008 I - 0.1331240357358706, 
    y = 3.608003221870287 I + 0.07678378523787788], [x = - 1.733751846381093, y = - 0.1535675710019696]]
    (I530) solve(1+a*x+x^3,x)
                                                                   sqrt(3) I   1
                                            3                     (--------- - -) a
                    sqrt(3) I   1   sqrt(4 a  + 27)   1 1/3            2       2
    (%o530) [x = (- --------- - -) (--------------- - -)    - --------------------------, 
                        2       2          3/2        2                  3
                                        2 3                      sqrt(4 a  + 27)   1 1/3
                                                              3 (--------------- - -)
                                                                        3/2        2
                                                                     2 3
                                                         sqrt(3) I   1
                                 3                    (- --------- - -) a
         sqrt(3) I   1   sqrt(4 a  + 27)   1 1/3             2       2
    x = (--------- - -) (--------------- - -)    - --------------------------, 
             2       2          3/2        2                  3
                             2 3                      sqrt(4 a  + 27)   1 1/3
                                                   3 (--------------- - -)
                                                             3/2        2
                                                          2 3
                 3
         sqrt(4 a  + 27)   1 1/3               a
    x = (--------------- - -)    - --------------------------]
                3/2        2                  3
             2 3                      sqrt(4 a  + 27)   1 1/3
                                   3 (--------------- - -)
                                             3/2        2
                                          2 3
    (I531) solve(x^3-1)
                                    sqrt(3) I - 1        sqrt(3) I + 1
    (%o531)                    [x = -------------, x = - -------------, x = 1]
                                          2                    2
    (I532) solve(x^6-1)
                 sqrt(3) I + 1      sqrt(3) I - 1                 sqrt(3) I + 1        sqrt(3) I - 1
    (%o532) [x = -------------, x = -------------, x = - 1, x = - -------------, x = - -------------, 
                       2                  2                             2                    2
                                                                                                   x = 1]
    (I533) ev(x^6-1,%[1])
                                                           6
                                            (sqrt(3) I + 1)
    (%o533)                                 ---------------- - 1
                                                   64
    (I534) expand(%)
    (%o534)                                           0
    (I535) x^2-1
                                                    2
    (%o535)                                        x  - 1
    (I536) solve(%,x)
    (%o536)                                   [x = - 1, x = 1]
    (I537) ev(%th(2),%[1])
    (%o537)                                           0
    (%o537)                                         done
    

\>$solve([x+2\*y=10,5\*x-3\*y+6=9\*x+8\*y+4]) // SIKU Y


$$\left[ \left[ y=-\frac{38}{3} , x=\frac{106}{3} \right]  \right] $$\>p1 &= (x^2+y^2+x=6); p2 &= (x+y=3); $p1, $'p2 


$$y+x=3$$![images/Tugas%202-169.png](images/Tugas%202-169.png)

\>$solve(p2,x), $p1 with %, p3 &= expand(%); $p3


$$2\,y^2-7\,y+12=6$$![images/Tugas%202-171.png](images/Tugas%202-171.png)

![images/Tugas%202-172.png](images/Tugas%202-172.png)

\>$expand(p3/2), $%-6+(7/4)^2, $factor(%), $%\*16


$$\left(4\,y-7\right)^2=1$$![images/Tugas%202-174.png](images/Tugas%202-174.png)

![images/Tugas%202-175.png](images/Tugas%202-175.png)

![images/Tugas%202-176.png](images/Tugas%202-176.png)

\>&load(fourier\_elim)


    
            C:/Program Files/Euler x64/maxima/share/maxima/5.35.1/share/fourier_elim/fourier_elim.lisp
    

\>$fourier\_elim([x^2-1\>0],[x])


$$\left[ 1<x \right] \lor \left[ x<-1 \right] $$\>$fourier\_elim([x^2-1#0],[x])


$$\left[ -1<x , x<1 \right] \lor \left[ 1<x \right] \lor \left[ x<-1   \right] $$\>$fourier\_elim([x^2+1#0],[x])


$${\it universalset}$$\>$fourier\_elim([minf<x,x\>inf],[x])


$${\it emptyset}$$\>$fourier\_elim([x^3-1\>0],[x])


$$\left[ 1<x , x^2+x+1>0 \right] \lor \left[ x<1 , -x^2-x-1>0   \right] $$\>$fourier\_elim([x^2+x+1\>0],[x])


$$\left[ x^2+x+1>0 \right] $$## Contoh Penyelesaian Latihan Soal Aljabar

Set latihan R.2


Sederhanakan bentuk pangkat pecahan silang:


$$49. \left(\frac{24a^{10}b^{-8}c^7}{12a^6b^{-3}c^5}\right)^{-5}$$\>$ ratsimp(((24\*a^10\*b^(-8)\*c^7)/(12\*a^6\*b^(-3)\*c^5))^(-5))


$$\frac{b^{25}}{32\,a^{20}\,c^{10}}$$Melalui penerapan peranti ratsimp() bersama eksekusi flag $, pecahan polinomial tingkat ekstrem
berhasil diringkas tanpa melanggar tatanan kaidah aljabar.


$$50.\left(\frac{125p^{12}q^{-14}r^{22}}{25p^{8}q^{6}r^{-15}}\right)^{-4}$$\>$ ratsimp(((125\*p^12\*q^(-14)\*r^22)/(25\*p^8\*q^6\*r^(-15)))^(-4))


$$\frac{q^{80}}{625\,p^{16}\,r^{148}}$$Hitung operasi pangkat linier berurutan:


$$90. \quad 2^6 \cdot 2^{-3} \div 2^{10} \div 2^{-8}$$\>2^6\*2^(-3)/2^10/2^(-8)


           2.00 

Karena barisan logika aritmatika di soal nomor 90 hanya meminta operasi skalar numerik secara utuh,
tanda awalan $ menjadi tidak relevan, kalkulasi berjalan otomatis secara akurat.


$$91. \quad \frac{4(8-6)^2-4\cdot3+2\cdot8}{3^1+19^0}$$\>(4\*(8-6)^2-4\*3+2\*8)/(3^1+19^0)


           5.00 

Sederhanakan perkalian basis variabel berpangkat polinom:


$$104. \quad (m^{x-b}\cdot n^{x+b})^{x}(m^{b}n^{-b})^{x}$$\>$ radcan((m^(x-b)\*n^(x+b))^(x)\*(m^b\*n^(-b))^(x))


$$m^{x^2}\,n^{x^2}$$Ketika perintah rasional biasa ratsimp() membentur batasan limit simplifikasi pangkat bertumpuk, opsi
tingkat lebih lanjut yakni radcan() dipanggil guna me-reduksi komplikasi akar/pangkat.


$$106. \quad \left[\left(\frac{x^r}{y^t}\right)^2 \left(\frac{x^{2r}}{y^{4t}}\right)^{-2}\right]^{-3}$$\>$ radcan(((x^r/y^t)^2\*(x^(2\*r)/y^(4\*t))^(-2))^(-3))


$$\frac{x^{6\,r}}{y^{18\,t}}$$Set Latihan R.3


Mengurangkan polinomial:


$$12. \quad (2x^4-3x^2+7x)-(5x^3+2x^2-3x+5)$$\>$ (2\*x^4-3\*x^2+7\*x)-(5\*x^3-2\*x^2-3\*x+5)


$$2\,x^4-5\,x^3-x^2+10\,x-5$$Memanfaatkan integrasi $ langsung mengeluarkan penyederhanaan aljabar parsial linear.


$$17. \quad (a-b)(2a^3-ab+3b^2)$$\>& powerdisp: true;

\>$ radcan((a-b)\*(2\*a^3-a\*b+3\*b^2))


$$2\,a^4+\left(-a^2-2\,a^3\right)\,b+4\,a\,b^2-3\,b^3$$Mengaktifkan token powerdisp membalikkan orientasi barisan tampilan derajat dari naik (ascending)
atau turun.


$$47. \quad (a^n+b^n)(a^n-b^n)$$\>$ radcan((a^n+b^n)\*(a^n-b^n))


$$a^{2\,n}-b^{2\,n}$$$$49. \quad (a^n+b^n)^2$$\>$ radcan((a^n+b^n)^2)


$$a^{2\,n}+2\,a^{n}\,b^{n}+b^{2\,n}$$$$54. \quad (t^{m+n})^{m+n}\cdot (t^{m-n})^{m-n}$$\>$ radcan((t^(m+n))^(m+n)\*(t^(m-n))^(m-n))


$$t^{2\,m^2+2\,n^2}$$$$55. \quad (a+b+c)^2$$\>$ radcan((a+b+c)^2)


$$a^2+2\,a\,b+b^2+\left(2\,a+2\,b\right)\,c+c^2$$Set Latihan R.4


Ekstraksi titik potong dan distribusi ulang via operasi faktorisasi:


$$56. \quad 25ab^4-25az^4$$\>$ factor(25\*a\*b^4-25\*a\*z^4)


$$-25\,a\,\left(a-b+b\,i\right)\,\left(a+b+b\,i\right)\,\left(a^2+b^2  +2\,a\,b\,i+b^2\,i^2\right)$$Perintah factor() mendeteksi celah perkalian skalar, lalu memecah nilai persamaan menuju irisan
linier paling minimum.


$$66. \quad 5a^2-10ab+5b^2$$\>$ factor(5\*a^2-10\*a\*b+5\*b^2)


$$5\,\left(-a+b\right)^2$$$$76. \quad 27x^6-8$$\>$ factor(27\*x^6-8)


$$\left(-2+3\,x^2\right)\,\left(4+6\,x^2+9\,x^4\right)$$$$136. \quad bdy^2+ady+bcy+ac$$\>$ factor(b\*d\*y^2+a\*d\*y+b\*c\*y+a\*c)


$$\left(a+b\,y\right)\,\left(c+d\,y\right)$$$$137. \quad 25y^{2m}-(x^{2n}-2x^n+1)$$\>$ factor(25\*y^(2\*m)-(x^(2\*n)-2\*x^n+1))


$$\left(1-x^{n}+5\,y^{m}\right)\,\left(-1+x^{n}+5\,y^{m}\right)$$Set Latihan R.5


Menemukan akar-akar kuadrat:


$$60. \quad 5x^2-75=0$$\>$ solve(5\*x^2-75=0,x)


$$\left[ x=-\sqrt{15} , x=\sqrt{15} \right] $$Menyederhanakan subjek rumus spesifik, misal perumusan fisika / luas segitiga mencari tumpuan alas b:


$$61. \quad A=\frac{1}{2}bh,\quad for\quad b$$\>$ solve(A=(1/2)\*b\*h, b)


$$\left[ \begin{pmatrix}\frac{2-b\,h}{2} & \frac{80143857-12755291\,b  \,h}{25510582} \\ \frac{8-b\,h}{2} & \frac{10-b\,h}{2} \\   \end{pmatrix}=0 \right] $$$$63. \quad P=2l+2w,\quad for\quad w$$\>$ solve(P=2\*l+2\*w, w)


$$\left[ w=\frac{-2\,l+P}{2} \right] $$Mengisolasi persamaan ke koordinat intersep sumbu standar f(x)=y:


$$70. \quad Ax+By=C,\quad for\quad y$$\>$ solve(A\*x+B\*y=C,y)


$$\left[ \begin{pmatrix}x+y-C & \frac{80143857\,x+51021164\,y-  25510582\,C}{25510582} \\ 4\,x+3\,y-C & 5\,x+4\,y-C \\ \end{pmatrix}=  0 \right] $$$$86. \quad (3x^2+7x-20)(x^2-4x)=0$$\>$ solve((3\*x^2+7\*x-20)\*(x^2-4\*x)=0, x)


$$\left[ x=\frac{5}{3} , x=-4 , x=0 , x=4 \right] $$Set Latihan R.6


Mengeksekusi penyerderhanaan fungsi silang secara tuntas berkat bantuan radcan():


$$18. \quad \frac{x^2-y^2}{(x-y)^2} \cdot \frac{1}{x+y}$$\>$ radcan((x^2-y^2)/((x-y)^2)/(x+y))


$$-\frac{1}{-x+y}$$$$68. \quad \frac{\frac{1-x}{x}+\frac{x}{1+x}}{\frac{1+x}{x}+\frac{x}{1-x}}$$\>$ radcan(((1-x)/x+x/(1+x))/((1+x)/x+x/(1-x)))


$$\frac{1-x}{1+x}$$$$75. \quad \left[\frac{\frac{x+1}{x-1}+1}{\frac{x+1}{x-1}-1}\right]^5$$\>$ radcan((((x+1)/(x-1)+1)/((x+1)/(x-1)-1))^5)


$$x^5$$Pecahan rumit (termasuk bersarang) diproses langsung ke wujud akar tunggalnya (x^5).


$$76. \quad 1+\frac{1}{1+\frac{1}{1+\frac{1}{1+\frac{1}{x}}}}$$\>$ radcan(1+(1)/(1+(1)/(1+(1)/(1+(1)/x))))


$$\frac{3+5\,x}{2+3\,x}$$Penggunaan bersama metode faktorisasi terhadap fraksi eksponensial panjang demi menyusun format
paling enak dipandang.


$$77. \quad \frac{n(n+1)(n+2}{2\cdot 3}+\frac{(n+1)(n+2)}{2}$$\>$ factor(radcan((n\*(n+1)\*(n+2)/(2\*3)+((n+1)\*(n+2))/(2))))


$$\frac{\left(1+n\right)\,\left(2+n\right)\,\left(3+n\right)}{6}$$Set Latihan 2.3


Diketahui


$$f(x)=3x+1$$$$g(x)=x^2-2x-6$$$$h(x)=x^3$$

Tentukan operasi substitusi silang


$$7. \quad f(h(-3))$$\>function f(x) &=3\*x+1; $'f(x)=f(x); ...  
\>   function g(x) &=x^2-2\*x-6; $'g(x)=g(x); ...  
\>   function h(x) &=x^3; $'h(x)=h(x);

\>f(h(-3))


         -80.00 

Mekanisme internal akan menghitung lapis bagian terdalam fungsi terlebih dahulu sebelum
disubstitusikan utuh mengarah ke wujud kulit perumusan akhir.


$$15. \quad h(h(x))$$\>$h(h(x))


$$x^9$$Penentuan batas interval (domain validity).


$$f(g(x)), g(f(x))$$

dan domain


$$27. \quad f(x)=2x+1, g(x)=\sqrt{x}$$\>function f(x)&=2\*x+1; $'f(x)=f(x); ...  
\>   function g(x)&=sqrt(x); $'g(x)=g(x);

\>$f(g(x))


$$1+2\,\sqrt{x}$$Jelas bahwa rentang interval akar tidak menerima limit rasional minus. Domain terkunci di ambang


$$\{x\ge 0|x\in \mathbb{R} \}$$\>$g(f(x))


$$\sqrt{1+2\,x}$$Dengan memisahkan ruas di dalam kurung kurawal, diperoleh pertidaksamaan linier batas riil.


$$1+2x\ge 0$$

sehingga domain bergeser ke:


$$\left\{x\ge -\frac{1}{2}\|x\in \mathbb{R}\right\}$$Mencari fungsi komponen pembentuk.


$$43. \quad h(x)=\frac{x^3-1}{x^3+1}$$\>function h(x)&=(x^3-1)/(x^3+1);

\>// Ambil f(x)=(x-1)/(x+1) dan g(x)=x^3;

\>function f(x)&=(x-1)/(x+1); ...  
\>   function g(x)&=x^3;

\>&is(f(g(x))=h(x))


    
                                                    true
    

Uji komparasi logikal boolean antara dua buah ruas secara absolut menggunakan perintah khusus "is()"
memvalidasi temuan aljabar.


\>&kill(f,g,h)


    
                                                    done
    

$$h(x)=2(x-1)^{\frac{5}{3}}+5(x-1)^{\frac{2}{3}}$$\>function h(x)&=2\*(x-1)^(5/3)+5\*(x-1)^(2/3);


Ambil


$$f(x)=2x^{\frac{5}{3}}+5x^{\frac{2}{3}}$$$$g(x)=x-1$$\>function f(x)&=2\*x^(5/3)+5\*x^(2/3);...  
\>   function g(x)&=x-1;

\>&is(h(x)=f(g(x)))


    
                                                    true
    

Set Latihan 3.1


Menyederhanakan penambahan/pengurangan besaran bilangan imajiner:


$$18. \quad (-5-i)+(6+2i)$$\>&((-5-%i)+(6+2\*%i))


    
                                                    1 + I
    

Huruf %i bertindak menyambung sintaks memori alokasi konstan Maxima untuk simbol bilangan imajiner
(I).


$$20. \quad (7-\sqrt{-36})+(2+\sqrt{-9})$$\>&((7-sqrt(-36))+(2+sqrt(-9)))


    
                                                   9 - 3 I
    

$$66. \quad \frac{i}{2+i}$$\>&rectform(%i/(2+%i))


    
                                                   1   2 I
                                                   - + ---
                                                   5    5
    

Perintah rectform() merasionalkan dominasi bentuk silang akar di bagian penyebut secara independen.


$$76. \quad \frac{1-i}{(1+i)^2}$$\>&rectform((1-%i)/((1+%i)^2))


    
                                                     1   I
                                                   - - - -
                                                     2   2
    

$$78. \quad \frac{3+2i}{1-i}+\frac{6+2i}{1-i}$$\>&rectform((3+2\*%i)/(1-%i)+(6+2\*%i)/(1-%i))


    
                                                  5   13 I
                                                  - + ----
                                                  2    2
    

Set Latihan 3.2


Mencari himpunan kuadrat sejati:


$$56. \quad 3x^2+3x=-4$$\>$solve(3\*x^2+3\*x=-4,x)


$$\left[ x=\frac{-3-\sqrt{39}\,i}{6} , x=\frac{-3+\sqrt{39}\,i}{6}   \right] $$$$85. \quad x-3\sqrt{x}-4=0$$\>$solve(x-3\*sqrt(x)-4=0,x)


$$\left[ x=4+3\,\sqrt{x} \right] $$Jika algoritma Maxima gagal menemukan presisi penyeimbang karena halangan pangkat setengah,
aplikasikan manual pemisalan subyek.


$$a=\sqrt{x}$$

sehingga persamaan disederhanakan murni menjadi:


$$a^2-3a-4=0$$\>$solve(a^2-3\*a-4=0)


$$\left[ a=4 , a=-1 \right] $$diperoleh


$$\left[x=2,x=i\right]$$$$90. \quad x^{\frac{1}{2}}-4x^{\frac{1}{4}}=-3$$\>$solve(x^(1/2)-4\*x^(1/4)=-3,x)


$$\left[ \sqrt{x}=-3+4\,x^{\frac{1}{4}} \right] $$Kembali lagi pemisalan rasional dibutuhkan.


$$a=x^{\frac{1}{4}}$$

sehingga persamaan direduksi drastis:


$$a^2-4a=-3$$\>$solve(a^2-4\*a=-3,a)


$$\left[ a=3 , a=1 \right] $$diperoleh


$$\left[x=3^\frac{1}{4},x=1\right]$$$$126. \quad (x+1)^3=(x-1)^3+26$$\>$solve((x+1)^3=(x-1)^3+26,x)


$$\left[ x=-2 , x=2 \right] $$$$133. \quad \sqrt{x-3}-\sqrt[4]{x-3}=2$$\>$solve(sqrt(x-3)-(x-3)^(1/4)=2,x)


$$\left[ \sqrt{-3+x}=2+\left(-3+x\right)^{\frac{1}{4}} \right] $$Modifikasi pemisalan:


$$a=\sqrt[4]{x-3}$$

menghasilkan:


$$a^2-a=2$$\>$solve(a^2-a=2,a)


$$\left[ a=2 , a=-1 \right] $$\>$solve((x-3)^(1/4)=2), $solve((x-3)^(1/4)=-1)


$$\left[ \left(-3+x\right)^{\frac{1}{4}}=-1 \right] $$![images/Tugas%202-279.png](images/Tugas%202-279.png)

\>$rectform(solve(-3+x=(-1)^(1/4),x))


$$\left[ x=3+\frac{1}{\sqrt{2}}+\frac{i}{\sqrt{2}} \right] $$Set Latihan 3.4


$$10. \quad x-\frac{12}{x}=1$$\>$solve(x-12/x=1,x)


$$\left[ x=-3 , x=4 \right] $$Menangani persamaan ruas pecah silang melalui simplifikasi lintasan gabungan dari solver.


$$28. \quad \frac{1}{x-15}-\frac{1}{x}=\frac{15}{x^2-15x}$$\>$solve(ratsimp(1/(x-15)-1/x=15/(x^2-15\*x)),x)


$${\it all}$$$$70. \quad \sqrt{4p+5}+\sqrt{p+5}=3$$\>$solve(sqrt(4\*p+5)+sqrt(p+5)=3,p)


$$\left[ \sqrt{5+4\,p}=3-\sqrt{5+p} \right] $$Pendekatan manual substitusi akar ganda ke kanan dan kiri, untuk selanjutnya merasionalkannya ke
pangkat bulat.


$$4p+5=9-6\sqrt{p+5}+(p+5)$$$$p-3=-2\sqrt{p+5}$$

kuadratkan kedua ruas, diperoleh


$$p^2-10p-11=0$$\>$solve(p^2-10\*p-11=0,p)


$$\left[ p=11 , p=-1 \right] $$$$94. \quad \frac{x+3}{x+2}-\frac{x+4}{x+3}=\frac{x+5}{x+4}-\frac{x+6}{x+5}$$\>$solve((x+3)/(x+2)-(x+4)/(x+3)=(x+5)/(x+4)-(x+6)/(x+5),x)


$$\left[ x=-\frac{7}{2} \right] $$$$96. \quad \sqrt{15+\sqrt{2x+80}}=5$$\>$solve(sqrt(15+sqrt(2\*x+80))=5,x)


$$\left[ x=10 \right] $$Set Latihan 3.5


Menghimpun rentang akar menggunakan metode pembatasan logikal ganda fourier.


$$23. \quad |x+3|-2=8$$\>&load(fourier\_elim)


    
            C:/Program Files/Euler x64/maxima/share/maxima/5.35.1/share/fourier_elim/fourier_elim.lisp
    

\>$fourier\_elim([abs(x+3)-2=8],[x])


$${\it emptyset}$$$$43. \quad |2x|\ge 6$$\>$fourier\_elim([abs(2\*x)\>=6],[x])


$$\left[ x=3 \right] \lor \left[ 3<x \right] $$Interval batas validasi dikumpulkan menuju satu rentang (x &gt; 3 / x &lt; -3).


$$60. \quad \left|\frac{2x-1}{3}\right|\ge \frac{5}{6}$$\>$fourier\_elim([abs((2\*x-1)/3)\>=5/6],[x])


$$\left[ x=-\frac{3}{4} \right] \lor \left[ x=\frac{7}{4} \right]   \lor \left[ x<-\frac{3}{4} \right] \lor \left[ \frac{7}{4}<x   \right] $$$$72. \quad |x+2|\le |x-5|$$\>$fourier\_elim([abs(x+2)<=abs(x-5)],[x])


$$\left[ x=\frac{3}{2} \right] \lor \left[ x=-2 \right] \lor \left[ -  2<x , x<\frac{3}{2} \right] \lor \left[ x<-2 \right] $$$$74. \quad |x|+|x+1|<10$$\>$fourier\_elim([abs(x)+abs(x+1)<10],[x])


$$\left[ x<\frac{9}{2} \right] $$Set Latihan 4.1


26. Pembuktian sisa pembagian 0 terhadap nilai kandidat intersep polinomial panjang.


$$g(x)=x^4-x^3-3x^2+5x-2$$\>function g(x)&=x^4-x^3-3\*x^3+5\*x-2;

\>g(1)


           0.00 

\>g(-2)


          36.00 

\>g(3)


         -14.00 

Dapat dipastikan bahwa 1 merupakan akar valid (menghasilkan nol) dari deretan kandidat polinomial.


Mencari ekstraksi titik x perpotongan fungsi


$$36. \quad (x^2-5x+6)^2$$\>$solve((x^2-5\*x+6)^2=0,x)


$$\left[ x=3 , x=2 \right] $$54. Penerapan substitusi estimasi polinomial derajat 4.


$$-0.006093x^4+0.849362x^3-51.892087x^2+1627.3581x+41334.7289$$\>&kill(f); function f(x)&=-0.006093\*x^4+0.849362\*x^3-51.892087\*x^2+1627.3581\*x+41334.7289;

\>f(1945-1940)


       48276.58 

\>f(1985-1940)


       61897.37 

\>f(2008-1940)


       48835.94 

Mengekspansi domain sejati pertidaksamaan silang linier ke kuadratik menggunakan eliminasi Fourier.


$$61. \quad 2y-3\ge 1-y+5$$\>$fourier\_elim([2\*y-3\>=1-y+5],[y])


$$\left[ y=3 \right] \lor \left[ 3<y \right] $$$$62. \quad (x-2)(x+5)>x(x-3)$$\>$fourier\_elim([(x-2)\*(x+5)\>x\*(x-3)],[x])


$$\left[ \frac{5}{3}<x \right] $$Set Latihan 4.3


Pembuktian sisa faktorial bagi habis.


$$3. \quad g(x)=x^3-2x^2-11x+12$$\>$factor(x^3-2\*x^2-11\*x+12)


$$\left(-4+x\right)\,\left(-1+x\right)\,\left(3+x\right)$$Jelas bahwa hanya (x-4) dan (x-1) yang merupakan faktor bagi genap dari kelompok fungsi g.


Merinci hasil bagi beserta sisanya:


$$19. \quad (x^4-1)\div (x-1)$$\>$factor(x^4-1)


$$\left(-1+x\right)\,\left(1+x\right)\,\left(1+x^2\right)$$Membuktikan bahwa hasil reduksinya mencapai rentang:


$$(x^2+1)(x+1)$$

yang berakhir sisa modulus eksak bernilai 0.


30. Substitusi berantai dan eksekusi plot2d untuk membangkitkan grafik di kanvas bidang rasional
(Cartesius).


$$f(x)=x^5$$\>&kill(f); function f(x)&=x^5;

\>f(2)


          32.00 

\>f(-2)


         -32.00 

\>f(3)


         243.00 

\>&f(2+3\*%i)


    
                                                          5
                                                 (2 + 3 I)
    

\>plot2d("f(x)",-3,3):


![images/Tugas%202-319.png](images/Tugas%202-319.png)

$$54. \quad -x^4+2x^3+3x^2-4x-4$$\>&kill(f); function f(x)&=-x^4+2\*x^3+3\*x^2-4\*x-4; plot2d("f(x)",-5,5):


![images/Tugas%202-321.png](images/Tugas%202-321.png)

Mengoperasikan pembagian panjang bersarang yang mencakup besaran domain Imajiner (i).


$$71. \quad (x^3+3ix^2-4ix-2)\div(x+i)$$\>&divide(x^3+3\*%i\*x^2-4\*%i\*x-2, x+%i, x)


    
                                                          2
                                      [2 - 4 I + 2 I x + x , - 6 - 2 I]
    

divide(f(x), g(x), x) mengembalikan kombinasi dua ruas bertipe [hasil hitung sejati, modulus (sisa)
bagi] secara konsisten. Jadi, hasil baginya adalah


$$x^2+2ix-4i+2$$

dan sisanya adalah -6 -2i.


