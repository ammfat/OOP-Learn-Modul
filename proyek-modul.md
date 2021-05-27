My parts:

1. Input dan Branching
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

Selanjutnya, di dalam _class_ yang membutuhkan _input_, deklarasikan _object_ dari _class_ Scanner, misal:

```
public class AmbilInput {
    Scanner scanner = new Scanner(System.in);
}
```

... Terdapat beberapa _method_ yang dapat digunakan untuk menerima _input_, satu _method_ untuk tiap tipe data.

-   .nextInt() : untuk menerima tipe data integer
-   .nextShort() : untuk menerima tipe data short
-   .nextLong() : untuk menerima tipe data long
-   .nextDouble() : untuk menerima tipe data double
-   .nextFloat() : untuk menerima tipe data float
-   .nextLine() : untuk menerima tipe data string
-   .nextBoolean() : untuk menerima tipa data boolean

### Contoh 1: Salam

## 1.2. Branching

## 1.2.1. Struktur if-else

### Contoh 1

hahaha

## 1.2.2 Struktur if-elif-else

## 1.2.3. Struktur switch-case

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
