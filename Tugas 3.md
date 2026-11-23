# Menggambar Grafik 2D dengan EMT
Notebook ini menjelaskan tentang cara menggambar berbagai kurva dan grafik 2D dengan software EMT.
EMT menyediakan fungsi plot2d() untuk menggambar berbagai kurva dan grafik dua dimensi (2D).


## Plot Dasar

Terdapat fungsi-fungsi plot yang sangat dasar. Terdapat koordinat layar, yang selalu memiliki rentang
dari 0 hingga 1024 di setiap sumbunya, tidak peduli apakah layarnya persegi atau tidak. Dan ada
koordinat plot, yang dapat diatur dengan setplot(). Pemetaan antara koordinat-koordinat tersebut
bergantung pada jendela plot saat ini. Contohnya, shrinkwindow() bawaan menyisakan ruang untuk label
sumbu dan judul plot.


Pada contoh ini, kita hanya menggambar beberapa garis acak dengan berbagai warna. Untuk detail
mengenai fungsi-fungsi ini, pelajari fungsi-fungsi inti dari EMT.


\>clg; // bersihkan layar

\>window(0,0,1024,1024); // gunakan seluruh jendela

\>setplot(0,1,0,1); // atur koordinat plot

\>hold on; // mulai mode timpa (overwrite)

\>n=100; X=random(n,2); Y=random(n,2);  // dapatkan titik-titik acak

\>colors=rgb(random(n),random(n),random(n)); // dapatkan warna acak

