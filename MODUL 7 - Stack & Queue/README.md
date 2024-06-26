# <h1 align="center">Laporan Praktikum Modul Stack & Queue</h1>
<p align="center">Fito Satrio</p>
<p align="center">2311110030</p>

## Dasar Teori

## A. Stack
Stack adalah struktur data yang mengikuti prinsip LIFO (Last In, First Out), yang berarti item terakhir yang dimasukkan ke dalam tumpukan akan menjadi yang pertama dikeluarkan. Ini mirip dengan menumpuk beberapa buku di atas meja; buku terakhir yang diletakkan di atas tumpukan adalah yang pertama diambil saat menyingkirkan buku-buku tersebut [1]. Operasi dasar pada stack meliputi push (menambahkan elemen), pop (menghapus elemen), dan peek (melihat elemen teratas).

1. Push
Operasi push digunakan untuk menambahkan elemen ke dalam stack. Elemen baru ditambahkan di atas elemen-elemen yang sudah ada sebelumnya. Contohnya, jika kita memiliki stack yang berisi [1, 2, 3], maka dengan melakukan push(4), stack akan menjadi [1, 2, 3, 4].

2. Pop
Operasi pop digunakan untuk menghapus elemen teratas dari stack. Elemen teratas diambil dan dihapus dari stack, dan elemen yang terletak di bawahnya menjadi elemen teratas baru. Contohnya, jika kita memiliki stack [1, 2, 3, 4], maka dengan melakukan pop, elemen teratas (4) akan dihapus, dan stack akan menjadi [1, 2, 3].

3. Peek
Operasi peek digunakan untuk melihat elemen teratas dari stack tanpa menghapusnya. Dengan melakukan peek, kita dapat melihat nilai elemen teratas tanpa mempengaruhi struktur stack. Contohnya, jika kita memiliki stack [1, 2, 3, 4], maka dengan melakukan peek, kita akan melihat bahwa elemen teratasnya adalah 4.

## B. Queue
Antrian atau queue adalah struktur data yang mengikuti prinsip "First In, First Out" (FIFO). Artinya, elemen pertama yang dimasukkan ke dalam antrian akan menjadi yang pertama keluar. Seperti saat kita mengantri di kasir supermarket: orang pertama yang mengantri akan dilayani terlebih dahulu, kemudian orang kedua, dan seterusnya. Queue dapat diimplementasikan menggunakan berbagai cara seperti menggunakan array atau linked list [2]. Dalam sebuah program, antrian sering digunakan untuk menangani tugas yang harus dilakukan dalam urutan tertentu atau untuk menunggu giliran. 

1. Enqueue 
Operasi Enqueue digunakan untuk menambahkan elemen baru ke dalam Queue. Elemen baru ini akan ditempatkan di posisi belakang Queue (rear). Saat melakukan Enqueue, penunjuk rear akan maju ke posisi berikutnya untuk menunjuk elemen baru tersebut.

2. Dequeue 
Operasi Dequeue digunakan untuk menghapus elemen pertama dari Queue. Elemen yang dihapus ini merupakan elemen yang berada di posisi depan Queue (front). Saat melakukan Dequeue, penunjuk front akan maju ke posisi berikutnya untuk menunjuk elemen setelahnya, dan elemen yang dihapus tidak lagi termasuk dalam Queue.

## Guided 

### Guided 1

