# Visualisasi dan Perhitungan Geometri dengan EMT
Euler menyediakan beberapa fungsi untuk melakukan visualisasi dan perhitungan geometri, baik
secara numerik maupun analitik (seperti biasanya tentunya, menggunakan Maxima).
Fungsi-fungsi untuk visualisasi dan perhitungan geometri tersebut disimpan di dalam file
program "geometry.e", sehingga file tersebut harus dipanggil sebelum menggunakan
fungsi-fungsi atau perintah-perintah untuk geometri.


\>load geometry.e


    Numerical and symbolic geometry.

## Fungsi-fungsi Geometri

Fungsi-fungsi untuk Menggambar Objek Geometri:


  defaultd:=textheight()*1.5: nilai asli untuk parameter d  
  setPlotrange(x1,x2,y1,y2): menentukan rentang x dan y pada bidang koordinat  
  setPlotRange(r): pusat bidang koordinat (0,0) dan batas-batas sumbu-x dan y adalah -r sd r  
  plotPoint (P, "P"): menggambar titik P dan diberi label "P"  
  plotSegment (A,B, "AB", d): menggambar ruas garis AB, diberi label "AB" sejauh d  
  plotLine (g, "g", d): menggambar garis g diberi label "g" sejauh d  
  plotCircle (c,"c",v,d): Menggambar lingkaran c dan diberi label "c"  
  plotLabel (label, P, V, d): menuliskan label pada posisi P  

Fungsi-fungsi Geometri Analitik (numerik maupun simbolik):


  turn(v, phi): memutar vektor v sejauh phi  
  turnLeft(v):   memutar vektor v ke kiri  
  turnRight(v):  memutar vektor v ke kanan  
  normalize(v): normal vektor v  
  crossProduct(v, w): hasil kali silang vektor v dan w.  
  lineThrough(A, B): garis melalui A dan B, hasilnya [a,b,c] sdh. ax+by=c.  
  lineWithDirection(A,v): garis melalui A searah vektor v  
  getLineDirection(g): vektor arah (gradien) garis g  
  getNormal(g): vektor normal (tegak lurus) garis g  
  getPointOnLine(g):  titik pada garis g  
  perpendicular(A, g):  garis melalui A tegak lurus garis g  
  parallel (A, g):  garis melalui A sejajar garis g  
  lineIntersection(g, h):  titik potong garis g dan h  
  projectToLine(A, g):   proyeksi titik A pada garis g  
  distance(A, B):  jarak titik A dan B  
  distanceSquared(A, B):  kuadrat jarak A dan B  
  quadrance(A, B): kuadrat jarak A dan B  
  areaTriangle(A, B, C):  luas segitiga ABC  
  computeAngle(A, B, C):   besar sudut &lt;ABC  
  angleBisector(A, B, C): garis bagi sudut &lt;ABC  
  circleWithCenter (A, r): lingkaran dengan pusat A dan jari-jari r  
  getCircleCenter(c):  pusat lingkaran c  
  getCircleRadius(c):  jari-jari lingkaran c  
  circleThrough(A,B,C):  lingkaran melalui A, B, C  
  middlePerpendicular(A, B): titik tengah AB  
  lineCircleIntersections(g, c): titik potong garis g dan lingkaran c  
  circleCircleIntersections (c1, c2):  titik potong lingkaran c1 dan c2  
  planeThrough(A, B, C):  bidang melalui titik A, B, C  

Fungsi-fungsi Khusus Untuk Geometri Simbolik:


  getLineEquation (g,x,y): persamaan garis g dinyatakan dalam x dan y  
  getHesseForm (g,x,y,A): bentuk Hesse garis g dinyatakan dalam x dan y dengan titik A pada  
  sisi positif (kanan/atas) garis  
  quad(A,B): kuadrat jarak AB  
  spread(a,b,c): Spread segitiga dengan panjang sisi-sisi a,b,c, yakni sin(alpha)^2 dengan  
  alpha sudut yang menghadap sisi a.  
  crosslaw(a,b,c,sa): persamaan 3 quads dan 1 spread pada segitiga dengan panjang sisi a, b, c.  
  triplespread(sa,sb,sc): persamaan 3 spread sa,sb,sc yang memebntuk suatu segitiga  
  doublespread(sa): Spread sudut rangkap Spread 2*phi, dengan sa=sin(phi)^2 spread a.  

## Contoh 1: Luas, Lingkaran Luar, Lingkaran Dalam Segitiga

Untuk menggambar objek-objek geometri, langkah pertama adalah menentukan rentang sumbu-sumbu
koordinat. Semua objek geometri akan digambar pada satu bidang koordinat, sampai didefinisikan bidang
koordinat yang baru.


\>setPlotRange(-0.5,2.5,-0.5,2.5); // mendefinisikan bidang koordinat baru


Sekarang tentukan tiga titik dan gambarlah.


\>A=[1,0]; plotPoint(A,"A"); // definisi dan gambar tiga titik

\>B=[0,1]; plotPoint(B,"B");

\>C=[2,2]; plotPoint(C,"C"):


![images/Tugas%206-001.png](images/Tugas%206-001.png)

Kemudian tiga ruas garis.


\>plotSegment(A,B,"c"); // c=AB

\>plotSegment(B,C,"a"); // a=BC

\>plotSegment(A,C,"b"): // b=AC


![images/Tugas%206-002.png](images/Tugas%206-002.png)

Fungsi geometri mencakup fungsi untuk membuat garis dan lingkaran. Format untuk garis adalah [a,b,c],
yang merepresentasikan garis dengan persamaan ax+by=c.


\>lineThrough(B,C) // garis yang melalui B dan C


    [-1,  2,  2]

Hitung garis tegak lurus yang melalui A pada BC.


\>h=perpendicular(A,lineThrough(B,C)); // garis h tegak lurus BC melalui A


Dan perpotongannya dengan BC.


\>D=lineIntersection(h,lineThrough(B,C)); // D adalah titik potong h dan BC


Gambarlah itu.


\>plotPoint(D,value=1); // koordinat D ditampilkan

\>aspect(1); plotSegment(A,D): // tampilkan semua gambar hasil plot...()


![images/Tugas%206-003.png](images/Tugas%206-003.png)

Hitung luas ABC:


$$L_{\triangle ABC}= \frac{1}{2}AD.BC.$$\>norm(A-D)\*norm(B-C)/2 // AD=norm(A-D), BC=norm(B-C)


    1.5

Bandingkan dengan rumus determinan.


\>areaTriangle(A,B,C) // hitung luas segitiga langsung dengan fungsi


    1.5

Cara lain menghitung luas segitigas ABC:


\>distance(A,D)\*distance(B,C)/2


    1.5

Sudut di C.


\>degprint(computeAngle(B,C,A))


    36°52'11.63''

Sekarang lingkaran luar dari segitiga tersebut.


\>c=circleThrough(A,B,C); // lingkaran luar segitiga ABC

\>R=getCircleRadius(c); // jari2 lingkaran luar

\>O=getCircleCenter(c); // titik pusat lingkaran c

\>plotPoint(O,"O"); // gambar titik "O"

\>plotCircle(c,"Lingkaran luar segitiga ABC"):


![images/Tugas%206-005.png](images/Tugas%206-005.png)

Tampilkan koordinat titik pusat dan jari-jari lingkaran luar.


\>O, R


    [1.16667,  1.16667]
    1.17851130198

Sekarang akan digambar lingkaran dalam segitiga ABC. Titik pusat lingkaran dalam adalah titik potong
garis-garis bagi sudut.


\>l=angleBisector(A,C,B); // garis bagi <ACB

\>g=angleBisector(C,A,B); // garis bagi <CAB

\>P=lineIntersection(l,g) // titik potong kedua garis bagi sudut


    [0.86038,  0.86038]

Tambahkan semuanya ke dalam plot.


\>color(5); plotLine(l); plotLine(g); color(1); // gambar kedua garis bagi sudut

\>plotPoint(P,"P"); // gambar titik potongnya

\>r=norm(P-projectToLine(P,lineThrough(A,B))) // jari-jari lingkaran dalam


    0.509653732104

\>plotCircle(circleWithCenter(P,r),"Lingkaran dalam segitiga ABC"): // gambar lingkaran dalam


![images/Tugas%206-006.png](images/Tugas%206-006.png)

## Latihan

1. Tentukan ketiga titik singgung lingkaran dalam dengan sisi-sisi segitiga ABC.


2. Gambar segitiga dengan titik-titik sudut ketiga titik singgung tersebut. Merupakan segitiga apakah
itu?


3. Hitung luas segitiga tersebut.


4. Tunjukkan bahwa garis bagi sudut yang ke tiga juga melalui titik pusat lingkaran dalam.


5. Gambar jari-jari lingkaran dalam.


6. Hitung luas lingkaran luar dan luas lingkaran dalam segitiga ABC. Adakah hubungan antara luas
kedua lingkaran tersebut dengan luas segitiga ABC?


7. Tunjukan bahwa ketiga garis sumbu masing-masing sisi segitiga ABC berpotongan di satu titik


8. Tunjukan bahwa ketiga garis bagi sudut segitiga ABC Berpotongan di satu titik


9. Tunjukan bahwa ketiga garis tinggi segitiga ABC berpotongan di satu titik


10. Tunjukan bahwa ketiga garis berat segitiga ABC berpotongan di satu titik


\>clg; &remvalue(all)


    
                                                     []
    

\>setPlotRange(-0.5, 2.5, -0.5, 2.5);

\>A=[1,0]; B=[0,1]; C=[2,2]; 

\>plotPoint(A,"A"); plotPoint(B,"B"); plotPoint(C,"C"):


![images/Tugas%206-007.png](images/Tugas%206-007.png)

\>plotSegment(A,B,"c"); plotSegment(B,C,"a"); plotSegment(A,C,"b"):


![images/Tugas%206-008.png](images/Tugas%206-008.png)

\>g1 = angleBisector(A,B,C); g2 = angleBisector(B,A,C); g3=angleBisector(A,C,B);

\>P = lineIntersection(g1,g2); 

\>r = distance(P, projectToLine(P, lineThrough(A,B))); r


    0.509653732104

\>T1 = projectToLine(P, lineThrough(A,B));

\>T2 = projectToLine(P, lineThrough(B,C));

\>T3 = projectToLine(P, lineThrough(A,C));

\>T1, T2, T3


    [0.5,  0.5]
    [0.632456,  1.31623]
    [1.31623,  0.632456]

\>plotLine(g1,""); plotLine(g2,""); plotLine(g3, ""):


![images/Tugas%206-009.png](images/Tugas%206-009.png)

\>plotCircle([P[1],P[2],r]):


![images/Tugas%206-010.png](images/Tugas%206-010.png)

\>color(2);

\>plotPoint(T1,"T1"); plotPoint(T2,"T2"); plotPoint(T3,"T3"):


![images/Tugas%206-011.png](images/Tugas%206-011.png)

Jadi, titik singgung lingkaran adalah T1,T2,T3 dengan lingkaran yang tertera pada segitiga sama kaki
dan setiap garis bagi sudut melalui titik pusat lingkaran dalam.


\>plotSegment(T1, T2, "t1"); plotSegment(T2, T3, "t2"); plotSegment(T3, T1, "t3"):


![images/Tugas%206-012.png](images/Tugas%206-012.png)

\>L=areaTriangle(A,B,C)


    1.5

\>areaTriangle(T1, T2, T3)


    0.324341649025

\>color(3);

\>plotSegment(P, T1, "r"); plotSegment(P, T2, "r"); plotSegment(P, T3, "r"):


![images/Tugas%206-013.png](images/Tugas%206-013.png)

Jari-jari lingkaran dalam


\>getCircleRadius(circleThrough(A,B,C))


    1.17851130198

\>color(4); G1=perpendicular((A+B)/2,lineThrough(A,B)); G2=perpendicular((A+C)/2,lineThrough(A,C));  ...  
\>   G3=perpendicular((B+C)/2,lineThrough(B,C));

\>plotLine(G1); plotLine(G2); plotLine(G3):


![images/Tugas%206-014.png](images/Tugas%206-014.png)

\>P2=lineIntersection(G1,G2)


    [1.16667,  1.16667]

\>R=distance(P2,A)


    1.17851130198

\>plotCircle([P2[1],P2[2],R]):


![images/Tugas%206-015.png](images/Tugas%206-015.png)

\>luaskecil=pi\*r^2


    0.81601903655

\>luasbesar=pi\*R^2


    4.36332312999

\>c=distance(A,B); b=distance(A,C); a=distance(B,C); a, b, c


    2.2360679775
    2.2360679775
    1.41421356237

\>s=1/2\*(a+b+c)


    2.94317475869

\>L


    1.5

\>pi\*(L/s)^2


    0.81601903655

\>R


    1.17851130198

\>a\*b\*c/(4\*L)


    1.17851130198

Jadi, terdapat hubungan, yaitu


$$r=\frac{L}{s}$$dan


$$R=\frac{abc}{4L}$$\>AB=lineThrough(A,B); AC=lineThrough(A,C); BC=lineThrough(B,C); 

\>l1=perpendicular(A,BC); l2=perpendicular(B,AC); l3=perpendicular(C,AB); 

\>color(6); plotLine(l1); plotLine(l2); plotLine(l3):


![images/Tugas%206-018.png](images/Tugas%206-018.png)

\>BeratA = lineThrough(A, (B+C)/2); BeratB = lineThrough(B, (A+C)/2); ...  
\>   BeratC = lineThrough(C, (A+B)/2);

\>color(2); plotLine(BeratA); plotLine(BeratB); plotLine(BeratC):


![images/Tugas%206-019.png](images/Tugas%206-019.png)

# Contoh 2: Geometri Simbolik

Kita dapat menghitung geometri secara eksak dan simbolik menggunakan Maxima.


