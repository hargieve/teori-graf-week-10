# teori-graf-week-10
Hungarian Algorithm and Welsh-Powell Algorithm

Hungarian Algorithm
Matriks 
9, 2, 7
6, 4, 3
5, 8, 1

langkah 1 (baris dikurangi nilai minimum)
baris 1, min = 2, [9-2, 2-2, 7-2] = [7, 0, 5]
baris 2, min = 3, [6-3, 4-3, 3-3] = [3, 1, 0]
baris 3, min = 1, [5-1, 8-1, 1-1] = [4, 7, 0]

matriks sementara 
7, 0, 5
3, 1, 0 
4, 7, 0

langkah 2 (kolom dikurangi nilai minimum)
kolom 1, min = 3, [7-3, 3-3, 4-3] = [4, 0, 1]
kolom 2, min = 0, [0-0, 1-0, 7-0] = [0, 1, 7]
kolom 3, min = 0, [5-0, 0-0, 0-0] = [5, 0, 0]

matriks sementara   |   matriks asli 

4, 0, 5             |   9, 2, 7
0, 1, 0             |   6, 4, 3
1, 7, 0             |   5, 8, 1

langkah 3 (cek di matriks sementara nilai yang 0)
baris 1, nol di kolom 2
baris 2, nol di kolom 1, 3
baris 3, nol di kolom 3

langkah 4 konversi nilai nol ke matriks asli
baris 1, kolom 2 = 2
baris 2, kolom 1 = 6
baris 3, kolom 3 = 1

langkah 5 tambahkan total nilai 
2 + 6 + 1 = 9 


Welsh-Powell Algorithm
Program ini menerapkan Algoritma Welsh–Powell untuk melakukan pewarnaan graf (graph coloring).
Tujuannya adalah memberikan warna berbeda untuk simpul (vertex) yang bersebelahan, sehingga tidak ada dua simpul yang dihubungkan oleh sisi (edge) memiliki warna yang sama.

Input berupa graf tak berarah (undirected graph) yang direpresentasikan dalam bentuk dictionary (kamus Python).

Format:
graph = {
    'A': ['B', 'C', 'D'],
    'B': ['A', 'C', 'E'],
    'C': ['A', 'B', 'D', 'E'],
    'D': ['A', 'C', 'E'],
    'E': ['B', 'C', 'D']
}

Penjelasan:

Setiap key adalah nama simpul (vertex).

Setiap value adalah daftar simpul tetangga (adjacent vertices) yang terhubung langsung dengannya.

Contoh:

'A': ['B', 'C', 'D'] artinya simpul A terhubung ke B, C, dan D.

Graf dianggap tak berarah, jadi jika A terhubung ke B, maka B juga harus terhubung ke A.

Output berupa hasil pewarnaan setiap simpul dalam bentuk teks di terminal.

Format:
Simpul <nama_simpul> ---> Warna <nomor_warna>

Contoh Output:
Hasil Pewarnaan Graf (Welsh–Powell):
Simpul A ---> Warna 1
Simpul C ---> Warna 1
Simpul D ---> Warna 2
Simpul B ---> Warna 2
Simpul E ---> Warna 3

Penjelasan:

Simpul A dan C mendapat warna 1 karena mereka tidak saling terhubung langsung.

Simpul D dan B mendapat warna 2 karena mereka tidak bertetangga langsung dengan simpul yang punya warna sama.

Simpul E mendapat warna 3 karena terhubung dengan simpul yang sudah memakai warna 1 dan 2.