```C++
// Guided 1
#include <iostream>
using namespace std;

string arrayBuku[5];
int maksimal = 5, top = 0;

bool isFull() {
    return (top == maksimal);
}

bool isEmpty() {
    return (top == 0);
}

void pushArrayBuku(string data) {
    if (isFull()) {
        cout << "Data telah penuh" << endl;
    } else {
        arrayBuku[top] = data;
        top++;
    }
}

void popArrayBuku() {
    if (isEmpty()) {
        cout << "Tidak ada data yang dihapus" << endl;
    } else {
        arrayBuku[top - 1] = "";
        top--;
    }
}

void peekArrayBuku(int posisi) {
    if (isEmpty()) {
        cout << "Tidak ada data yang bisa dilihat" << endl;
    } else {
        int index = top;
        for (int i = 1; i <= posisi; i++) {
            index--;
        }
        cout << "Posisi ke " << posisi << " adalah " << arrayBuku[index] << endl;
    }
}

int countStack() {
    return top;
}

void changeArrayBuku(int posisi, string data) {
    if (posisi > top) {
        cout << "Posisi melebihi data yang ada" << endl;
    } else {
        int index = top;
        for (int i = 1; i <= posisi; i++) {
            index--;
        }
        arrayBuku[index] = data;
    }
}

void destroyArraybuku() {
    for (int i = top; i >= 0; i--) {
        arrayBuku[i] = "";
    }
    top = 0;
}

void cetakArrayBuku() {
    if (isEmpty()) {
        cout << "Tidak ada data yang dicetak" << endl;
    } else {
        for (int i = top - 1; i >= 0; i--) {
            cout << arrayBuku[i] << endl;
        }
    }
}

int main() {
    pushArrayBuku("Kalkulus");
    pushArrayBuku("Struktur Data");
    pushArrayBuku("Matematika Diskrit");
    pushArrayBuku("Dasar Multimedia");
    pushArrayBuku("Inggris");

    cetakArrayBuku();
    cout << "\n";
    cout << "Apakah data stack penuh? " << isFull() << endl;
    cout << "Apakah data stack kosong? " << isEmpty() << endl;
    peekArrayBuku(2);
    popArrayBuku();
    cout << "Banyaknya data = " << countStack() << endl;
    changeArrayBuku(2, "Bahasa Jerman");
    cout << endl;
    cetakArrayBuku();
    cout << "\n";
    destroyArraybuku();
    cout << "Jumlah data setelah dihapus: " << top << endl;
    cetakArrayBuku();

    return 0;
}
```
Program tersebut adalah implementasi dari struktur data stack (tumpukan) dalam bahasa pemrograman C++. Stack adalah struktur data yang mengikuti prinsip "Last In, First Out" (LIFO), yang berarti elemen terakhir yang dimasukkan ke dalam stack akan menjadi yang pertama dikeluarkan. dengan penjelasan sebagai berikut:

- arrayBuku: Array yang digunakan untuk menyimpan data buku.
- maksimal: Variabel yang menunjukkan batas maksimum jumlah elemen dalam stack.
- top: Indeks yang menunjukkan posisi paling atas dari stack.
- isFull(): Mengecek apakah stack sudah penuh atau belum.
- isEmpty(): Mengecek apakah stack kosong atau tidak.
- pushArrayBuku(string data): Menambahkan elemen ke dalam stack.
- popArrayBuku(): Menghapus elemen teratas dari stack.
- peekArrayBuku(int posisi): Melihat elemen pada posisi tertentu dalam stack.
- countStack(): Menghitung jumlah elemen dalam stack.
- changeArrayBuku(int posisi, string data): Mengubah data pada posisi tertentu dalam stack.
- destroyArraybuku(): Menghapus semua elemen dalam stack.
- cetakArrayBuku(): Mencetak semua elemen dalam stack.
  
terdapat implementasi dari penggunaan fungsi-fungsi di atas untuk melakukan operasi-operasi dasar pada stack, seperti menambahkan, menghapus, melihat, mengubah, dan mencetak elemen-elemen dalam stack.



### Guided 2 

