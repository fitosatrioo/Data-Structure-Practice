# <h1 align="center">Laporan Praktikum Modul Struct</h1>
<p align="center">Fito Satrio</p>
<p align="center">2311110030</p>

## Dasar Teori

Struct merupakan sebuah fitur yang memungkinkan pengguna untuk mendefinisikan sebuah tipe data baru yang terdiri dari beberapa anggota yang berbeda. Setiap anggota ini dapat memiliki tipe data yang berbeda pula. Secara umum, struct digunakan untuk mengelompokkan data terkait menjadi satu unit yang lebih besar. Kata kunci struct memberi tahu kompiler bahwa template struktur sedang ditentukan, yang dapat digunakan untuk membuat variabel struktur. Bidang-bidang yang membentuk struktur disebut anggota atau elemen struktur. Semua elemen dalam suatu struktur secara logis berhubungan satu sama lain [1]. 
	
Setiap variabel dalam struct memiliki tipe data tertentu, yang bisa berupa tipe data primitif seperti int, float, char, atau bahkan tipe data yang lebih kompleks seperti string, array, atau struct lainnya [2]. Variabel dalam sebuah struct memungkinkan kita untuk mengorganisir dan mengelola data dengan cara yang lebih terstruktur dalam program. Variabel ini memungkinkan kita untuk menggabungkan berbagai jenis data terkait ke dalam satu unit yang dapat dengan mudah diakses dan dimanipulasi.
	
## Guided 

### Guided 1

```C++
// Guided 1
#include <iostream>
using namespace std;

struct buku {
	string JudulBuku;
	string pengarang;
	string penerbit;
	int tebalHalaman;
	int hargaBuku;
};

int main(){
	
buku mybook, mybook2;

mybook.JudulBuku = "Harry Potter";
mybook.pengarang = "J.K Rowling";
mybook.penerbit = "Scholastic Press";
mybook.tebalHalaman = 870;
mybook.hargaBuku = 2000000;

mybook2.JudulBuku = "Kata";
mybook2.pengarang = "Tere Liye";
mybook2.penerbit = "Scholastic Press";
mybook2.tebalHalaman = 250;
mybook2.hargaBuku = 3500000;


cout << "=== Deskripsi Buku ===" << endl;
cout <<"Judul Buku: " << mybook.JudulBuku << endl;
cout <<"Nama Pengarang: " << mybook.pengarang << endl;
cout <<"Nama penerbit: " << mybook.penerbit << endl;
cout <<"Tebal Halaman: " << mybook.tebalHalaman << endl;
cout <<"Harga Buku: " << mybook.hargaBuku << endl;
cout << "" << endl;
cout <<"Judul Buku: " << mybook2.JudulBuku << endl;
cout <<"Nama Pengarang: " << mybook2.pengarang << endl;
cout <<"Nama penerbit: " << mybook2.penerbit << endl;
cout <<"Tebal Halaman: " << mybook2.tebalHalaman << endl;
cout <<"Harga Buku: " << mybook2.hargaBuku << endl;


return 0;

}


```
Program di atas adalah contoh sederhana dari penggunaan struktur (struct) dalam bahasa pemrograman C++. Program ini membuat sebuah struktur bernama buku yang memiliki lima anggota: JudulBuku (Menyimpan judul buku dalam bentuk string), pengarang (Menyimpan nama pengarang buku dalam bentuk string), penerbit (Menyimpan nama penerbit buku dalam bentuk string), tebalHalaman (Menyimpan jumlah halaman buku dalam bentuk bilangan bulat), dan hargaBuku (Menyimpan harga buku dalam bentuk bilangan bulat).

Setelah mendefinisikan struktur buku, program kemudian membuat dua objek dari struktur tersebut, yaitu mybook dan mybook2. Setiap objek ini merepresentasikan sebuah buku dengan data yang berbeda.

Data buku pertama (mybook) adalah sebagai berikut:

- Judul Buku: "Harry Potter"

- Pengarang: "J.K Rowling"

- Penerbit: "Scholastic Press"

- Tebal Halaman: 870

- Harga Buku: 2,000,000

Sedangkan data buku kedua (mybook2) adalah sebagai berikut:

- Judul Buku: "Kata"

- Pengarang: "Tere Liye"

- Penerbit: "Scholastic Press"