\>loop 1 to n; color(colors[#]); plot(X[#],Y[#]); end; // gambar plot

\>hold off; // akhiri mode timpa

\>insimg; // sisipkan ke notebook


![images/Tugas%203-001.png](images/Tugas%203-001.png)

\>reset;


Grafik perlu ditahan (hold), karena perintah plot() akan membersihkan jendela plot.


Untuk menghapus semua yang telah kita buat, kita menggunakan reset().


Untuk menampilkan gambar hasil plot di layar notebook, perintah plot2d() dapat diakhiri dengan titik
dua (:). Cara lain adalah perintah plot2d() diakhiri dengan titik koma (;), kemudian menggunakan
perintah insimg() untuk menampilkan gambar hasil plot.


Sebagai contoh lain, kita menggambar plot sebagai sisipan (inset) di dalam plot lain. Hal ini
dilakukan dengan mendefinisikan jendela plot yang lebih kecil. Perhatikan bahwa jendela ini tidak
menyediakan ruang untuk label sumbu di luar jendela plot. Kita harus menambahkan sedikit margin untuk
ini sesuai kebutuhan. Perhatikan bahwa kita menyimpan dan mengembalikan jendela penuh, dan menahan
plot saat ini sementara kita menggambar sisipan tersebut.


\>plot2d("x^3");

\>xw=200; yw=100; ww=300; hw=300;

\>ow=window();

\>window(xw,yw,xw+ww,yw+hw);

\>hold on;

\>barclear(xw-50,yw-10,ww+60,ww+60);

\>plot2d("x^4-x",grid=6):


![images/Tugas%203-002.png](images/Tugas%203-002.png)

\>hold off;

\>window(ow);


Plot dengan banyak figur (gambar) dicapai dengan cara yang sama. Terdapat fungsi utilitas figure()
untuk melakukan hal ini.


## Aspek Plot

Plot bawaan menggunakan jendela plot persegi. Anda dapat mengubahnya dengan fungsi aspect(). Jangan
lupa untuk mereset aspeknya nanti. Anda juga dapat mengubah nilai bawaan ini di menu dengan "Set
Aspect" ke rasio aspek tertentu atau ke ukuran saat ini dari jendela grafis.


Namun Anda juga dapat mengubahnya hanya untuk satu plot. Untuk ini, ukuran saat ini dari area plot
akan diubah, dan jendela diatur sedemikian rupa sehingga label memiliki ruang yang cukup.


\>aspect(2); // rasio panjang dan lebar 2:1

\>plot2d(["sin(x)","cos(x)"],0,2pi):


![images/Tugas%203-003.png](images/Tugas%203-003.png)

\>aspect();

\>reset;


Fungsi reset() mengembalikan pengaturan bawaan plot termasuk rasio aspeknya.


# Plot 2D di Euler

EMT Math Toolbox memiliki plot dalam 2D, baik untuk data maupun fungsi. EMT menggunakan fungsi
plot2d. Fungsi ini dapat menggambar fungsi dan data.


Dimungkinkan juga untuk melakukan plot di Maxima menggunakan Gnuplot atau di Python menggunakan Math
Plot Lib.


Euler dapat menggambar plot 2D dari


* 
ekspresi

* 
fungsi, variabel, atau kurva terparameterisasi,

* 
vektor nilai x-y,

* 
sekumpulan titik di bidang,

* 
kurva implisit dengan level atau rentang level.

* 
Fungsi kompleks


Gaya plot mencakup berbagai gaya untuk garis dan titik, plot batang, dan plot berbayang (shaded).


# Plot Ekspresi atau Variabel

Sebuah ekspresi tunggal dalam "x" (misalnya "4*x^2") atau nama sebuah fungsi (misalnya "f")
menghasilkan grafik dari fungsi tersebut.


Berikut adalah contoh paling dasar, yang menggunakan rentang bawaan dan mengatur rentang-y yang tepat
agar sesuai dengan plot fungsinya.


Catatan: Jika Anda mengakhiri baris perintah dengan titik dua ":", plot akan disisipkan ke dalam
jendela teks. Jika tidak, tekan TAB untuk melihat plot jika jendela plot tertutup.


\>plot2d("x^5"):


![images/Tugas%203-004.png](images/Tugas%203-004.png)

\>aspect(1.5); plot2d("x^3-x+x^2"):


![images/Tugas%203-005.png](images/Tugas%203-005.png)

\>a:=5.6; plot2d("exp(-a\*x^2)/a"); insimg(30); // menampilkan gambar hasil plot setinggi 25 baris


![images/Tugas%203-006.png](images/Tugas%203-006.png)

Dari beberapa contoh sebelumnya Anda dapat melihat bahwa aslinya gambar plot menggunakan sumbu X
dengan rentang nilai dari -2 sampai dengan 2. Untuk mengubah rentang nilai X dan Y, Anda dapat
menambahkan nilai-nilai batas X (dan Y) di belakang ekspresi yang digambar.


Rentang plot diatur dengan parameter-parameter yang ditetapkan berikut ini


* 
a,b: rentang-x (bawaan -2,2)

* 
c,d: rentang-y (bawaan: skala mengikuti nilai)

* 
r: sebagai alternatif, radius di sekitar pusat plot

* 
cx,cy: koordinat pusat plot (bawaan 0,0)


\>plot2d("x^3-x",-1,2):


![images/Tugas%203-007.png](images/Tugas%203-007.png)

\>plot2d("sin(x)",-2\*pi,2\*pi): // plot sin(x) pada interval [-2pi, 2pi]


![images/Tugas%203-008.png](images/Tugas%203-008.png)

\>plot2d("cos(x)","sin(3\*x)",xmin=0,xmax=2pi):


![images/Tugas%203-009.png](images/Tugas%203-009.png)

Alternatif dari tanda titik dua adalah perintah insimg(lines), yang menyisipkan plot dengan menempati
jumlah baris teks yang ditentukan.


Pada opsi-opsi yang ada, plot dapat diatur agar muncul


* 
di jendela terpisah yang dapat diubah ukurannya,

* 
di jendela notebook.


Lebih banyak gaya dapat dicapai dengan perintah-perintah plot yang spesifik.


Bagaimanapun, tekan tombol tabulator untuk melihat plot, jika plot tersebut tersembunyi.


Untuk membagi jendela menjadi beberapa plot, gunakan perintah figure(). Pada contoh ini, kita
menggambar x^1 hingga x^4 ke dalam 4 bagian jendela. figure(0) mereset ke jendela bawaan.


\>reset;

\>figure(2,2); ...  
\>   for n=1 to 4; figure(n); plot2d("x^"+n); end; ...  
\>   figure(0):


![images/Tugas%203-010.png](images/Tugas%203-010.png)

Di plot2d(), terdapat gaya alternatif yang tersedia dengan grid=x. Sebagai gambaran, kita menampilkan
berbagai gaya grid dalam satu figur (lihat di bawah untuk perintah figure()). Gaya grid=0 tidak
disertakan. Gaya tersebut tidak menampilkan grid dan bingkai.


\>figure(3,3); ...  
\>   for k=1:9; figure(k); plot2d("x^3-x",-2,1,grid=k); end; ...  
\>   figure(0):


![images/Tugas%203-011.png](images/Tugas%203-011.png)

Jika argumen pada plot2d() adalah ekspresi yang diikuti oleh empat angka, angka-angka ini merupakan
rentang x dan y untuk plot tersebut.


Secara alternatif, a, b, c, d dapat ditentukan sebagai parameter yang ditetapkan seperti a=... dst.


Pada contoh berikut, kita mengubah gaya grid, menambahkan label, dan menggunakan label vertikal untuk
sumbu y.


\>aspect(1.5); plot2d("sin(x)",0,2pi,-1.2,1.2,grid=3,xl="x",yl="sin(x)"):


![images/Tugas%203-012.png](images/Tugas%203-012.png)

\>plot2d("sin(x)+cos(2\*x)",0,4pi):


![images/Tugas%203-013.png](images/Tugas%203-013.png)

Gambar yang dihasilkan dengan menyisipkan plot ke dalam jendela teks disimpan di direktori yang sama
dengan notebook, secara default berada di subdirektori bernama "images". Gambar-gambar tersebut juga
digunakan oleh ekspor HTML.


Anda cukup menandai gambar apa pun dan menyalinnya ke clipboard dengan Ctrl-C. Tentu saja, Anda juga
dapat mengekspor grafik saat ini dengan fungsi-fungsi di menu File.


Fungsi atau ekspresi di plot2d dievaluasi secara adaptif. Untuk kecepatan lebih, matikan plot adaptif
dengan &lt;adaptive dan tentukan jumlah subinterval dengan n=... Ini hanya diperlukan pada kasus-kasus
yang jarang terjadi.


\>plot2d("sign(x)\*exp(-x^2)",-1,1,<adaptive,n=10000):


![images/Tugas%203-014.png](images/Tugas%203-014.png)

\>plot2d("x^x",r=1.2,cx=1,cy=1):


![images/Tugas%203-015.png](images/Tugas%203-015.png)

Perhatikan bahwa x^x tidak terdefinisi untuk x&lt;=0. Fungsi plot2d menangkap error ini, dan mulai
menggambar segera setelah fungsinya terdefinisi. Ini berlaku untuk semua fungsi yang mengembalikan
NAN di luar rentang definisinya.


\>plot2d("log(x)",-0.1,2):


![images/Tugas%203-016.png](images/Tugas%203-016.png)

Parameter square=true (atau &gt;square) memilih rentang-y secara otomatis sehingga hasilnya adalah
jendela plot berbentuk persegi. Perhatikan bahwa secara default, Euler menggunakan ruang persegi di
dalam jendela plot.


\>plot2d("x^3-x",\>square):


![images/Tugas%203-017.png](images/Tugas%203-017.png)

\>plot2d(''integrate("sin(x)\*exp(-x^2)",0,x)'',0,2): // gambar plot integral


![images/Tugas%203-018.png](images/Tugas%203-018.png)

Jika Anda membutuhkan lebih banyak ruang untuk label-y, panggil shrinkwindow() dengan parameter yang
lebih kecil, atau tetapkan nilai positif untuk "smaller" di plot2d().


\>plot2d("gamma(x)",1,10,yl="y-values",smaller=6,<vertical):


![images/Tugas%203-019.png](images/Tugas%203-019.png)

Ekspresi simbolik juga dapat digunakan, karena mereka disimpan sebagai ekspresi string sederhana.


\>x=linspace(0,2pi,1000); plot2d(sin(5x),cos(7x)):


![images/Tugas%203-020.png](images/Tugas%203-020.png)

\>a:=5.6; expr &= exp(-a\*x^2)/a; // definisikan ekspresi

\>plot2d(expr,-2,2): // gambar plot dari -2 hingga 2


![images/Tugas%203-021.png](images/Tugas%203-021.png)

\>plot2d(expr,r=1,thickness=2): // gambar plot dalam persegi di sekitar (0,0)


![images/Tugas%203-022.png](images/Tugas%203-022.png)

\>plot2d(&diff(expr,x),\>add,style="--",color=red): // tambahkan plot lain


![images/Tugas%203-023.png](images/Tugas%203-023.png)

\>plot2d(&diff(expr,x,2),a=-2,b=2,c=-2,d=1): // gambar plot dalam persegi panjang


![images/Tugas%203-024.png](images/Tugas%203-024.png)

\>plot2d(&diff(expr,x),a=-2,b=2,\>square): // pertahankan plot berbentuk persegi


![images/Tugas%203-025.png](images/Tugas%203-025.png)

\>plot2d("x^2",0,1,steps=1,color=red,n=10):


![images/Tugas%203-026.png](images/Tugas%203-026.png)

\>plot2d("x^2",\>add,steps=2,color=blue,n=10):


![images/Tugas%203-027.png](images/Tugas%203-027.png)

# Fungsi dengan satu Parameter

Fungsi plot terpenting untuk plot planar adalah plot2d(). Fungsi ini diimplementasikan dalam bahasa
Euler di file "plot.e", yang dimuat pada saat memulai program.


Berikut adalah beberapa contoh penggunaan fungsi. Seperti biasa di EMT, untuk fungsi-fungsi yang
bekerja pada fungsi atau ekspresi lain, Anda dapat memberikan parameter tambahan (selain x) yang
bukan merupakan variabel global ke fungsi tersebut dengan parameter titik koma atau dengan kumpulan
pemanggilan (call collection).


\>plot2d("x^2-4\*x+3", -5, 5):


![images/Tugas%203-028.png](images/Tugas%203-028.png)

\>plot2d("x^5-10\*x^3+6\*x^2-1100", -75, 75):


![images/Tugas%203-029.png](images/Tugas%203-029.png)

\>function h(x)&= cos(x^2-1);


\>plot2d("h", -10, 10):


![images/Tugas%203-030.png](images/Tugas%203-030.png)

\>plot2d("h", -5, 5):


![images/Tugas%203-031.png](images/Tugas%203-031.png)

\>plot2d("h", -100, 100):


![images/Tugas%203-032.png](images/Tugas%203-032.png)

\>function r(y)&=cos(6\*y);

\>plot2d("r",-10,10):


![images/Tugas%203-033.png](images/Tugas%203-033.png)

\>function f(x,a) := x^2/a+a\*x^2-x; // definisikan sebuah fungsi


Berikut adalah ringkasan dari fungsi-fungsi yang diterima


* 
ekspresi atau ekspresi simbolik dalam x

* 
fungsi atau fungsi simbolik berdasarkan nama seperti "f"

* 
fungsi simbolik hanya dengan nama f


Fungsi plot2d() juga menerima fungsi simbolik. Untuk fungsi simbolik, namanya saja sudah berfungsi.


\>function f(x) &= diff(x^x,x)


    
                                                x
                                               x  (log(x) + 1)
    

\>plot2d(f,0,2):


![images/Tugas%203-034.png](images/Tugas%203-034.png)

Tentu saja, untuk ekspresi atau ekspresi simbolik, nama variabelnya sudah cukup untuk menggambarnya.


\>expr &= sin(x)\*exp(-x)


    
                                                  - x
                                                 E    sin(x)
    

\>plot2d(expr,0,3pi):


![images/Tugas%203-035.png](images/Tugas%203-035.png)

\>function f(x) &= x^x;

\>plot2d(f,r=1,cx=1,cy=1,color=blue,thickness=2);

\>plot2d(&diff(f(x),x),\>add,color=red,style="-.-"):


![images/Tugas%203-036.png](images/Tugas%203-036.png)

Untuk gaya garis terdapat berbagai opsi.


* 
style="...". Pilih dari "-", "--", "-.", ".", ".-.", "-.-".

* 
color: Lihat di bawah untuk warna.

* 
thickness: Nilai bawaan adalah 1.


Warna dapat dipilih sebagai salah satu warna bawaan, atau sebagai warna RGB.


* 
0..15: indeks warna bawaan.

* 
konstanta warna: white, black, red, green, blue, cyan, olive, lightgray, gray, darkgray, orange,
* lightgreen, turquoise, lightblue, lightorange, yellow

* 
rgb(red,green,blue): parameternya adalah bilangan real di [0,1].


\>plot2d("exp(-x^2)",r=2,color=red,thickness=3,style="--"):


![images/Tugas%203-037.png](images/Tugas%203-037.png)

Berikut adalah tampilan warna-warna yang telah ditentukan sebelumnya di EMT.


\>aspect(2); columnsplot(ones(1,16),lab=0:15,grid=0,color=0:15):


![images/Tugas%203-038.png](images/Tugas%203-038.png)

Namun Anda dapat menggunakan warna apa saja.


\>columnsplot(ones(1,16),grid=0,color=rgb(0,0,linspace(0,1,15))):


![images/Tugas%203-039.png](images/Tugas%203-039.png)

# Menggambar Beberapa Kurva pada bidang koordinat yang sama

Menggambar lebih dari satu fungsi (fungsi ganda) ke dalam satu jendela dapat dilakukan dengan
berbagai cara. Salah satu metodenya adalah menggunakan &gt;add untuk beberapa pemanggilan plot2d di
seluruh pemanggilan, kecuali pemanggilan pertama. Kita sudah menggunakan fitur ini pada contoh-contoh
di atas.


\>aspect(); plot2d("cos(x)",r=2,grid=6); plot2d("x",style=".",\>add):


![images/Tugas%203-040.png](images/Tugas%203-040.png)

\>aspect(1.5); plot2d("sin(x)",0,2pi); plot2d("cos(x)",color=blue,style="--",\>add):


![images/Tugas%203-041.png](images/Tugas%203-041.png)

Salah satu kegunaan &gt;add adalah untuk menambahkan titik pada kurva.


\>plot2d("sin(x)",0,pi); plot2d(2,sin(2),\>points,\>add):


![images/Tugas%203-042.png](images/Tugas%203-042.png)

Kita menambahkan titik potong beserta labelnya (pada posisi "cl" untuk kiri tengah/center left), dan
menyisipkan hasilnya ke dalam notebook. Kita juga menambahkan judul pada plot tersebut.


\>plot2d(["cos(x)","x"],r=1.1,cx=0.5,cy=0.5, ...  
\>     color=[black,blue],style=["-","."], ...  
\>     grid=1);

\>x0=solve("cos(x)-x",1);  ...  
\>     plot2d(x0,x0,\>points,\>add,title="Intersection Demo");  ...  
\>     label("cos(x) = x",x0,x0,pos="cl",offset=20):


![images/Tugas%203-043.png](images/Tugas%203-043.png)

Pada demo berikut, kita menggambar fungsi sinc(x)=sin(x)/x beserta ekspansi Taylor ke-8 dan ke-16
nya. Kita menghitung ekspansi ini menggunakan Maxima melalui ekspresi simbolik.


Plot ini dilakukan pada perintah multi-baris berikut dengan tiga pemanggilan plot2d(). Pemanggilan
kedua dan ketiga memiliki flag &gt;add yang disetel, yang membuat plot-plot tersebut menggunakan rentang
dari plot sebelumnya.


Kita menambahkan kotak label untuk menjelaskan fungsi-fungsi tersebut.


\>$taylor(sin(x)/x,x,0,4)


$$\frac{x^4}{120}-\frac{x^2}{6}+1$$\>plot2d("sinc(x)",0,4pi,color=green,thickness=2); ...  
\>     plot2d(&taylor(sin(x)/x,x,0,8),\>add,color=blue,style="--"); ...  
\>     plot2d(&taylor(sin(x)/x,x,0,16),\>add,color=red,style="-.-"); ...  
\>     labelbox(["sinc","T8","T16"],styles=["-","--","-.-"], ...  
\>       colors=[black,blue,red]):


![images/Tugas%203-045.png](images/Tugas%203-045.png)

Pada contoh berikut, kita menghasilkan Polinomial Bernstein.


$$B_i(x) = \binom{n}{i} x^i (1-x)^{n-i}$$\>plot2d("(1-x)^10",0,1); // gambar fungsi pertama

\>for i=1 to 10; plot2d("bin(10,i)\*x^i\*(1-x)^(10-i)",\>add); end;

\>insimg;


![images/Tugas%203-047.png](images/Tugas%203-047.png)

Metode kedua adalah menggunakan sepasang matriks nilai-x dan matriks nilai-y dengan ukuran yang sama.


Kita menghasilkan matriks nilai dengan satu Polinomial Bernstein di setiap barisnya. Untuk ini, kita
cukup menggunakan vektor kolom i. Silakan lihat bagian pengenalan tentang bahasa matriks untuk
mempelajari detail lebih lanjut.


\>x=linspace(0,1,500);

\>n=10; k=(0:n)'; // n adalah vektor baris, k adalah vektor kolom

\>y=bin(n,k)\*x^k\*(1-x)^(n-k); // maka y adalah sebuah matriks

\>plot2d(x,y):


![images/Tugas%203-048.png](images/Tugas%203-048.png)

Perhatikan bahwa parameter warna dapat berupa vektor. Maka setiap warna digunakan untuk setiap baris
dari matriks tersebut.


\>x=linspace(0,1,200); y=x^(1:10)'; plot2d(x,y,color=1:10):


![images/Tugas%203-049.png](images/Tugas%203-049.png)

Metode lainnya adalah menggunakan vektor ekspresi (string). Anda kemudian dapat menggunakan array
warna, array gaya, dan array ketebalan dengan panjang yang sama.


\>plot2d(["sin(x)","cos(x)"],0,2pi,color=4:5): 


![images/Tugas%203-050.png](images/Tugas%203-050.png)

\>plot2d(["sin(x)","cos(x)"],0,2pi): // gambar vektor ekspresi


![images/Tugas%203-051.png](images/Tugas%203-051.png)

Kita dapat memperoleh vektor semacam itu dari Maxima menggunakan makelist() dan mxm2str().


\>v &= makelist(binomial(10,i)\*x^i\*(1-x)^(10-i),i,0,10) // buat list


    
                    10            9              8  2             7  3             6  4
            [(1 - x)  , 10 (1 - x)  x, 45 (1 - x)  x , 120 (1 - x)  x , 210 (1 - x)  x , 
                              5  5             4  6             3  7            2  8              9   10
                   252 (1 - x)  x , 210 (1 - x)  x , 120 (1 - x)  x , 45 (1 - x)  x , 10 (1 - x) x , x  ]
    

\>mxm2str(v) // dapatkan vektor string dari vektor simbolik


    (1-x)^10
    10*(1-x)^9*x
    45*(1-x)^8*x^2
    120*(1-x)^7*x^3
    210*(1-x)^6*x^4
    252*(1-x)^5*x^5
    210*(1-x)^4*x^6
    120*(1-x)^3*x^7
    45*(1-x)^2*x^8
    10*(1-x)*x^9
    x^10

\>plot2d(mxm2str(v),0,1): // gambar fungsi-fungsi


![images/Tugas%203-052.png](images/Tugas%203-052.png)

Alternatif lain adalah menggunakan bahasa matriks Euler.


Jika sebuah ekspresi menghasilkan matriks fungsi, dengan satu fungsi di setiap baris, semua fungsi
ini akan digambar ke dalam satu plot.


Untuk ini, gunakan vektor parameter dalam bentuk vektor kolom. Jika array warna ditambahkan, warna
tersebut akan digunakan untuk setiap baris plot.


\>n=(1:10)'; plot2d("x^n",0,1,color=1:10):


![images/Tugas%203-053.png](images/Tugas%203-053.png)

Ekspresi dan fungsi satu baris dapat melihat variabel global.


Jika Anda tidak dapat menggunakan variabel global, Anda harus menggunakan fungsi dengan parameter
ekstra, dan memberikan parameter ini sebagai parameter titik koma.


Hati-hati, pastikan menaruh semua parameter yang ditetapkan ke bagian akhir perintah plot2d. Pada
contoh ini kita memberikan a=5 ke fungsi f, yang kita gambar dari -10 hingga 10.


\>function f(x,a) := 1/a\*exp(-x^2/a); ...  
\>   plot2d("f",-10,10;5,thickness=2,title="a=5"):


![images/Tugas%203-054.png](images/Tugas%203-054.png)

Sebagai alternatif, gunakan koleksi dengan nama fungsi dan semua parameter ekstra. Daftar khusus ini
disebut kumpulan pemanggilan (call collections), dan itu adalah cara yang disukai untuk meneruskan
argumen ke sebuah fungsi yang mana fungsi itu sendiri diteruskan sebagai argumen ke fungsi lain.


Pada contoh berikut, kita menggunakan perulangan (loop) untuk menggambar beberapa fungsi (lihat
tutorial tentang pemrograman perulangan for).


\>plot2d({{"f",1}},-10,10); ...  
\>   for a=2:10; plot2d({{"f",a}},\>add); end:


![images/Tugas%203-055.png](images/Tugas%203-055.png)

Kita bisa mencapai hasil yang sama dengan cara berikut menggunakan bahasa matriks EMT. Setiap baris
dari matriks f(x,a) adalah satu fungsi. Selain itu, kita dapat mengatur warna untuk setiap baris
matriks tersebut. Klik dua kali pada fungsi getspectral() untuk melihat penjelasannya.


\>x=-10:0.01:10; a=(1:10)'; plot2d(x,f(x,a),color=getspectral(a/10)):


![images/Tugas%203-056.png](images/Tugas%203-056.png)

## Label Teks

Dekorasi sederhana dapat berupa


* 
judul dengan title="..."

* 
label x dan y dengan xl="...", yl="..."

* 
label teks lainnya dengan label("...",x,y)


Perintah label akan menggambar di plot saat ini pada koordinat plot (x,y). Perintah ini dapat
mengambil argumen posisional.


\>plot2d("x^3-x",-1,2,title="y=x^3-x",yl="y",xl="x"):


![images/Tugas%203-057.png](images/Tugas%203-057.png)

\>expr := "log(x)/x"; ...  
\>     plot2d(expr,0.5,5,title="y="+expr,xl="x",yl="y"); ...  
\>     label("(1,0)",1,0); label("Max",E,expr(E),pos="lc"):


![images/Tugas%203-058.png](images/Tugas%203-058.png)

Terdapat juga fungsi labelbox(), yang dapat menampilkan fungsi-fungsi dan teks. Fungsi ini mengambil
vektor string dan warna, satu item untuk setiap fungsi.


\>function f(x) &= x^2\*exp(-x^2);  ...  
\>   plot2d(&f(x),a=-3,b=3,c=-1,d=1);  ...  
\>   plot2d(&diff(f(x),x),\>add,color=blue,style="--"); ...  
\>   labelbox(["function","derivative"],styles=["-","--"], ...  
\>      colors=[black,blue],w=0.4):


![images/Tugas%203-059.png](images/Tugas%203-059.png)

Kotak ini ditambatkan di kanan atas secara bawaan, namun &gt;left menambatkannya di kiri atas. Anda
dapat memindahkannya ke tempat mana pun yang Anda suka. Posisi tambatan adalah sudut kanan atas dari
kotak, dan angka-angkanya adalah pecahan dari ukuran jendela grafis. Lebarnya otomatis.


Untuk plot titik, kotak label juga berfungsi. Tambahkan parameter &gt;points, atau vektor bendera
(flags), satu untuk setiap label.


Pada contoh berikut, hanya terdapat satu fungsi. Jadi kita dapat menggunakan string daripada vektor
string. Kita mengatur warna teks menjadi hitam untuk contoh ini.


\>n=10; plot2d(0:n,bin(n,0:n),\>addpoints); ...  
\>   labelbox("Binomials",styles="[]",\>points,x=0.1,y=0.1, ...  
\>   tcolor=black,\>left):


![images/Tugas%203-060.png](images/Tugas%203-060.png)

Gaya plot ini juga tersedia di statplot(). Seperti di plot2d() warna dapat diatur untuk setiap baris
plot. Ada lebih banyak plot khusus untuk tujuan statistik (lihat tutorial tentang statistik).


\>statplot(1:10,random(2,10),color=[red,blue]):


![images/Tugas%203-061.png](images/Tugas%203-061.png)

Fitur yang serupa adalah fungsi textbox().


Lebarnya secara bawaan adalah lebar maksimal dari baris-baris teks. Tetapi ia juga dapat diatur oleh
pengguna.


\>function f(x) &= exp(-x)\*sin(2\*pi\*x); ...  
\>   plot2d("f(x)",0,2pi); ...  
\>   textbox(latex("\\text{Example of a damped oscillation}\\ f(x)=e^{-x}sin(2\\pi x)"),w=0.85):


![images/Tugas%203-062.png](images/Tugas%203-062.png)

Label teks, judul, kotak label, dan teks lainnya dapat berisi string Unicode (lihat sintaks EMT untuk
info lebih lanjut tentang string Unicode).


\>plot2d("x^3-x",title=u"x &rarr; x&sup3; - x"):


![images/Tugas%203-063.png](images/Tugas%203-063.png)

Label pada sumbu x dan y dapat dibuat vertikal, begitu pula sumbunya.


\>plot2d("sinc(x)",0,2pi,xl="x",yl=u"x &rarr; sinc(x)",\>vertical):


![images/Tugas%203-064.png](images/Tugas%203-064.png)

## LaTeX

Anda juga dapat menggambar formula LaTeX jika Anda telah menginstal sistem LaTeX. Saya
merekomendasikan MiKTeX. Path ke file biner "latex" dan "dvipng" harus berada di dalam path sistem,
atau Anda harus mengatur LaTeX di menu opsi.


Perhatikan, bahwa mem-parsing LaTeX cukup lambat. Jika Anda ingin menggunakan LaTeX pada plot
animasi, Anda sebaiknya memanggil latex() sebelum perulangan sekali saja dan menggunakan hasilnya
(sebuah gambar di dalam matriks RGB).


Pada plot berikut, kita menggunakan LaTeX untuk label x dan y, sebuah label, kotak label, dan judul
plotnya.


\>plot2d("exp(-x)\*sin(x)/x",a=0,b=2pi,c=0,d=1,grid=6,color=blue, ...  
\>     title=latex("\\text{Function $\\Phi$}"), ...  
\>     xl=latex("\\phi"),yl=latex("\\Phi(\\phi)")); ...  
\>   textbox( ...  
\>     latex("\\Phi(\\phi) = e^{-\\phi} \\frac{\\sin(\\phi)}{\\phi}"),x=0.8,y=0.5); ...  
\>   label(latex("\\Phi",color=blue),1,0.4):


![images/Tugas%203-065.png](images/Tugas%203-065.png)

Seringkali, kita menginginkan spasi dan label teks yang tidak seragam pada sumbu-x. Kita dapat
menggunakan xaxis() dan yaxis() seperti yang akan kita tunjukkan nanti.


Cara termudah adalah membuat plot kosong dengan bingkai menggunakan grid=4, dan kemudian menambahkan
grid dengan ygrid() dan xgrid(). Pada contoh berikut, kita menggunakan tiga string LaTeX untuk label
pada sumbu-x dengan xtick().


\>plot2d("sinc(x)",0,2pi,grid=4,<ticks); ...  
\>   ygrid(-2:0.5:2,grid=6); ...  
\>   xgrid([0:2]\*pi,<ticks,grid=6);  ...  
\>   xtick([0,pi,2pi],["0","\\pi","2\\pi"],\>latex):


![images/Tugas%203-066.png](images/Tugas%203-066.png)

Tentu saja, fungsi juga dapat digunakan.


\>function map f(x) ...


    if x>0 then return x^4
    else return x^2
    endif
    endfunction
</pre>
Parameter "map" membantu dalam menggunakan fungsi tersebut untuk vektor. Untuk


plotnya, ini tidak diperlukan. Namun untuk mendemonstrasikan bahwa vektorisasi


itu berguna, kita menambahkan beberapa titik kunci ke plot pada x=-1, x=0 dan x=1.


Pada plot berikut, kita juga memasukkan beberapa kode LaTeX. Kita menggunakannya untuk


dua label dan sebuah kotak teks. Tentu saja, Anda hanya dapat menggunakan


LaTeX jika Anda telah menginstal LaTeX dengan benar.


\>plot2d("f",-1,1,xl="x",yl="f(x)",grid=6);  ...  
\>   plot2d([-1,0,1],f([-1,0,1]),\>points,\>add); ...  
\>   label(latex("x^3"),0.72,f(0.72)); ...  
\>   label(latex("x^2"),-0.52,f(-0.52),pos="ll"); ...  
\>   textbox( ...  
\>     latex("f(x)=\\begin{cases} x^3 & x\>0 \\\\ x^2 & x \\le 0\\end{cases}"), ...  
\>     x=0.7,y=0.2):


![images/Tugas%203-067.png](images/Tugas%203-067.png)

## Interaksi Pengguna

Saat menggambar sebuah fungsi atau ekspresi, parameter &gt;user memungkinkan pengguna untuk memperbesar
(zoom) dan menggeser plot menggunakan tombol kursor atau mouse. Pengguna dapat


* 
memperbesar dengan + atau -

* 
menggeser plot dengan tombol kursor

* 
memilih jendela plot dengan mouse

* 
mereset tampilan dengan tombol spasi

* 
keluar dengan tombol return/enter


Tombol spasi akan mereset plot ke jendela plot semula.


Saat menggambar data, bendera &gt;user hanya akan menunggu ketukan tombol.


\>plot2d({{"x^3-a\*x",a=1}},\>user,title="Press any key!"):


![images/Tugas%203-068.png](images/Tugas%203-068.png)

\>plot2d("exp(x)\*sin(x)",user=true, ...  
\>     title="+/- or cursor keys (return to exit)"):


![images/Tugas%203-069.png](images/Tugas%203-069.png)

Hal berikut mendemonstrasikan cara lanjutan dari interaksi pengguna (lihat tutorial tentang
pemrograman untuk detailnya).


Fungsi bawaan mousedrag() menunggu peristiwa mouse atau keyboard. Fungsi ini melaporkan mouse ditekan
(down), mouse digerakkan (moved) atau mouse dilepas (up), serta penekanan tombol. Fungsi dragpoints()
memanfaatkan ini, dan memungkinkan pengguna menyeret (drag) titik mana pun di dalam plot.


Pertama-tama kita memerlukan sebuah fungsi plot. Sebagai contoh, kita melakukan interpolasi pada 5
titik dengan polinomial. Fungsi ini harus menggambar di area plot yang tetap.


\>function plotf(xp,yp,select) ...


      d=interp(xp,yp);
      plot2d("interpval(xp,d,x)";d,xp,r=2);
      plot2d(xp,yp,>points,>add);
      if select>0 then
        plot2d(xp[select],yp[select],color=red,>points,>add);
      endif;
      title("Drag one point, or press space or return!");
    endfunction
</pre>
Perhatikan parameter titik koma di plot2d (d dan xp), yang diteruskan ke evaluasi fungsi interp().
Tanpa ini, kita harus menulis fungsi plotinterp() terlebih dahulu, yang mengakses nilai-nilai secara
global.


Sekarang kita membuat beberapa nilai acak, dan membiarkan pengguna menyeret titik-titiknya.


\>t=-1:0.5:1; dragpoints("plotf",t,random(size(t))-0.5):


![images/Tugas%203-070.png](images/Tugas%203-070.png)

Ada juga fungsi, yang menggambar fungsi lain bergantung pada vektor parameter, dan memungkinkan
pengguna menyesuaikan parameter-parameter ini.


Pertama kita membutuhkan fungsi plotnya.


\>function plotf([a,b]) := plot2d("exp(a\*x)\*cos(2pi\*b\*x)",0,2pi;a,b);


Kemudian kita membutuhkan nama untuk parameternya, nilai awal dan matriks nx2 untuk rentangnya, dan
baris judul opsional.


Ada penggeser (slider) interaktif, yang nilainya dapat diatur oleh pengguna. Fungsi dragvalues()
menyediakan hal ini.


\>dragvalues("plotf",["a","b"],[-1,2],[[-2,2];[1,10]], ...  
\>     heading="Drag these values:",hcolor=black):


![images/Tugas%203-071.png](images/Tugas%203-071.png)

Nilai yang diseret dimungkinkan untuk dibatasi pada bilangan bulat. Sebagai contoh, kita menulis
sebuah fungsi plot, yang menggambar polinomial Taylor derajat n pada fungsi kosinus.


\>function plotf(n) ...


    plot2d("cos(x)",0,2pi,>square,grid=6);
    plot2d(&"taylor(cos(x),x,0,@n)",color=blue,>add);
    textbox("Taylor polynomial of degree "+n,0.1,0.02,style="t",>left);
    endfunction
</pre>
Sekarang kita membiarkan derajat n bervariasi dari 0 hingga 20 dalam 20 pemberhentian. Hasil dari
dragvalues() digunakan untuk menggambar sketsa dengan n ini, dan untuk menyisipkan plot ke dalam
notebook.


\>nd=dragvalues("plotf","degree",2,[0,20],20,y=0.8, ...  
\>      heading="Drag the value:"); ...  
\>   plotf(nd):


![images/Tugas%203-072.png](images/Tugas%203-072.png)

Berikut adalah demonstrasi sederhana dari fungsi tersebut. Pengguna dapat menggambar di atas jendela
plot, meninggalkan jejak titik-titik.


\>function dragtest ...


      plot2d(none,r=1,title="Drag with the mouse, or press any key!");
      start=0;
      repeat
        {flag,m,time}=mousedrag();
        if flag==0 then return; endif;
        if flag==2 then
          hold on; mark(m[1],m[2]); hold off;
        endif;
      end
    endfunction
</pre>
\>dragtest // lihat hasilnya dan cobalah lakukan!


## Gaya pada Plot 2D

Secara bawaan, EMT menghitung tanda sumbu otomatis dan menambahkan label ke setiap tanda. Hal ini
dapat diubah dengan parameter grid. Gaya bawaan sumbu dan labelnya dapat dimodifikasi. Selain itu,
label dan judul dapat ditambahkan secara manual. Untuk mengatur ulang ke gaya bawaan, gunakan
reset().


\>aspect();

\>figure(3,4); ...  
\>    figure(1); plot2d("x^3-x",grid=0); ... // tanpa grid, bingkai, atau sumbu

\> figure(2); plot2d("x^3-x",grid=1); ... // sumbu-x-y

\> figure(3); plot2d("x^3-x",grid=2); ... // tanda sumbu bawaan

\> figure(4); plot2d("x^3-x",grid=3); ... // sumbu-x-y dengan label di dalam

\> figure(5); plot2d("x^3-x",grid=4); ... // tanpa tanda sumbu, hanya label

\> figure(6); plot2d("x^3-x",grid=5); ... // bawaan, tapi tanpa margin

\> figure(7); plot2d("x^3-x",grid=6); ... // sumbu saja

\> figure(8); plot2d("x^3-x",grid=7); ... // sumbu saja, tanda pada sumbu

\> figure(9); plot2d("x^3-x",grid=8); ... // sumbu saja, tanda yang lebih halus pada sumbu

\> figure(10); plot2d("x^3-x",grid=9); ... // bawaan, tanda kecil di dalam

\> figure(11); plot2d("x^3-x",grid=10); ...// tanpa tanda sumbu, sumbu saja

\> figure(0):


![images/Tugas%203-073.png](images/Tugas%203-073.png)

Parameter &lt;frame mematikan bingkai, dan framecolor=blue mengatur bingkai menjadi warna biru.


Jika Anda menginginkan tanda sumbu (ticks) Anda sendiri, Anda dapat menggunakan style=0, dan
menambahkan semuanya nanti.


\>aspect(1.5); 

\>plot2d("x^3-x",grid=0); // gambar plot

\>frame; xgrid([-1,0,1]); ygrid(0): // tambahkan bingkai dan grid


![images/Tugas%203-074.png](images/Tugas%203-074.png)

Untuk judul plot dan label sumbu, lihat contoh berikut.


\>plot2d("exp(x)",-1,1);

\>textcolor(black); // atur warna teks menjadi hitam

\>title(latex("y=e^x")); // judul di atas plot

\>xlabel(latex("x")); // "x" untuk sumbu-x

\>ylabel(latex("y"),\>vertical); // "y" vertikal untuk sumbu-y

\>label(latex("(0,1)"),0,1,color=blue): // beri label pada titik


![images/Tugas%203-075.png](images/Tugas%203-075.png)

Sumbu-sumbu dapat digambar secara terpisah dengan xaxis() dan yaxis().


\>plot2d("x^3-x",<grid,<frame);

\>xaxis(0,xx=-2:1,style="-\>"); yaxis(0,yy=-5:5,style="-\>"):


![images/Tugas%203-076.png](images/Tugas%203-076.png)

Teks pada plot dapat diatur dengan label(). Pada contoh berikut, "lc" berarti lower center (tengah
bawah). Ini mengatur posisi label relatif terhadap koordinat plot.


\>function f(x) &= x^3-x


    
                                                    3
                                                   x  - x
    

\>plot2d(f,-1,1,\>square);

\>x0=fmin(f,0,1); // hitung titik minimum

\>label("Rel. Min.",x0,f(x0),pos="lc"): // tambahkan label di sana


![images/Tugas%203-077.png](images/Tugas%203-077.png)

Terdapat juga kotak-kotak teks.


\>plot2d(&f(x),-1,1,-2,2); // function

\>plot2d(&diff(f(x),x),\>add,style="--",color=red); // derivative

\>labelbox(["f","f'"],["-","--"],[black,red]): // kotak label


![images/Tugas%203-078.png](images/Tugas%203-078.png)

\>plot2d(["exp(x)","1+x"],color=[black,blue],style=["-","-.-"]):


![images/Tugas%203-079.png](images/Tugas%203-079.png)

\>gridstyle("-\>",color=gray,textcolor=gray,framecolor=gray);  ...  
\>    plot2d("x^3-x",grid=1);   ...  
\>    settitle("y=x^3-x",color=black); ...  
\>    label("x",2,0,pos="bc",color=gray);  ...  
\>    label("y",0,6,pos="cl",color=gray); ...  
\>    reset():


![images/Tugas%203-080.png](images/Tugas%203-080.png)

Untuk kendali yang lebih jauh, sumbu-x dan sumbu-y dapat dibuat secara manual.


Perintah fullwindow() memperluas jendela plot karena kita tidak lagi membutuhkan tempat untuk label
di luar jendela plot. Gunakan shrinkwindow() atau reset() untuk mengembalikannya ke pengaturan
bawaan.


\>fullwindow; ...  
\>    gridstyle(color=darkgray,textcolor=darkgray); ...  
\>    plot2d(["2^x","1","2^(-x)"],a=-2,b=2,c=0,d=4,<grid,color=4:6,<frame); ...  
\>    xaxis(0,-2:1,style="-\>"); xaxis(0,2,"x",<axis); ...  
\>    yaxis(0,4,"y",style="-\>"); ...  
\>    yaxis(-2,1:4,\>left); ...  
\>    yaxis(2,2^(-2:2),style=".",<left); ...  
\>    labelbox(["2^x","1","2^-x"],colors=4:6,x=0.8,y=0.2); ...  
\>    reset:


![images/Tugas%203-081.png](images/Tugas%203-081.png)

Berikut adalah contoh lain, di mana string Unicode digunakan dan sumbu berada di luar area plot.


\>aspect(1.5); 

\>plot2d(["sin(x)","cos(x)"],0,2pi,color=[red,green],<grid,<frame); ...  
\>    xaxis(-1.1,(0:2)\*pi,xt=["0",u"&pi;",u"2&pi;"],style="-",\>ticks,\>zero);  ...  
\>    xgrid((0:0.5:2)\*pi,<ticks); ...  
\>    yaxis(-0.1\*pi,-1:0.2:1,style="-",\>zero,\>grid); ...  
\>    labelbox(["sin","cos"],colors=[red,green],x=0.5,y=0.2,\>left); ...  
\>    xlabel(u"&phi;"); ylabel(u"f(&phi;)"):


![images/Tugas%203-082.png](images/Tugas%203-082.png)

# Plotting Data 2D

Jika x dan y adalah vektor data, data ini akan digunakan sebagai koordinat-x dan koordinat-y dari
sebuah kurva. Pada kasus ini, a, b, c, dan d, atau sebuah radius r dapat ditentukan, atau jendela
plot akan menyesuaikan secara otomatis dengan data tersebut. Secara alternatif, &gt;square dapat diatur
untuk mempertahankan rasio aspek persegi.


Menggambar plot dari sebuah ekspresi hanyalah singkatan untuk plot data. Untuk plot data, Anda
membutuhkan satu atau lebih baris nilai-x, dan satu atau lebih baris nilai-y. Dari rentang dan
nilai-x, fungsi plot2d akan menghitung data untuk digambar, secara bawaan menggunakan evaluasi
adaptif pada fungsi tersebut. Untuk plot titik gunakan "&gt;points", untuk campuran garis dan titik
gunakan "&gt;addpoints".


Namun Anda dapat memasukkan data secara langsung.


* 
Gunakan vektor baris untuk x dan y pada satu fungsi.

* 
Matriks untuk x dan y digambar baris demi baris.


Berikut adalah contoh dengan satu baris untuk x dan y.


\>x=-10:0.1:10; y=exp(-x^2)\*x; plot2d(x,y):


![images/Tugas%203-083.png](images/Tugas%203-083.png)

Data juga dapat digambar sebagai titik-titik. Gunakan points=true untuk hal ini. Plot ini berfungsi
seperti poligon, namun hanya menggambar sudut-sudutnya.


* 
style="...": Pilih dari "[]", "&lt;&gt;", "o", ".", "..", "+", "*", "[]#", "&lt;&gt;#", "o#", "..#", "#", "|".


Untuk menggambar kumpulan titik, gunakan &gt;points. Jika warnanya adalah vektor warna, setiap titik


mendapatkan warna yang berbeda. Untuk matriks koordinat dan vektor kolom, warnanya berlaku pada
baris-baris matriks tersebut.


Parameter &gt;addpoints menambahkan titik-titik ke segmen garis untuk plot data.


\>xdata=[1,1.5,2.5,3,4]; ydata=[3,3.1,2.8,2.9,2.7]; // data

\>plot2d(xdata,ydata,a=0.5,b=4.5,c=2.5,d=3.5,style="."); // garis

\>plot2d(xdata,ydata,\>points,\>add,style="o"): // tambahkan titik


![images/Tugas%203-084.png](images/Tugas%203-084.png)

\>p=polyfit(xdata,ydata,1); // dapatkan garis regresi

\>plot2d("polyval(p,x)",\>add,color=red): // tambahkan plot garis


![images/Tugas%203-085.png](images/Tugas%203-085.png)

# Menggambar Daerah Yang Dibatasi Kurva

Plot data pada dasarnya adalah poligon. Kita juga dapat menggambar kurva atau kurva terisi (filled
curves).


* 
filled=true mengisi plot tersebut.

* 
style="...": Pilih dari "#", "/", "\", "\/".

* 
fillcolor: Lihat di atas untuk warna yang tersedia.


Warna isian ditentukan oleh argumen "fillcolor", dan &lt;outline opsional mencegah penggambaran batas
untuk semua gaya kecuali gaya bawaan.


\>t=linspace(0,2pi,1000); // parameter untuk kurva

\>x=sin(t)\*exp(t/pi); y=cos(t)\*exp(t/pi); // x(t) dan y(t)

\>figure(1,2); aspect(16/9)

\>figure(1); plot2d(x,y,r=10); // gambar kurva

\>figure(2); plot2d(x,y,r=10,\>filled,style="/",fillcolor=red); // isi kurva

\>figure(0):


![images/Tugas%203-086.png](images/Tugas%203-086.png)

Pada contoh-contoh berikut kita menggambar elips terisi dan dua heksagon terisi menggunakan kurva
tertutup dengan 6 titik dan gaya isian yang berbeda.


\>x=linspace(0,2pi,1000); plot2d(sin(x),cos(x)\*0.5,r=1,\>filled,style="/"):


![images/Tugas%203-087.png](images/Tugas%203-087.png)

\>t=linspace(0,2pi,6); ...  
\>   plot2d(cos(t),sin(t),\>filled,style="/",fillcolor=red,r=1.2):


![images/Tugas%203-088.png](images/Tugas%203-088.png)

\>t=linspace(0,2pi,6); plot2d(cos(t),sin(t),\>filled,style="#"):


![images/Tugas%203-089.png](images/Tugas%203-089.png)

Contoh lain adalah septagon (segi tujuh), yang kita buat dengan 7 titik pada lingkaran satuan.


\>t=linspace(0,2pi,7);  ...  
\>    plot2d(cos(t),sin(t),r=1,\>filled,style="/",fillcolor=red):


![images/Tugas%203-090.png](images/Tugas%203-090.png)

Berikut ini adalah himpunan nilai maksimal dari empat kondisi linear kurang dari atau sama dengan 3.
Ini adalah A[k].v&lt;=3 untuk semua baris A. Untuk mendapatkan sudut yang bagus, kita menggunakan n yang
relatif besar.


\>A=[2,1;1,2;-1,0;0,-1];

\>function f(x,y) := max([x,y].A');

\>plot2d("f",r=4,level=[0;3],color=green,n=111):


![images/Tugas%203-091.png](images/Tugas%203-091.png)

Poin utama dari bahasa matriks adalah ia memungkinkan kita menghasilkan tabel dari fungsi-fungsi
secara mudah.


\>t=linspace(0,2pi,1000); x=cos(3\*t); y=sin(4\*t);


Kita sekarang memiliki vektor nilai x dan y. plot2d() dapat menggambar nilai-nilai ini


sebagai kurva yang menghubungkan titik-titik tersebut. Plot ini dapat diisi. Pada kasus ini


ini menghasilkan gambaran yang bagus berkat aturan penggulungan (winding rule), yang digunakan untuk


isiannya.


\>plot2d(x,y,<grid,<frame,\>filled):


![images/Tugas%203-092.png](images/Tugas%203-092.png)

Vektor interval digambar terhadap nilai-x sebagai area terisi


di antara nilai batas bawah dan batas atas dari interval tersebut.


Hal ini dapat berguna untuk menggambar galat komputasi. Namun ini juga dapat


digunakan untuk menggambar galat statistik.


\>t=0:0.1:1; ...  
\>    plot2d(t,interval(t-random(size(t)),t+random(size(t))),style="|");  ...  
\>    plot2d(t,t,add=true):


![images/Tugas%203-093.png](images/Tugas%203-093.png)

Jika x adalah vektor yang diurutkan, dan y adalah vektor interval, maka plot2d akan menggambar
rentang interval yang terisi pada bidang tersebut. Gaya isiannya sama dengan gaya poligon.


\>t=-1:0.01:1; x=~t-0.01,t+0.01~; y=x^3-x;

\>plot2d(t,y):


![images/Tugas%203-094.png](images/Tugas%203-094.png)

Dimungkinkan untuk mengisi area nilai untuk fungsi tertentu. Untuk


ini, parameter level harus berupa matriks 2xn. Baris pertama adalah batas bawah


dan baris kedua berisi batas atas.


\>expr := "2\*x^2+x\*y+3\*y^4+y"; // definisikan ekspresi f(x,y)

\>plot2d(expr,level=[0;1],style="-",color=blue): // 0 <= f(x,y) <= 1


![images/Tugas%203-095.png](images/Tugas%203-095.png)

Kita juga dapat mengisi rentang nilai seperti


$$-1 \le (x^2+y^2)^2-x^2+y^2 \le 0.$$\>plot2d("(x^2+y^2)^2-x^2+y^2",r=1.2,level=[-1;0],style="/"):


![images/Tugas%203-097.png](images/Tugas%203-097.png)

\>plot2d("cos(x)","sin(x)^3",xmin=0,xmax=2pi,\>filled,style="/"):


![images/Tugas%203-098.png](images/Tugas%203-098.png)

# Grafik Fungsi Parametrik

Nilai-x tidak perlu diurutkan. (x,y) secara sederhana mendeskripsikan sebuah kurva. Jika x diurutkan,
maka kurva tersebut adalah grafik dari sebuah fungsi.


Pada contoh berikut, kita menggambar sebuah spiral


$$\gamma(t) = t \cdot (\cos(2\pi t),\sin(2\pi t))$$Kita entah perlu menggunakan titik yang sangat banyak agar terlihat mulus, atau menggunakan fungsi
adaptive() untuk mengevaluasi ekspresinya (lihat fungsi adaptive() untuk detail lebih lanjut).


\>t=linspace(0,1,1000); ...  
\>   plot2d(t\*cos(2\*pi\*t),t\*sin(2\*pi\*t),r=1):


![images/Tugas%203-100.png](images/Tugas%203-100.png)

Sebagai alternatif, sangat memungkinkan untuk menggunakan dua ekspresi pada kurva. Hal berikut ini
menggambar kurva yang sama seperti di atas.


\>plot2d("x\*cos(2\*pi\*x)","x\*sin(2\*pi\*x)",xmin=0,xmax=1,r=1):


![images/Tugas%203-101.png](images/Tugas%203-101.png)

\>t=linspace(0,1,1000); r=exp(-t); x=r\*cos(2pi\*t); y=r\*sin(2pi\*t);

\>plot2d(x,y,r=1):


![images/Tugas%203-102.png](images/Tugas%203-102.png)

Pada contoh selanjutnya, kita menggambar kurva


$$\gamma(t) = (r(t) \cos(t), r(t) \sin(t))$$dengan


$$r(t) = 1 + \dfrac{\sin(3t)}{2}.$$\>t=linspace(0,2pi,1000); r=1+sin(3\*t)/2; x=r\*cos(t); y=r\*sin(t); ...  
\>   plot2d(x,y,\>filled,fillcolor=red,style="/",r=1.5):


![images/Tugas%203-105.png](images/Tugas%203-105.png)

# Menggambar Grafik Bilangan Kompleks

Array bilangan kompleks juga dapat digambar. Titik-titik grid nantinya akan saling terhubung. Jika
sejumlah garis grid ditentukan (atau vektor 1x2 untuk garis grid) pada argumen cgrid, hanya garis
grid tersebut yang akan terlihat.


Matriks bilangan kompleks akan otomatis tergambar sebagai grid di bidang kompleks.


Pada contoh berikut, kita memplot bayangan dari lingkaran satuan di bawah fungsi eksponensial.
Parameter cgrid menyembunyikan beberapa kurva grid.


\>aspect(); r=linspace(0,1,50); a=linspace(0,2pi,80)'; z=r\*exp(I\*a);...  
\>   plot2d(z,a=-1.25,b=1.25,c=-1.25,d=1.25,cgrid=10):


![images/Tugas%203-106.png](images/Tugas%203-106.png)

\>aspect(1.25); r=linspace(0,1,50); a=linspace(0,2pi,200)'; z=r\*exp(I\*a);

\>plot2d(exp(z),cgrid=[40,10]):


![images/Tugas%203-107.png](images/Tugas%203-107.png)

\>r=linspace(0,1,10); a=linspace(0,2pi,40)'; z=r\*exp(I\*a);

\>plot2d(exp(z),\>points,\>add):


![images/Tugas%203-108.png](images/Tugas%203-108.png)

Vektor bilangan kompleks secara otomatis akan digambar sebagai kurva di bidang kompleks dengan bagian
riil dan bagian imajinernya.


Pada contoh ini, kita menggambar lingkaran satuan dengan


$$\gamma(t) = e^{it}$$\>t=linspace(0,2pi,1000); ...  
\>   plot2d(exp(I\*t)+exp(4\*I\*t),r=2):


![images/Tugas%203-110.png](images/Tugas%203-110.png)

# Plot Statistik

Ada banyak fungsi yang dikhususkan untuk plot statistik. Salah satu yang paling sering digunakan
adalah plot kolom (column plot).


Jumlah kumulatif dari nilai terdistribusi normal 0-1 akan menghasilkan jalan acak (random walk).


\>plot2d(cumsum(randnormal(1,1000))):


![images/Tugas%203-111.png](images/Tugas%203-111.png)

Penggunaan dua baris akan menunjukkan pergerakan dalam dua dimensi.


\>X=cumsum(randnormal(2,1000)); plot2d(X[1],X[2]):


![images/Tugas%203-112.png](images/Tugas%203-112.png)

\>columnsplot(cumsum(random(10)),style="/",color=blue):


![images/Tugas%203-113.png](images/Tugas%203-113.png)

Hal ini juga dapat menampilkan string sebagai label.


\>months=["Jan","Feb","Mar","Apr","May","Jun", ...  
\>     "Jul","Aug","Sep","Oct","Nov","Dec"];

\>values=[10,12,12,18,22,28,30,26,22,18,12,8];

\>columnsplot(values,lab=months,color=red,style="-");

\>title("Temperature"):


![images/Tugas%203-114.png](images/Tugas%203-114.png)

\>k=0:10;

\>plot2d(k,bin(10,k),\>bar):


![images/Tugas%203-115.png](images/Tugas%203-115.png)

\>plot2d(k,bin(10,k)); plot2d(k,bin(10,k),\>points,\>add):


![images/Tugas%203-116.png](images/Tugas%203-116.png)

\>plot2d(normal(1000),normal(1000),\>points,grid=6,style=".."):


![images/Tugas%203-117.png](images/Tugas%203-117.png)

\>plot2d(normal(1,1000),\>distribution,style="O"):


![images/Tugas%203-118.png](images/Tugas%203-118.png)

\>plot2d("qnormal",0,5;2.5,0.5,\>filled):


![images/Tugas%203-119.png](images/Tugas%203-119.png)

Untuk menggambar plot distribusi statistik eksperimental, Anda dapat menggunakan distribution=n
dengan plot2d.


\>w=randexponential(1,1000); // exponential distribution

\>plot2d(w,\>distribution): // or distribution=n with n intervals


![images/Tugas%203-120.png](images/Tugas%203-120.png)

Atau Anda dapat menghitung distribusi dari data dan memplot hasilnya dengan &gt;bar di plot3d, atau
dengan plot kolom.


\>w=normal(1000); // 0-1-normal distribution

\>{x,y}=histo(w,10,v=[-6,-4,-2,-1,0,1,2,4,6]); // batas interval v

\>plot2d(x,y,\>bar):


![images/Tugas%203-121.png](images/Tugas%203-121.png)

Fungsi statplot() mengatur gaya dengan sebuah string sederhana.


\>statplot(1:10,cumsum(random(10)),"b"):


![images/Tugas%203-122.png](images/Tugas%203-122.png)

\>n=10; i=0:n; ...  
\>   plot2d(i,bin(n,i)/2^n,a=0,b=10,c=0,d=0.3); ...  
\>   plot2d(i,bin(n,i)/2^n,points=true,style="ow",add=true,color=blue):


![images/Tugas%203-123.png](images/Tugas%203-123.png)

Selain itu, data dapat digambar sebagai plot batang. Dalam kasus ini, x harus diurutkan dan satu
elemen lebih panjang dari y. Batang tersebut akan membentang dari x[i] ke x[i+1] dengan nilai y[i].
Jika x memiliki ukuran yang sama dengan y, ia akan diperpanjang satu elemen menggunakan jarak
(spacing) terakhir.


Gaya isian dapat digunakan sama seperti yang di atas.


\>n=10; k=bin(n,0:n); ...  
\>   plot2d(-0.5:n+0.5,k,bar=true,fillcolor=lightgray):


![images/Tugas%203-124.png](images/Tugas%203-124.png)

Data untuk plot batang (bar=1) dan histogram (histogram=1) dapat diberikan secara eksplisit pada xv
dan yv, atau dapat dihitung dari distribusi empiris pada xv dengan &gt;distribution (atau
distribution=n). Histogram dari nilai-nilai xv akan dihitung secara otomatis dengan &gt;histogram. Jika
&gt;even ditentukan, nilai-nilai xv akan dihitung dalam interval bilangan bulat.


\>plot2d(normal(10000),distribution=50):


![images/Tugas%203-125.png](images/Tugas%203-125.png)

\>k=0:10; m=bin(10,k); x=(0:11)-0.5; plot2d(x,m,\>bar):


![images/Tugas%203-126.png](images/Tugas%203-126.png)

\>columnsplot(m,k):


![images/Tugas%203-127.png](images/Tugas%203-127.png)

\>plot2d(random(600)\*6,histogram=6):


![images/Tugas%203-128.png](images/Tugas%203-128.png)

Untuk distribusi, terdapat parameter distribution=n, yang menghitung nilai-nilai secara otomatis dan
mencetak distribusi relatif dengan n sub-interval.


\>plot2d(normal(1,1000),distribution=10,style="\\/"):


![images/Tugas%203-129.png](images/Tugas%203-129.png)

Dengan parameter even=true, ini akan menggunakan interval bilangan bulat.


\>plot2d(intrandom(1,1000,10),distribution=10,even=true):


![images/Tugas%203-130.png](images/Tugas%203-130.png)

Perhatikan bahwa ada banyak plot statistik yang mungkin berguna. Silakan lihat tutorial mengenai
statistik.


\>columnsplot(getmultiplicities(1:6,intrandom(1,6000,6))):


![images/Tugas%203-131.png](images/Tugas%203-131.png)

\>plot2d(normal(1,1000),\>distribution); ...  
\>     plot2d("qnormal(x)",color=red,thickness=2,\>add):


![images/Tugas%203-132.png](images/Tugas%203-132.png)

Ada banyak juga plot khusus untuk statistik. Boxplot menunjukkan kuartil dari distribusi ini dan
banyaknya pencilan (outlier). Berdasarkan definisi, pencilan pada boxplot adalah data yang melebihi
1,5 kali rentang 50% bagian tengah dari plot tersebut.


\>M=normal(5,1000); boxplot(quartiles(M)):


![images/Tugas%203-133.png](images/Tugas%203-133.png)

# Fungsi Implisit

Plot implisit menunjukkan garis-garis level (level lines) yang menyelesaikan f(x,y)=level, di mana
"level" bisa berupa satu nilai atau vektor dari nilai. Jika level="auto", akan ada nc garis level,
yang akan tersebar secara merata di antara minimum dan maksimum fungsi tersebut. Warna yang lebih
gelap atau lebih terang dapat ditambahkan dengan &gt;hue untuk menunjukkan nilai fungsi tersebut. Untuk
fungsi implisit, xv harus berupa fungsi atau ekspresi dari parameter x dan y, atau, sebagai
alternatif, xv bisa berupa matriks nilai.


Euler dapat menandai garis level


$$f(x,y) = c$$dari sembarang fungsi.


Untuk menggambar himpunan f(x,y)=c dari satu atau lebih konstanta c Anda dapat menggunakan plot2d()
dengan plot implisitnya di bidang. Parameter untuk c adalah level=c, di mana c dapat berupa vektor
garis level. Selain itu, skema warna dapat digambar di latar belakang untuk menunjukkan nilai dari
fungsi tersebut untuk tiap titik pada plot. Parameter "n" menentukan tingkat kehalusan plot tersebut.


\>aspect(1.5); 

\>plot2d("x^2+y^2-x\*y-x",r=1.5,level=0,contourcolor=red):


![images/Tugas%203-135.png](images/Tugas%203-135.png)

\>expr := "2\*x^2+x\*y+3\*y^4+y"; // definisikan ekspresi f(x,y)

\>plot2d(expr,level=0): // Solusi dari f(x,y)=0


![images/Tugas%203-136.png](images/Tugas%203-136.png)

\>plot2d(expr,level=0:0.5:20,\>hue,contourcolor=white,n=200): // bagus


![images/Tugas%203-137.png](images/Tugas%203-137.png)

\>plot2d(expr,level=0:0.5:20,\>hue,\>spectral,n=200,grid=4): // lebih bagus


![images/Tugas%203-138.png](images/Tugas%203-138.png)

Hal ini berfungsi untuk plot data juga. Namun Anda harus menentukan rentangnya


untuk label sumbunya.


\>x=-2:0.05:1; y=x'; z=expr(x,y);

\>plot2d(z,level=0,a=-1,b=2,c=-2,d=1,\>hue):


![images/Tugas%203-139.png](images/Tugas%203-139.png)

\>plot2d("x^3-y^2",\>contour,\>hue,\>spectral):


![images/Tugas%203-140.png](images/Tugas%203-140.png)

\>plot2d("x^3-y^2",level=0,contourwidth=3,\>add,contourcolor=red):


![images/Tugas%203-141.png](images/Tugas%203-141.png)

\>z=z+normal(size(z))\*0.2;

\>plot2d(z,level=0.5,a=-1,b=2,c=-2,d=1):


![images/Tugas%203-142.png](images/Tugas%203-142.png)

\>plot2d(expr,level=[0:0.2:5;0.05:0.2:5.05],color=lightgray):


![images/Tugas%203-143.png](images/Tugas%203-143.png)

\>plot2d("x^2+y^3+x\*y",level=1,r=4,n=100):


![images/Tugas%203-144.png](images/Tugas%203-144.png)

\>plot2d("x^2+2\*y^2-x\*y",level=0:0.1:10,n=100,contourcolor=white,\>hue):


![images/Tugas%203-145.png](images/Tugas%203-145.png)

Sangat memungkinkan juga untuk mengisi himpunan


$$a \le f(x,y) \le b$$dengan rentang level.


Dimungkinkan untuk mengisi area nilai dari fungsi tertentu. Untuk ini, parameter level harus berupa
matriks 2xn. Baris pertama adalah batas bawah dan baris kedua berisi batas atas.


\>plot2d(expr,level=[0;1],style="-",color=blue): // 0 <= f(x,y) <= 1


![images/Tugas%203-147.png](images/Tugas%203-147.png)

Plot implisit juga dapat menunjukkan rentang dari beberapa level. Maka parameter level harus berupa
matriks 2xn untuk interval level, di mana baris pertamanya berisi awal dan baris keduanya memuat
akhir dari tiap interval. Sebagai alternatif, vektor baris sederhana dapat digunakan untuk level, dan
parameter dl memperluas nilai level tersebut menjadi interval.


\>plot2d("x^4+y^4",r=1.5,level=[0;1],color=blue,style="/"):


![images/Tugas%203-148.png](images/Tugas%203-148.png)

\>plot2d("x^2+y^3+x\*y",level=[0,2,4;1,3,5],style="/",r=2,n=100):


![images/Tugas%203-149.png](images/Tugas%203-149.png)

\>plot2d("x^2+y^3+x\*y",level=-10:20,r=2,style="-",dl=0.1,n=100):


![images/Tugas%203-150.png](images/Tugas%203-150.png)

\>plot2d("sin(x)\*cos(y)",r=pi,\>hue,\>levels,n=100):


![images/Tugas%203-151.png](images/Tugas%203-151.png)

Sangat mungkin juga untuk menandai area


$$a \le f(x,y) \le b.$$Hal ini dilakukan dengan menambahkan sebuah level yang memiliki dua baris.


\>plot2d("(x^2+y^2-1)^3-x^2\*y^3",r=1.3, ...  
\>     style="#",color=red,<outline, ...  
\>     level=[-2;0],n=100):


![images/Tugas%203-153.png](images/Tugas%203-153.png)

Dimungkinkan untuk menentukan sebuah level yang spesifik. Misal, kita dapat memplot penyelesaian dari
suatu persamaan seperti


$$x^3-xy+x^2y^2=6$$\>plot2d("x^3-x\*y+x^2\*y^2",r=6,level=1,n=100):


![images/Tugas%203-155.png](images/Tugas%203-155.png)

\>function starplot1 (v, style="/", color=green, lab=none) ...


      if !holding() then clg; endif;
      w=window(); window(0,0,1024,1024);
      h=holding(1);
      r=max(abs(v))*1.2;
      setplot(-r,r,-r,r);
      n=cols(v); t=linspace(0,2pi,n);
      v=v|v[1]; c=v*cos(t); s=v*sin(t);
      cl=barcolor(color); st=barstyle(style);
      loop 1 to n
        polygon([0,c[#],c[#+1]],[0,s[#],s[#+1]],1);
        if lab!=none then
          rlab=v[#]+r*0.1;
          {col,row}=toscreen(cos(t[#])*rlab,sin(t[#])*rlab);
          ctext(""+lab[#],col,row-textheight()/2);
        endif;
      end;
      barcolor(cl); barstyle(st);
      holding(h);
      window(w);
    endfunction
</pre>
Tidak ada grid atau tanda sumbu di sini. Selain itu, kita menggunakan jendela penuh untuk plot ini.


Kita memanggil reset sebelum kita menguji plot ini untuk mengembalikan pengaturan bawaan grafisnya.
Ini tidak diperlukan, jika Anda yakin bahwa plot Anda sudah berfungsi dengan baik.


\>reset; starplot1(normal(1,10)+5,color=red,lab=1:10):


![images/Tugas%203-156.png](images/Tugas%203-156.png)

Terkadang, Anda mungkin ingin memplot sesuatu yang tidak dapat dilakukan oleh plot2d secara persis,
namun hampir bisa.


Pada fungsi berikut, kita membuat plot impuls logaritmik. plot2d bisa melakukan plot logaritmik,
namun tidak untuk batang impuls.


\>function logimpulseplot1 (x,y) ...


      {x0,y0}=makeimpulse(x,log(y)/log(10));
      plot2d(x0,y0,>bar,grid=0);
      h=holding(1);
      frame();
      xgrid(ticks(x));
      p=plot();
      for i=-10 to 10;
        if i<=p[4] and i>=p[3] then
           ygrid(i,yt="10^"+i);
        endif;
      end;
      holding(h);
    endfunction
</pre>
Mari kita mengujinya dengan nilai-nilai yang terdistribusi secara eksponensial.


\>aspect(1.5); x=1:10; y=-log(random(size(x)))\*200; ...  
\>   logimpulseplot1(x,y):


![images/Tugas%203-157.png](images/Tugas%203-157.png)

Mari kita buat animasi pada kurva 2D menggunakan plot langsung (direct plots). Perintah plot(x,y)
secara sederhana akan memplot sebuah kurva ke dalam jendela plot. setplot(a,b,c,d) mengatur jendela
ini.


Fungsi wait(0) memaksa plot untuk muncul pada jendela grafis. Jika tidak, penggambaran ulang terjadi
dalam interval waktu yang lebih lambat/jarang.


\>function animliss (n,m) ...


    t=linspace(0,2pi,500);
    f=0;
    c=framecolor(0);
    l=linewidth(2);
    setplot(-1,1,-1,1);
    repeat
      clg;
      plot(sin(n*t),cos(m*t+f));
      wait(0);
      if testkey() then break; endif;
      f=f+0.02;
    end;
    framecolor(c);
    linewidth(l);
    endfunction
</pre>
Tekan tombol mana saja untuk menghentikan animasi ini.


\>animliss(2,3); // lihat hasilnya, jika sudah puas, tekan ENTER


# Plot Logaritmik

EMT menggunakan parameter "logplot" untuk skala logaritmik.


Plot logaritmik dapat digambar baik menggunakan skala logaritmik di sumbu y dengan logplot=1, atau
menggunakan skala logaritmik di sumbu x dan y dengan logplot=2, atau di sumbu x dengan logplot=3.


 - logplot=1: y-logaritmik  
 - logplot=2: x-y-logaritmik  
 - logplot=3: x-logaritmik  

\>plot2d("exp(x^3-x)\*x^2",1,5,logplot=1):


![images/Tugas%203-158.png](images/Tugas%203-158.png)

\>plot2d("exp(x+sin(x))",0,100,logplot=1):


![images/Tugas%203-159.png](images/Tugas%203-159.png)

\>plot2d("exp(x+sin(x))",10,100,logplot=2):


![images/Tugas%203-160.png](images/Tugas%203-160.png)

\>plot2d("gamma(x)",1,10,logplot=1):


![images/Tugas%203-161.png](images/Tugas%203-161.png)

\>plot2d("log(x\*(2+sin(x/100)))",10,1000,logplot=3):


![images/Tugas%203-162.png](images/Tugas%203-162.png)

Ini juga dapat berfungsi dengan plot data.


\>x=10^(1:20); y=x^2-x;

\>plot2d(x,y,logplot=2):


![images/Tugas%203-163.png](images/Tugas%203-163.png)

## Grafik Fungsi Satu Variabel dalam Bentuk Ekspresi Langsung

$$y=x^2-4x+3$$\>plot2d("x^2-4x+3",-10,10):


![images/Tugas%203-165.png](images/Tugas%203-165.png)

\>plot2d("cos(4\*x)",-10,10):


![images/Tugas%203-166.png](images/Tugas%203-166.png)

\>plot2d("(cos((x^2)/4))^2",-5,5):


![images/Tugas%203-167.png](images/Tugas%203-167.png)

\>plot2d("sin(x^2+1)",-5,5):


![images/Tugas%203-168.png](images/Tugas%203-168.png)

## Grafik Fungsi Satu Variabel yang Rumusnya Disimpan dalam Variabel Ekspresi

$$f(x)=x^2+1$$\>reset; fx:="x^2+1";

\>plot2d(fx,-5,5):


![images/Tugas%203-170.png](images/Tugas%203-170.png)

$$g(x)=x^2+x-5$$\>function g(x)&=x^2+x-5;

\>plot2d("g",-5,5):


![images/Tugas%203-172.png](images/Tugas%203-172.png)

$$h(x)=4x-x^3$$\>hx="4\*x-x^3";

\>plot2d("h",-5,5):


![images/Tugas%203-174.png](images/Tugas%203-174.png)

## Grafik Fungsi Satu Variabel yang Fungsinya Didefinisikan sebagai Fungsi Numerik

$$f(x)=x^2-4x+4$$\>function f(x):=x^2-4\*x+4

\>plot2d("f",-2,6):


![images/Tugas%203-176.png](images/Tugas%203-176.png)

$$f(x)=sin(x)cos(x)$$\>function f(x):=sin(x)\*cos(x)

\>plot2d("f",-pi,pi):


![images/Tugas%203-178.png](images/Tugas%203-178.png)

## Grafik Fungsi Satu Variabel yang Fungsinya Didefinisikan sebagai Fungsi Simbolik

$$f(x)=x^3-3x$$\>function f(x)&=x^3-3\*x;

\>plot2d("f",-3,3):


![images/Tugas%203-180.png](images/Tugas%203-180.png)

$$\frac{dy}{dx}, y=sin(x)e^x$$\>plot2d(&diff(sin(x)\*exp(x),x),-pi,pi):


![images/Tugas%203-182.png](images/Tugas%203-182.png)

## Grafik Beberapa Kurva Sekaligus

$$y=x^2,y=x^3,y=x^4$$\>plot2d(["x^2","x^3","x^4"],-2,2):


![images/Tugas%203-184.png](images/Tugas%203-184.png)

$$y=sin(x),y=cos(x)$$\>x=linspace(-2,2,100);

\>plot2d(x,[sin(x);cos(x)]):


![images/Tugas%203-186.png](images/Tugas%203-186.png)

## Grafik Beberapa Kurva dalam Satu Bidang Koordinat

$$y=x^2,y=x^3$$\>plot2d("x^2",-2,2);

\>plot2d("x^3",-2,2,\>add):


![images/Tugas%203-188.png](images/Tugas%203-188.png)

$$y=x^2, scatter (titik sebar)$$\>plot2d(1:10,(1:10)^2+random(1,10),\>points);

\>plot2d("x^2",1,10,\>add):


![images/Tugas%203-190.png](images/Tugas%203-190.png)

## Label Sumbu Koordinat, Label Kurva, dan Keterangan Kurva (Legend)

$$y=sin(x)$$dengan keterangan sumbu x sebagai waktu, sumbu y sebagai amplitudo, dan judul, yaitu gelombang sinus.


\>plot2d("sin(x)",0,2\*pi,xl="waktu(t)",yl="amplitudo",title="gelombang sinus"):


![images/Tugas%203-192.png](images/Tugas%203-192.png)

$$y=x^2$$dengan label kurva di titik tertentu.


\>plot2d("x^2",-2,2);

\>label("titik minimum",0,0):


![images/Tugas%203-194.png](images/Tugas%203-194.png)

## Mengatur Ukuran Grafik Format (Style), dan Warna Kurva

$$y=xin(x)$$dengan warna merah dan ketebalan 3 satuan.


\>plot2d("sin(x)",color=red,thickness=3):


![images/Tugas%203-196.png](images/Tugas%203-196.png)

$$y=x^2$$dengan warna biru dan garis putus-putus.


\>plot2d("x^2",color=blue,style="--"):


![images/Tugas%203-198.png](images/Tugas%203-198.png)

## Grafik Sekumpulan Kurva dengan Satu Perintah plot2d

$$y=ax^2, a=[1,5]$$\>function f(x,a):=a\*x^2;

\>plot2d("f(x,1)",-2,2);

\>for a=2:5;plot2d("f(x,"+a+")",-2,2,\>add); end:


![images/Tugas%203-200.png](images/Tugas%203-200.png)

\>plot2d("sin(x)",0,2\*pi);

\>for c=0:.5:2; plot2d("sin(x-"+c+")",0,2\*pi,\>add); end:


![images/Tugas%203-201.png](images/Tugas%203-201.png)

## Gambar Kurva Interaktif

$$y=sin\left(\frac{1}{x}\right)$$\>plot2d("sin(1/x)",.01,1):


![images/Tugas%203-203.png](images/Tugas%203-203.png)

\>zoom():


![images/Tugas%203-204.png](images/Tugas%203-204.png)

\>mouse():


![images/Tugas%203-205.png](images/Tugas%203-205.png)

## Grafik Kurva Fungsi Parametrik

$$x(t)=cos(t),y(t)=sin(t)$$\>t=linspace(0,2\*pi,100);

\>plot2d(cos(t),sin(t)):


![images/Tugas%203-207.png](images/Tugas%203-207.png)

\>t=linspace(0,2\*pi,500);

\>plot2d(sin(3\*t),cos(4\*t)):


![images/Tugas%203-208.png](images/Tugas%203-208.png)

## Grafik Kurva Fungsi Implisit

$$F(x,y)=x^2+y^2-4=0$$\>plot2d("x^2+y^2-4",r=3,level=0):


![images/Tugas%203-210.png](images/Tugas%203-210.png)

$$F(x,y)=x^3+y^3-3xy=0$$\>plot2d("x^3+y^3-3\*x\*y",r=3,level=0):


![images/Tugas%203-212.png](images/Tugas%203-212.png)

## Grafik Kurva Fungsi Kompleks

$$z=e^{it}$$\>t=linspace(0,2\*pi,100);

\>z=exp(%i\*t);

\>plot2d(z):


![images/Tugas%203-214.png](images/Tugas%203-214.png)

$$w=z^3-z$$\>w=z^3-z;

\>plot2d(w):


![images/Tugas%203-216.png](images/Tugas%203-216.png)

## Grafik Daerah Terbatas

$$y=x^2$$\>plot2d("x^2",-1,1,\>filled,fillcolor=lightblue):


![images/Tugas%203-218.png](images/Tugas%203-218.png)

$$y=x^2,y=x^4$$\>x=linspace(-1,1,100);

\>plot2d(x,[x^2;x^4],\>filled,fillcolor=cyan):


![images/Tugas%203-220.png](images/Tugas%203-220.png)

## Grafik Segi Banyak

Segitiga


\>x=[0,2,1,0]; y=[0,0,2,0]; plot2d(x,y):


![images/Tugas%203-221.png](images/Tugas%203-221.png)

\>t=linspace(0,2\*pi,7); x=cos(t); y=sin(t); plot2d(x,y,\>filled,fillcolor=yellow):


![images/Tugas%203-222.png](images/Tugas%203-222.png)

# Rujukan Lengkap Fungsi plot2d()

 function plot2d (xv, yv, btest, a, b, c, d, xmin, xmax, r, n,  ..  
 logplot, grid, frame, framecolor, square, color, thickness, style, ..  
 auto, add, user, delta, points, addpoints, pointstyle, bar, histogram,  ..  
 distribution, even, steps, own, adaptive, hue, level, contour,  ..  
 nc, filled, fillcolor, outline, title, xl, yl, maps, contourcolor, ..  
 contourwidth, ticks, margin, clipping, cx, cy, insimg, spectral,  ..  
 cgrid, vertical, smaller, dl, niveau, levels)  

Fungsi plot serbaguna untuk plot pada bidang (plot 2D). Fungsi ini bisa melakukan


plot untuk fungsi satu variabel, plot data, kurva pada bidang, plot batang, grid bilangan


kompleks, dan plot implisit fungsi dua variabel.


Parameter


x,y       : persamaan, fungsi, atau vektor data


a,b,c,d   : Area plot (bawaan a=-2,b=2)


r         : jika r diatur, maka a=cx-r, b=cx+r, c=cy-r, d=cy+r


           r bisa berupa vektor [rx,ry] atau vektor [rx1,rx2,ry1,ry2].


xmin,xmax : rentang parameter untuk kurva


auto      : Menentukan rentang-y secara otomatis (bawaan)


square    : jika true, mencoba mempertahankan rentang x-y berbentuk persegi


n         : jumlah interval (bawaan adalah adaptif)


grid      : 0 = tanpa grid dan label,


           1 = sumbu saja,


           2 = grid normal (lihat di bawah untuk jumlah garis grid)


           3 = sumbu di dalam


           4 = tanpa grid


           5 = grid penuh termasuk margin


           6 = tanda sumbu pada bingkai


           7 = sumbu saja


           8 = sumbu saja, sub-tanda sumbu


frame     : 0 = tanpa bingkai


framecolor: warna bingkai dan grid


margin    : angka antara 0 dan 0.4 untuk margin di sekitar plot


color     : Warna kurva. Jika berupa vektor warna,


           warna tersebut akan digunakan untuk setiap baris matriks dari plot. Dalam kasus


           plot titik, parameter ini harus berupa vektor kolom. Jika vektor baris atau


           matriks warna penuh digunakan untuk plot titik, itu akan digunakan untuk


           setiap titik data.


thickness : ketebalan garis pada kurva


           Nilai ini bisa lebih kecil dari 1 untuk garis yang sangat tipis.


style     : Gaya plot untuk garis, penanda, dan isian.


           Untuk titik-titik gunakan


           "[]", "&lt;&gt;", ".", "..", "...",


           "*", "+", "|", "-", "o"


           "[]#", "&lt;&gt;#", "o#" (bentuk terisi)


           "[]w", "&lt;&gt;w", "ow" (tidak transparan)


           Untuk garis gunakan


           "-", "--", "-.", ".", ".-.", "-.-", "-&gt;"


           Untuk poligon terisi atau plot batang gunakan


           "#", "#O", "O", "/", "\", "\/",


           "+", "|", "-", "t"


points    : menggambar titik tunggal dan bukannya segmen garis


addpoints : jika true, menggambar segmen garis dan titik


add       : tambahkan plot ini pada plot yang sudah ada


user      : mengaktifkan interaksi pengguna untuk fungsi-fungsi


delta     : ukuran langkah pada interaksi pengguna


bar       : plot batang (x adalah batas interval, y adalah nilai interval)


histogram : memplot frekuensi x dalam n subinterval


distribution=n : memplot distribusi x dengan n subinterval


even      : menggunakan nilai bilangan bulat untuk histogram otomatis.


steps     : memplot fungsi sebagai fungsi tangga (steps=1,2)


adaptive  : gunakan plot adaptif (n adalah jumlah langkah minimal)


level     : memplot garis level pada fungsi implisit dua variabel


outline   : menggambar batas pada rentang level.


Jika nilai levelnya berupa matriks 2xn, rentang levelnya akan digambar


dalam warna yang menggunakan gaya isian yang diberikan. Jika outline bernilai true, ia


akan digambar dengan warna kontur. Dengan menggunakan fitur ini, area


f(x,y) di antara batas-batas dapat ditandai.


hue       : tambahkan warna hue ke plot level untuk menunjukkan nilai


           fungsi


contour   : Gunakan plot level dengan level otomatis


nc        : jumlah garis level otomatis


title     : judul plot (bawaan "")


xl, yl    : label untuk sumbu-x dan sumbu-y


smaller   : jika &gt;0, akan ada lebih banyak ruang ke kiri untuk label.


vertical  :


 Mengaktifkan atau menonaktifkan label vertikal. Ini mengubah variabel global


 verticallabels secara lokal untuk satu plot. Nilai 1 mengatur teks hanya vertikal, 


 nilai 2 menggunakan label numerik vertikal pada sumbu y.


filled    : mengisi plot pada sebuah kurva


fillcolor : warna isian untuk plot batang dan kurva terisi


outline   : batas untuk poligon terisi


logplot   : mengatur plot logaritmik


           1 = logplot di y,


           2 = logplot di xy,


           3 = logplot di x


own       :


 Sebuah string, yang menunjuk pada rutin plot sendiri. Dengan &gt;user, Anda mendapatkan


 interaksi pengguna yang sama seperti pada plot2d. Rentangnya akan ditetapkan


 sebelum tiap panggilan ke fungsi Anda.


maps      : memetakan ekspresi (0 lebih cepat), fungsi selalu dipetakan.


contourcolor : warna garis kontur


contourwidth : lebar garis kontur


clipping  : beralih ke clipping (bawaannya adalah true)


title     :


 Ini dapat digunakan untuk mendeskripsikan plot. Judulnya akan muncul di atas


 plot tersebut. Selain itu, label untuk sumbu x dan y dapat ditambahkan dengan


 xl="string" atau yl="string". Label lain dapat ditambahkan dengan


 fungsi label() atau labelbox(). Judul dapat berupa string unicode


 atau gambar dari formula Latex.


cgrid     :


 Menentukan jumlah garis grid untuk plot grid kompleks.


 Harus merupakan pembagi dari ukuran matriks dikurangi 1 (jumlah


 subinterval). cgrid bisa berupa vektor [cx,cy].


Gambaran Umum


Fungsi ini dapat memplot


* 
ekspresi, kumpulan panggilan (call collections) atau fungsi dari satu variabel,

* 
kurva parametrik,

* 
data x terhadap data y,

* 
fungsi implisit,

* 
plot batang,

* 
grid kompleks,

* 
poligon.


Jika fungsi atau ekspresi untuk xv diberikan, plot2d() akan menghitung


nilai dalam rentang yang diberikan menggunakan fungsi atau ekspresi tersebut.


Ekspresi harus berupa ekspresi dalam variabel x. Rentang harus


didefinisikan pada parameter a dan b kecuali rentang bawaan


[-2,2] yang akan digunakan. Rentang-y akan dihitung secara otomatis,


kecuali c dan d ditentukan, atau suatu radius r, yang akan menghasilkan rentang


[-r,r] untuk x dan y. Untuk plot dari fungsi-fungsi, plot2d akan menggunakan


evaluasi adaptif pada fungsi tersebut secara bawaan. Untuk mempercepat


plot pada fungsi yang rumit, matikan hal ini dengan &lt;adaptive, dan


secara opsional turunkan jumlah interval n. Selain itu, plot2d()


secara bawaan akan menggunakan pemetaan. Maksudnya, ia akan menghitung elemen plot


demi elemen. Jika ekspresi Anda atau fungsi Anda bisa menangani


vektor x, Anda dapat mematikannya dengan &lt;maps agar evaluasi berjalan lebih cepat.


Perhatikan bahwa plot adaptif selalu dihitung elemen demi elemen. 


Jika fungsi atau ekspresi untuk keduanya baik xv maupun yv ditentukan,


plot2d() akan menghitung kurva dengan nilai-nilai xv sebagai koordinat-x


dan nilai-nilai yv sebagai koordinat-y. Dalam kasus ini, rentang harus


didefinisikan untuk parameter tersebut menggunakan xmin, xmax. Ekspresi yang terkandung


di dalam string harus selalu berupa ekspresi dalam variabel parameter x.