File geometry.e menyediakan fungsi yang sama (dan lebih banyak) di Maxima. Namun, kita dapat
menggunakan perhitungan simbolik sekarang.


\>A &= [1,0]; B &= [0,1]; C &= [2,2]; // menentukan tiga titik A, B, C


Fungsi untuk garis dan lingkaran bekerja sama seperti fungsi Euler, namun menyediakan perhitungan
simbolik.


\>c &= lineThrough(B,C) // c=BC


    
                                 [- 1, 2, 2]
    

Kita dapat memperoleh persamaan garis dengan mudah.


\>$getLineEquation(c,x,y), $solve(%,y) | expand // persamaan garis c


$$\left[ y=\frac{x}{2}+1 \right] $$![images/Tugas%206-021.png](images/Tugas%206-021.png)

\>$getLineEquation(lineThrough([x1,y1],[x2,y2]),x,y), $solve(%,y) // persamaan garis melalui(x1, y1) dan (x2, y2)


$$\left[ y=\frac{-\left({\it x_1}-x\right)\,{\it y_2}-\left(x-  {\it x_2}\right)\,{\it y_1}}{{\it x_2}-{\it x_1}} \right] $$![images/Tugas%206-023.png](images/Tugas%206-023.png)

\>$getLineEquation(lineThrough(A,[x1,y1]),x,y) // persamaan garis melalui A dan (x1, y1)


$$\left({\it x_1}-1\right)\,y-x\,{\it y_1}=-{\it y_1}$$\>h &= perpendicular(A,lineThrough(B,C)) // h melalui A tegak lurus BC


    
                                  [2, 1, 2]
    

\>Q &= lineIntersection(c,h) // Q titik potong garis c=BC dan h


    
                                     2  6
                                    [-, -]
                                     5  5
    

\>$projectToLine(A,lineThrough(B,C)) // proyeksi A pada BC


$$\left[ \frac{2}{5} , \frac{6}{5} \right] $$\>$distance(A,Q) // jarak AQ


$$\frac{3}{\sqrt{5}}$$\>cc &= circleThrough(A,B,C); $cc // (titik pusat dan jari-jari) lingkaran melalui A, B, C


$$\left[ \frac{7}{6} , \frac{7}{6} , \frac{5}{3\,\sqrt{2}} \right] $$\>r&=getCircleRadius(cc); $r , $float(r) // tampilkan nilai jari-jari


$$1.178511301977579$$![images/Tugas%206-029.png](images/Tugas%206-029.png)

\>$computeAngle(A,C,B) // nilai <ACB


$$\arccos \left(\frac{4}{5}\right)$$\>$solve(getLineEquation(angleBisector(A,C,B),x,y),y)[1] // persamaan garis bagi <ACB


$$y=x$$\>P &= lineIntersection(angleBisector(A,C,B),angleBisector(C,B,A)); $P // titik potong 2 garis bagi sudut


$$\left[ \frac{\sqrt{2}\,\sqrt{5}+2}{6} , \frac{\sqrt{2}\,\sqrt{5}+2  }{6} \right] $$\>P() // hasilnya sama dengan perhitungan sebelumnya


    [0.86038,  0.86038]

contoh 2.35


Sebuah titik sudut dari segitiga sama sisi berada di (2,3) dan persamaan sisi di depannya adalah
x+y=2. Tentukan persamaan sisi-sisi lainnya.


\>&A:[2,3]; ...  
\>   &mBC:-1;

\>// $solve(sqrt(3)\*(1-m)=m+1,m); m1&=rhs(%[1]); $m1 // tes saja

\>&solm: solve((tan(pi/3))^2=((m-mBC)/(1+m\*mBC))^2,m); ...  
\>   &m1:radcan(rhs(solm[1])); ...  
\>   &m2:radcan(rhs(solm[2])); $m1, $m2


$$\sqrt{3}+2$$![images/Tugas%206-034.png](images/Tugas%206-034.png)

\>&l1:y-A[2]=m1\*(x-A[1]); ...  
\>   &l2:y-A[2]=m2\*(x-A[1]);

\>g1 &= expand(lhs(l1)-rhs(l1))=0; $g1


$$y+\sqrt{3}\,x-2\,x-2\,\sqrt{3}+1=0$$\>g2 &= expand(lhs(l2)-rhs(l2))=0; $g2


$$y-\sqrt{3}\,x-2\,x+2\,\sqrt{3}+1=0$$\>$y-A[2]=m1\*(x-A[1])


$$y-3=\left(2-\sqrt{3}\right)\,\left(x-2\right)$$\>$y-A[2]=m2\*(x-A[1])


$$y-3=\left(\sqrt{3}+2\right)\,\left(x-2\right)$$\>A=[2,3]; ...  
\>   m1=2-sqrt(3); ...  
\>   m2=2+sqrt(3); ...  
\>   function f1(x)&=m1\*(x-A[1])+A[2]; ...  
\>   function f2(x)&=m2\*(x-A[1])+A[2]; ...  
\>   function f3(x)&=2-x; ...  
\>   aspect(1); ...  
\>   plot2d("f1",a=-1,b=3,c=0,d=4); ...  
\>   plot2d("f2",\>add); ...  
\>   plot2d("f3",\>add); ...  
\>   plot2d(A[1],A[2],points=true,style="o",\>add):


![images/Tugas%206-039.png](images/Tugas%206-039.png)

Contoh 2.36


Satu diagonal dari segiempat adalah bagian dari garis


$$\frac{x}{a}+\frac{y}{b}=1$$

yang intersep di antara sumbu-sumbu. Tentukan persamaan diagonal lainnya.


\>m1&=-b/a; $m1


$$-\frac{b}{a}$$\>m2&=a/b; $m2


$$\frac{a}{b}$$\>A&=[a,0]; B&=[0,b]; $A, $B


$$\left[ 0 , b \right] $$![images/Tugas%206-044.png](images/Tugas%206-044.png)

\>g1&=lineThrough(A,B); $g1


$$\left[ -b , -a , -a\,b \right] $$\>g2&=middlePerpendicular(A,B); $g2


$$\left[ a , -b , \frac{a^2}{2}-\frac{b^2}{2} \right] $$\>$getLineEquation(g2,x,y), $solve(%,y)


$$\left[ y=\frac{2\,a\,x+b^2-a^2}{2\,b} \right] $$![images/Tugas%206-048.png](images/Tugas%206-048.png)

Contoh 4.5


Tunjukkan bahwa garis 4x-y=17 adalah sebuah diameter dari lingkaran x^2+y^2-8x+2y=0


Karena


$$x^2+y^2-8x+2y=0 \rightarrow (x-4)^2+(y+1)^2=17$$memiliki pusat (4,-1) dan jari-jari sqrt(17)


\>c&=[4,-1,sqrt(17)]; $c


$$\left[ 4 , -1 , \sqrt{17} \right] $$\>Cc&=getCircleEquation(c,x,y); $Cc


$$\left(y+1\right)^2+\left(x-4\right)^2=17$$\>g&=[4,-1,17]; $g


$$\left[ 4 , -1 , 17 \right] $$\>l&=getLineEquation(g,x,y); $l


$$4\,x-y=17$$\>$solve([Cc,l],[x,y])


$$\left[ \left[ x=5 , y=3 \right]  , \left[ x=3 , y=-5 \right]    \right] $$\>A=[5,3]; B=[3,-5]; ...  
\>   M=(A+B)/2


    [4,  -1]

\>aspect(1); ...  
\>   plot2d("(x-4)^2+(y+1)^2-17",level=0,a=-1,b=9,c=-6,d=4); ...  
\>   plot2d("4\*x-17",\>add); ...  
\>   plot2d(5,3,points=true,style="o",\>add); ...  
\>   plot2d(3,-5,points=true,style="o",\>add); ...  
\>   plot2d(4,-1,points=true,style="o",\>add):


![images/Tugas%206-055.png](images/Tugas%206-055.png)

## Perpotongan Garis dan Lingkaran

Tentu saja, kita juga dapat memotong garis dengan lingkaran, dan lingkaran dengan lingkaran.


\>A &:= [1,0]; c=circleWithCenter(A,4);

\>B &:= [1,2]; C &:= [2,1]; l=lineThrough(B,C);

\>setPlotRange(5); plotCircle(c); plotLine(l);


Perpotongan sebuah garis dengan lingkaran menghasilkan dua titik dan jumlah titik potongnya.


\>{P1,P2,f}=lineCircleIntersections(l,c);

\>P1, P2, f


    [4.64575,  -1.64575]
    [-0.645751,  3.64575]
    2

\>plotPoint(P1); plotPoint(P2):


![images/Tugas%206-056.png](images/Tugas%206-056.png)

Hal yang sama di Maxima.


\>c &= circleWithCenter(A,4) // lingkaran dengan pusat A jari-jari 4


    
                                  [1, 0, 4]
    

\>l &= lineThrough(B,C) // garis l melalui B dan C


    
                                  [1, 1, 3]
    

\>$lineCircleIntersections(l,c) | radcan, // titik potong lingkaran c dan garis l


$$\left[ \left[ \sqrt{7}+2 , 1-\sqrt{7} \right]  , \left[ 2-\sqrt{7}   , \sqrt{7}+1 \right]  \right] $$Akan ditunjukkan bahwa sudut-sudut yang menghadap busur yang sama adalah sama besar.


\>C=A+normalize([-2,-3])\*4; plotPoint(C); plotSegment(P1,C); plotSegment(P2,C);

\>degprint(computeAngle(P1,C,P2))


    69°17'42.68''

\>C=A+normalize([-4,-3])\*4; plotPoint(C); plotSegment(P1,C); plotSegment(P2,C);

\>degprint(computeAngle(P1,C,P2))


    69°17'42.68''

\>insimg;


![images/Tugas%206-058.png](images/Tugas%206-058.png)

## Garis Sumbu

Berikut adalah langkah-langkah menggambar garis sumbu ruas garis AB:


1. Gambar lingkaran dengan pusat A melalui B.


2. Gambar lingkaran dengan pusat B melalui A.


3. Tarik garis melalui kedua titik potong kedua lingkaran tersebut. Garis ini merupakan garis sumbu
(melalui titik tengah dan tegak lurus) AB.


\>A=[2,2]; B=[-1,-2];

\>c1=circleWithCenter(A,distance(A,B));

\>c2=circleWithCenter(B,distance(A,B));

\>{P1,P2,f}=circleCircleIntersections(c1,c2);

\>l=lineThrough(P1,P2);

\>setPlotRange(5); plotCircle(c1); plotCircle(c2);

\>plotPoint(A); plotPoint(B); plotSegment(A,B); plotLine(l):


![images/Tugas%206-059.png](images/Tugas%206-059.png)

Selanjutnya, kita melakukan hal yang sama di Maxima dengan koordinat umum.


\>A &= [a1,a2]; B &= [b1,b2];

\>c1 &= circleWithCenter(A,distance(A,B));

\>c2 &= circleWithCenter(B,distance(A,B));

\>P &= circleCircleIntersections(c1,c2); P1 &= P[1]; P2 &= P[2];


Persamaan untuk titik-titik potong cukup rumit. Namun kita dapat menyederhanakannya, jika kita
menyelesaikan untuk y.


\>g &= getLineEquation(lineThrough(P1,P2),x,y);

\>$solve(g,y)


$$\left[ y=\frac{-\left(2\,{\it b_1}-2\,{\it a_1}\right)\,x+{\it b_2}  ^2+{\it b_1}^2-{\it a_2}^2-{\it a_1}^2}{2\,{\it b_2}-2\,{\it a_2}}   \right] $$Ini memang sama dengan garis sumbu, yang mana dihitung dengan cara yang sama sekali berbeda.


\>$solve(getLineEquation(middlePerpendicular(A,B),x,y),y)


$$\left[ y=\frac{-\left(2\,{\it b_1}-2\,{\it a_1}\right)\,x+{\it b_2}  ^2+{\it b_1}^2-{\it a_2}^2-{\it a_1}^2}{2\,{\it b_2}-2\,{\it a_2}}   \right] $$\>h &=getLineEquation(lineThrough(A,B),x,y);

\>$solve(h,y)


$$\left[ y=\frac{\left({\it b_2}-{\it a_2}\right)\,x-{\it a_1}\,  {\it b_2}+{\it a_2}\,{\it b_1}}{{\it b_1}-{\it a_1}} \right] $$Perhatikan hasil kali gradien garis g dan h adalah:


$$\frac{-(b_1-a_1)}{(b_2-a_2)}\times \frac{(b_2-a_2)}{(b_1-a_1)} = -1.$$Artinya kedua garis tegak lurus.


# Contoh 3: Rumus Heron

Rumus Heron menyatakan bahwa luas segitiga dengan panjang sisi-sisi a, b dan c adalah:


$$L = \sqrt{s(s-a)(s-b)(s-c)}\quad \text{ dengan } s=(a+b+c)/2,$$atau bisa ditulis dalam bentuk lain:


$$L = \frac{1}{4}\sqrt{(a+b+c)(b+c-a)(a+c-b)(a+b-c)}$$Untuk membuktikan hal ini kita misalkan C(0,0), B(a,0) dan A(x,y), b=AC, c=AB. Luas segitiga ABC
adalah


$$L_{\triangle ABC}=\frac{1}{2}a\times y.$$Nilai y didapat dengan menyelesaikan sistem persamaan:


$$x^2+y^2=b^2, \quad (x-a)^2+y^2=c^2.$$\>setPlotRange(-1,10,-1,8); plotPoint([0,0], "C(0,0)"); plotPoint([5.5,0], "B(a,0)");  ...  
\>    plotPoint([7.5,6], "A(x,y)");

\>plotSegment([0,0],[5.5,0], "a",25); plotSegment([5.5,0],[7.5,6],"c",15);  ...  
\>   plotSegment([0,0],[7.5,6],"b",25); 

