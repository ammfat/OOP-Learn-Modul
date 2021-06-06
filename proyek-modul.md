My parts:

1. Input dan Branching [DONE]
2. Looping [DONE]
3. Array
4. ArrayList

---

# 1. Input dan Branching

## 1.1. Input

Sebuah program aplikasi yang kompleks akan memerlukan interaksi antara pengguna dengan program. Pengguna dapat berinteraksi dengan program dengan cara memberikan masukan (_input_). Pada materi ini, akan dibahas bagaimana pengguna dapat memberikan _input_ melalui _keyboard_.

Agar program dapat menerima masukan dari pengguna, pertama Anda harus mengimpor _class_ `java.util.Scanner`, dengan cara menambahkan baris berikut sebelum deklarasi _class_ yang melakukan proses _input_.

```
import java.util.Scanner;
```

Selanjutnya, di dalam _class_ yang membutuhkan _input_, deklarasikan _object_ dari _class_ `Scanner`, misal:

```
public class AmbilInput {
    Scanner scanner = new Scanner(System.in);
}
```

Mungkin sekarang timbul pertanyaan, apa itu "`System.in`" yang terletak pada argumen `Scanner`?

`System.in` merupakan sebuah _predefined object_, sebuah objek yang sudah tertanam (_built-in_) pada Java, yang merepresentasikan _standard input stream_. Sederhananya, ia adalah objek yang digunakan apabila kita ingin menerima _input_ melalui _keyboard_.

Selain `System.in`, _standard stream_ lain yang umum digunakan pada Java diantaranya sebagai berikut.

-   `System.out` : untuk menampilkan _output_ ke layar.
-   `System.err` : untuk mengirimkan pesan _error_.

Terdapat beberapa _method_ yang dapat digunakan untuk menerima _input_, satu _method_ untuk tiap tipe data.

-   `.nextInt()` : untuk menerima tipe data integer
-   `.nextShort()` : untuk menerima tipe data short
-   `.nextLong()` : untuk menerima tipe data long
-   `.nextDouble()` : untuk menerima tipe data double
-   `.nextFloat()` : untuk menerima tipe data float
-   `.nextLine()` : untuk menerima tipe data string
-   `.nextBoolean()` : untuk menerima tipe data boolean

### Contoh 1: Sapa \<nama>

```
import java.util.Scanner;

public class JavaMenyapa {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Nama kamu: ");
        String nama = scanner.nextLine();

        System.out.println("Halo " + nama + ". Aku Javaludin, salam kenal yaa ^^/");
    }
}
```

Pada program di atas, kita menampilkan nama yang dimasukkan pengguna pada baris `String nama = scanner.nextLine();`.

### Contoh 2: Pembagian a / b

```
import java.util.Scanner;

public class BagiAB {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        double a, b, c;

        System.out.print("Masukkan nilai a\t: ");
        a = scanner.nextDouble();

        System.out.print("Masukkan nilai b\t: ");
        b = scanner.nextDouble();

        c = a / b;
        System.out.print("Hasil a + b\t\t: " + c);
    }
}
```

## 1.2. Branching

Selain antarmuka yang menerima masukan pengguna, sebuah program yang kompleks umumnya juga dapat menangani beberapa kondisi dengan cara yang berbeda.

Misal, Anda diminta membuat program yang menerima input angka `integer` dari pengguna, lalu menentukan apakah angka tersebut merupakan bilangan ganjil atau genap. Secara algoritma deskriptif, prosesnya dapat dituliskan sebagai berikut.

1. Dapatkan input angka dari pengguna.
2. **Jika** angka tersebut habis dibagi 2, **maka** ia adalah bilangan genap. **Jika tidak**, maka ia adalah bilangan ganjil.

Pada bahasa pemrograman, algoritma di atas dapat dituliskan ke dalam kode dalam bentuk struktur percabangan (_branching_). Pada Java, terdapat empat bentuk struktur _branching_, yaitu struktur `if`, `if-else`, `if-else if-else`, dan `switch`.

## 1.2.1. Struktur if

