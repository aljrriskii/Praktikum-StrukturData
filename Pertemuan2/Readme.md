# **Implementasi Linked List Menggunakan Python**

Dokumen ini menjelaskan cara kerja serta implementasi struktur data **Linked List** secara sederhana menggunakan Python.  
Linked List tersusun dari beberapa node yang saling terhubung, di mana setiap node memuat data dan referensi ke node berikutnya.

---

## **1. Struktur Node**

Setiap node terdiri dari dua bagian utama:
- `data`: nilai yang disimpan
- `next`: penunjuk ke node berikutnya

```python
class Node:
    def __init__(self, data=None, pointer=None):
        self.data = data
        self.next = pointer
```

---

## **2. Kelas LinkedList**

`LinkedList` menyimpan pointer ke elemen pertama (`head`) dan menyediakan berbagai operasi untuk menambah atau menghapus node.

```python
class LinkedList:
    def __init__(self):
        self.head = None
```

---

## **2.1 Menambahkan Elemen di Awal (insert_at_first)**

```python
def insert_at_first(self, data):
    node = Node(data, self.head)
    self.head = node
```

---

## **2.2 Menambahkan Elemen di Akhir (insert_at_last)**

```python
def insert_at_last(self, data):
    if self.head is None:
        self.head = Node(data)
    else:
        node_sekarang = self.head
        while node_sekarang.next:
            node_sekarang = node_sekarang.next

        node = Node(data)
        node_sekarang.next = node
```

---

## **2.3 Menyisipkan Elemen pada Index Tertentu (insert_at)**

```python
def insert_at(self, index, data):
    if index < 0 or index > self.length() - 1:
        print("indeks tidak valid")
    elif index == 0:
        self.insert_at_first(data)
    else:
        urutan = 0
        node_sekarang = self.head

        while urutan < index - 1:
            urutan += 1
            node_sekarang = node_sekarang.next

        node = Node(data, node_sekarang.next)
        node_sekarang.next = node
```

---

## **2.4 Menghapus Elemen Pertama (remove_first)**

```python
def remove_first(self):
    if self.head is None:
        print("tidak ada data yang bisa dihapus")
    else:
        self.head = self.head.next
```

---

## **2.5 Menghapus Elemen Terakhir (remove_last)**

```python
def remove_last(self):
    if self.head is None:
        print("tidak ada data yang bisa dihapus")
    elif self.head.next is None:
        self.head = None
    else:
        node_sebelumnya = None
        node_sekarang = self.head

        while node_sekarang.next:
            node_sebelumnya = node_sekarang
            node_sekarang = node_sekarang.next

        node_sebelumnya.next = None
```

---

## **2.6 Menghapus Elemen Berdasarkan Index (remove_at)**

```python
def remove_at(self, index):
    if index < 0 or index >= self.length():
        print("index invalid")
    elif index == 0:
        self.remove_first()
    else:
        urutan = 0
        node_sekarang = self.head

        while urutan < index - 1:
            node_sekarang = node_sekarang.next
            urutan += 1

        node_sekarang.next = node_sekarang.next.next
```

---

## **2.7 Menampilkan Isi Linked List (print)**

```python
def print(self):
    if self.head is None:
        print("data kosong")
    else:
        text_print = ''
        node_sekarang = self.head

        while node_sekarang:
            text_print += str(node_sekarang.data) + " → "
            node_sekarang = node_sekarang.next

        print(text_print)
```

---

## **2.8 Menghitung Jumlah Node (length)**

```python
def length(self):
    urutan = 0
    data_sekarang = self.head

    while data_sekarang:
        data_sekarang = data_sekarang.next
        urutan += 1

    return urutan
```

---

## **3. Contoh Penggunaan Semua Operasi**

```python
ll = LinkedList()

# insert
ll.insert_at_first("jeruk")
ll.insert_at_first("mangga")
ll.insert_at_first("manggis")
ll.insert_at_last("apel")
ll.insert_at(2, "anggur")

# remove
ll.remove_first()
ll.remove_last()
ll.remove_at(1)
ll.remove_at(1)

# print
ll.print()
print(ll.length())
```

---