\>plotSegment([7.5,6],[7.5,0],"t=y",25):


![images/Tugas%206-068.png](images/Tugas%206-068.png)

\>&remvalue(x,y,a,b,c); &assume(a\>0); sol &= solve([x^2+y^2=b^2,(x-a)^2+y^2=c^2],[x,y]); $sol


$$\left[ \left[ x=\frac{-c^2+b^2+a^2}{2\,a} , y=-\frac{\sqrt{-c^4+2\,  b^2\,c^2+2\,a^2\,c^2-b^4+2\,a^2\,b^2-a^4}}{2\,a} \right]  , \left[ x=  \frac{-c^2+b^2+a^2}{2\,a} , y=\frac{\sqrt{-c^4+2\,b^2\,c^2+2\,a^2\,c  ^2-b^4+2\,a^2\,b^2-a^4}}{2\,a} \right]  \right] $$Ekstrak solusi y.


\>ysol &= y with sol[2][2]; $'y=sqrt(factor(ysol^2))


$$y=\frac{\sqrt{\left(-c+b+a\right)\,\left(c-b+a\right)\,\left(c+b-a  \right)\,\left(c+b+a\right)}}{2\,a}$$Kita mendapatkan rumus Heron.


\>function H(a,b,c) &= sqrt(factor((ysol\*a/2)^2)); $'H(a,b,c)=H(a,b,c)


$$H\left(a , b , c\right)=\frac{\sqrt{\left(-c+b+a\right)\,\left(c-b+  a\right)\,\left(c+b-a\right)\,\left(c+b+a\right)}}{4}$$\>$'Luas=H(2,5,6) // luas segitiga dengan panjang sisi-sisi 2, 5, 6


$${\it Luas}=\frac{3\,\sqrt{39}}{4}$$Tentu saja, setiap segitiga siku-siku adalah kasus yang sudah dikenal luas.


\>H(3,4,5) //luas segitiga siku-siku dengan panjang sisi 3, 4, 5


    6

Dan ini juga jelas, bahwa ini adalah segitiga dengan luas maksimal serta dua sisinya 3 dan 4.


\>aspect (1.5); plot2d(&H(3,4,x),1,7): // Kurva luas segitiga sengan panjang sisi 3, 4, x (1<= x <=7)


![images/Tugas%206-073.png](images/Tugas%206-073.png)

Kasus umum juga berlaku.


\>$solve(diff(H(a,b,c)^2,c)=0,c)


$$\left[ c=-\sqrt{b^2+a^2} , c=\sqrt{b^2+a^2} , c=0 \right] $$Sekarang mari kita temukan himpunan semua titik di mana b+c=d untuk suatu konstanta d. Diketahui
secara luas bahwa ini adalah sebuah elips.


\>s1 &= subst(d-c,b,sol[2]); $s1


$$\left[ x=\frac{\left(d-c\right)^2-c^2+a^2}{2\,a} , y=\frac{\sqrt{-  \left(d-c\right)^4+2\,c^2\,\left(d-c\right)^2+2\,a^2\,\left(d-c  \right)^2-c^4+2\,a^2\,c^2-a^4}}{2\,a} \right] $$Dan buat fungsinya dari hal ini.


\>function fx(a,c,d) &= rhs(s1[1]); $fx(a,c,d), function fy(a,c,d) &= rhs(s1[2]); $fy(a,c,d)


$$\frac{\sqrt{-\left(d-c\right)^4+2\,c^2\,\left(d-c\right)^2+2\,a^2\,  \left(d-c\right)^2-c^4+2\,a^2\,c^2-a^4}}{2\,a}$$![images/Tugas%206-077.png](images/Tugas%206-077.png)

Sekarang kita dapat menggambar himpunannya. Sisi b bervariasi dari 1 hingga 4. Sudah sangat diketahui
bahwa kita akan mendapatkan elips.


\>aspect(1); plot2d(&fx(3,x,5),&fy(3,x,5),xmin=1,xmax=4,square=1):


![images/Tugas%206-078.png](images/Tugas%206-078.png)

Kita dapat memeriksa persamaan umum untuk elips ini, yaitu


$$\frac{(x-x_m)^2}{u^2}+\frac{(y-y_m)}{v^2}=1,$$di mana (xm,ym) adalah titik pusat, serta u dan v adalah setengah sumbunya.


\>$ratsimp((fx(a,c,d)-a/2)^2/u^2+fy(a,c,d)^2/v^2 with [u=d/2,v=sqrt(d^2-a^2)/2])


$$1$$Kita melihat bahwa tinggi dan juga luas segitiga menjadi maksimal untuk x=0. Dengan demikian luas
segitiga dengan a+b+c=d adalah maksimal, jika berupa segitiga sama sisi. Kita ingin menurunkannya
secara analitik.


\>eqns &= [diff(H(a,b,d-(a+b))^2,a)=0,diff(H(a,b,d-(a+b))^2,b)=0]; $eqns


$$\left[ \frac{d\,\left(d-2\,a\right)\,\left(d-2\,b\right)}{8}-\frac{  \left(-d+2\,b+2\,a\right)\,d\,\left(d-2\,b\right)}{8}=0 , \frac{d\,  \left(d-2\,a\right)\,\left(d-2\,b\right)}{8}-\frac{\left(-d+2\,b+2\,  a\right)\,d\,\left(d-2\,a\right)}{8}=0 \right] $$Kita mendapatkan beberapa nilai minimum, yang dimiliki oleh segitiga dengan satu sisinya 0, dan
solusinya a=b=c=d/3.


\>$solve(eqns,[a,b])


$$\left[ \left[ a=\frac{d}{3} , b=\frac{d}{3} \right]  , \left[ a=0   , b=\frac{d}{2} \right]  , \left[ a=\frac{d}{2} , b=0 \right]  ,   \left[ a=\frac{d}{2} , b=\frac{d}{2} \right]  \right] $$Terdapat juga metode Lagrange, memaksimalkan H(a,b,c)^2 terhadap a+b+c=d.


\>&solve([diff(H(a,b,c)^2,a)=la,diff(H(a,b,c)^2,b)=la, ...  
\>      diff(H(a,b,c)^2,c)=la,a+b+c=d],[a,b,c,la])


    
                         d      d
            [[a = 0, b = -, c = -, la = 0], 
                         2      2
         d             d                d      d
    [a = -, b = 0, c = -, la = 0], [a = -, b = -, c = 0, la = 0], 
         2             2                2      2
                                3
         d      d      d       d
    [a = -, b = -, c = -, la = ---]]
         3      3      3       108
    

Kita dapat membuat plot dari situasi ini


Pertama, tentukan titik-titiknya di Maxima.


\>A &= at([x,y],sol[2]); $A


$$\left[ \frac{-c^2+b^2+a^2}{2\,a} , \frac{\sqrt{-c^4+2\,b^2\,c^2+2\,  a^2\,c^2-b^4+2\,a^2\,b^2-a^4}}{2\,a} \right] $$\>B &= [0,0]; $B, C &= [a,0]; $C


$$\left[ a , 0 \right] $$![images/Tugas%206-085.png](images/Tugas%206-085.png)

Kemudian tentukan rentang plot, dan gambarlah titik-titiknya.


\>setPlotRange(0,5,-2,3); ...  
\>   a=4; b=3; c=2; ...  
\>   plotPoint(mxmeval("B"),"B"); plotPoint(mxmeval("C"),"C"); ...  
\>   plotPoint(mxmeval("A"),"A"):


![images/Tugas%206-086.png](images/Tugas%206-086.png)

Gambarlah ruas-ruas garisnya.


\>plotSegment(mxmeval("A"),mxmeval("C")); ...  
\>   plotSegment(mxmeval("B"),mxmeval("C")); ...  
\>   plotSegment(mxmeval("B"),mxmeval("A")):


![images/Tugas%206-087.png](images/Tugas%206-087.png)

Hitung garis sumbunya di Maxima.


\>h &= middlePerpendicular(A,B); g &= middlePerpendicular(B,C);


Dan titik pusat dari lingkaran luar.


\>U &= lineIntersection(h,g);


Kita mendapatkan rumus untuk jari-jari lingkaran luar.


\>&assume(a\>0,b\>0,c\>0); $distance(U,B) | radcan


$$\frac{i\,a\,b\,c}{\sqrt{c-b-a}\,\sqrt{c-b+a}\,\sqrt{c+b-a}\,\sqrt{c  +b+a}}$$Mari kita tambahkan ini ke plot.


\>plotPoint(U()); ...  
\>   plotCircle(circleWithCenter(mxmeval("U"),mxmeval("distance(U,C)"))):


![images/Tugas%206-089.png](images/Tugas%206-089.png)

Menggunakan geometri, kita menurunkan rumus sederhana


$$\frac{a}{\sin(\alpha)}=2r$$untuk jari-jarinya. Kita dapat memeriksa, apakah ini benar dengan Maxima. Maxima akan memfaktorkan
ini hanya jika kita mengkuadratkannya.


\>$c^2/sin(computeAngle(A,B,C))^2  | factor


$$-\frac{4\,a^2\,b^2\,c^2}{\left(c-b-a\right)\,\left(c-b+a\right)\,  \left(c+b-a\right)\,\left(c+b+a\right)}$$# Contoh 4: Garis Euler dan Parabola

Garis Euler adalah garis yang ditentukan dari sembarang segitiga yang bukan sama sisi. Ini adalah
garis pusat dari segitiga, dan melewati beberapa titik penting yang ditentukan dari segitiga,
termasuk titik tinggi, titik pusat lingkaran luar, titik berat, titik Exeter dan titik pusat
lingkaran sembilan titik pada segitiga.


Sebagai demonstrasi, kita menghitung dan menggambar garis Euler dalam sebuah segitiga.


Pertama, kita mendefinisikan titik-titik sudut segitiga di Euler. Kita menggunakan definisi yang
dapat dilihat dalam ekspresi simbolik.


\>A::=[-1,-1]; B::=[2,0]; C::=[1,2];


Untuk memplot objek geometri, kita mengatur area plot, dan menambahkan titik-titiknya ke dalamnya.
Semua plot objek geometri ditambahkan ke plot saat ini.


\>setPlotRange(3); plotPoint(A,"A"); plotPoint(B,"B"); plotPoint(C,"C");


Kita juga dapat menambahkan sisi-sisi dari segitiga.


\>plotSegment(A,B,""); plotSegment(B,C,""); plotSegment(C,A,""):


![images/Tugas%206-092.png](images/Tugas%206-092.png)

Berikut adalah luas segitiga, menggunakan rumus determinan. Tentu saja, kita harus mengambil nilai
mutlak dari hasil ini.


\>$areaTriangle(A,B,C)


$$-\frac{7}{2}$$Kita dapat menghitung koefisien dari sisi c.


\>c &= lineThrough(A,B)


    
                                [- 1, 3, - 2]
    

Dan juga mendapatkan rumus untuk garis ini.


\>$getLineEquation(c,x,y)


$$3\,y-x=-2$$Untuk bentuk Hesse, kita perlu menentukan suatu titik, sedemikian rupa sehingga titik tersebut berada
di sisi positif bentuk Hesse. Memasukkan titik tersebut akan menghasilkan jarak positif ke garisnya.


\>$getHesseForm(c,x,y,C), $at(%,[x=C[1],y=C[2]])


$$\frac{7}{\sqrt{10}}$$![images/Tugas%206-096.png](images/Tugas%206-096.png)

Sekarang kita menghitung lingkaran luar ABC.


\>LL &= circleThrough(A,B,C); $getCircleEquation(LL,x,y)


$$\left(y-\frac{5}{14}\right)^2+\left(x-\frac{3}{14}\right)^2=\frac{  325}{98}$$\>O &= getCircleCenter(LL); $O


$$\left[ \frac{3}{14} , \frac{5}{14} \right] $$Gambarlah lingkaran dan titik pusatnya. Cu dan U bersifat simbolik. Kita mengevaluasi
ekspresi-ekspresi ini untuk Euler.


\>plotCircle(LL()); plotPoint(O(),"O"):


![images/Tugas%206-099.png](images/Tugas%206-099.png)

Kita dapat menghitung perpotongan garis-garis tinggi pada ABC (titik tinggi/orthocenter) secara
numerik dengan perintah berikut.


\>H &= lineIntersection(perpendicular(A,lineThrough(C,B)),...  
\>     perpendicular(B,lineThrough(A,C))); $H


$$\left[ \frac{11}{7} , \frac{2}{7} \right] $$Sekarang kita dapat menghitung garis Euler dari segitiga.


\>el &= lineThrough(H,O); $getLineEquation(el,x,y)


$$-\frac{19\,y}{14}-\frac{x}{14}=-\frac{1}{2}$$Tambahkan ini ke plot kita.


\>plotPoint(H(),"H"); plotLine(el(),"Garis Euler"):


![images/Tugas%206-102.png](images/Tugas%206-102.png)

Pusat gravitasi (titik berat) seharusnya berada di garis ini.


\>M &= (A+B+C)/3; $getLineEquation(el,x,y) with [x=M[1],y=M[2]]


$$-\frac{1}{2}=-\frac{1}{2}$$\>plotPoint(M(),"M"): // titik berat


![images/Tugas%206-104.png](images/Tugas%206-104.png)

Teori mengatakan bahwa MH=2*MO. Kita perlu menyederhanakannya dengan radcan untuk mencapai hal ini.


\>$distance(M,H)/distance(M,O)|radcan


$$2$$Fungsi-fungsi ini juga mencakup fungsi untuk sudut.


\>$computeAngle(A,C,B), degprint(%())


$$\arccos \left(\frac{4}{\sqrt{5}\,\sqrt{13}}\right)$$    60°15'18.43''