- Tebal Halaman: 250

- Harga Buku: 3,500,000

Setelah data diinisialisasi, program menampilkan deskripsi buku ke layar menggunakan perintah cout. Setiap anggota dari setiap objek mybook dan mybook2 diakses dan ditampilkan secara terpisah. Ini memungkinkan kita untuk melihat detail seperti judul buku, pengarang, penerbit, jumlah halaman, dan harga buku untuk kedua objek tersebut.

### Guided 2 

```C++
// Guided 2

#include <iostream>
#include <string>
using namespace std;

struct hewan {
    string Nama_hewan;
    string Jenis_kelamin;
    string cara_berkembangbiak;
    string alat_pernafasan;
    string tempat_hidup;
    bool karnivora;
};

struct hewanDarat {
    hewan info_hewan;
    int jumlah_kaki;
    bool menyusui;
    string suara;
};

struct hewanLaut {
    hewan info_hewan;
    string sirip;
    string pertahanan_diri;
};

int main() {
    hewanDarat hewan_darat1; // Renamed variable to hewan_darat1
    hewanLaut hewan_laut1;   // Renamed variable to hewan_laut1
    
    hewan_darat1.info_hewan.Nama_hewan = "Kucing Ireng";
    hewan_darat1.info_hewan.Jenis_kelamin = "betina";
    hewan_darat1.info_hewan.cara_berkembangbiak = "Vivipar / melahirkan";
    hewan_darat1.info_hewan.alat_pernafasan = "Paru - Paru";
    hewan_darat1.info_hewan.tempat_hidup = "Darat";
    hewan_darat1.info_hewan.karnivora = true;
    hewan_darat1.jumlah_kaki = 4;
    hewan_darat1.menyusui = true;
    hewan_darat1.suara = "meow";

    hewan_laut1.info_hewan.Nama_hewan = "Ikan Hiu";
    hewan_laut1.info_hewan.Jenis_kelamin = "jantan";
    hewan_laut1.info_hewan.cara_berkembangbiak = "Ovovivipar";
    hewan_laut1.info_hewan.alat_pernafasan = "Insang";
    hewan_laut1.info_hewan.tempat_hidup = "Laut";
    hewan_laut1.info_hewan.karnivora = true;
    hewan_laut1.sirip = "besar dan kuat";
    hewan_laut1.pertahanan_diri = "menggunakan gigi dan sirip";

    cout <<"=== HEWAN DARAT ===" << endl;
    cout <<"Nama Hewan: " << hewan_darat1.info_hewan.Nama_hewan << endl;
    cout <<"Jenis Kelamin: " << hewan_darat1.info_hewan.Jenis_kelamin << endl;
    cout <<"Cara Berkembangbiak: " << hewan_darat1.info_hewan.cara_berkembangbiak << endl;
    cout <<"Alat Pernafasan: " << hewan_darat1.info_hewan.alat_pernafasan << endl;
    cout <<"Tempat Hidup: " << hewan_darat1.info_hewan.tempat_hidup << endl;
    cout <<"Apakah Karnivora?: " << (hewan_darat1.info_hewan.karnivora ? "Ya" : "Tidak") << endl;
    cout <<"Jumlah Kaki: " << hewan_darat1.jumlah_kaki << endl;
    cout <<"Apakah Menyusui?: " << (hewan_darat1.menyusui ? "Ya" : "Tidak") << endl;
    cout <<"Suara: " << hewan_darat1.suara << endl;

    cout <<"\n=== HEWAN LAUT ===" << endl;
    cout <<"Nama Hewan: " << hewan_laut1.info_hewan.Nama_hewan << endl;
    cout <<"Jenis Kelamin: " << hewan_laut1.info_hewan.Jenis_kelamin << endl;
    cout <<"Cara Berkembangbiak: " << hewan_laut1.info_hewan.cara_berkembangbiak << endl;
    cout <<"Alat Pernafasan: " << hewan_laut1.info_hewan.alat_pernafasan << endl;
    cout <<"Tempat Hidup: " << hewan_laut1.info_hewan.tempat_hidup << endl;
    cout <<"Apakah Karnivora?: " << (hewan_laut1.info_hewan.karnivora ? "Ya" : "Tidak") << endl;
    cout <<"Bentuk Sirip: " << hewan_laut1.sirip << endl;
    cout <<"Pertahanan Diri: " << hewan_laut1.pertahanan_diri << endl;

    return 0;
}

```
Program ini adalah contoh sederhana dari penggunaan struktur data dalam pemrograman C++. Struktur data digunakan untuk mengelompokkan beberapa variabel yang memiliki hubungan dan membentuk suatu entitas yang lebih besar.

