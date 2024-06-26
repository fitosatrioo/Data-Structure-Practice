# <h1 align="center">Laporan Praktikum Modul Linked List</h1>
<p align="center">Fito Satrio</p>
<p align="center">2311110030</p>

## Dasar Teori

Linked list merupakan suatu struktur data yang terdiri dari serangkaian node yang saling terhubung. Setiap node menyimpan sebuah elemen data dan referensi atau pointer ke node berikutnya dalam urutan. Ini berbeda dengan array, di mana elemen-elemen data disimpan secara berurutan dalam memori. Linked List memiliki keunggulan dibandingkan Array dalam hal menambahkan dan mengurangi elemennya [1].

Ada beberapa jenis linked list, tetapi yang paling umum adalah single linked list dan double linked list. Dalam single linked list, setiap node memiliki satu pointer yang menunjuk ke node berikutnya dalam urutan. Ini membuat akses linier ke elemen-elemen dalam linked list, karena Anda harus melalui setiap node dari awal untuk mencapai elemen yang diinginkan. berbeda dengan double linked list yang menambahkan satu pointer tambahan pada setiap simpul yaitu pointer prev yang menunjuk ke simpul sebelumnya.

## A. Single Linked List
Single linked list merupakan struktur data linier yang terdiri dari serangkaian elemen data yang disusun dalam urutan linier. Setiap elemen dalam single linked list disebut "node" dan terdiri dari dua bagian: data itu sendiri dan referensi atau pointer ke node berikutnya dalam urutan [2]. Single linked list sangat penting dalam pemrograman karena fleksibilitasnya dalam penambahan dan penghapusan elemen. Ketika elemen baru ditambahkan ke linked list, ia dapat ditempatkan di mana saja dalam memori, dan pointer dari node sebelumnya diperbarui untuk menunjuk ke elemen baru. 

```r
   HEAD
    ↓
[ data | next ] -> [ data | next ] -> [ data | next ] -> NULL

```
Di sini, "HEAD" adalah pointer yang menunjuk ke node pertama dalam linked list. Setiap node terdiri dari dua bagian: bagian pertama menyimpan elemen data, dan bagian kedua adalah pointer yang menunjuk ke node berikutnya [3]. Node terakhir dalam linked list memiliki pointer bernilai NULL, menunjukkan akhir dari linked list.

## B. Double Linked List
Double linked list adalah struktur data linier yang terdiri dari serangkaian node, di mana setiap node memiliki dua bagian utama: data yang disimpan dan dua pointer. Pointer pertama menunjuk ke node sebelumnya dalam urutan, dan pointer kedua menunjuk ke node berikutnya dalam urutan. Ini memungkinkan navigasi maju dan mundur dalam linked list dengan mudah.

```r
   HEAD
    ↓
NULL <- [prev | data | next] <-> [prev | data | next] <-> [prev | data | next] <-> NULL
```
Di sini, "HEAD" adalah pointer yang menunjuk ke node pertama dalam linked list. Setiap node menyimpan elemen data dan dua pointer: satu untuk node sebelumnya dan satu untuk node berikutnya. Node pertama memiliki pointer ke NULL untuk prev karena tidak ada node sebelumnya, dan node terakhir memiliki pointer ke NULL untuk next karena tidak ada node setelahnya.

## Guided 

### Guided 1