Persamaan untuk titik pusat lingkaran dalam tidak begitu bagus (sederhana).


\>Q &= lineIntersection(angleBisector(A,C,B),angleBisector(C,B,A))|radcan; $Q


$$\left[ \frac{\left(2^{\frac{3}{2}}+1\right)\,\sqrt{5}\,\sqrt{13}-15  \,\sqrt{2}+3}{14} , \frac{\left(\sqrt{2}-3\right)\,\sqrt{5}\,\sqrt{  13}+5\,2^{\frac{3}{2}}+5}{14} \right] $$Mari kita hitung juga ekspresi untuk jari-jari lingkaran dalam.


\>r &= distance(Q,projectToLine(Q,lineThrough(A,B)))|ratsimp; $r


$$\frac{\sqrt{\left(-41\,\sqrt{2}-31\right)\,\sqrt{5}\,\sqrt{13}+115  \,\sqrt{2}+614}}{7\,\sqrt{2}}$$\>LD &=  circleWithCenter(Q,r); // Lingkaran dalam


Mari kita tambahkan ini ke dalam plot.


\>color(5); plotCircle(LD()):


![images/Tugas%206-109.png](images/Tugas%206-109.png)

## Parabola

Selanjutnya akan dicari persamaan tempat kedudukan titik-titik yang berjarak sama ke titik C dan ke
garis AB.


\>p &= getHesseForm(lineThrough(A,B),x,y,C)-distance([x,y],C); $p='0


$$\frac{3\,y-x+2}{\sqrt{10}}-\sqrt{\left(2-y\right)^2+\left(1-x  \right)^2}=0$$Persamaan tersebut dapat digambar menjadi satu dengan gambar sebelumnya.


\>plot2d(p,level=0,add=1,contourcolor=6):


![images/Tugas%206-111.png](images/Tugas%206-111.png)

Ini seharusnya menjadi sebuah fungsi, tetapi solver bawaan Maxima hanya dapat menemukan solusinya,
jika kita mengkuadratkan persamaannya. Akibatnya, kita mendapatkan solusi semu.


\>akar &= solve(getHesseForm(lineThrough(A,B),x,y,C)^2-distance([x,y],C)^2,y)


    
            [y = - 3 x - sqrt(70) sqrt(9 - 2 x) + 26, 
                                  y = - 3 x + sqrt(70) sqrt(9 - 2 x) + 26]
    

Solusi pertamanya adalah


$$y=-3\,x-\sqrt{70}\,\sqrt{9-2\,x}+26$$Menambahkan solusi pertama ke dalam plot menunjukkan, bahwa ini memang jalur yang kita cari. Teori
memberitahu kita bahwa ini adalah sebuah parabola yang diputar.


\>plot2d(&rhs(akar[1]),add=1):


![images/Tugas%206-113.png](images/Tugas%206-113.png)

\>function g(x) &= rhs(akar[1]); $'g(x)= g(x)// fungsi yang mendefinisikan kurva di atas


$$g\left(x\right)=-3\,x-\sqrt{70}\,\sqrt{9-2\,x}+26$$\>T &=[-1, g(-1)]; // ambil sebarang titik pada kurva tersebut

\>dTC &= distance(T,C); $fullratsimp(dTC), $float(%) // jarak T ke C


$$2.135605779339061$$![images/Tugas%206-116.png](images/Tugas%206-116.png)

\>U &= projectToLine(T,lineThrough(A,B)); $U // proyeksi T pada garis AB 


$$\left[ \frac{80-3\,\sqrt{11}\,\sqrt{70}}{10} , \frac{20-\sqrt{11}\,  \sqrt{70}}{10} \right] $$\>dU2AB &= distance(T,U); $fullratsimp(dU2AB), $float(%) // jatak T ke AB


$$2.135605779339061$$![images/Tugas%206-119.png](images/Tugas%206-119.png)

Ternyata jarak T ke C sama dengan jarak T ke AB. Coba Anda pilih titik T yang lain dan ulangi
perhitungan-perhitungan di atas untuk menunjukkan bahwa hasilnya juga sama.


# Contoh 5: Trigonometri Rasional

Ini terinspirasi dari presentasi N.J. Wildberger. Di dalam bukunya "Divine Proportions", Wildberger
mengusulkan untuk mengganti gagasan klasik dari jarak (distance) dan sudut (angle) dengan jarak
kuadrat (quadrance) dan bentangan (spread). Dengan menggunakan kedua hal ini, sangatlah mungkin untuk
menghindari fungsi trigonometri pada banyak contoh, dan tetap berada di bentuk "rasional".


Berikut ini, saya memperkenalkan konsep-konsep tersebut, dan memecahkan beberapa masalah. Saya
menggunakan perhitungan simbolik Maxima di sini, yang mana sebenarnya menutupi keunggulan utama dari
trigonometri rasional bahwa perhitungan ini dapat dilakukan dengan menggunakan kertas dan pensil
saja. Anda dipersilakan untuk mengecek hasilnya tanpa menggunakan komputer.


Poin pentingnya adalah bahwa perhitungan rasional simbolis sering kali menghasilkan bentuk yang
sederhana. Sebaliknya, trigonometri klasik menghasilkan bentuk trigonometri yang rumit, yang mana
hanya bisa dievaluasi sebagai perkiraan numerik saja.


\>load geometry;


Untuk perkenalan pertama, kita menggunakan segitiga siku-siku dengan proporsi Mesir yang terkenal
yaitu 3, 4, dan 5. Perintah berikut adalah perintah Euler untuk memplot geometri bidang yang terdapat
dalam file Euler "geometry.e".


\>C&:=[0,0]; A&:=[4,0]; B&:=[0,3]; ...  
\>   setPlotRange(-1,5,-1,5); ...  
\>   plotPoint(A,"A"); plotPoint(B,"B"); plotPoint(C,"C"); ...  
\>   plotSegment(B,A,"c"); plotSegment(A,C,"b"); plotSegment(C,B,"a"); ...  
\>   insimg(30);


![images/Tugas%206-120.png](images/Tugas%206-120.png)

Tentu saja,


$$\sin(w_a)=\frac{a}{c},$$di mana wa adalah sudut di A. Cara yang biasa untuk menghitung sudut ini, adalah dengan mengambil
invers dari fungsi sinus. Hasilnya adalah sudut yang sulit dicerna, yang hanya bisa dicetak secara
perkiraan.


\>wa := arcsin(3/5); degprint(wa)


    36°52'11.63''

Trigonometri rasional mencoba menghindari ini.


Gagasan pertama trigonometri rasional adalah quadrance (jarak kuadrat), yang menggantikan jarak
(distance). Sebenarnya, ini hanyalah jarak yang dikuadratkan. Pada uraian berikut, a, b, dan c
menyatakan quadrance dari sisi-sisinya.


Lalu teorema Pythagoras secara sederhana menjadi a+b=c.


\>a &= 3^2; b &= 4^2; c &= 5^2; &a+b=c


    
                                   25 = 25
    

Gagasan kedua trigonometri rasional adalah bentangan (spread). Spread mengukur bukaan antara
garis-garis. Bernilai 0, jika garis-garis tersebut sejajar, dan 1, jika garis-garis tersebut tegak
lurus. Ini adalah kuadrat sinus dari sudut antara kedua garis tersebut.


Spread dari garis AB dan AC pada gambar di atas didefinisikan sebagai


$$s_a = \sin(\alpha)^2 = \frac{a}{c},$$di mana a dan c adalah quadrance dari setiap segitiga siku-siku dengan salah satu sudut di A.


\>sa &= a/c; $sa


$$\frac{9}{25}$$Ini lebih mudah dihitung daripada sudut, tentu saja. Tetapi Anda kehilangan sifat bahwa sudut-sudut
dapat dijumlahkan dengan mudah.


Tentu saja, kita dapat mengubah nilai perkiraan kita untuk sudut wa menjadi sebuah spread, dan
mencetaknya sebagai pecahan.


\>fracprint(sin(wa)^2)


    9/25

Aturan cosinus pada trigonometri klasik diterjemahkan menjadi "cross law" (hukum silang) berikut.


$$(c+b-a)^2 = 4 b c \, (1-s_a)$$Di sini a, b, dan c adalah quadrance sisi-sisi segitiga, dan sa adalah spread pada sudut A. Sisi a,
seperti biasa, berhadapan dengan sudut A.


Hukum-hukum ini diimplementasikan dalam file geometry.e yang kita muat ke dalam Euler.


\>$crosslaw(aa,bb,cc,saa)


$$\left[ \left({\it bb}-{\it aa}+\frac{7}{6}\right)^2 , \left(  {\it bb}-{\it aa}+\frac{7}{6}\right)^2 , \left({\it bb}-{\it aa}+  \frac{5}{3\,\sqrt{2}}\right)^2 \right] =\left[ \frac{14\,{\it bb}\,  \left(1-{\it saa}\right)}{3} , \frac{14\,{\it bb}\,\left(1-{\it saa}  \right)}{3} , \frac{5\,2^{\frac{3}{2}}\,{\it bb}\,\left(1-{\it saa}  \right)}{3} \right] $$Pada kasus kita, kita mendapatkan


\>$crosslaw(a,b,c,sa)


$$1024=1024$$Mari kita gunakan cross law ini untuk mencari spread di A. Untuk melakukannya, kita membentuk aturan
silang untuk quadrance a, b, dan c, dan menyelesaikannya untuk spread sa yang belum diketahui.


Anda dapat melakukannya dengan tangan secara mudah, tetapi saya menggunakan Maxima. Tentu saja, kita
mendapatkan hasil yang sudah kita miliki.


\>$crosslaw(a,b,c,x), $solve(%,x)


$$\left[ x=\frac{9}{25} \right] $$![images/Tugas%206-128.png](images/Tugas%206-128.png)

Kita sudah mengetahuinya. Definisi spread adalah kasus khusus dari hukum silang.


Kita juga dapat menyelesaikan ini untuk a,b,c secara umum. Hasilnya adalah rumus yang menghitung
spread sudut suatu segitiga jika diberikan quadrance ketiga sisinya.


\>$solve(crosslaw(aa,bb,cc,x),x)


$$\left[ \left[ \frac{168\,{\it bb}\,x+36\,{\it bb}^2+\left(-72\,  {\it aa}-84\right)\,{\it bb}+36\,{\it aa}^2-84\,{\it aa}+49}{36} ,   \frac{168\,{\it bb}\,x+36\,{\it bb}^2+\left(-72\,{\it aa}-84\right)  \,{\it bb}+36\,{\it aa}^2-84\,{\it aa}+49}{36} , \frac{15\,2^{\frac{  5}{2}}\,{\it bb}\,x+18\,{\it bb}^2+\left(-36\,{\it aa}-15\,2^{\frac{  3}{2}}\right)\,{\it bb}+18\,{\it aa}^2-15\,2^{\frac{3}{2}}\,{\it aa}  +25}{18} \right] =0 \right] $$Kita bisa membuat fungsi dari hasilnya. Fungsi tersebut sudah didefinisikan pada file geometry.e dari
Euler.


\>$spread(a,b,c)


$$\frac{9}{25}$$Sebagai contoh, kita dapat menggunakannya untuk menghitung sudut segitiga dengan sisi


$$a, \quad a, \quad \frac{4a}{7}$$Hasilnya adalah bilangan rasional, yang tidak begitu mudah didapatkan jika kita menggunakan
trigonometri klasik.


\>$spread(a,a,4\*a/7)


$$\frac{6}{7}$$Ini adalah sudutnya dalam derajat.


\>degprint(arcsin(sqrt(6/7)))


    67°47'32.44''

## Contoh Lain

Sekarang, mari kita coba contoh yang lebih tingkat lanjut.


Kita menetapkan tiga sudut segitiga sebagai berikut.


\>A&:=[1,2]; B&:=[4,3]; C&:=[0,4]; ...  
\>   setPlotRange(-1,5,1,7); ...  
\>   plotPoint(A,"A"); plotPoint(B,"B"); plotPoint(C,"C"); ...  
\>   plotSegment(B,A,"c"); plotSegment(A,C,"b"); plotSegment(C,B,"a"); ...  
\>   insimg;


![images/Tugas%206-133.png](images/Tugas%206-133.png)

Menggunakan Pythagoras, mudah untuk menghitung jarak antara dua titik. Pertama saya menggunakan
fungsi jarak dari file Euler untuk geometri. Fungsi distance menggunakan geometri klasik.


\>$distance(A,B)


$$\sqrt{10}$$Euler juga memuat fungsi-fungsi untuk menghitung quadrance antara dua titik.


Pada contoh berikut, karena c+b tidak sama dengan a, segitiga tersebut bukanlah segitiga siku-siku.


\>c &= quad(A,B); $c, b &= quad(A,C); $b, a &= quad(B,C); $a,


$$17$$![images/Tugas%206-136.png](images/Tugas%206-136.png)

![images/Tugas%206-137.png](images/Tugas%206-137.png)

Pertama, mari kita hitung sudut tradisional. Fungsi computeAngle menggunakan metode biasa berdasarkan
perkalian titik dua vektor. Hasilnya adalah aproksimasi floating point.


$$A=<1,2>\quad B=<4,3>,\quad C=<0,4>$$$$\mathbf{a}=C-B=<-4,1>,\quad \mathbf{c}=A-B=<-3,-1>,\quad \beta=\angle ABC$$$$\mathbf{a}.\mathbf{c}=|\mathbf{a}|.|\mathbf{c}|\cos \beta$$$$\cos \angle ABC =\cos\beta=\frac{\mathbf{a}.\mathbf{c}}{|\mathbf{a}|.|\mathbf{c}|}=\frac{12-1}{\sqrt{17}\sqrt{10}}=\frac{11}{\sqrt{17}\sqrt{10}}$$\>wb &= computeAngle(A,B,C); $wb, $(wb/pi\*180)()