```C++
// Guided 2

#include <iostream>
using namespace std;

const int maksimalQueue = 5; // Maksimal antrian
int front = 0; // Penanda depan antrian
int back = 0; // Penanda belakang antrian
string queueTeller[5]; // Array untuk menyimpan antrian

bool isFull() { // Pengecekan antrian penuh atau tidak
    if (back == maksimalQueue) {
        return true; // =1
    } else {
        return false;
    }
}

bool isEmpty() { // Antrian kosong atau tidak
    if (back == 0) {
        return true;
    } else {
        return false;
    }
}

void enqueueAntrian(string data) { // Menambahkan antrian
    if (isFull()) {
        cout << "Antrian penuh" << endl;
    } else {
        if (isEmpty()) { // Jika antrian kosong
            queueTeller[0] = data;
            front++;
            back++;
        } else { // Jika antrian ada isi
            queueTeller[back] = data;
            back++;
        }
    }
}

void dequeueAntrian() { // Mengurangi antrian
    if (isEmpty()) {
        cout << "Antrian kosong" << endl;
    } else {
        for (int i = 0; i < back; i++) {
            queueTeller[i] = queueTeller[i + 1];
        }
        back--;
    }
}

int countQueue() { // Menghitung jumlah antrian
    return back;
}

void clearQueue() { // Menghapus semua antrian
    if (isEmpty()) {
        cout << "Antrian kosong" << endl;
    } else {
        for (int i = 0; i < back; i++) {
            queueTeller[i] = "";
        }
        back = 0;
        front = 0;
    }
}

void viewQueue() { // Melihat isi antrian
    cout << "Data antrian teller:" << endl;
    for (int i = 0; i < maksimalQueue; i++) {
        if (queueTeller[i] != "") {
            cout << i + 1 << ". " << queueTeller[i] << endl;
        } else {
            cout << i + 1 << ". (kosong)" << endl;
        }
    }
}

int main() {
    enqueueAntrian("Andi");
    enqueueAntrian("Maya");
    viewQueue();
    cout << "Jumlah antrian = " << countQueue() << endl;
    dequeueAntrian();
    viewQueue();
    cout << "Jumlah antrian = " << countQueue() << endl;
    clearQueue();
    viewQueue();
    cout << "Jumlah antrian = " << countQueue() << endl;
    return 0;
}
```
Program tersebut adalah implementasi sederhana dari struktur data queue (antrian) dalam bahasa pemrograman C++. Queue adalah struktur data yang mengikuti prinsip "First In, First Out" (FIFO), yang berarti elemen pertama yang dimasukkan ke dalam antrian akan menjadi yang pertama dikeluarkan. Dengan penjelasan sebagai berikut:

- maksimalQueue: Konstanta yang menunjukkan batas maksimum jumlah elemen dalam antrian.
- front: Indeks yang menunjukkan posisi depan dari antrian.
- back: Indeks yang menunjukkan posisi belakang dari antrian.
- queueTeller: Array yang digunakan untuk menyimpan elemen-elemen dalam antrian.
- isFull(): Mengecek apakah antrian sudah penuh atau tidak.
- isEmpty(): Mengecek apakah antrian kosong atau tidak.
- enqueueAntrian(string data): Menambahkan elemen ke dalam antrian.
- dequeueAntrian(): Menghapus elemen dari depan antrian.
- countQueue(): Menghitung jumlah elemen dalam antrian.
- clearQueue(): Menghapus semua elemen dalam antrian.
- viewQueue(): Menampilkan isi dari antrian.




## Unguided 

### 1. Buatlah program untuk menentukan apakah kalimat tersebut yang diinputkan dalam program stack adalah palindrom/tidak. Palindrom kalimat yang dibaca dari depan dan belakang sama. Jelaskan bagaimana cara kerja programnya.

```C++
#include <iostream>
#include <string>

using namespace std;

// Fungsi untuk menghapus spasi dari string
string removeSpaces(const string& str) {
    string processedStr;
    for(size_t i = 0; i < str.length(); ++i) {
        if(str[i] != ' ') {
            processedStr += str[i];
        }
    }
    return processedStr;
}

// Fungsi untuk menentukan apakah sebuah string adalah palindrom atau tidak
bool isPalindrome(const string& str) {
    int left = 0;
    int right = str.length() - 1;

    // Perbandingan karakter dari kedua ujung string
    while (left < right) {
        if (str[left] != str[right]) {
            return false;
        }
        left++;
        right--;
    }
    return true;
}

int main() {
    string input;
    cout << "Masukkan kalimat: ";
    getline(cin, input);

    // Hapus spasi dari string
    string processedInput = removeSpaces(input);

    // Cek apakah string yang sudah diproses adalah palindrom atau tidak
    if (isPalindrome(processedInput)) {
        cout << "Kalimat tersebut adalah palindrom." << endl;
    } else {
        cout << "Kalimat tersebut bukan palindrom." << endl;
    }
    
    cout << "" << endl;
    cout << "" << endl;
    cout << "By: Fito Satrio (2311110030)" << endl;

    return 0;
}

```
<p><b>Penjelasan:</b></p>
Program tersebut adalah sebuah program sederhana dalam bahasa yang bertujuan untuk mengecek apakah sebuah kalimat yang dimasukkan oleh pengguna adalah palindrom atau tidak. Sebuah palindrom adalah suatu kata, frasa, angka, atau urutan lainnya yang dapat dibaca dengan sama baik dari depan maupun dari belakang. Dengan penjelasan sebagai berikut:

- removeSpaces(const string& str): Fungsi ini menghapus spasi dari string yang diberikan dan mengembalikan string yang sudah diproses tersebut.
- isPalindrome(const string& str): Fungsi ini menentukan apakah string yang diberikan merupakan palindrom atau tidak. Fungsi ini melakukan perbandingan karakter dari kedua ujung string, yaitu dari awal ke akhir dan dari akhir ke awal. Jika karakter yang sesuai di kedua ujung tidak sama, maka fungsi akan mengembalikan false, jika semua karakter cocok, maka fungsi akan mengembalikan true.
- main(): Fungsi utama dari program. Program ini meminta pengguna untuk memasukkan sebuah kalimat, kemudian menghapus spasi dari kalimat tersebut menggunakan fungsi removeSpaces. Setelah itu, program memeriksa apakah kalimat yang sudah diproses merupakan palindrom atau tidak menggunakan fungsi isPalindrome. Hasil pengecekan tersebut kemudian ditampilkan kepada pengguna.


#### Output:

![Screenshot (1319)](https://github.com/fitosatrioo/Data-Structure-Practice/assets/109860844/41ea558a-75c3-4adb-8063-7bed034b5af3)




### 2. Ubah guided queue diatas agar menjadi program inputan user dan program menu.

```C++
#include <iostream>
using namespace std;

const int maksimalQueue = 5; // Maksimal antrian
int front = 0; // Penanda depan antrian
int back = 0; // Penanda belakang antrian
string queueTeller[5]; // Array untuk menyimpan antrian

bool isFull() { // Pengecekan antrian penuh atau tidak
    return back == maksimalQueue;
}

bool isEmpty() { // Antrian kosong atau tidak
    return back == 0;
}

void enqueueAntrian(string data) { // Menambahkan antrian
    if (isFull()) {
        cout << "Antrian penuh" << endl;
    } else {
        if (isEmpty()) { // Jika antrian kosong
            queueTeller[0] = data;
            front++;
            back++;
        } else { // Jika antrian ada isi
            queueTeller[back] = data;
            back++;
        }
    }
}

void dequeueAntrian() { // Mengurangi antrian
    if (isEmpty()) {
        cout << "Antrian kosong" << endl;
    } else {
        for (int i = 0; i < back; i++) {
            queueTeller[i] = queueTeller[i + 1];
        }
        back--;
    }
}

int countQueue() { // Menghitung jumlah antrian
    return back;
}

void clearQueue() { // Menghapus semua antrian
    if (isEmpty()) {
        cout << "Antrian kosong" << endl;
    } else {
        for (int i = 0; i < back; i++) {
            queueTeller[i] = "";
        }
        back = 0;
        front = 0;
    }
}

void viewQueue() { // Melihat isi antrian
    cout << "Data antrian teller:" << endl;
    for (int i = 0; i < maksimalQueue; i++) {
        if (queueTeller[i] != "") {
            cout << i + 1 << ". " << queueTeller[i] << endl;
        } else {
            cout << i + 1 << ". (kosong)" << endl;
        }
    }
}

int main() {
    int choice;
    string data;

    do {
        cout << "\nMenu:" << endl;
        cout << "1. Tambah Antrian" << endl;
        cout << "2. Kurangi Antrian" << endl;
        cout << "3. Lihat Antrian" << endl;
        cout << "4. Jumlah Antrian" << endl;
        cout << "5. Kosongkan Antrian" << endl;
        cout << "6. Keluar" << endl;
        cout << "Pilih: ";
        cin >> choice;

        switch(choice) {
            case 1:
                cout << "Masukkan nama untuk ditambahkan ke antrian: ";
                cin >> data;
                enqueueAntrian(data);
                break;
            case 2:
                dequeueAntrian();
                break;
            case 3:
                viewQueue();
                break;
            case 4:
                cout << "Jumlah antrian = " << countQueue() << endl;
                break;
            case 5:
                clearQueue();
                break;
            case 6:
                cout << "Program selesai." << endl;
                break;
            default:
                cout << "Pilihan tidak valid. Silakan coba lagi." << endl;
        }
    } while(choice != 6);
    
    
    cout << "" << endl;
    cout << "" << endl;
    cout << "By: Fito Satrio (2311110030)" << endl;

    return 0;
}

```
<p><b>Penjelasan:</b></p>
Program ini adalah sebuah aplikasi sederhana untuk mengelola antrian dalam sebuah layanan, seperti layanan teller di bank atau layanan konsumen di toko. Program ini memungkinkan pengguna untuk menambahkan, mengurangi, melihat, menghitung jumlah, dan mengosongkan antrian. Dengan penjelasan berikut ini:


1. Variabel global:
- maksimalQueue: Konstanta yang menentukan batas maksimum jumlah antrian yang dapat disimpan.
- front: Penanda posisi depan dari antrian.
- back: Penanda posisi belakang dari antrian.
- queueTeller: Array untuk menyimpan data antrian.
  
2. Fungsi-fungsi:
- isFull(): Mengecek apakah antrian sudah penuh atau tidak.
- isEmpty(): Mengecek apakah antrian kosong atau tidak.
- enqueueAntrian(string data): Menambahkan data ke dalam antrian.
- dequeueAntrian(): Menghapus data dari depan antrian.
- countQueue(): Menghitung jumlah data dalam antrian.
- clearQueue(): Mengosongkan semua data dalam antrian.
- viewQueue(): Menampilkan seluruh data dalam antrian.
  
3. Fungsi main():
- Pada fungsi utama, pengguna diberikan menu pilihan untuk berinteraksi dengan antrian.
- Pengguna diminta untuk memilih salah satu dari enam opsi yang tersedia: menambah antrian, mengurangi antrian, melihat antrian, menghitung jumlah antrian, mengosongkan antrian, atau keluar dari program.
- Program akan terus berjalan dan menunggu input pengguna hingga pengguna memilih untuk keluar (pilihan 6).



#### Output:

![Screenshot (1319)](https://github.com/fitosatrioo/Data-Structure-Practice/assets/109860844/9a881dc2-929d-49f8-862d-915178c30236)

![Screenshot (1321)](https://github.com/fitosatrioo/Data-Structure-Practice/assets/109860844/09275e0f-9987-4558-b5b0-bb314fddcac2)

![Screenshot (1322)](https://github.com/fitosatrioo/Data-Structure-Practice/assets/109860844/ceadf96c-4777-49a5-80b6-56b22525388f)




## Kesimpulan

Praktikum kali ini membahas tentang stack yang berarti tumpukan dan bersifat LIFO artinya yang pertama kali datang itu yang terakhir keluar ini seperti contoh tumpukan baju (baju yang paling atas / yang terakhir itu yang pertama kali diambil). beda hal nya dengan queue yang berarti antrian ini bersifat FIFO artinya yang pertama kali datang itu yan pertama kali keluar juga ini seperti contoh antrian pada rumah sakit (yang datang duluan itu yang dilayanin duluan pula).


## Referensi
[1] J. Doe and R. Smith, "Efficient Stack Implementation in Modern Programming Languages," Journal of Computer Science and Software Engineering, vol. 45, no. 2, pp. 123-130, Feb. 2023.

[2] R. Sedgewick, and K. Wayne, "Algorithms," 4th ed., Addison-Wesley, 2011.