Struktur `if` digunakan untuk pengambilan keputusan terhadap dua buah kemungkinan, apakah kondisi bernilai `true` atau `false`.

Percabangan `if` memiliki bentuk dasar sebagai berikut.

```
if (kondisi) {
    statement
}
```

Statement pada tubuh `if` hanya akan dieksekusi apabila blok kondisi bernilai `true`.

### Contoh 1: Sapa Hanya Andi

```
import java.util.Scanner;

public class SapaHanyaAndi {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Masukkan nama: ");
        String nama = scanner.nextLine();

        if (nama.equals("Andi")) {
            System.out.println("Halo, Andi! :)");
            System.out.println("Sampai nanti ya, Andi!");
            System.out.println("...");
            System.out.println("Mmm, Andi, siapa perempuan di belakangmu itu?");
        }
    }
}
```

Program di atas menerima masukan dari pengguna melalui baris `String nama = scanner.nextLine();`. Kemudian pada struktur _branching_, ditulis kondisi yang harus dipenuhi agar statement di tubuh `if` dieksekusi, yaitu pada bagian `if (nama.equals("Andi"))`.

Apabila pengguna memberi masukan "Andi", maka statement `nama.equals("Andi")` akan menghasilkan nilai `true`. Oleh sebab blok kondisi bernilai `true`, maka seluruh statement di tubuh `if` akan dieksekusi.

Sebaliknya, apabila pengguna memberi masukan _selain_ "Andi", maka statement `nama.equals("Andi")` akan menghasilkan nilai `false` dan statement di tubuh `if` tidak akan dieksekusi.

### Contoh 2: Cashback Belanja

**_Class Belanja_**

```
public class Belanja {
    private final double faktor = 0.2;
    private final int totalHarga;
    private double bayar, cashback = 0;

    public Belanja(int totalHarga) {
        this.totalHarga = totalHarga;
    }

    public void hitungHarga() {
        bayar = totalHarga;

        if (totalHarga >= 500000) {
            cashback = faktor * totalHarga;
        }

        bayar = bayar - cashback;
        System.out.println("Silakan bayar sebesar\t: " + bayar);
    }
}
```

**_Class BelanjaKeterusan_**

```
import java.util.Scanner;

public class BelanjaKeterusan {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Total harga\t: ");
        int totalHarga = scanner.nextInt();

        Belanja belanja = new Belanja(totalHarga);
        belanja.hitungHarga();
    }
}

```

## 1.2.2. Struktur if-else

Struktur `if-else` digunakan untuk mengatur statement yang dijalankan sewaktu kondisi bernilai `true` atau `false`.

Percabangan `if-else` memiliki bentuk dasar sebagai berikut.

```
if (kondisi) {
    statement yang dijalankan bila kondisi bernilai true
} else {
    statement yang dijalankan bila kondisi bernilai false
}
```

### Contoh 1: Sapa Hanya Andi v2

```
import java.util.Scanner;

public class SapaHanyaAndi {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Masukkan nama: ");
        String nama = scanner.nextLine();

        if (nama.equals("Andi")) {
            System.out.println("Halo, Andi! :)");
            System.out.println("Sampai nanti ya, Andi!");
            System.out.println("...");
            System.out.println("Mmm, Andi, siapa perempuan di belakangmu itu?");
        } else {
            System.out.println("Loh, siapa kamu?!!");
        }
    }
}
```

### Contoh 2: Cashback Belanja v2

**_Class Belanja_**

```
public class Belanja {
    private final double faktor1 = 0.2, faktor2 = 0.05;
    private final int totalHarga;
    private double bayar, cashback = 0;

    public Belanja(int totalHarga) {
        this.totalHarga = totalHarga;
    }

    public void hitungHarga() {
        bayar = totalHarga;

        if (totalHarga >= 500000) {
            cashback = faktor1 * totalHarga;
        } else {
            cashback = faktor2 * totalHarga;
        }

        bayar = bayar - cashback;
        System.out.println("Silakan bayar sebesar\t: " + bayar);
    }
}
```