$$\arccos \left(\frac{11}{\sqrt{10}\,\sqrt{17}}\right)$$    32.4711922908

Menggunakan pensil dan kertas, kita dapat melakukan hal yang sama dengan cross law. Kita memasukkan
quadrance a, b, dan c ke dalam cross law dan selesaikan x.


\>$crosslaw(a,b,c,x), $solve(%,x), //(b+c-a)^=4b.c(1-x)


$$\left[ x=\frac{49}{50} \right] $$![images/Tugas%206-144.png](images/Tugas%206-144.png)

Itulah yang dilakukan oleh fungsi spread yang didefinisikan dalam "geometry.e".


\>sb &= spread(b,a,c); $sb


$$\frac{49}{170}$$Maxima mendapatkan hasil yang sama menggunakan trigonometri biasa, jika kita memaksanya. Maxima
menyelesaikan bentuk sin(arccos(...)) menjadi hasil pecahan. Sebagian besar siswa tidak dapat
melakukan hal ini.


\>$sin(computeAngle(A,B,C))^2


$$\frac{49}{170}$$Setelah kita mengetahui spread di B, kita dapat menghitung tinggi ha pada sisi a. Ingatlah bahwa


$$s_b=\frac{h_a}{c}$$berdasarkan definisinya.


\>ha &= c\*sb; $ha


$$\frac{49}{17}$$Gambar berikut telah dihasilkan dengan program geometri C.a.R., yang bisa menggambar quadrance dan
spread.


image: (20) Rational_Geometry_CaR.png


Berdasarkan definisi panjang ha adalah akar kuadrat dari nilai quadrance-nya.


\>$sqrt(ha)


$$\frac{7}{\sqrt{17}}$$Sekarang kita dapat menghitung luas segitiga. Jangan lupa, bahwa kita sedang berurusan dengan
quadrance!


\>$sqrt(ha)\*sqrt(a)/2


$$\frac{7}{2}$$Rumus determinan biasa memberikan hasil yang sama.


\>$areaTriangle(B,A,C)


$$\frac{7}{2}$$## Rumus Heron

Sekarang, mari kita selesaikan persoalan ini secara umum!


\>&remvalue(a,b,c,sb,ha);


Pertama-tama kita menghitung spread di B untuk segitiga dengan sisi-sisi a, b, dan c. Kemudian kita
hitung luas kuadratnya ("quadrea"?), memfaktorkannya dengan Maxima, dan kita mendapatkan rumus Heron
yang terkenal.


Harus diakui, ini sulit untuk dilakukan dengan pensil dan kertas.


\>$spread(b^2,c^2,a^2), $factor(%\*c^2\*a^2/4)


$$\frac{\left(-c+b+a\right)\,\left(c-b+a\right)\,\left(c+b-a\right)\,  \left(c+b+a\right)}{16}$$![images/Tugas%206-153.png](images/Tugas%206-153.png)

## Aturan Triple Spread

Kelemahan dari spread adalah tidak bisa dijumlahkan begitu saja layaknya sebuah sudut.


Meskipun demikian, tiga bentangan (spread) segitiga memenuhi aturan "triple spread" berikut.


\>&remvalue(sa,sb,sc); $triplespread(sa,sb,sc)


$$\left({\it sc}+{\it sb}+{\it sa}\right)^2=2\,\left({\it sc}^2+  {\it sb}^2+{\it sa}^2\right)+4\,{\it sa}\,{\it sb}\,{\it sc}$$Aturan ini berlaku untuk setiap tiga sudut yang berjumlah 180Â°.


$$\alpha+\beta+\gamma=\pi$$Karena spread dari


$$\alpha, \pi-\alpha$$adalah sama, aturan triple spread juga berlaku, jika


$$\alpha+\beta=\gamma$$Karena spread sudut negatifnya adalah sama, aturan triple spread juga berlaku, jika


$$\alpha+\beta+\gamma=0$$Sebagai contoh, kita dapat menghitung bentangan sudut 60Â°. Nilainya adalah 3/4. Namun, persamaannya
memiliki solusi kedua, di mana semua spread adalah 0.


\>$solve(triplespread(x,x,x),x)


$$\left[ x=\frac{3}{4} , x=0 \right] $$Spread dari 90Â° sudah jelas 1. Jika dua sudut berjumlah 90Â°, penyebaran mereka memecahkan persamaan
triple spread dengan a,b,1. Dari perhitungan berikut kita mendapatkan a+b=1.


\>$triplespread(x,y,1), $solve(%,x)


$$\left[ x=1-y \right] $$![images/Tugas%206-161.png](images/Tugas%206-161.png)

Karena spread dari 180Â°-t sama dengan spread dari t, rumus triple spread juga berlaku jika salah
satu sudut adalah jumlah atau selisih dari dua sudut lainnya.


Oleh karena itu kita dapat menemukan spread dari sudut ganda. Perhatikan bahwa di sini juga terdapat
dua solusi. Kita menjadikannya sebagai sebuah fungsi.


\>$solve(triplespread(a,a,x),x), function doublespread(a) &= factor(rhs(%[1]))


$$\left[ x=4\,a-4\,a^2 , x=0 \right] $$    
                                - 4 (a - 1) a
    

## Garis Bagi Sudut

Ini adalah situasi yang sudah kita ketahui.


\>C&:=[0,0]; A&:=[4,0]; B&:=[0,3]; ...  
\>   setPlotRange(-1,5,-1,5); ...  
\>   plotPoint(A,"A"); plotPoint(B,"B"); plotPoint(C,"C"); ...  
\>   plotSegment(B,A,"c"); plotSegment(A,C,"b"); plotSegment(C,B,"a"); ...  
\>   insimg;


![images/Tugas%206-163.png](images/Tugas%206-163.png)

Mari kita hitung panjang garis bagi sudut di A. Tetapi kita ingin menyelesaikannya untuk a,b,c secara
umum.


\>&remvalue(a,b,c);


Jadi pertama-tama kita menghitung penyebaran sudut baginya di A, menggunakan rumus triple spread.


Masalah dengan rumus ini muncul kembali. Terdapat dua buah solusi. Kita harus memilih penyelesaian
yang benar. Solusi lain merujuk pada sudut bagi 180Â°-wa.


\>$triplespread(x,x,a/(a+b)), $solve(%,x), sa2 &= rhs(%[1]); $sa2


$$\frac{-\sqrt{b}\,\sqrt{b+a}+b+a}{2\,b+2\,a}$$![images/Tugas%206-165.png](images/Tugas%206-165.png)

![images/Tugas%206-166.png](images/Tugas%206-166.png)

Mari kita periksa persegi panjang (segitiga siku-siku) Mesir.


\>$sa2 with [a=3^2,b=4^2]


$$\frac{1}{10}$$Kita dapat mencetak sudut tersebut di Euler, setelah mengubah penyebarannya ke bentuk radian.


\>wa2 := arcsin(sqrt(1/10)); degprint(wa2)


    18°26'5.82''

Titik P adalah perpotongan garis bagi sudut dengan sumbu-y.


\>P := [0,tan(wa2)\*4]


    [0,  1.33333]

\>plotPoint(P,"P"); plotSegment(A,P):


![images/Tugas%206-168.png](images/Tugas%206-168.png)

Mari kita periksa sudutnya pada contoh spesifik kita ini.


\>computeAngle(C,A,P), computeAngle(P,A,B)


    0.321750554397
    0.321750554397

Sekarang kita menghitung panjang garis bagi AP.


Kita menggunakan aturan sinus pada segitiga APC. Teorema ini menyatakan bahwa


$$\frac{BC}{\sin(w_a)} = \frac{AC}{\sin(w_b)} = \frac{AB}{\sin(w_c)}$$berlaku di segitiga manapun. Kuadratkan rumus tersebut, hal itu diterjemahkan ke dalam apa yang
disebut "hukum spread" (spread law)


$$\frac{a}{s_a} = \frac{b}{s_b} = \frac{c}{s_b}$$di mana a,b,c menunjukkan quadrance.


Karena spread dari CPA adalah 1-sa2, kita mendapatkan bisa/1=b/(1-sa2) darinya dan kita bisa
menghitung bisa (quadrance dari garis bagi sudut).


\>&factor(ratsimp(b/(1-sa2))); bisa &= %; $bisa


$$\frac{2\,b\,\left(b+a\right)}{\sqrt{b}\,\sqrt{b+a}+b+a}$$Mari kita periksa rumus ini untuk nilai-nilai rasio Mesir yang kita gunakan.


\>sqrt(mxmeval("at(bisa,[a=3^2,b=4^2])")), distance(A,P)


    4.21637021356
    4.21637021356

Kita juga dapat menghitung P menggunakan rumus spread.


\>py&=factor(ratsimp(sa2\*bisa)); $py


$$-\frac{b\,\left(\sqrt{b}\,\sqrt{b+a}-b-a\right)}{\sqrt{b}\,\sqrt{b+  a}+b+a}$$Nilainya adalah sama seperti yang kita peroleh dengan rumus trigonometri.


\>sqrt(mxmeval("at(py,[a=3^2,b=4^2])"))


    1.33333333333

## Sudut Tali Busur

Perhatikan situasi berikut ini.


\>setPlotRange(1.2); ...  
\>   color(1); plotCircle(circleWithCenter([0,0],1)); ...  
\>   A:=[cos(1),sin(1)]; B:=[cos(2),sin(2)]; C:=[cos(6),sin(6)]; ...  
\>   plotPoint(A,"A"); plotPoint(B,"B"); plotPoint(C,"C"); ...  
\>   color(3); plotSegment(A,B,"c"); plotSegment(A,C,"b"); plotSegment(C,B,"a"); ...  
\>   color(1); O:=[0,0];  plotPoint(O,"0"); ...  
\>   plotSegment(A,O); plotSegment(B,O); plotSegment(C,O,"r"); ...  
\>   insimg;


![images/Tugas%206-173.png](images/Tugas%206-173.png)

Kita bisa menggunakan Maxima untuk menyelesaikan persamaan triple spread untuk sudut di titik pusat O
demi mendapatkan r. Dengan begitu, kita akan memperoleh rumus untuk jari-jari kuadratis lingkaran
luarnya (pericircle) dalam bentuk quadrance dari sisi-sisinya.


Kali ini, Maxima menghasilkan beberapa angka nol kompleks yang bisa kita abaikan saja.


\>&remvalue(a,b,c,r); // hapus nilai-nilai sebelumnya untuk perhitungan baru

\>rabc &= rhs(solve(triplespread(spread(b,r,r),spread(a,r,r),spread(c,r,r)),r)[4]); $rabc


$$-\frac{a\,b\,c}{c^2-2\,b\,c+a\,\left(-2\,c-2\,b\right)+b^2+a^2}$$Kita bisa membuat hal ini menjadi fungsi Euler.


\>function periradius(a,b,c) &= rabc;


Mari kita periksa hasilnya untuk titik-titik kita A,B,C.


\>a:=quadrance(B,C); b:=quadrance(A,C); c:=quadrance(A,B);


Jari-jarinya memang 1.


\>periradius(a,b,c)


    1

Faktanya, bentangan (spread) CBA hanya bergantung pada b dan c. Ini merupakan teorema sudut tali
busur.


\>$spread(b,a,c)\*rabc | ratsimp


$$\frac{b}{4}$$Pada kenyataannya spread-nya adalah b/(4r), dan kita dapat melihat bahwa sudut tali busur untuk tali
busur b merupakan setengah dari sudut pusatnya.


\>$doublespread(b/(4\*r))-spread(b,r,r) | ratsimp


$$0$$# Contoh 6: Jarak Minimal pada Bidang

## Catatan Awal

Fungsi yang menugaskan jarak AM antara titik tetap A dan M pada suatu titik M di sebuah bidang datar,
memiliki garis ketinggian (level lines) yang cukup sederhana: lingkaran-lingkaran yang berpusat di A.


\>&remvalue();

\>A=[-1,-1];

\>function d1(x,y):=sqrt((x-A[1])^2+(y-A[2])^2)

\>fcontour("d1",xmin=-2,xmax=0,ymin=-2,ymax=0,hue=1, ...  
\>   title="If you see ellipses, please set your window square"):


![images/Tugas%206-177.png](images/Tugas%206-177.png)

serta grafiknya juga agak sederhana: bagian atas dari sebuah kerucut:


\>plot3d("d1",xmin=-2,xmax=0,ymin=-2,ymax=0):


![images/Tugas%206-178.png](images/Tugas%206-178.png)

Tentu saja nilai minimum 0 dicapai di A.


## Dua titik

Sekarang kita melihat pada fungsi MA+MB di mana A dan B adalah dua titik (tetap). Merupakan sebuah
"fakta umum" bahwa kurva ketinggiannya berbentuk elips, dengan titik fokusnya A dan B; kecuali untuk
jarak minimum AB yang konstan pada segmen [AB]:


\>B=[1,-1];

\>function d2(x,y):=d1(x,y)+sqrt((x-B[1])^2+(y-B[2])^2)

\>fcontour("d2",xmin=-2,xmax=2,ymin=-3,ymax=1,hue=1):


![images/Tugas%206-179.png](images/Tugas%206-179.png)

Grafiknya lebih menarik:


\>plot3d("d2",xmin=-2,xmax=2,ymin=-3,ymax=1):


![images/Tugas%206-180.png](images/Tugas%206-180.png)

Restriksi terhadap garis (AB) lebih terkenal:


\>plot2d("abs(x+1)+abs(x-1)",xmin=-3,xmax=3):


![images/Tugas%206-181.png](images/Tugas%206-181.png)

## Tiga titik

Sekarang segalanya menjadi tidak begitu sederhana: Agak sedikit kurang dikenal bahwa MA+MB+MC
mencapai minimumnya pada satu titik di bidang tersebut namun untuk menentukannya tidaklah mudah:


1) Jika salah satu sudut segitiga ABC lebih dari 120Â° (katakanlah di A), maka nilai minimum dicapai
di titik ini (katakanlah AB+AC).


Contoh:


\>C=[-4,1];

\>function d3(x,y):=d2(x,y)+sqrt((x-C[1])^2+(y-C[2])^2)

\>plot3d("d3",xmin=-5,xmax=3,ymin=-4,ymax=4);

\>insimg;


![images/Tugas%206-182.png](images/Tugas%206-182.png)

\>fcontour("d3",xmin=-4,xmax=1,ymin=-2,ymax=2,hue=1,title="The minimum is on A");

\>P=(A\_B\_C\_A)'; plot2d(P[1],P[2],add=1,color=12);

\>insimg;


![images/Tugas%206-183.png](images/Tugas%206-183.png)

2) Namun jika semua sudut segitiga ABC kurang dari 120Â°, nilai minimum berada di titik F di bagian
dalam segitiga, yang mana merupakan satu-satunya titik yang melihat sisi-sisi ABC dengan sudut yang
sama (yaitu masing-masing 120Â°):


\>C=[-0.5,1];

\>plot3d("d3",xmin=-2,xmax=2,ymin=-2,ymax=2):


![images/Tugas%206-184.png](images/Tugas%206-184.png)

\>fcontour("d3",xmin=-2,xmax=2,ymin=-2,ymax=2,hue=1,title="The Fermat point");

\>P=(A\_B\_C\_A)'; plot2d(P[1],P[2],add=1,color=12);

\>insimg;


![images/Tugas%206-185.png](images/Tugas%206-185.png)

Kegiatan yang menarik untuk membuat figur di atas dengan perangkat lunak geometri; misalnya, saya
tahu perangkat lunak yang ditulis dalam Java yang memiliki instruksi "garis kontur"...


Semua hal di atas telah ditemukan oleh hakim dari Perancis bernama Pierre de Fermat; dia menulis
surat kepada akademisi amatir lainnya seperti pendeta Marin Mersenne dan Blaise Pascal yang bekerja
di bidang pajak pendapatan. Oleh karena itu titik unik F sedemikian rupa sehingga FA+FB+FC bernilai
minimum, disebut titik Fermat dari segitiga. Namun tampaknya beberapa tahun sebelumnya, Torricelli
yang berkebangsaan Italia telah menemukan titik ini sebelum Fermat! Bagaimanapun juga, tradisinya
adalah mencatat titik ini sebagai titik F...


## Empat titik

Langkah selanjutnya adalah menambahkan titik ke-4 yaitu titik D dan mencoba meminimalkan MA+MB+MC+MD;
misalkan Anda adalah operator TV kabel dan ingin menemukan di lapangan mana Anda harus meletakkan
antena sehingga Anda dapat mensuplai empat desa dan menggunakan sesedikit mungkin panjang kabel!


\>D=[1,1];

\>function d4(x,y):=d3(x,y)+sqrt((x-D[1])^2+(y-D[2])^2)

\>plot3d("d4",xmin=-1.5,xmax=1.5,ymin=-1.5,ymax=1.5):


![images/Tugas%206-186.png](images/Tugas%206-186.png)

\>fcontour("d4",xmin=-1.5,xmax=1.5,ymin=-1.5,ymax=1.5,hue=1);

\>P=(A\_B\_C\_D)'; plot2d(P[1],P[2],points=1,add=1,color=12);

\>insimg;


![images/Tugas%206-187.png](images/Tugas%206-187.png)

Masih terdapat nilai minimum dan nilainya tidak dicapai di satupun titik sudut A, B, C, maupun D:


\>function f(x):=d4(x[1],x[2])

\>neldermin("f",[0.2,0.2])


    [0.142858,  0.142857]

Tampaknya dalam kasus ini, koordinat titik optimal bersifat rasional atau mendekati rasional...


Sekarang jika ABCD merupakan suatu persegi, kita berharap bahwa titik optimalnya akan berada di titik
pusat ABCD:


\>C=[-1,1];

\>plot3d("d4",xmin=-1,xmax=1,ymin=-1,ymax=1):


![images/Tugas%206-188.png](images/Tugas%206-188.png)

\>fcontour("d4",xmin=-1.5,xmax=1.5,ymin=-1.5,ymax=1.5,hue=1);

\>P=(A\_B\_C\_D)'; plot2d(P[1],P[2],add=1,color=12,points=1);

\>insimg;


![images/Tugas%206-189.png](images/Tugas%206-189.png)

# Contoh 7: Bola Dandelin dengan Povray

Anda bisa menjalankan demonstrasi ini, jika Anda sudah menginstal Povray, dan menempatkan
pvengine.exe di path program.


Pertama-tama kita menghitung jari-jari bola.


Jika Anda melihat gambar di bawah, Anda bisa melihat bahwa kita memerlukan dua lingkaran yang
bersinggungan dengan kedua garis yang membentuk kerucut, dan satu garis yang membentuk bidang yang
memotong kerucut.


Kita menggunakan file geometry.e dari Euler untuk hal ini.


\>load geometry;


Pertama, dua garis yang membentuk kerucut.


\>g1 &= lineThrough([0,0],[1,a])


    
                                 [- a, 1, 0]
    

\>g2 &= lineThrough([0,0],[-1,a])


    
                                [- a, - 1, 0]
    

Kemudian, garis yang ketiga.


\>g &= lineThrough([-1,0],[1,1])


    
                                 [- 1, 2, 1]
    

Kita mengeplot semuanya sejauh ini.


\>setPlotRange(-1,1,0,2);

\>color(black); plotLine(g(),"")

\>a:=2; color(blue); plotLine(g1(),""), plotLine(g2(),""):


![images/Tugas%206-190.png](images/Tugas%206-190.png)

Sekarang kita ambil titik secara umum pada sumbu-y.


\>P &= [0,u]


    
                                    [0, u]
    

Hitung jarak menuju g1.


\>d1 &= distance(P,projectToLine(P,g1)); $d1


$$\sqrt{\left(\frac{a^2\,u}{a^2+1}-u\right)^2+\frac{a^2\,u^2}{\left(a  ^2+1\right)^2}}$$Hitung jarak menuju g.


\>d &= distance(P,projectToLine(P,g)); $d


$$\sqrt{\left(\frac{u+2}{5}-u\right)^2+\frac{\left(2\,u-1\right)^2}{  25}}$$Dan cari titik pusat dari kedua lingkaran, tempat di mana jaraknya sama besar.


\>sol &= solve(d1^2=d^2,u); $sol


$$\left[ u=\frac{-\sqrt{5}\,\sqrt{a^2+1}+2\,a^2+2}{4\,a^2-1} , u=  \frac{\sqrt{5}\,\sqrt{a^2+1}+2\,a^2+2}{4\,a^2-1} \right] $$Terdapat dua solusi.


Kita mengevaluasi solusi simbolisnya, lalu menemukan kedua titik pusat, serta kedua jaraknya.


\>u := sol()


    [0.333333,  1]

\>dd := d()


    [0.149071,  0.447214]

Gambarlah lingkaran ke dalam gambar (figur).


\>color(red);

\>plotCircle(circleWithCenter([0,u[1]],dd[1]),"");

\>plotCircle(circleWithCenter([0,u[2]],dd[2]),"");

\>insimg;


![images/Tugas%206-194.png](images/Tugas%206-194.png)

## Plot dengan Povray

Selanjutnya kita mengeplot semuanya dengan Povray. Perhatikan bahwa Anda dapat mengubah sembarang
perintah dalam urutan perintah Povray berikut ini, lalu menjalankan ulang semua perintah dengan
menekan Shift-Return.


Pertama kita memuat fungsi povray.


\>load povray;

\>defaultpovray="C:\\Program Files\\POV-Ray\\v3.7\\bin\\pvengine.exe"


    C:\Program Files\POV-Ray\v3.7\bin\pvengine.exe

Kita mengatur scene dengan benar.


\>povstart(zoom=11,center=[0,0,0.5],height=10,angle=140);


Selanjutnya kita menulis kedua bola ke dalam file Povray.


\>writeln(povsphere([0,0,u[1]],dd[1],povlook(red)));

\>writeln(povsphere([0,0,u[2]],dd[2],povlook(red)));


Dan juga kerucut, dibuat transparan.


\>writeln(povcone([0,0,0],0,[0,0,a],1,povlook(lightgray,1)));


Kita menghasilkan bidang yang dibatasi pada kerucut.


\>gp=g();

\>pc=povcone([0,0,0],0,[0,0,a],1,"");

\>vp=[gp[1],0,gp[2]]; dp=gp[3];

\>writeln(povplane(vp,dp,povlook(blue,0.5),pc));


Sekarang kita menghasilkan dua titik di lingkaran, tempat dimana bola tersebut menyentuh kerucut.


\>function turnz(v) := return [-v[2],v[1],v[3]]

\>P1=projectToLine([0,u[1]],g1()); P1=turnz([P1[1],0,P1[2]]);

\>writeln(povpoint(P1,povlook(yellow)));

\>P2=projectToLine([0,u[2]],g1()); P2=turnz([P2[1],0,P2[2]]);

\>writeln(povpoint(P2,povlook(yellow)));


Kemudian kita menghasilkan dua titik di mana bola tersebut menyentuh bidang datar. Ini merupakan
titik-titik fokus dari elips tersebut.


\>P3=projectToLine([0,u[1]],g()); P3=[P3[1],0,P3[2]];

\>writeln(povpoint(P3,povlook(yellow)));

\>P4=projectToLine([0,u[2]],g()); P4=[P4[1],0,P4[2]];

\>writeln(povpoint(P4,povlook(yellow)));


Selanjutnya kita menghitung perpotongan dari P1P2 terhadap bidang datar.


\>t1=scalp(vp,P1)-dp; t2=scalp(vp,P2)-dp; P5=P1+t1/(t1-t2)\*(P2-P1);

\>writeln(povpoint(P5,povlook(yellow)));


Kita menyambungkan titik-titik tersebut dengan ruas garis.


\>writeln(povsegment(P1,P2,povlook(yellow)));

\>writeln(povsegment(P5,P3,povlook(yellow)));

\>writeln(povsegment(P5,P4,povlook(yellow)));


Sekarang kita membuat pita abu-abu, tempat di mana bola-bola tersebut menyentuh bidang.


\>pcw=povcone([0,0,0],0,[0,0,a],1.01);

\>pc1=povcylinder([0,0,P1[3]-defaultpointsize/2],[0,0,P1[3]+defaultpointsize/2],1);

\>writeln(povintersection([pcw,pc1],povlook(gray)));

\>pc2=povcylinder([0,0,P2[3]-defaultpointsize/2],[0,0,P2[3]+defaultpointsize/2],1);

\>writeln(povintersection([pcw,pc2],povlook(gray)));


Mulai jalankan program Povray.


\>povend();


![images/Tugas%206-195.png](images/Tugas%206-195.png)

Untuk mendapatkan wujud Anaglyph dari ini, kita harus meletakkan semuanya ke dalam fungsi scene.
Fungsi ini nantinya akan digunakan dua kali.


\>function scene () ...


    global a,u,dd,g,g1,defaultpointsize;
    writeln(povsphere([0,0,u[1]],dd[1],povlook(red)));
    writeln(povsphere([0,0,u[2]],dd[2],povlook(red)));
    writeln(povcone([0,0,0],0,[0,0,a],1,povlook(lightgray,1)));
    gp=g();
    pc=povcone([0,0,0],0,[0,0,a],1,"");
    vp=[gp[1],0,gp[2]]; dp=gp[3];
    writeln(povplane(vp,dp,povlook(blue,0.5),pc));
    P1=projectToLine([0,u[1]],g1()); P1=turnz([P1[1],0,P1[2]]);
    writeln(povpoint(P1,povlook(yellow)));
    P2=projectToLine([0,u[2]],g1()); P2=turnz([P2[1],0,P2[2]]);
    writeln(povpoint(P2,povlook(yellow)));
    P3=projectToLine([0,u[1]],g()); P3=[P3[1],0,P3[2]];
    writeln(povpoint(P3,povlook(yellow)));
    P4=projectToLine([0,u[2]],g()); P4=[P4[1],0,P4[2]];
    writeln(povpoint(P4,povlook(yellow)));
    t1=scalp(vp,P1)-dp; t2=scalp(vp,P2)-dp; P5=P1+t1/(t1-t2)*(P2-P1);
    writeln(povpoint(P5,povlook(yellow)));
    writeln(povsegment(P1,P2,povlook(yellow)));
    writeln(povsegment(P5,P3,povlook(yellow)));
    writeln(povsegment(P5,P4,povlook(yellow)));
    pcw=povcone([0,0,0],0,[0,0,a],1.01);
    pc1=povcylinder([0,0,P1[3]-defaultpointsize/2],[0,0,P1[3]+defaultpointsize/2],1);
    writeln(povintersection([pcw,pc1],povlook(gray)));
    pc2=povcylinder([0,0,P2[3]-defaultpointsize/2],[0,0,P2[3]+defaultpointsize/2],1);
    writeln(povintersection([pcw,pc2],povlook(gray)));
    endfunction
</pre>
Anda memerlukan kacamata merah/cyan untuk melihat keindahan efek berikut.


\>povanaglyph("scene",zoom=11,center=[0,0,0.5],height=10,angle=140);


![images/Tugas%206-196.png](images/Tugas%206-196.png)

# Contoh 8: Geometri Bumi

Pada buku catatan ini, kita ingin melakukan sejumlah perhitungan bola (spherical). Fungsi-fungsinya
terdapat dalam file "spherical.e" di folder examples. Kita harus memuat file tersebut terlebih
dahulu.


