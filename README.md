1. Inti Dari File Yang Kamu Upload
File itu menjelaskan 3 hal penting:
1️⃣ Apa itu Array?
Bayangin array itu kayak:

- Kotak berjejer dengan jumlah tetap.
Jumlah kotaknya tidak bisa ditambah
Bisa isi angka di dalamnya
Bisa ambil isi berdasarkan nomor urut
Contoh:
Salin kode

Index:   0   1   2
Array:  [5] [8] [3]
Kalau mau ambil angka 8 → ambil index 1.
2️⃣ Bedanya Array dan List di Python
Array
List
Ukuran tetap
Bisa bertambah
Lebih hemat memori
Lebih fleksibel
 Jadi:
Kalau data sudah pasti jumlahnya → pakai array
Kalau datanya sering berubah → pakai list
3️⃣ Game of Life Itu Apa?
Game of Life dibuat oleh
John H. Conway
Game ini unik karena:
Tidak ada pemain
Hanya aturan
Sel hidup dan mati berubah otomatis
Game ini termasuk konsep: Cellular automaton
 2. Aturan Game of Life (Versi Paling Mudah)
Bayangkan ada kotak-kotak seperti papan catur.
Setiap kotak bisa:
1 = hidup
0 = mati
Aturannya:
Sel hidup + 2 atau 3 tetangga hidup → tetap hidup
Sel hidup + kurang dari 2 → mati (kesepian)
Sel hidup + lebih dari 3 → mati (terlalu ramai)
Sel mati + tepat 3 tetangga hidup → jadi hidup
 3. Implementasi Paling Sederhana
Kita buat versi mudah dipahami.
 array_adt.py
Python
Salin kode
class Array:
    def __init__(self, size):
        self.data = [0] * size  # isi awal 0
        self.size = size

    def __getitem__(self, index):
        return self.data[index]

    def __setitem__(self, index, value):
        self.data[index] = value
    game_of_life.py
Python
Salin kode
from array_adt import Array

ROWS = 3
COLS = 3

# Buat papan kosong
def buat_papan():
    papan = Array(ROWS)
    for i in range(ROWS):
        papan[i] = Array(COLS)
    return papan

# Hitung tetangga hidup
def hitung_tetangga(papan, r, c):
    total = 0
    for i in range(-1, 2):
        for j in range(-1, 2):
            if i == 0 and j == 0:
                continue
            rr = r + i
            cc = c + j
            if 0 <= rr < ROWS and 0 <= cc < COLS:
                total += papan[rr][cc]
    return total

# Buat generasi baru
def generasi_baru(papan):
    baru = buat_papan()
    for r in range(ROWS):
        for c in range(COLS):
            tetangga = hitung_tetangga(papan, r, c)

            if papan[r][c] == 1 and tetangga in (2,3):
                baru[r][c] = 1
            elif papan[r][c] == 0 and tetangga == 3:
                baru[r][c] = 1
            else:
                baru[r][c] = 0
    return baru

# Tampilkan papan
def tampilkan(papan):
    for r in range(ROWS):
        for c in range(COLS):
            print("■" if papan[r][c] == 1 else ".", end=" ")
        print()
    print()

# Program utama
papan = buat_papan()

# Pola awal
papan[0][1] = 1
papan[1][1] = 1
papan[2][1] = 1

print("Awal:")
tampilkan(papan)

papan = generasi_baru(papan)

print("Setelah 1 Generasi:")
tampilkan(papan)

 4. Penjelasan Kode Biar Benar-Benar Paham
Kita buat papan 3x3
Kita isi beberapa sel jadi hidup (1)
Kita hitung tetangga setiap sel
Kita buat generasi baru sesuai aturan
Kita tampilkan hasilnya
Itu saja. Tidak ada rumus aneh.

 5. Cara Upload ke GitHub (Paling Mudah)
Cara Tanpa Ribet (Tanpa Terminal)
Masuk GitHub
Klik New Repository
Nama: game-of-life
Klik Create
Klik Add File
Upload:
array_adt.py
game_of_life.py
Klik Commit
Selesai 
