## Anggota Kelompok

- Mohammad Fadhil Rasyidin Parinduri // 5025201131
- Marcelino Salim // 5025201026
- Aisyah Nurhalimah // 5025201081 

### Soal Shift

- [link](https://docs.google.com/document/d/1asm7lgnTJxr17DxsE_McdUimPsRjesi6ZrHRpmXPZ4s/edit?usp=sharing)

Kendala:

1. banyak tugas sedikit waktu (butuh introspeksi diri untuk memperbaiki manajemen waktu)
2. hehe

# Laporan Resmi
## Daftar Isi
- [Laporan Resmi](#laporan-resmi)
  - [Daftar Isi](#daftar-isi)
  - [Topologi](#topologi)
  - [Config](#config)
  - [Sebelum Memulai](#sebelum-memulai)
- [Soal 1](#soal-1)
- [Soal 2](#soal-2)
    - [Test](#test)
- [Soal 3](#soal-3)
    - [Script](#script)
    - [Test](#test-1)
- [Soal 4](#soal-4)
    - [Script](#script-1)
    - [Test](#test-2)
- [Soal 5](#soal-5)
    - [Script](#script-2)
    - [Test](#test-3)
- [Soal 6](#soal-6)
    - [Script](#script-3)
    - [Test](#test-4)
- [Soal 7](#soal-7)
    - [Script](#script-4)
    - [Test](#test-5)


## Topologi
<img width="620" alt="image" src="https://user-images.githubusercontent.com/81240334/201657306-35384e24-8d6d-4d6a-84c4-e85e602bcf64.jpeg">

## Config

- **Ostania**
    ```
    auto eth0
    iface eth0 inet dhcp

    auto eth1
    iface eth1 inet static
        address 10.19.1.1
        netmask 255.255.255.0

    auto eth2
    iface eth2 inet static
        address 10.19.2.1
        netmask 255.255.255.0

    auto eth3
    iface eth3 inet static
        address 10.19.3.1
        netmask 255.255.255.0
    ```

- **SSS & Garden**
    ```
    auto eth0
    iface eth0 inet dhcp
    ```

- **Wise**
    ```
    auto eth0
    iface eth0 inet static
        address 10.19.2.2
        netmask 255.255.255.0
        gateway 10.19.2.1
    ```

- **Berlint**
    ```
    auto eth0
    iface eth0 inet static
        address 10.19.2.3
        netmask 255.255.255.0
        gateway 10.19.2.1
    ```

- **Westalis**
    ```
    auto eth0
    iface eth0 inet static
        address 10.19.2.4
        netmask 255.255.255.0
        gateway 10.19.2.1
    ```

- **Eden**
    ```
    auto eth0
    iface eth0 inet static
        address 10.19.3.2
        netmask 255.255.255.0
        gateway 10.19.3.1
    ```

- **NewstonCastle**
    ```
    auto eth0
    iface eth0 inet static
        address 10.19.3.3
        netmask 255.255.255.0
        gateway 10.19.3.1
    ```

- **KemonoPark**
    ```
    auto eth0
    iface eth0 inet static
        address 10.19.3.4
        netmask 255.255.255.0
        gateway 10.19.3.1
    ```