**_Class BelanjaKeterusan_**

```
import java.util.Scanner;

public class BelanjaKeterusan {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Total harga\t: ");
        int totalHarga = scanner.nextInt();

        Belanja belanja = new Belanja(totalHarga);
        belanja.hitungHarga();
    }
}

```

## 1.2.3. Struktur if-else if-else

Struktur `if-else if-else` digunakan untuk mengatur statement yang dijalankan sewaktu kondisi berupa pilihan.

Percabangan `if-else if-else` memiliki bentuk dasar sebagai berikut.

```
if (kondisiA) {
    statement yang dijalankan, bila kondisiA true
} else if (kondisiB) {
    statement yang dijalankan, bila kondisiB true
} else if (kondisiC) {
    statement yang dijalankan, bila kondisiC true
}
...
else {
    statement yang dijalankan untuk kondisi selain itu
}
```

### Contoh 1: Sapa Andi dan Beni

```
import java.util.Scanner;

public class SapaAndiBeni {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Masukkan nama: ");
        String nama = scanner.nextLine();

        if (nama.equals("Andi")) {
            System.out.println("Halo, Andi! :)");
            System.out.println("Sampai nanti ya, Andi!");
            System.out.println("...");
            System.out.println("Mmm, Andi, siapa perempuan di belakangmu itu?");
        } else if (nama.equals("Beni")) {
            System.out.println("Halo, Beni!");
            System.out.println("Apa kabarmu? Semoga kamu baik-baik saja.");
        } else {
            System.out.println("Loh, siapa kamu?!!");
        }
    }
}
```

### Contoh 2: Mutu Huruf Nilai

```
import java.util.Scanner;

public class MutuHuruf {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        char mutuHuruf;

        System.out.print("Nilai (0-100)\t: ");
        double nilai = scanner.nextDouble();

        if (nilai >= 90) {
            mutuHuruf = 'A';
        } else if (nilai >= 80) {
            mutuHuruf = 'B';
        } else if (nilai >= 70) {
            mutuHuruf = 'C';
        } else if (nilai >= 60) {
            mutuHuruf = 'D';
        } else {
            mutuHuruf = 'E';
        }

        System.out.println("Nilai\t\t: " + nilai);
        System.out.println("Mutu Huruf\t: " + mutuHuruf);
    }
}
```

## 1.2.4. Struktur switch

Struktur `switch` digunakan untuk melakukan tindakan berbeda terhadap sejumlah kemungkinan nilai.

Percabangan `switch` memiliki bentuk dasar sebagai berikut.

```
switch (ekspresi) {
    case nilaiSatu:
        statement_1
        break;
    case nilaiDua:
        statement_2
        break;
    ...
    default: statement_n;
}
```

### Contoh 1: Sapa Andi dan Beni v2

```
import java.util.Scanner;

public class SapaAndiBeni {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Masukkan nama: ");
        String nama = scanner.nextLine();

        switch (nama) {
            case "Andi":
                System.out.println("Halo, Andi! :)");
                System.out.println("Sampai nanti ya, Andi!");
                System.out.println("...");
                System.out.println("Mmm, Andi, siapa perempuan di belakangmu itu?");
                break;
            case "Beni":
                System.out.println("Halo, Beni!");
                System.out.println("Apa kabarmu? Semoga kamu baik-baik saja.");
                break;
            default:
                System.out.printl   n("Loh, siapa kamu?!!");
                break;
        }
    }
}
```

Apabila Anda _copas_ kode di atas pada Netbeans IDE, Netbeans akan menyarankan perubahan secara sintaks. Anda bebas memilih menggunakan penulisan sintaks yang ditawarkan ataupun tetap menggunakan sintaks awal. Berikut adalah sintaks kode setelah diubah sesuai saran dari Netbeans IDE