Di dalam program ini, terdapat tiga buah struktur data yang didefinisikan:

struct hewan: Struktur data ini berisi informasi umum tentang hewan, seperti nama hewan, jenis kelamin, cara berkembang biak, alat pernafasan, tempat hidup, dan apakah hewan tersebut karnivora atau bukan.

struct hewanDarat: Struktur data ini merupakan turunan dari hewan dan menambahkan informasi khusus untuk hewan darat, seperti jumlah kaki, apakah hewan tersebut menyusui, dan suara yang dihasilkan.

struct hewanLaut: Struktur data ini juga merupakan turunan dari hewan namun memiliki informasi spesifik untuk hewan laut, seperti bentuk sirip dan cara pertahanan diri.

Setelah mendefinisikan struktur data, program kemudian membuat dua objek: hewan_darat1 dan hewan_laut1 yang merupakan instansi dari hewanDarat dan hewanLaut masing-masing. Program kemudian mengisi data untuk kedua objek tersebut.


## Unguided 

### 1. Modifikasi tugas guided pertama, sehingga setiap item yang terdapat pada sruct buku berupa array yang berukuran 5, isi dengan data kemudian tampilkan.


```C++
#include <iostream>
#include <string>
using namespace std;

struct buku {
    string JudulBuku[5];
    string pengarang[5];
    string penerbit[5];
    int tebalHalaman[5];
    int hargaBuku[5];
};

int main() {
    buku mybook;

    // Memasukkan data buku dari input pengguna
    for (int i = 0; i < 5; ++i) {
        cout << "Masukkan data untuk buku " << i + 1 << ":" << endl;
        cout << "Judul Buku: ";
        getline(cin, mybook.JudulBuku[i]);
        cout << "Nama Pengarang: ";
        getline(cin, mybook.pengarang[i]);
        cout << "Nama penerbit: ";
        getline(cin, mybook.penerbit[i]);
        cout << "Tebal Halaman: ";
        cin >> mybook.tebalHalaman[i];
        cout << "Harga Buku: ";
        cin >> mybook.hargaBuku[i];
        cin.ignore(); // Membersihkan buffer untuk input berikutnya
        cout << endl;
    }

    // Menampilkan data buku
    cout << "=== Deskripsi Buku ===" << endl;
    for (int i = 0; i < 5; ++i) {
        cout << "Buku " << i + 1 << ":" << endl;
        cout << "Judul Buku: " << mybook.JudulBuku[i] << endl;
        cout << "Nama Pengarang: " << mybook.pengarang[i] << endl;
        cout << "Nama penerbit: " << mybook.penerbit[i] << endl;
        cout << "Tebal Halaman: " << mybook.tebalHalaman[i] << endl;
        cout << "Harga Buku: " << mybook.hargaBuku[i] << endl;
        cout << endl;
    }
    
    cout << "" << endl;
    cout << "" << endl;
    cout << "By: Fito Satrio (2311110030)" << endl;

    return 0;
    
    
}

```
<p><b>Penjelasan:</b></p>
Program di atas adalah sebuah contoh sederhana tentang bagaimana menggunakan struktur data  untuk menyimpan informasi tentang beberapa buku. Program ini memanfaatkan struktur data buku yang memiliki beberapa array untuk menyimpan informasi tentang judul buku, pengarang, penerbit, tebal halaman, dan harga buku untuk hingga lima buku.

Pertama-tama, di dalam fungsi main(), sebuah objek mybook dari tipe buku dibuat.

Selanjutnya, program meminta pengguna untuk memasukkan data untuk masing-masing buku menggunakan loop for. Di dalam loop tersebut, program meminta pengguna untuk memasukkan judul buku, nama pengarang, nama penerbit, tebal halaman, dan harga buku. Data yang dimasukkan oleh pengguna disimpan ke dalam array yang sesuai di dalam objek mybook.

