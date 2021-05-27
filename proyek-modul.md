# Looping

---

**Looping** (perulangan) merupakan proses di dalam program yang dapat mengeksekusi beberapa _statement_ yang sama secara berulang-ulang sampai ada kondisi yang membuatnya berhenti. Terdapat tiga jenis perulangan, yaitu for, while, dan do-while.

## 1. For

Perulangan for umum digunakan apabila jumlah perulangan telah/dapat diketahui secara pasti. Pernyataan pada badan perulangan akan terus dieksekusi hingga kondisi bernilai False. Perulangan for memiliki bentuk dasar sebagai berikut.

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

### Contoh 3

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

Coba Anda kembangkan program di atas agar bisa digunakan untuk menentukan apakah suatu bilangan merupakan bilangan prima atau bukan.

## 2. While