\>load "spherical.e";


Untuk memasukkan letak geografis, kita menggunakan vektor dengan dua koordinat dalam satuan radian
(Utara dan Timur, nilai negatif untuk Selatan dan Barat). Berikut ini adalah letak koordinat untuk
Kampus FMIPA UNY.


\>FMIPA=[rad(-7,-46.467),rad(110,23.05)]


    [-0.13569,  1.92657]

Anda dapat mencetak posisi ini dengan sposprint (cetak posisi sferis).


\>sposprint(FMIPA) // posisi garis lintang dan garis bujur FMIPA UNY


    S 7°46.467' E 110°23.050'

Mari kita tambahkan dua kota lagi, Solo dan Semarang.


\>Solo=[rad(-7,-34.333),rad(110,49.683)]; Semarang=[rad(-6,-59.05),rad(110,24.533)];

\>sposprint(Solo), sposprint(Semarang),


    S 7°34.333' E 110°49.683'
    S 6°59.050' E 110°24.533'

Pertama-tama kita menghitung vektor dari yang satu menuju yang lainnya pada sebuah bola ideal. Vektor
ini berupa [heading,distance] dalam satuan radian. Untuk menghitung jarak di atas muka bumi, kita
mengalikannya dengan jari-jari bumi di lintang 7Â°.


\>br=svector(FMIPA,Solo); degprint(br[1]), br[2]\*rearth(7)-\>km // perkiraan jarak FMIPA-Solo


    65°20'26.60''
    53.8192923514

Ini adalah hasil perkiraan yang baik. Rutinitas berikut menggunakan nilai aproksimasi yang lebih baik
lagi. Untuk jarak yang sedekat ini hasilnya hampir sama.


\>esdist(FMIPA,Semarang)+" km" // perkiraan jarak FMIPA-Semarang


    88011.4026318 km

Terdapat sebuah fungsi khusus untuk arah (heading), yang mana memperhitungkan
bentuk bumi yang elips. Sekali lagi, kita mencetaknya dengan cara tingkat lanjut.


\>sdegprint(esdir(FMIPA,Solo))


         65.34°

Besar sudut dari sebuah segitiga akan melebihi 180Â° di atas bola.


\>asum=sangle(Solo,FMIPA,Semarang)+sangle(FMIPA,Solo,Semarang)+sangle(FMIPA,Semarang,Solo); degprint(asum)


    180°0'10.77''

Ini dapat digunakan untuk menghitung luas dari suatu segitiga. Catatan: Untuk segitiga
yang kecil, hal ini kurang begitu akurat dikarenakan adanya galat pengurangan di
bagian asum-pi.


\>(asum-pi)\*rearth(48Â°)^2-\>" km^2" // perkiraan luas segitiga FMIPA-Solo-Semarang


    Variable Â not found!
    Error in degree
    Error in:
    (asum-pi)*rearth(48Â°)^2-&gt;" km^2" // perkiraan luas segitiga FMIPA-Solo-Semarang ...
                         ^

Terdapat fungsi untuk melakukan perhitungan ini, yang mana menggunakan lintang rata-rata dari
segitiga untuk menghitung jari-jari bumi, serta memperhatikan adanya error/galat pembulatan
untuk segitiga-segitiga yang berukuran sangat kecil.


\>esarea(Solo,FMIPA,Semarang)-\>" km^2", //perkiraan yang sama dengan fungsi esarea()


    2123.64310526 km^2

Kita juga bisa menambahkan vektor ke posisi. Sebuah vektor berisi nilai
arah (heading) dan jarak, yang keduanya dalam satuan radian. Untuk mendapatkan sebuah vektor, kita memakai
svector. Untuk menambahkan sebuah vektor ke suatu posisi, kita menggunakan saddvector.


\>v=svector(FMIPA,Solo); sposprint(saddvector(FMIPA,v)), sposprint(Solo),


    S 7°34.333' E 110°49.683'
    S 7°34.333' E 110°49.683'

Fungsi-fungsi ini mengasumsikan keberadaan suatu bola ideal. Berlaku hal yang sama di bumi.


\>sposprint(esadd(FMIPA,esdir(FMIPA,Solo),esdist(FMIPA,Solo))), sposprint(Solo),


    S 7°34.333' E 110°49.683'
    S 7°34.333' E 110°49.683'

Let us turn to a larger example, Tugu Jogja dan Monas Jakarta (menggunakan Google Earth untuk mencari
koordinatnya).


\>Tugu=[-7.7833,110.3661]; Monas=[-6.175,106.811944];

\>sposprint(Tugu), sposprint(Monas)


    S 445°57.014' E 6323°30.704'
    S 353°48.086' E 6119°52.416'

Menurut perhitungan Google Earth, jaraknya adalah 429.66km. Kita mendapatkan
perkiraan nilai yang cukup bagus.


\>esdist(Tugu,Monas)+" km" // perkiraan jarak Tugu Jogja - Monas Jakarta


    11102676.8138 km

Besar arah (heading) nilainya sama dengan yang dihitung di Google Earth.


\>degprint(esdir(Tugu,Monas))


    156°7'51.59''

Meskipun demikian, kita tak lagi memperoleh nilai persis titik targetnya, apabila kita menambahkan
heading dan jarak menuju ke posisi aslinya. Hal ini terjadi karena kita
tidak menghitung nilai kebalikan fungsi secara persis, melainkan kita mengambil
perkiraan dari jari-jari bumi di sepanjang lintasan.


\>sposprint(esadd(Tugu,esdir(Tugu,Monas),esdist(Tugu,Monas)))


    N 6°10.028' W 0°7.639'

Akan tetapi, tingkat kemelesetannya/errornya tidak besar.


\>sposprint(Monas),


    S 353°48.086' E 6119°52.416'

Tentunya, kita tidak bisa berlayar menggunakan posisi heading yang terus sama dari satu tujuan
menuju ke tujuan lainnya, jika kita ingin menempuh rute yang terpendek. Bayangkan saja, jika Anda terbang kearah Timur Laut
dari titik mana pun di bumi. Maka lintasan spiral Anda akan membentur kutub
utara. Lingkaran besar (Great circles) tidak memiliki heading yang nilainya konstan!


Perhitungan berikut menunjukkan bahwa posisi kita telah jauh melenceng dari
letak tujuan yang benar, seandainya kita memakai heading yang terus sama di sepanjang perjalanan kita.


\>dist=esdist(Tugu,Monas); hd=esdir(Tugu,Monas);


Sekarang kita menjumlahkan 10 kali dari sepersepuluh jarak tempuhnya, menggunakan heading menuju ke Monas, yang mana kita peroleh di saat berada di Tugu.


\>p=Tugu; loop 1 to 10; p=esadd(p,hd,dist/10); end;


Hasilnya menyimpang sangat jauh.


\>sposprint(p), skmprint(esdist(p,Monas))


    S 84°33.566' E 90°4.158'
     10689.737km

Sebagai contoh yang lainnya, mari kita mengambil dua posisi titik yang berbeda
di bumi namun berada pada garis lintang yang sama.


\>P1=[30,10]; P2=[30,50];


Jalur terdekat dari titik P1 ke titik P2 bukanlah merupakan lingkaran lintang 30Â°,
melainkan sebuah jalur yang lebih pendek lagi yang bermula 10Â° lebih jauh mengarah utara dari P1.


\>sdegprint(esdir(P1,P2))


        155.66°

Tetapi, jika kita terus-terusan menuruti angka kompas ini, kita akan bergerak spiral
lalu menubruk kutub utara! Sehingga kita diharuskan menyesuaikan heading kita di sepanjang
jalan. Untuk perkiraan saja, kita menyesuaikannya di batas 1/10 dari total keseluruhan jarak.


\>p=P1;  dist=esdist(P1,P2); ...  
\>     loop 1 to 10; dir=esdir(p,P2); sdegprint(dir), p=esadd(p,dir,dist/10); end;


        155.66°
        150.54°
        143.04°
        131.56°
        113.91°
         89.99°
         66.08°
         48.43°
         36.95°
         29.46°

Ukuran jaraknya kurang begitu tepat, berhubung karena kita akan menambahkan sedikit nilai kesalahan/galat,
bilamana kita terus-terusan mematuhi heading yang sama dengan durasi waktu yang sangat lama.


\>skmprint(esdist(p,P2))


         0.079km

Kita memperoleh perkiraan yang bagus, jika kita selalu menyesuaikan heading kita setelah berselang 1/100 dari total keseluruhan jarak
yang dibentangkan antara Tugu menuju ke Monas.


\>p=Tugu; dist=esdist(Tugu,Monas); ...  
\>     loop 1 to 100; p=esadd(p,esdir(p,Monas),dist/100); end;

\>skmprint(esdist(p,Monas))


         0.590km

Bagi keperluan navigasi, kita bisa melacak urut-urutan koordinat rute di GPS menyusuri jalan memutar sepanjang lingkaran besar (great circle)
menuju sasaran ke Monas menggunakan fungsi perintah navigate.