```C++
// Guided 1
#include <iostream>
using namespace std;

///PROGRAM SINGLE LINKED LIST NON-CIRCULAR
//Deklarasi Struct Node
struct Node{
    //komponen/member
    int data;
    Node *next;
};
    Node *head;
    Node *tail;
//Inisialisasi Node
void init(){
    head = NULL;
    tail = NULL;
}
// Pengecekan
bool isEmpty(){
    if (head == NULL)
    return true;
    else
    return false;
}
//Tambah Depan
void insertDepan(int nilai){
    //Buat Node baru
    Node *baru = new Node;
    baru->data = nilai;
    baru->next = NULL;
    if (isEmpty() == true){
        head = tail = baru;
        tail->next = NULL;
    }
    else{
        baru->next = head;
        head = baru;
    }
}
//Tambah Belakang
void insertBelakang(int nilai){
    //Buat Node baru
    Node *baru = new Node;
    baru->data = nilai;
    baru->next = NULL;
    if (isEmpty() == true){
        head = tail = baru;
        tail->next = NULL;
    }
    else{
    tail->next = baru;
    tail = baru;
    }
}
//Hitung Jumlah List
int hitungList(){
    Node *hitung;
    hitung = head;
    int jumlah = 0;
    while( hitung != NULL ){
        jumlah++;
        hitung = hitung->next;
    }
    return jumlah;
}
//Tambah Tengah
void insertTengah(int data, int posisi){
    if( posisi < 1 || posisi > hitungList() ){
        cout << "Posisi diluar jangkauan" << endl;
    }
    else if( posisi == 1){
        cout << "Posisi bukan posisi tengah" << endl;
    }
    else{
        Node *baru, *bantu;
        baru = new Node();
        baru->data = data;
        // tranversing
            bantu = head;
            int nomor = 1;
        while( nomor < posisi - 1 ){
            bantu = bantu->next;
            nomor++;
        }
        baru->next = bantu->next;
        bantu->next = baru;
    }
}
//Hapus Depan
void hapusDepan() {
    Node *hapus;
    if (isEmpty() == false){
        if (head->next != NULL){
            hapus = head;
            head = head->next;
            delete hapus;
        }
        else{
            head = tail = NULL;
        }
    }
    else{
        cout << "List kosong!" << endl;
    }
}
//Hapus Belakang
void hapusBelakang() {
    Node *hapus;
    Node *bantu;
    if (isEmpty() == false){
        if (head != tail){
            hapus = tail;
            bantu = head;
            while (bantu->next != tail){
                bantu = bantu->next;
            }
            tail = bantu;
            tail->next = NULL;
        delete hapus;
        }
        else{
            head = tail = NULL;
        }
    }
    else{
        cout << "List kosong!" << endl;
    }
}
//Hapus Tengah
void hapusTengah(int posisi){
    Node *hapus, *bantu, *bantu2;
    if( posisi < 1 || posisi > hitungList() ){
        cout << "Posisi di luar jangkauan" << endl;
    }
    else if( posisi == 1){
        cout << "Posisi bukan posisi tengah" << endl;
    }
    else{
        int nomor = 1;
        bantu = head;
        while( nomor <= posisi ){
            if( nomor == posisi-1 ){
                bantu2 = bantu;
            }
            if( nomor == posisi ){
                hapus = bantu;
            }
            bantu = bantu->next;
            nomor++;
        }
        bantu2->next = bantu;
    delete hapus;
    }
}
//Ubah Depan
void ubahDepan(int data){
    if (isEmpty() == false){
        head->data = data;
    }
    else{
        cout << "List masih kosong!" << endl;
    }
}
//Ubah Tengah
void ubahTengah(int data, int posisi){
    Node *bantu;
    if (isEmpty() == false){
        if( posisi < 1 || posisi > hitungList() ){
            cout << "Posisi di luar jangkauan" << endl;
        }
        else if( posisi == 1){
            cout << "Posisi bukan posisi tengah" << endl;
        }
        else{
            bantu = head;
            int nomor = 1;
            while (nomor < posisi){
                bantu = bantu->next;nomor++;
            }
            bantu->data = data;
        }
    }
    else{
        cout << "List masih kosong!" << endl;
    }
}
//Ubah Belakang
void ubahBelakang(int data){
    if (isEmpty() == false){
        tail->data = data;
    }
    else{
        cout << "List masih kosong!" << endl;
    }
}
//Hapus List
void clearList(){
    Node *bantu, *hapus;
    bantu = head;
    while (bantu != NULL){
        hapus = bantu;
        bantu = bantu->next;
        delete hapus;
    }
    head = tail = NULL;
    cout << "List berhasil terhapus!" << endl;
}
//Tampilkan List
void tampil(){
    Node *bantu;
    bantu = head;
    if (isEmpty() == false){
        while (bantu != NULL){
            cout << bantu->data << ends;
            bantu = bantu->next;
        }
        cout << endl;
    }
    else{
        cout << "List masih kosong!" << endl;
    }
}
int main(){
    init();
    insertDepan(3);
    tampil();
    insertBelakang(5);
    tampil();
    insertDepan(2);
    tampil();
    insertDepan(1);
    tampil();
    hapusDepan();
    tampil();
    hapusBelakang();
    tampil();
    insertTengah(7,2);
    tampil();
    hapusTengah(2);
    tampil();
    ubahDepan(1);
    tampil();
    ubahBelakang(8);
    tampil();
    ubahTengah(11, 2);
    tampil();

    insertTengah(7,1);
    tampil();
    return 0;
}
```
Program diatas merupakan implementasi dari struktur data single linked list non-circular dan setiap node memiliki pointer yang menunjukkan ke node berikutnya dalam list. Program ini melakukan serangkaian operasi pengujian terhadap fungsi-fungsi tersebut, seperti menambahkan, menghapus, dan mengubah nilai dari node-node dalam list. dengan penjelasan sebagai berikut: 
- isEmpty() berguna untuk memeriksa apakah list kosong
- insertDepan(int nilai) untuk Menambahkan node baru dengan nilai tertentu di bagian depan list
- insertBelakang(int nilai) untuk menambahkan node baru dengan nilai tertentu di bagian belakang list
- hitungList() untuk Menghitung jumlah node dalam list
- insertTengah(int data, int posisi) untuk menambahkan node baru dengan nilai tertentu pada posisi tengah tertentu dalam list
- hapusDepan() untuk menghapus node pertama dari list
- hapusBelakang() untuk menghapus node terakhir dari list
- hapusTengah(int posisi) untuk menghapus node pada posisi tengah tertentu dari list
- ubahDepan(int data) untuk mengubah nilai data dari node pertama
- ubahTengah(int data, int posisi) untuk mengubah nilai data dari node pada posisi tengah tertentu
- ubahBelakang(int data) untuk mengubah nilai data dari node terakhir
- clearList() untuk menghapus semua node dari list.