```
import java.util.Scanner;

public class SapaAndiBeni {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Masukkan nama: ");
        String nama = scanner.nextLine();

        switch (nama) {
            case "Andi" -> {
                System.out.println("Halo, Andi! :)");
                System.out.println("Sampai nanti ya, Andi!");
                System.out.println("...");
                System.out.println("Mmm, Andi, siapa perempuan di belakangmu itu?");
            }
            case "Beni" -> {
                System.out.println("Halo, Beni!");
                System.out.println("Apa kabarmu? Semoga kamu baik-baik saja.");
            }
            default -> System.out.println("Loh, siapa kamu?!!");
        }
    }
}
```

### Contoh 2: Mutu Huruf Nilai v2

```
import java.util.Scanner;

public class MutuHuruf {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        char mutuHuruf;

        System.out.print("Nilai (0-100)\t: ");
        double nilai = scanner.nextDouble();

        if (nilai >= 90) {
            mutuHuruf = 'A';
        } else if (nilai >= 80) {
            mutuHuruf = 'B';
        } else if (nilai >= 70) {
            mutuHuruf = 'C';
        } else if (nilai >= 60) {
            mutuHuruf = 'D';
        } else {
            mutuHuruf = 'E';
        }

        System.out.println("Nilai\t\t: " + nilai);
        System.out.println("Mutu Huruf\t: " + mutuHuruf);

        switch (mutuHuruf) {
            case 'A':
                System.out.println("Sangat bagus! Jaga terus!!");
                break;
            case 'B':
                System.out.println("Sedikit lagi untuk mencapai puncak!");
                break;
            case 'C':
                System.out.println("Hati-hati! Kamu di zona rawan, TERUS SEMANGAT!!");
                break;
            case 'D':
                System.out.println("Ayoo! Perbanyak belajar, KAMU PASTI BISA!");
                break;
            case 'E':
                System.out.println("Yuk, bisa yuk!");
                break;
            default:
                System.out.println("Terdapat kesalahan pada sistem");
        }
    }
}
```

---

# 2. Looping

**Looping** (perulangan) merupakan proses di dalam program yang dapat mengeksekusi beberapa _statement_ yang sama secara berulang-ulang sampai ada kondisi yang membuatnya berhenti. Terdapat tiga jenis perulangan, yaitu for, while, dan do-while.

## 2.1. For

Perulangan `for` umum digunakan apabila jumlah perulangan telah/dapat diketahui secara pasti. Pernyataan pada badan perulangan akan terus dieksekusi hingga kondisi bernilai False.

Perulangan for memiliki bentuk dasar sebagai berikut.

```
for (inisiasi; kondisi; penaikan_penurunan) {
	pernyataan
}
```

### Contoh 1: For Penaikan

```
public class ForLoop {
    public static void main(String[] args) {
        for (int i = 0; i < 10; i = i + 1) {
            System.out.println("Perulangan ke-" + i);
        }
    }
}
```

Secara sederhana, baris `for (int i = 0; i < 10; i = i + 1)` dapat dibaca “isi variabel `i` dengan nilai `0`. Jika nilai `i` masih kurang dari `10`, eksekusi pernyataan di bawah. Setiap pernyataan di bawah dieksekusi, tambah nilai `i` sebesar `1`.”
Bagian `i = i + 1` dapat disingkat menjadi `i++`. Sehingga bentuk lengkapnya menjadi `for (int i = 0; i < 10; i++)`.

Baris `System.out.println("Perulangan ke-" + i);` akan mencetak tulisan `“Perulangan ke-”` dan nilai `i` dimana nilai `i` akan selalu berubah di tiap perulangan.

### Contoh 2: For Penurunan

```
public class ForLoop {
    public static void main(String[] args) {
        for (int i = 10; i >= 0; i--) {
            System.out.println(i + "..");
        }

        System.out.println("Ignition... And liftoff");
    }
}
```

Perbedaan dari For penaikan (_increment_) dan penurunan (_decrement_) hanyalah pada bagian `i--`. Konsep penaikan dan penurunan ini dapat digunakan pada seluruh bentuk perulangan, tidak hanya perulangan `for`.

### Contoh 3: Dengan Branching