Setelah selesai memasukkan data untuk semua buku, program menampilkan deskripsi dari setiap buku yang telah dimasukkan menggunakan loop for. Program mencetak judul buku, nama pengarang, nama penerbit, tebal halaman, dan harga buku untuk setiap buku.



#### Output:
![Screenshot (1265)](https://github.com/fitosatrioo/Data-Structure-Practice/assets/109860844/15c4d2ac-16ea-4a6a-a14d-36e42c23b981)
![Screenshot (1266)](https://github.com/fitosatrioo/Data-Structure-Practice/assets/109860844/4b17f325-a6a3-405b-8552-a455395e17f0)


#### Full Screenshoot Code:
![Screenshot (1267)](https://github.com/fitosatrioo/Data-Structure-Practice/assets/109860844/12abfba1-9374-4eb5-8dd6-81fe3bc4e7c0)







### 2. Apa yang terjadi jika deklarasi variabel struct yang dibuat pada tugas guided 1, berjenis array. Bagaimana cara mengisi dan menampilkannya.


<p><b>Penjelasan:</b></p>
Jika variabel struct yang dibuat pada tugas guided I berjenis array maka akan menghasilkan array yang setiap elemennya merupakan struct. Ini memungkinkan menyimpan banyak data dengan tipe data yang sama dalam satu struktur. Contohnya dapat dilihat pada unguided satu, dimana variabel dideklarasikan sebagai array dengan 5 elemen, yang setiap elemen berupa struct berisi data buku dari 5 buku berbeda. 

Ketika variabel struct yang dibuat pada tugas guided I dideklarasikan sebagai array, maka kita akan memiliki sebuah array di mana setiap elemennya adalah sebuah struct yang berisi data yang terdefinisi dalam struktur tersebut. Misalnya, jika kita menggunakan contoh dari tugas guided I yang memiliki variabel struct hewan, kita dapat mendeklarasikan array dari struct tersebut, seperti hewan array_hewan[5];. Ini akan menghasilkan sebuah array yang dapat menyimpan data tentang beberapa hewan dalam satu struktur.

Proses pengisian data pada array tersebut dilakukan dengan cara mengakses setiap elemen array secara berurutan dan mengisi nilai atribut-atribut yang sesuai untuk setiap hewan. Misalnya, jika atribut dari struct hewan adalah Nama_hewan, Jenis_kelamin, cara_berkembangbiak, dan seterusnya, maka setiap elemen array akan diisi dengan data-data tersebut sesuai dengan informasi yang dimiliki oleh hewan yang bersangkutan.

Untuk menampilkan data yang disimpan dalam array tersebut, kita dapat menggunakan perulangan (seperti loop for) untuk mengakses setiap elemen array dan menampilkan nilai atribut-atributnya dengan menggunakan fungsi cout. Dengan menggunakan loop, kita bisa menampilkan informasi tentang setiap hewan dalam array secara berurutan.


## Kesimpulan
- ### Hasil Praktikum
Praktikum kali ini membahas tentang struct yang merupakan sebuah fitur yang dapat menyimpan sebuah variabel dengan tipe data yang berbeda - beda. dari guided 1 dan 2 kita mempelajari satu kelas struct dan multiclass struct yang dapat berhubungan dengan kelas struct yang lainnya. kita dapat lihat pada guided 2, untuk menghubungkannya kita menggunakan variabel hewan_info.

- ### Pelajaran yang didapat
Dari struct memungkinkan pengelompokan data terkait menjadi satu unit yang disebut sebagai tipe data baru. Ini memudahkan pengorganisasian data dalam program. Struct dapat memiliki atribut (variabel) dan metode (fungsi) yang memungkinkan untuk memanipulasi dan mengakses data yang terkandung di dalamnya. Struct dapat digunakan dalam berbagai konteks, dari representasi objek dalam pemrograman berorientasi objek hingga penyimpanan data terstruktur dalam program yang lebih umum. Dengan struct, kita dapat membuat representasi data yang kompleks dan terstruktur, yang memudahkan dalam manajemen dan pengolahan data.

## Referensi
[1] S. N Mohanty, P. K. Tripathy, Data Structure and Algorithms Using C++ A Practical Implementation, USA: Wiley, 2021.

[2] A. D. Samala, B. Ramadhani, F. Ranurja, Pemrograman C++, Padang: UNP Press, 2021. 