### Guided 2 

```C++
// Guided 2

#include <iostream>
using namespace std;

class Node {
public:
    int data;
    Node* prev;
    Node* next;
};

class DoublyLinkedList {
public:
    Node* head;
    Node* tail;

    DoublyLinkedList() {
        head = NULL;
        tail = NULL;
    }

    void push(int data) {
        Node* newNode = new Node;
        newNode->data = data;
        newNode->prev = NULL;
        newNode->next = head;
        if (head != NULL) {
            head->prev = newNode;
        }
        else {
            tail = newNode;
        }
        head = newNode;
    }

    void pop() {
        if (head == NULL) {
            return;
        }
        Node* temp = head;
        head = head->next;
        if (head != NULL) {
            head->prev = NULL;
        }
        else {
            tail = NULL;
        }
        delete temp;
    }

    bool update(int oldData, int newData) {
        Node* current = head;
        while (current != NULL) {
            if (current->data == oldData) {
                current->data = newData;
                return true;
            }
            current = current->next;
        }
        return false;
    }

    void deleteAll() {
        Node* current = head;
        while (current != NULL) {
            Node* temp = current;
            current = current->next;
            delete temp;
        }
        head = NULL;
        tail = NULL;
    }

    void display() {
        Node* current = head;
        while (current != NULL) {
            cout << current->data << " ";
            current = current->next;
        }
        cout << endl;
    }
};

int main() {
    DoublyLinkedList list;
    while (true) {
        cout << "1. Add data" << endl;
        cout << "2. Delete data" << endl;
        cout << "3. Update data" << endl;
        cout << "4. Clear data" << endl;
        cout << "5. Display data" << endl;
        cout << "6. Exit" << endl;
        int choice;
        cout << "Enter your choice: ";
        cin >> choice;
        switch (choice) {
        case 1: {
            int data;
            cout << "Enter data to add: ";
            cin >> data;
            list.push(data);
            break;
        }
        case 2: {
            list.pop();
            break;
        }
        case 3: {
            int oldData, newData;
            cout << "Enter old data: ";
            cin >> oldData;
            cout << "Enter new data: ";
            cin >> newData;
            bool updated = list.update(oldData, newData);
            if (!updated) {
                cout << "Data not found" << endl;
            }
            break;
        }
        case 4: {
            list.deleteAll();
            break;
        }
        case 5: {
            list.display();
            break;
        }
        case 6: {
            return 0;
        }
        default: {
            cout << "Invalid choice" << endl;
            break;
        }
        }
    }
    return 0;
}


```
Program diatas merupakan implementasi dari Doubly Linked List. Doubly Linked List adalah struktur data linear di mana setiap elemen disimpan dalam sebuah node yang memiliki dua pointer, yaitu pointer ke node sebelumnya (prev) dan pointer ke node berikutnya (next). Pengguna dapat memilih operasi yang diinginkan dengan memasukkan angka yang sesuai dengan pilihan yang disediakan. Program akan terus berjalan dalam loop hingga pengguna memilih untuk keluar (pilihan 6). dengan penjelasan sebagai berikut:
- DoublyLinkedList() untuk menginisialisasi pointer head dan tail menjadi NULL saat objek dari kelas DoublyLinkedList dibuat.
- push(int data) untuk menambahkan node baru dengan data tertentu di depan linked list.
- pop() untuk menghapus node pertama dari linked list.
- update(int oldData, int newData) untuk mengupdate nilai data dari node yang memiliki nilai data tertentu.
- deleteAll() untuk menghapus semua node dari linked list.
- display() untuk menampilkan isi linked list dari depan ke belakang.


## Unguided 

### 1. Buatlah program menu Single Linked List Non-Circular untuk menyimpan Nama dan usia mahasiswa, dengan menggunakan inputan dari user. Lakukan operasi berikut:

```C++
#include <iostream>
using namespace std;

// Struktur node untuk menyimpan data mahasiswa
struct Node {
    string nama_030;
    int usia_030;
    Node* next;
};

class LinkedList {
private:
    Node* head;

public:
    // Konstruktor
    LinkedList() {
        head = NULL;
    }

    // Fungsi untuk menambahkan node di depan linked list
    void tambahDepan(string nama_030, int usia_030) {
        Node* newNode = new Node;
        newNode->nama_030 = nama_030;
        newNode->usia_030 = usia_030;
        newNode->next = head;
        head = newNode;
    }

    // Fungsi untuk menambahkan node di belakang linked list
    void tambahBelakang(string nama_030, int usia_030) {
        Node* newNode = new Node;
        newNode->nama_030 = nama_030;
        newNode->usia_030 = usia_030;
        newNode->next = NULL;

        if (head == NULL) {
            head = newNode;
            return;
        }

        Node* temp = head;
        while (temp->next != NULL) {
            temp = temp->next;
        }
        temp->next = newNode;
    }

    // Fungsi untuk menampilkan isi linked list
    void tampilkan() {
        Node* temp = head;
        while (temp != NULL) {
            cout << "Nama: " << temp->nama_030 << ", Usia: " << temp->usia_030 << endl;
            temp = temp->next;
        }
    }

    // Fungsi untuk menghapus node dari linked list
    void hapus(string nama_030) {
        Node* temp = head;
        Node* prev = NULL;

        // Cari node yang akan dihapus
        while (temp != NULL && temp->nama_030 != nama_030) {
            prev = temp;
            temp = temp->next;
        }

        // Jika node tidak ditemukan
        if (temp == NULL) {
            cout << "Data dengan nama " << nama_030 << " tidak ditemukan." << endl;
            return;
        }

        // Jika node yang akan dihapus adalah head
        if (prev == NULL) {
            head = temp->next;
            delete temp;
            cout << "Data dengan nama " << nama_030 << " berhasil dihapus." << endl;
            return;
        }

        // Jika node yang akan dihapus bukan head
        prev->next = temp->next;
        delete temp;
        cout << "Data dengan nama " << nama_030 << " berhasil dihapus." << endl;
    }
    
    // Fungsi untuk menyisipkan node di antara dua mahasiswa berdasarkan nama
    void sisipDiAntara(string nama_awal, string nama_akhir, string nama_030, int usia_030) {
        Node* newNode = new Node;
        newNode->nama_030 = nama_030;
        newNode->usia_030 = usia_030;

        Node* temp = head;
        Node* prev = NULL;

        // Cari node dengan nama_awal
        while (temp != NULL && temp->nama_030 != nama_awal) {
            prev = temp;
            temp = temp->next;
        }

        // Jika node tidak ditemukan
        if (temp == NULL) {
            cout << "Data dengan nama " << nama_awal << " tidak ditemukan." << endl;
            return;
        }

        // Jika node dengan nama_awal ditemukan
        prev = temp;
        temp = temp->next;

        // Cari node dengan nama_akhir
        while (temp != NULL && temp->nama_030 != nama_akhir) {
            prev = temp;
            temp = temp->next;
        }

        // Jika node tidak ditemukan
        if (temp == NULL) {
            cout << "Data dengan nama " << nama_akhir << " tidak ditemukan." << endl;
            return;
        }

        // Sisipkan newNode di antara node dengan nama_awal dan nama_akhir
        prev->next = newNode;
        newNode->next = temp;
    }
    
     // Fungsi untuk menambahkan node di awal linked list
    void tambahDiAwal(string nama_030, int usia_030) {
        Node* newNode = new Node;
        newNode->nama_030 = nama_030;
        newNode->usia_030 = usia_030;
        newNode->next = head;
        head = newNode;
    }
    
   // Fungsi untuk mengubah data mahasiswa berdasarkan nama
    void ubahData(string nama_lama, string nama_baru, int usia_baru) {
        Node* temp = head;

        // Cari node dengan nama_lama
        while (temp != NULL && temp->nama_030 != nama_lama) {
            temp = temp->next;
        }

        // Jika node tidak ditemukan
        if (temp == NULL) {
            cout << "Data dengan nama " << nama_lama << " tidak ditemukan." << endl;
            return;
        }

        // Ubah nama dan usia node menjadi nama_baru dan usia_baru
        temp->nama_030 = nama_baru;
        temp->usia_030 = usia_baru;
        cout << "Data mahasiswa berhasil diubah." << endl;
    }
};

int main() {
    LinkedList list;
    string nama_030;
    int usia_030;


	// Memasukkan data pertama dari pengguna
    cout << "Masukkan nama anda: ";
    getline(cin, nama_030);
    cout << "Masukkan usia anda: ";
    cin >> usia_030;
    cin.ignore(); // Membersihkan buffer

    // Menambahkan data pertama ke linked list
    list.tambahDepan(nama_030, usia_030);

    // Memasukkan 6 data lagi dari pengguna
    for (int i = 0; i < 7; ++i) {
        cout << "Masukkan nama mahasiswa ke-" << i+1 << ": ";
        getline(cin, nama_030);
        cout << "Masukkan usia mahasiswa ke-" << i+1 << ": ";
        cin >> usia_030;
        cin.ignore(); // Membersihkan buffer

        // Menambahkan data ke linked list
        list.tambahBelakang(nama_030, usia_030);
    }

    // Menampilkan isi linked list
    cout << "\nData Mahasiswa:\n";
    list.tampilkan();

    // Meminta pengguna untuk menghapus data
    cout << "\nMasukkan nama mahasiswa yang ingin dihapus: ";
    getline(cin, nama_030);

    // Menghapus data dari linked list
    list.hapus(nama_030);
    

    // Menampilkan isi linked list setelah penghapusan
    cout << "\nData Mahasiswa setelah penghapusan:\n";
    list.tampilkan();
    
    // Meminta pengguna untuk menyisipkan data di antara dua nama mahasiswa
    string nama_awal, nama_akhir;
    cout << "\nMasukkan nama mahasiswa awal: ";
    getline(cin, nama_awal);
    cout << "Masukkan nama mahasiswa akhir: ";
    getline(cin, nama_akhir);
    cout << "Masukkan nama mahasiswa yang ingin disisipkan: ";
    getline(cin, nama_030);
    cout << "Masukkan usia mahasiswa yang ingin disisipkan: ";
    cin >> usia_030;
    cin.ignore(); 

    // Menyisipkan data di antara dua nama mahasiswa
    list.sisipDiAntara(nama_awal, nama_akhir, nama_030, usia_030);
      // Menampilkan isi linked list setelah penyisipan
    cout << "\nData Mahasiswa setelah penyisipan:\n";
    list.tampilkan();
    
    
    // Memasukkan data pertama dari pengguna
    cout << "Masukkan nama mahasiswa: ";
    getline(cin, nama_030);
    cout << "Masukkan usia mahasiswa: ";
    cin >> usia_030;
    cin.ignore(); 

    // Menambahkan data pertama ke linked list
    list.tambahDiAwal(nama_030, usia_030);
      cout << "\nData Mahasiswa setelah ditambah:\n";
    list.tampilkan();
    
 	// Meminta pengguna untuk mengubah data mahasiswa berdasarkan nama
    string nama_lama;
    int usia_baru;
    cout << "\nMasukkan nama mahasiswa yang ingin diubah: ";
    getline(cin, nama_lama);
    cout << "Masukkan nama baru mahasiswa: ";
    getline(cin, nama_030);
    cout << "Masukkan usia baru mahasiswa: ";
    cin >> usia_baru;

    // Mengubah data mahasiswa berdasarkan nama
    list.ubahData(nama_lama, nama_030, usia_baru);

    // Menampilkan isi linked list setelah pengubahan
    cout << "\nSeluruh Data Mahasiswa:\n";
    list.tampilkan();
    
    

    cout << "" << endl;
    cout << "" << endl;
    cout << "By: Fito Satrio (2311110030)" << endl;
    return 0;
}
```
<p><b>Penjelasan:</b></p>
Program ini meminta input dari pengguna untuk menambahkan data mahasiswa ke linked list, menampilkan data mahasiswa, menghapus data mahasiswa, menyisipkan data di antara dua mahasiswa, menambahkan data di awal linked list, dan mengubah data mahasiswa. Setelah setiap operasi, program akan menampilkan data mahasiswa terbaru. dengan penjelasan sebagai berikut:

- tambahDepan(string nama, int usia) untuk menambahkan node baru di depan linked list dengan nama dan usia mahasiswa yang diberikan.
- tambahBelakang(string nama, int usia) untuk menambahkan node baru di belakang linked list dengan nama dan usia mahasiswa yang diberikan.
- tampilkan() untuk menampilkan isi linked list, yaitu nama dan usia semua mahasiswa.
- hapus(string nama) untuk menghapus node dengan nama mahasiswa yang diberikan dari linked list.
- sisipDiAntara(string nama_awal, string nama_akhir, string nama, int usia) untuk menyisipkan node baru di antara dua node yang sudah ada, yaitu di antara dua nama mahasiswa yang diberikan.
- tambahDiAwal(string nama, int usia) untuk menambahkan node baru di awal linked list dengan nama dan usia mahasiswa yang diberikan.
- ubahData(string nama_lama, string nama_baru, int usia_baru) untuk mengubah data mahasiswa (nama dan usia) berdasarkan nama lama yang diberikan.


#### Output:
a. Masukkan data sesuai urutan berikut. (Gunakan insert depan, belakang atau tengah). Data pertama yang dimasukkan adalah nama dan usia anda.

![Screenshot (1270)](https://github.com/fitosatrioo/Data-Structure-Practice/assets/109860844/f8a6d1e3-69fa-45e1-a9b2-d1bfa6010031)


b. Hapus data Akechi

![Screenshot (1271)](https://github.com/fitosatrioo/Data-Structure-Practice/assets/109860844/6632f711-5824-4f41-9119-168bd8ba66d5)


c. Tambahkan data berikut diantara John dan Jane : Futaba 18

![Screenshot (1272)](https://github.com/fitosatrioo/Data-Structure-Practice/assets/109860844/a9f7a7d6-5e2e-4a82-8bae-47f313f8381d)

d. Tambahkan data berikut diawal : Igor	20

![Screenshot (1273)](https://github.com/fitosatrioo/Data-Structure-Practice/assets/109860844/50007397-5bc4-4550-a669-46d8c07da199)

e. Ubah data Michael menjadi : Reyn 18

![Screenshot (1274)](https://github.com/fitosatrioo/Data-Structure-Practice/assets/109860844/8eeca3fb-256a-40cb-b8bc-2fc8e5b01dff)

f. Tampilkan seluruh data

![Screenshot (1274) 2](https://github.com/fitosatrioo/Data-Structure-Practice/assets/109860844/06fe2729-0d71-4a9f-b141-51e801d7df52)




### 2. Modifikasi Guided Double Linked List dilakukan dengan penambahan operasi untuk menambah data, menghapus, dan update di tengah / di urutan tertentu yang diminta. Selain itu, buatlah agar tampilannya menampilkan Nama produk dan harga.

```C++
#include <iostream>
using namespace std;

class Node {
public:
    string namaProduk_030; // Nama produk
    int harga_030; // Harga produk
    Node* prev_030;
    Node* next_030;
};

class DoublyLinkedList {
public:
    Node* head_030;
    Node* tail_030;

    DoublyLinkedList() {
        head_030 = NULL;
        tail_030 = NULL;
    }

    // Fungsi untuk menambahkan produk ke awal daftar
    void tambah(string namaProduk_030, int harga_030) {
        Node* newNode_030 = new Node;
        newNode_030->namaProduk_030 = namaProduk_030;
        newNode_030->harga_030 = harga_030;
        newNode_030->prev_030 = NULL;
        newNode_030->next_030 = head_030;
        if (head_030 != NULL) {
            head_030->prev_030 = newNode_030;
        } else {
            tail_030 = newNode_030;
        }
        head_030 = newNode_030;
    }

    // Fungsi untuk menambahkan produk setelah produk tertentu
    void tambahSetelah(string namaProduk_030, int harga_030, string namaProdukSebelumnya_030) {
        Node* current_030 = head_030;
        while (current_030 != NULL && current_030->namaProduk_030 != namaProdukSebelumnya_030) {
            current_030 = current_030->next_030;
        }
        if (current_030 != NULL) {
            Node* newNode_030 = new Node;
            newNode_030->namaProduk_030 = namaProduk_030;
            newNode_030->harga_030 = harga_030;
            newNode_030->prev_030 = current_030;
            newNode_030->next_030 = current_030->next_030;
            if (current_030->next_030 != NULL) {
                current_030->next_030->prev_030 = newNode_030;
            } else {
                tail_030 = newNode_030;
            }
            current_030->next_030 = newNode_030;
        } else {
            cout << "Produk sebelumnya tidak ditemukan" << endl;
        }
    }

    // Fungsi untuk menghapus produk dari awal daftar
    void hapus() {
        if (head_030 == NULL) {
            return;
        }
        Node* temp_030 = head_030;
        head_030 = head_030->next_030;
        if (head_030 != NULL) {
            head_030->prev_030 = NULL;
        } else {
            tail_030 = NULL;
        }
        delete temp_030;
    }

    // Fungsi untuk mengupdate nama produk dan harga berdasarkan nama produk lama
    bool update(string namaProdukLama_030, string namaProdukBaru_030, int hargaBaru_030) {
        Node* current_030 = head_030;
        while (current_030 != NULL) {
            if (current_030->namaProduk_030 == namaProdukLama_030) {
                current_030->namaProduk_030 = namaProdukBaru_030;
                current_030->harga_030 = hargaBaru_030;
                return true;
            }
            current_030 = current_030->next_030;
        }
        return false;
    }

    // Fungsi untuk menghapus produk berdasarkan nama produk
    void hapusBerdasarkanNama(string namaProduk_030) {
        Node* current_030 = head_030;
        while (current_030 != NULL && current_030->namaProduk_030 != namaProduk_030) {
            current_030 = current_030->next_030;
        }
        if (current_030 != NULL) {
            if (current_030->prev_030 != NULL) {
                current_030->prev_030->next_030 = current_030->next_030;
            } else {
                head_030 = current_030->next_030;
            }
            if (current_030->next_030 != NULL) {
                current_030->next_030->prev_030 = current_030->prev_030;
            } else {
                tail_030 = current_030->prev_030;
            }
            delete current_030;
        } else {
            cout << "Produk tidak ditemukan" << endl;
        }
    }

    // Fungsi untuk menghapus semua produk dari daftar
    void hapusSemua() {
        Node* current_030 = head_030;
        while (current_030 != NULL) {
            Node* temp_030 = current_030;
            current_030 = current_030->next_030;
            delete temp_030;
        }
        head_030 = NULL;
        tail_030 = NULL;
    }

    // Fungsi untuk menampilkan daftar produk beserta harga
    void tampilkan() {
        Node* current_030 = head_030;
        cout << "Nama Produk\tHarga" << endl;
        while (current_030 != NULL) {
            cout << current_030->namaProduk_030 << "\t" << current_030->harga_030 << endl;
            current_030 = current_030->next_030;
        }
        cout << endl;
    }
};

int main() {
    DoublyLinkedList list_030;

    // Menambahkan produk awal ke daftar
    list_030.tambah("Originote", 60000);
    list_030.tambah("Somethinc", 150000);
    list_030.tambah("Skintific", 100000);
    list_030.tambah("Wardah  ", 50000);
    list_030.tambah("Hanasui ", 30000);

    // Menampilkan produk awal
    cout << "Daftar Produk Awal:" << endl;
    list_030.tampilkan();

    // Menu operasi
    while (true) {
        cout << "Toko Skincare Purwokerto" << endl;
        cout << "1. Tambah Data" << endl;
        cout << "2. Hapus Data" << endl;
        cout << "3. Update Data" << endl;
        cout << "4. Tambah Data Urutan Tertentu" << endl;
        cout << "5. Hapus Data Urutan Tertentu" << endl;
        cout << "6. Hapus Seluruh Data" << endl;
        cout << "7. Tampilkan Data" << endl;
        cout << "8. Exit" << endl;

        int pilihan_030;
        cout << "Masukkan pilihan Anda: ";
        cin >> pilihan_030;

        switch (pilihan_030) {
            case 1: {
                string namaProduk_030;
                int harga_030;
                cout << "Masukkan nama produk: ";
                cin >> namaProduk_030;
                cout << "Masukkan harga: ";
                cin >> harga_030;
                list_030.tambah(namaProduk_030, harga_030);
                break;
            }
            case 2: {
                string namaProduk_030;
                cout << "Masukkan nama produk yang ingin dihapus: ";
                cin >> namaProduk_030;
                list_030.hapusBerdasarkanNama(namaProduk_030);
                break;
            }
            case 3: {
                string namaProdukLama_030, namaProdukBaru_030;
                int hargaBaru_030;
                cout << "Masukkan nama produk yang ingin diupdate: ";
                cin >> namaProdukLama_030;
                cout << "Masukkan nama produk baru: ";
                cin >> namaProdukBaru_030;
                cout << "Masukkan harga baru: ";
                cin >> hargaBaru_030;
                bool berhasil_030 = list_030.update(namaProdukLama_030, namaProdukBaru_030, hargaBaru_030);
                if (!berhasil_030) {
                    cout << "Data tidak ditemukan" << endl;
                }
                break;
            }
            case 4: {
                string namaProduk_030, namaProdukSebelumnya_030;
                int harga_030;
                cout << "Masukkan nama produk yang ingin ditambahkan: ";
                cin >> namaProduk_030;
                cout << "Masukkan harga: ";
                cin >> harga_030;
                cout << "Masukkan nama produk sebelumnya: ";
                cin >> namaProdukSebelumnya_030;
                list_030.tambahSetelah(namaProduk_030, harga_030, namaProdukSebelumnya_030);
                break;
            }
            case 5: {
                // Case 5: Hapus Data Urutan Tertentu
                break;
            }
            case 6: {
                list_030.hapusSemua();
                break;
            }
            case 7: {
                list_030.tampilkan();
                break;
            }
            case 8: {
                return 0;
            }
            default: {
                cout << "Pilihan tidak valid" << endl;
                break;
            }
        }
    }
    
    cout << "" << endl;
    cout << "" << endl;
    cout << "By: Fito Satrio (2311110030)" << endl;

    return 0;
}

```
<p><b>Penjelasan:</b></p>
Program ini meminta pengguna untuk melakukan operasi-operasi seperti menambah, menghapus, mengupdate, dan menampilkan data produk kemudian memberikan sebuah menu dengan pilihan operasi yang dapat dilakukan oleh pengguna. Pengguna dapat memilih operasi yang diinginkan dan program akan menjalankan operasi sesuai dengan pilihan pengguna. Setelah setiap operasi, program akan menampilkan hasil operasi tersebut. dengan penjelasan sebagai berikut:

- tambah(string namaProduk, int harga) untuk menambahkan produk baru ke awal daftar dengan nama produk dan harganya.
- tambahSetelah(string namaProduk, int harga, string namaProdukSebelumnya) untuk menambahkan produk baru setelah produk tertentu dengan nama produk dan harganya.
- hapus() unguk menghapus produk dari awal daftar.
- update(string namaProdukLama, string namaProdukBaru, int hargaBaru) untuk mengupdate nama dan harga produk berdasarkan nama produk lama.
- hapusBerdasarkanNama(string namaProduk) untuk menghapus produk dari daftar berdasarkan nama produk.
- hapusSemua() untuk menghapus semua produk dari daftar.
tampilkan(): Menampilkan semua produk beserta harganya.

#### Output:

![Screenshot (1281)](https://github.com/fitosatrioo/Data-Structure-Practice/assets/109860844/3373d016-ec8d-4849-ad65-942be65643c6)

1. Tambahkan produk Azarine dengan harga 65000 diantara Somethinc dan Skintific

![Screenshot (1277)](https://github.com/fitosatrioo/Data-Structure-Practice/assets/109860844/ead6d660-95e1-46ef-bc36-295410d67c38)

2. Hapus produk wardah

![Screenshot (1279)](https://github.com/fitosatrioo/Data-Structure-Practice/assets/109860844/c8523490-f6d4-4e93-beb1-848a0bfa737b)


3. Update produk Hanasui menjadi Cleora dengan harga 55.000

![Screenshot (1280)](https://github.com/fitosatrioo/Data-Structure-Practice/assets/109860844/95f5da9d-6b1b-4b50-8d86-81ce4c26e1ed)

4. Tampilkan menu seperti dibawah ini

![Screenshot (1280) 2](https://github.com/fitosatrioo/Data-Structure-Practice/assets/109860844/1b88eaf2-1026-4112-975a-9d88e5972c6d)

5. Tampilan Akhir

![Screenshot (1280) 3](https://github.com/fitosatrioo/Data-Structure-Practice/assets/109860844/2a2175ba-570f-4d16-82a5-1e0707bdfe5c)





## Kesimpulan
- ### Hasil Praktikum
Praktikum kali ini membahas tentang single linked list yang merupakan suatu bentuk struktur data yang berisi kumpulan data yang disebut sebagai node yang tersusun secara sekuensial kemudian Double Linked List yang merupakan struktur data Linked List yang mirip dengan Single Linked List, namun dengan tambahan satu pointer tambahan pada setiap simpul yaitu pointer prev yang menunjuk ke simpul sebelumnya

- ### Pelajaran yang didapat
Single linked list

Kelebihan:
Implementasi sederhana dan lebih ringan karena setiap node hanya perlu menyimpan satu pointer.
Cocok untuk aplikasi di mana navigasi maju cukup, seperti antrian (queue) dan stack.

Kekurangan:
Tidak mendukung navigasi mundur secara langsung, yang dapat mengakibatkan kinerja yang kurang efisien dalam beberapa operasi.
Operasi seperti menghapus elemen terakhir dalam linked list memerlukan waktu O(n), di mana n adalah jumlah elemen dalam linked list.

Double linked list

kelebihan:
Mendukung navigasi maju dan mundur, sehingga lebih efisien untuk operasi-operasi yang memerlukan penelusuran maju dan mundur.
Operasi penghapusan elemen dari akhir linked list menjadi lebih efisien dengan memiliki pointer ke node sebelumnya.

Kekurangan:
Memerlukan lebih banyak ruang memori karena setiap node harus menyimpan dua pointer tambahan.
Implementasi yang lebih kompleks dibandingkan dengan single linked list.

## Referensi
[1] Hermawan Wijaya, Wibisono Sukmo Wardhono, Issa Arwani, "Implementasi Linked List pada Interaksi Antar Marker Augmented Reality untuk Operand dan Operator Aritmatika", Jurnal Pengembangan Teknologi Informasi dan Ilmu Komputer, 2018.

[2] Felix Andreas Sutanto, "Panduan Praktis Pemrograman Visual Berbasis C++", Yogyakarta; 2021.

[3] M.A. Eljinini, "Practical Data Structures with C++, C#, and Java", Lulu.com, 2020.