Tak hanya statement sederhana seperti pada contoh-contoh sebelumnya, statement pengkondisian, input, bahkan perulangan lain pun bisa dimasukkan di dalam tubuh perulangan. Berikut adalah contoh penggunaan perulangan untuk mencari bilangan ganjil dan genap.

```
public class ForLoop {
    public static void main(String[] args) {
        for (int i = 1; i <= 10; i++) {
            if (i % 2 == 0) {
                System.out.println(i + " adalah bilangan GENAP");
            } else {
                System.out.println(i + " adalah bilangan GANJIL");
            }
        }

        System.out.println("Program selesai.");
    }
}
```

Cobalah modifikasi program di atas agar bisa digunakan untuk menentukan apakah suatu bilangan merupakan bilangan prima atau bukan.

### Contoh 4: Segitiga Bintang Terbalik

Perhatikan struktur teks berikut!

```
*****
****
***
**
*
```

Dengan menggunakan konsep perulangan, struktur diatas juga dapat dihasilkan.

**Class Segitiga**

```
public class Segitiga {
    private int lebar;

    public Segitiga(int lebar) {
        this.lebar = lebar;
    }

    public String gambarSegitiga() {
        String r = "";

        for (int i = lebar; i > 0; i--) {
            for (int j = i; j > 0; j--) {
                r = r + "*";
            }
            r = r + "\n";
        }

        return r;
    }
}
```

**Class SegitigaBeraksi**

```
public class SegitigaBeraksi {
    public static void main(String[] args) {
        Segitiga segitigaKu = new Segitiga(5);
        System.out.println(segitigaKu.gambarSegitiga());
    }
}
```

Cobalah modifikasi program di atas agar output segitiga yang dihasilkan tidak terbalik.

## 2.2. While

Pada perulangan `while`, pengecekan kondisi dilakukan di awal blok (sama seperti perulangan `for`). Apabila kondisi tidak terpenuhi (bernilai false) maka proses pengulangan tidak akan pernah dilakukan atau tidak berjalan.

Perulangan while memiliki bentuk dasar sebagai berikut.

```
while (kondisi) {
    pernyataan
}
```

### Contoh 1: Menentukan Bilangan Genap/Ganjil

```
import java.util.Scanner;

public class WhileLoop {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int i = 1;
        System.out.print("Masukkan banyak bilangan: ");
        int n = scanner.nextInt();

        while (i <= n) {
            if (i % 2 == 0) {
                System.out.println(i + " adalah bilangan GENAP");
            } else {
                System.out.println(i + " adalah bilangan GANJIL");
            }

            i++;
        }
    }
}
```

Berbeda dengan perulangan `for`, pada `while` inisiasi tidak dapat dilakukan pada blok `while()`. Oleh sebab itu, dituliskan baris `int i = 1;` untuk melakukan deklarasi dan inisiasi pada variabel `i`, yang akan digunakan sebagai variabel acuan kondisi perulangan.

Dari baris `while (i <= n)`, dapat diketahui bahwa perulangan akan dilakukan selama nilai `i` kurang dari atau sama dengan `n`. Nilai `n` diperoleh dari masukan pengguna melalui baris `int n = scanner.nextInt();`.

Pada tubuh perulangan, terdapat blok `if ... else ...` yang digunakan untuk memeriksa apakah suatu bilangan termasuk bilangan ganjil atau genap.

Hal paling penting dalam perulangan, termasuk `while`, adalah memastikan bahwa pada suatu titik perulangan harus berhenti. Pada kasus ini, perulangan harus berhenti ketika nilai `i` lebih dari nilai `n`. Agar nilai `i` bertambah setiap statement selesai dieksekusi, perlu ditambahkan operasi yang menambah nilai `i` pada tubuh perulangan. Hal ini dapat dilakukan dengan statement `i++` tepat sebelum tubuh perulangan `while` ditutup.

### Contoh 2: Deret Bilangan Prima (Nested Loop)

Sebuah perulangan juga dapat ditempatkan di dalam perulangan lainnya. Ini disebut perulangan bersarang (_nested loop_). Berikut adalah contoh penerepan _nested loop_ dengan `while`.

