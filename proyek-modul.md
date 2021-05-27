# Looping

---

Looping (perulangan) merupakan proses di dalam program yang dapat mengeksekusi beberapa statement yang sama secara berulang-ulang sampai ada kondisi yang membuatnya berhenti. Terdapat tiga jenis perulangan, yaitu for, while, dan do-while.

## 1. For

Perulangan for umum digunakan apabila jumlah perulangan telah/dapat diketahui secara pasti. Pernyataan pada badan perulangan akan terus dieksekusi hingga kondisi bernilai False. Perulangan for memiliki bentuk dasar sebagai berikut.

```
for (inisiasi; kondisi; penaikan_penurunan) {
	pernyataan
}
```

### Contoh 1: For penaikan

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

Baris System.out.println("Perulangan ke-" + i); akan mencetak tulisan “Perulangan ke-” dan nilai i

2. While
3. Do-while