\>load spherical; v=navigate(Tugu,Monas,10); ...  
\>     loop 1 to rows(v); sposprint(v[#]), end;


    S 445°57.014' E 6323°30.704'
    S 83°29.340' W 14°48.665'
    S 73°36.804' W 5°53.008'
    S 63°38.738' W 3°36.753'
    S 53°39.924' W 2°31.917'
    S 43°41.038' W 1°52.138'
    S 33°42.259' W 1°23.819'
    S 23°43.620' W 1°1.458'
    S 13°45.092' W 0°42.311'
    S 3°46.614' W 0°24.747'
    N 6°11.899' W 0°7.585'

Kita menulis sebuah perintah fungsi, yang mana menampilkan
bumi, beserta dengan kedua koordinat titiknya, dan tak lupa tempat perhentian-perhentian di sepanjang jalur yang berada di antaranya.


\>function testplot ...


    useglobal;
    plotearth;
    plotpos(Tugu,"Tugu Jogja"); plotpos(Monas,"Tugu Monas");
    plotposline(v);
    endfunction
</pre>
Sekarang gambar plotkan kesemuanya.


\>plot3d("testplot",angle=25, height=6,\>own,\>user,zoom=4):


![images/Tugas%206-197.png](images/Tugas%206-197.png)

Atau pakai plot3d untuk mengambil gambar dalam tampilan visual anaglyph-nya. Ini nampak begitu memukau
bila disaksikan memakai kacamata kombinasi warna merah dan cyan.


\>plot3d("testplot",angle=25,height=6,distance=5,own=1,anaglyph=1,zoom=4):


![images/Tugas%206-198.png](images/Tugas%206-198.png)

\>load geometry


    Numerical and symbolic geometry.

# Latihan

1. Gambarlah segi-n beraturan jika diketahui titik pusat O, n, dan jarak titik pusat ke titik-titik
sudut segi-n tersebut (jari-jari lingkaran luar segi-n), r.


Petunjuk:


* 
Besar sudut pusat yang menghadap masing-masing sisi segi-n adalah (360/n).

* 
Titik-titik sudut segi-n merupakan perpotongan lingkaran luar segi-n dan garis-garis yang melalui
* pusat dan saling membentuk sudut sebesar kelipatan (360/n).

* 
Untuk n ganjil, pilih salah satu titik sudut adalah di atas.

* 
Untuk n genap, pilih 2 titik di kanan dan kiri lurus dengan titik pusat.

* 
Anda dapat menggambar segi-3, 4, 5, 6, 7, dst beraturan.


\>setPlotRange(-8,8,-8,8); &remvalue(A,B,C,f3(x));


Segitiga Beraturan


\>A=[0,3]; function f3(x,y)&=x^2+y^2-9;  ...  
\>   m1&=tan(pi/2+(2\*pi)/3); m2&=tan(pi/2-(2\*pi)/3); $m1, $m2


$$-\frac{1}{\sqrt{3}}$$![images/Tugas%206-200.png](images/Tugas%206-200.png)

\>function M1&=m1\*x; function M2&=m2\*x; ...  
\>   s1 &= solve([f3(x,y)=0, y=m1\*x], [x,y]); ...  
\>   s2 &= solve([f3(x,y)=0, y=m2\*x], [x,y]); ...  
\>   B&=[x,y] with s1[1]; ...  
\>   C&=[x,y] with s2[2]; $B, $C


$$\left[ \frac{3^{\frac{3}{2}}}{2} , -\frac{3}{2} \right] $$![images/Tugas%206-202.png](images/Tugas%206-202.png)

\>B=B(); C=C(); circleThrough(A,B,C);

\>aspect(1); clg; plotSegment(A,B,""); plotSegment(A,C,""); plotSegment(B,C,""):


![images/Tugas%206-203.png](images/Tugas%206-203.png)

Segiempat Beraturan


\>&remvalue(A,B,C); &assume(r\>0); A&=[r,0]; B&=[-r,0]; ...  
\>   function f4(x,y)&=x^2+y^2-r^2;

\>m1&=tan(2\*pi/4); m2&=tan(pi+(2\*pi)/4); $m1,$m2


    Maxima said:
    tan: pi/2 isn't in the domain of tan.
     -- an error. To debug this try: debugmode(true);
    
    Error in:
    m1&amp;=tan(2*pi/4); m2&amp;=tan(pi+(2*pi)/4); $m1,$m2 ...
                   ^

\>function g(x,y)&=x; function h(x,y)&=-x; ...  
\>   s1 &= solve([f4(x,y)=0, x=0], [x,y]);  ...  
\>   C&=[x,y] with s1[1]; ...  
\>   D&=[x,y] with s1[2]; $C, $D


$$\left[ 0 , -r \right] $$![images/Tugas%206-205.png](images/Tugas%206-205.png)

\>r=4; A=A(); B=B(); C=C(); D=D();

\>circleThrough(A,B,C)


    [0,  0,  4]

\>clg; plotSegment(A,C,""); plotSegment(A,D,""); plotSegment(B,C,""); plotSegment(B,D,""):


![images/Tugas%206-206.png](images/Tugas%206-206.png)

Segilima Beraturan


\>&remvalue(all); A&=[0,r]; function f5(x,y)&=x^2+y^2-r^2; ...  
\>   m1&=tan(pi/2+(2\*pi)/5); m2&=tan(pi/2+2\*(2\*pi)/5); m3&=tan(pi/2+3\*(2\*pi)/5);  ...  
\>   m4&=tan(pi/2+4\*(2\*pi)/5);

\>s1 &= solve([f5(x,y)=0, y=m1\*x], [x,y]); s2 &= solve([f5(x,y)=0, y=m2\*x], [x,y]);  ...  
\>   s3 &= solve([f5(x,y)=0, y=m3\*x], [x,y]); s4 &= solve([f5(x,y)=0, y=m4\*x], [x,y]); $s1, $s2, $s3, $s4


$$\left[ \left[ x=-\frac{r}{\sqrt{\tan ^2\left(\frac{21\,\pi}{10}  \right)+1}} , y=-\frac{\tan \left(\frac{21\,\pi}{10}\right)\,r}{  \sqrt{\tan ^2\left(\frac{21\,\pi}{10}\right)+1}} \right]  , \left[ x=  \frac{r}{\sqrt{\tan ^2\left(\frac{21\,\pi}{10}\right)+1}} , y=\frac{  \tan \left(\frac{21\,\pi}{10}\right)\,r}{\sqrt{\tan ^2\left(\frac{21  \,\pi}{10}\right)+1}} \right]  \right] $$![images/Tugas%206-208.png](images/Tugas%206-208.png)

![images/Tugas%206-209.png](images/Tugas%206-209.png)

![images/Tugas%206-210.png](images/Tugas%206-210.png)

\>B&=[x,y] with s1[1]; C&=[x,y] with s2[1]; ...  
\>   D&=[x,y] with s3[2]; F&=[x,y] with s4[2]; $A, $B, $C, $D, $F


$$\left[ \frac{r}{\sqrt{\tan ^2\left(\frac{21\,\pi}{10}\right)+1}} ,   \frac{\tan \left(\frac{21\,\pi}{10}\right)\,r}{\sqrt{\tan ^2\left(  \frac{21\,\pi}{10}\right)+1}} \right] $$![images/Tugas%206-212.png](images/Tugas%206-212.png)

![images/Tugas%206-213.png](images/Tugas%206-213.png)

![images/Tugas%206-214.png](images/Tugas%206-214.png)

![images/Tugas%206-215.png](images/Tugas%206-215.png)

\>r=5; A=A(); B=B(); C=C(); D=D(); F=F();

\>clg; plotSegment(A,B,""); plotSegment(B,C,"");  ...  
\>   plotSegment(C,D,""); plotSegment(D,F,""); plotSegment(F,A,""):


![images/Tugas%206-216.png](images/Tugas%206-216.png)

Segienam Beraturan


\>&remvalue(all); &assume(r\>0); A&=[r,0]; B&=[-r,0]; ...  
\>   function f6(x,y)&=x^2+y^2-r^2; ...  
\>   m1&=tan((2\*pi)/6); m2&=tan(2\*(2\*pi)/6); m3&=tan(4\*(2\*pi)/6); m4&=tan(5\*(2\*pi)/6);  ...  
\>   s1&=solve([f6(x,y)=0, y=m1\*x], [x,y]); s2&=solve([f6(x,y)=0, y=m2\*x], [x,y]);  ...  
\>   s3&=solve([f6(x,y)=0, y=m3\*x], [x,y]); s4&=solve([f6(x,y)=0, y=m4\*x], [x,y]); $s1, $s2, $s3, $s4


$$\left[ \left[ x=\frac{r}{2} , y=-\frac{\sqrt{3}\,r}{2} \right]  ,   \left[ x=-\frac{r}{2} , y=\frac{\sqrt{3}\,r}{2} \right]  \right] $$![images/Tugas%206-218.png](images/Tugas%206-218.png)

![images/Tugas%206-219.png](images/Tugas%206-219.png)

![images/Tugas%206-220.png](images/Tugas%206-220.png)

\>C&=[x,y] with s1[1]; D&=[x,y] with s2[2]; F&=[x,y] with s3[2]; G&=[x,y] with s4[1];

\>r=6; A=A(); B=B(); C=C(); D=D(); F=F(); G=G();

\>clg; plotSegment(A,C,""); plotSegment(C,D,""); plotSegment(D,B,""); plotSegment(B,F,""); ...  
\>   plotSegment(F,G,""); plotSegment(G,A,""):


![images/Tugas%206-221.png](images/Tugas%206-221.png)

Segitujuh Beraturan


\>&remvalue(all); A&=[0,r]; function f7(x,y)&=x^2+y^2=r^2; ...  
\>   &makelist(concat('m, k) :: tan(pi/2 + k\*(2\*pi)/7), k, 1, 6); ...  
\>   &makelist(concat('s,l) :: solve([f7(x,y)=0, y=ev(concat('m,l))\*x], [x,y]), l, 1, 6);  ...  
\>   $s1, $s2, $s3, $s4, $s5, $s6


$$\left[ \left[ x=-\frac{r}{\sqrt{\tan ^2\left(\frac{31\,\pi}{14}  \right)+1}} , y=-\frac{\tan \left(\frac{31\,\pi}{14}\right)\,r}{  \sqrt{\tan ^2\left(\frac{31\,\pi}{14}\right)+1}} \right]  , \left[ x=  \frac{r}{\sqrt{\tan ^2\left(\frac{31\,\pi}{14}\right)+1}} , y=\frac{  \tan \left(\frac{31\,\pi}{14}\right)\,r}{\sqrt{\tan ^2\left(\frac{31  \,\pi}{14}\right)+1}} \right]  \right] $$![images/Tugas%206-223.png](images/Tugas%206-223.png)

![images/Tugas%206-224.png](images/Tugas%206-224.png)

![images/Tugas%206-225.png](images/Tugas%206-225.png)

![images/Tugas%206-226.png](images/Tugas%206-226.png)

![images/Tugas%206-227.png](images/Tugas%206-227.png)

\>B&=[x,y] with s1[1]; C&=[x,y] with s2[1]; D&=[x,y] with s3[1]; ...  
\>   F&=[x,y] with s4[2]; G&=[x,y] with s5[2]; H&=[x,y] with s6[2]; $A, $B, $C, $D, $F, $G, $H


$$\left[ \frac{r}{\sqrt{\tan ^2\left(\frac{31\,\pi}{14}\right)+1}} ,   \frac{\tan \left(\frac{31\,\pi}{14}\right)\,r}{\sqrt{\tan ^2\left(  \frac{31\,\pi}{14}\right)+1}} \right] $$![images/Tugas%206-229.png](images/Tugas%206-229.png)

![images/Tugas%206-230.png](images/Tugas%206-230.png)

![images/Tugas%206-231.png](images/Tugas%206-231.png)

![images/Tugas%206-232.png](images/Tugas%206-232.png)

![images/Tugas%206-233.png](images/Tugas%206-233.png)

![images/Tugas%206-234.png](images/Tugas%206-234.png)

\>r=7; A=A(); B=B(); C=C(); D=D(); F=F(); G=G(); H=H();

\>clg; plotSegment(A,B,""); plotSegment(B,C,""); plotSegment(C,D,"");  ...  
\>   plotSegment(D,F,""); plotSegment(F,G,""); plotSegment(G,H,""); plotSegment(H,A,""):


![images/Tugas%206-235.png](images/Tugas%206-235.png)

 2. Gambarlah suatu parabola yang melalui 3 titik yang diketahui.  

Petunjuk:


- Misalkan persamaan parabolanya y= ax^2+bx+c.


- Substitusikan koordinat titik-titik yang diketahui ke persamaan tersebut.


- Selesaikan SPL yang terbentuk untuk mendapatkan nilai-nilai a, b, c.


\>function f(x)&=p\*x^2+q\*x+r; A=[0,2]; B=[5, 5]; C=[-3,3];

\>$solve([f(0)=2, f(5)=5, f(-3)=3],[p,q,r])


$$\left[ \left[ p=\frac{7}{60} , q=\frac{1}{60} , r=2 \right]    \right] $$\>plot2d("(7/60)\*x^2+(1/60)\*x+2", a=-7, b=7, c=-2, d=7); ...  
\>   plotPoint(A,"A"); plotPoint(B,"B"); plotPoint(C,"C"):


![images/Tugas%206-237.png](images/Tugas%206-237.png)

\>&remvalue(all)


    
                                                     []
    

3. Gambarlah suatu segi-4 yang diketahui keempat titik sudutnya, misalnya A, B, C, D.


   - Tentukan apakah segi-4 tersebut merupakan segi-4 garis singgung (sisi-sisinya merupakan garis
singgung lingkaran yang sama yakni lingkaran dalam segi-4 tersebut).


   - Suatu segi-4 merupakan segi-4 garis singgung apabila keempat garis bagi sudutnya bertemu di satu
titik.


   - Jika segi-4 tersebut merupakan segi-4 garis singgung, gambar lingkaran dalamnya.


   - Tunjukkan bahwa syarat suatu segi-4 merupakan segi-4 garis singgung apabila hasil kali panjang
sisi-sisi yang berhadapan sama.


\>A=[-18,6]; B=[12,6]; C=[3,-6]; D=[-2,-6]; ...  
\>   g1=angleBisector(A,B,C); g2=angleBisector(B,C,D); ...  
\>   g3=angleBisector(C,D,A); g4=angleBisector(D,A,B); ...  
\>   g1, g2, g3, g4


    [-12,  24,  0]
    [24,  12,  0]
    [9,  -3,  0]
    [-4,  -12,  0]

\>function g1(x,y)&=-12\*x+24\*y; function g2(x,y)&=24\*x+12\*y;  ...  
\>   function g3(x,y)&=9\*x-3\*y; function g4(x,y)&=-4\*x-12\*y; 

\>s1&=solve([g1(x,y)=0, g2(x,y)=0],[x,y]); s2&=solve([g2(x,y)=0, g3(x,y)=0],[x,y]);  ...  
\>   s3&=solve([g3(x,y)=0, g4(x,y)=0],[x,y]); s4&=solve([g4(x,y)=0, g1(x,y)=0],[x,y]);  ...  
\>   $s1, $s2, $s3, $s3


$$\left[ \left[ x=0 , y=0 \right]  \right] $$![images/Tugas%206-239.png](images/Tugas%206-239.png)

![images/Tugas%206-240.png](images/Tugas%206-240.png)

![images/Tugas%206-241.png](images/Tugas%206-241.png)

\>aspect(1); clg; setPlotRange(-18, 18, -18, 18); T=projectToLine(O, lineThrough(A,B)); r=distance(O,T); ...  
\>   plotCircle([0,0,r]); ...  
\>   plotSegment(A,B,""); plotSegment(B,C,""); ...  
\>   plotSegment(C,D,""); plotSegment(D,A,""); ...  
\>   plotPoint(O, "O"); plotPoint(D, "D"):


![images/Tugas%206-242.png](images/Tugas%206-242.png)

4. Gambarlah suatu ellips jika diketahui kedua titik fokusnya, misalnya P dan Q. Ingat ellips dengan
fokus P dan Q adalah tempat kedudukan titik-titik yang jumlah jarak ke P dan ke Q selalu sama
(konstan).


\>P=[1,2]; Q=[-2,-1]; distance(P,Q)


    4.24264068712

\>k=6; clg; setPlotRange(-5,4,-4,5);  ...  
\>   plot2d("sqrt((x-P[1])^2+(y-P[2])^2)+sqrt((x-Q[1])^2+(y-Q[2])^2)-k", a=-5, b=4, c=-4, d=5, level=0, \>add); ...  
\>   plotPoint(P, "P"); plotPoint(Q, "Q"); ...  
\>   R=[-2,-2]; plotPoint(R,"R"); plotSegment(P,R,""); plotSegment(R,Q,""):


![images/Tugas%206-243.png](images/Tugas%206-243.png)

\>distance(P,R)+distance(R,Q)


    6

5. Gambarlah suatu hiperbola jika diketahui kedua titik fokusnya, misalnya P dan Q. Ingat hiperbola
dengan fokus P dan Q adalah tempat kedudukan titik-titik yang selisih jarak ke P dan ke Q selalu sama
(konstan).


\>P=[1,2]; Q=[-2,-1]; distance(P,Q)


    4.24264068712

\>k=2; clg; setPlotRange(-7, 6, -6, 7); ...  
\>   plot2d("(sqrt((x-P[1])^2+(y-P[2])^2) - sqrt((x-Q[1])^2+(y-Q[2])^2))^2 - k^2", a=-7, b=6, c=-6, d=7, level=0, \>add); ...  
\>   plotPoint(P, "P"); plotPoint(Q, "Q"):


![images/Tugas%206-244.png](images/Tugas%206-244.png)

6. Gambarlah suatu parabola jika diketahui titik fokus dan direktriksnya, misalnya P dan g. Ingat
parabola dengan fokus P adalah tempat kedudukan titik-titik yang berjarak sama terhadap titik fokus
dan direktriksnya.


\>P=[1,2]; g=[1,1,-1]; clg; setPlotRange(-5, 6, -4, 7); ...  
\>   plot2d("(x-P[1])^2 + (y-P[2])^2 - (g[1]\*x + g[2]\*y - g[3])^2 / (g[1]^2 + g[2]^2)", a=-5, b=6, c=-4, d=7, level=0, \>add); ...  
\>   plotPoint(P, "P"); plotLine(g):


![images/Tugas%206-245.png](images/Tugas%206-245.png)