```
import java.util.Scanner;

public class WhilePrimeSeries {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int i = 0;
        int isPrime = 0, isNotPrime = 0;
        int counter;

        System.out.print("Masukkan panjang deret: ");
        int n = scanner.nextInt();

        // Outer loop
        while (i <= n) {
            counter = 0;
            int j = 1;

            // Inner loop
            while (j <= i) {
                if (i % j == 0) {
                    counter += 1;
                }

                j++;
            }

            if (counter == 2) {
                isPrime += i;
            } else {
                isNotPrime += i;
            }

            i++;
        }

        System.out.println("Prime Series = " + isPrime);
        System.out.println("Non-prime Series = " + isNotPrime);
    }
}
```

## 2.3. Do-While

Struktur do-while memiliki bentuk yang mirip dengan `while`. Hanya saja, pada `do-while`, pengecekan kondisi dilakukan setelah tubuh perulangan. Dengan struktur demikian, maka perulangan pasti dimasuki setidaknya sebanyak satu kali meskipun kondisi bernilai `false`.

Perulangan while memiliki bentuk dasar sebagai berikut.

```
do {
    pernyataan
} while(kondisi);
```

### Contoh 1: Mencetak Huruf Alfabet (A-Z)

```
public class DoWhileAlfabet {

    public static void main(String[] args) {
        char c = 'A';

        do {
            System.out.println(c);
            c++;
        } while(c <= 'Z');
    }
}
```

Ada sesuatu yang 'berbeda' dengan contoh di atas? Ya, selain menggunakan tipe data angka sebagaimana pada contoh-contoh sebelumnya, Java juga mendukung penggunaan tipe data `char` sebagai _iterator_ perulangan. Ini berlaku untuk semua jenis perulangan (tidak hanya pada `do-while`).

Cobalah modifikasi program di atas agar menghasilkan output huruf 'Z' sampai dengan 'A'.

### Contoh 2: Menentukan Bilangan Prima

```
import java.util.Scanner;

public class DoWhilePrima {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int i = 1;
        int counter;

        System.out.print("Masukkan banyak bilangan: ");
        int n = scanner.nextInt();

        while (i <= n) {
            counter = 0;
            int j = 1;

            while (j <= i) {
                if (i % j == 0) {
                    counter += 1;
                }

                j++;
            }

            if (counter == 2) {
                System.out.println(i + " adalah bilangan PRIMA");
            } else {
                System.out.println(i + " adalah bilangan NON-PRIMA");
            }

            i++;
        }
    }
}
```

---

# 3. Array

Cobalah Anda buat program sederhana untuk menampilkan sebuah daftar yang berisi maksimal lima (5) musik yang sering Anda putar.

...

Apakah di dalam program tersebut Anda menulis kode serupa seperti ini?

```
public static void main(String[] args) {
    String musikFavorit = "Musik 1, Musik 2, Musik 3, Musik 4, Musik 5"
    System.out.println(musikFavorit);
}
```

Atau mungkin serupa seperti ini?

```
public static void main(String[] args) {
    String musikFavorit1 = "Musik 1",
            musikFavorit2 = "Musik 2",
            musikFavorit3 = "Musik 3",
            musikFavorit4 = "Musik 4",
            musikFavorit5 = "Musik 5";

    System.out.println(musikFavorit1);
    System.out.println(musikFavorit2);
    System.out.println(musikFavorit3);
    System.out.println(musikFavorit4);
    System.out.println(musikFavorit5);
}
```

Kode-kode tersebut tentunya berjalan normal. Namun, terdapat cara yang lebih baik untuk menampilkan kumpulan data identik dibanding cara di atas, yaitu dengan menggunakan `array` (larik).

_Array_ merupakan sebuah struktur data yang digunakan untuk menyimpan kumpulan data dengan tipe data yang sama. Oleh sebab menampung sekumpulan data, _array_ akan memiliki ukuran yang nilainya sama dengan banyaknya data yang ditampung oleh _array_ tersebut. Ukuran sebuah _array_, biasa juga disebut panjangnya, bersifat statis (tidak dapat diubah sepanjang program).

## 3.1. Deklarasi dan Inisialisasi Array

Berikut adalah cara-cara membuat _array_ pada Java dengan studi kasus sebelumnya.

```
// Cara 1: kurung siku setelah tipe data
String[] musikFavorit;
musikFavorit = new String[5];

// Cara 2: kurung siku setelah nama variabel
String musikFavorit[];
musikFavorit = new String[5];

// Cara 3: cara 1 atau 2 disingkat
String musikFavorit[] = new String[5];
```

Angka **5** pada baris kode di atas menunjukkan _array_ tersebut berukuran 5. _Array_ yang telah dibuat dapat diinisialisasi dengan cara berikut.

```
musikFavorit[0] = "Musik 1";
musikFavorit[1] = "Musik 2";
musikFavorit[2] = "Musik 3";
musikFavorit[3] = "Musik 4";
musikFavorit[4] = "Musik 5";
```

Anda juga dapat menyingkat deklarasi dan inisiasi dengan cara seperti berikut.

```
String musikFavorit[] = {"Musik 1", "Musik 2", "Musik 3", "Musik 4", "Musik 5"};
```

### Contoh 1: Daftar Musik Favorit

```
import java.util.Scanner;

public class ArrayContohMusik {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        scanner.useDelimiter("\n");

        String musikFavorit[] = new String[5];

        for (int i = 0; i < musikFavorit.length; i++) {
            System.out.print("Musik ke-" + (i+1) + ": ");
            musikFavorit[i] = scanner.nextLine();
        }

        for (String mF: musikFavorit) {
            System.out.println(mF);
        }
    }
}
```

Baris `scanner.useDelimiter("\n");` digunakan agar pengguna dapat memasukkan data di baris `musikFavorit[i] = scanner.nextLine();` pada perulangan secara _normal_. Silakan Anda coba hapus baris `scanner.useDelimiter("\n");` dan lihat efeknya pada program.

_Method_ `.length()` pada bagian `for (int i = 0; i < musikFavorit.length; i++)` digunakan untuk mendapatkan panjang _array_, sehingga perulangan dilakukan selama nilai `i` kurang dari panjang _array_.

Terdapat juga bentuk perulangan baru yang Anda pelajari, yaitu `for-each` pada bagian:

```
for (String mF: musikFavorit) {
    System.out.println(mF);
}
```

Bentuk perulangan ini sangat baik digunakan apabila Anda ingin _mendapatkan nilai_ yang ditampung pada _array_.

## 3.2. Array Multidimensi

Pada **Contoh 1**, _array_ yang dibuat merupakan _array_ 1 dimensi. Apakah ada _array_ 2 dimensi, 3 dimensi, 4 dimensi, atau singkatnya: multidimensi? Jawabannya, ada.

Cara membuat _array_ multidimensi adalah dengan memberikan lebih dari 1 kurung siku. Tiap kurung siku pada _array_ mewakili jumlah dimensinya.

```
String arrayKu[];        // array 1 dimensi
String arrayMu[][];      // array 2 dimensi
String arrayKita[][][];  // array 3 dimensi
```

Berapa banyak dimensi yang dapat dibuat? Sebanyak yang Anda sanggup ketik.

### Contoh 2: Array Multidimensi

```
import java.util.Scanner;

public class ArrayMultidimensi {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        String[][] nama = {
            {"Kang ", "Teh ", "Mbak "},
            {"Beni", "Eni", null}
        };

        System.out.println(nama[0][0] + nama[1][0]);
        System.out.println(nama[0][1] + nama[1][1]);
        System.out.println(nama[0][2] + nama[1][0]);

        System.out.print("Masukkan orang baru: ");
        String orangBaru = scanner.nextLine();

        nama[1][2] = orangBaru;

        System.out.print("-----\nSelamat datang ");
        System.out.println(nama[0][2] + nama[1][2]);
    }
}
```

---

# 4. Array List

## Subbab 1

## Subbab 2

### Contoh 1

### Contoh 2
