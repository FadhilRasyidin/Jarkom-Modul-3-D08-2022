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
- [Soal 1](#soal-1)
- [Soal 2](#soal-2)
- [Soal 3](#soal-3)
    - [Script](#script)
- [Soal 4](#soal-4)
    - [Script](#script-1)
- [Soal 5](#soal-5)
    - [Script](#script-2)
- [Soal 6](#soal-6)
    - [Script](#script-3)
- [Soal 7](#soal-7)
    - [Script](#script-4)


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
    
    setiap node, kita inisiasi pada `.bashrc` menggunakan `nano`. Setelah berhasil, akan dilakukan pengecekan internet untuk semua node dengan melakukan `ping google.com -c 3`

# Soal 1
> Loid bersama Franky berencana membuat peta tersebut dengan kriteria WISE sebagai DNS Server, Westalis sebagai DHCP Server, Berlint sebagai Proxy Server 

**WISE sebagai DNS Server** 

Untuk menjalankannya bisa langsung dengan melakukan command `bash wise-dns.sh`

    ```
    apt-get update
    apt-get install bind9 -y
    service bind9 start
    service bind9 status
    ```
**Westalis sebagai DHCP Server** 

Untuk menjalankannya bisa langsung dengan melakukan command `bash westalis-dhcp.sh`

    ```
    apt-get update
    apt-get install isc-dhcp-server -y
    ```
**Berlint sebagai Proxy Server** 

Untuk menjalankannya bisa langsung dengan melakukan command `bash berlint-proxy.sh`

    ```
    apt-get update
    apt-get install squid -y
    service squid restart
    service squid status
    ```


# Soal 2
> Ostania sebagai DHCP Relay

**Ostania sebagai DHCP Relay** 

    ```
    apt-get update
    apt-get install isc-dhcp-relay -y
    ```


# Soal 3
> Ada beberapa kriteria yang ingin dibuat oleh Loid dan Franky, yaitu:
> 1.	Semua client yang ada HARUS menggunakan konfigurasi IP dari DHCP Server.
> 2.	Client yang melalui Switch1 mendapatkan range IP dari [prefix IP].1.50 - [prefix IP].1.88 dan [prefix IP].1.120 - [prefix IP].1.155 
 

### Script

> Script dibawah ini terdapat pada **root node Westalis**, mengganti range IP Switch1 sesuai pada soal, yaitu prefix IP = 10.19, untuk menjalankannya bisa langsung dengan melakukan command `bash nomor3.sh`

- **Westalis**
    
    ```
    echo "
    subnet 10.19.2.0 netmask 255.255.255.0 {
    }
    subnet 10.19.1.0 netmask 255.255.255.0 {
        range 10.19.1.50 10.19.1.88;
        range 10.19.1.120 10.19.1.155;
        option routers 10.19.1.1;
        option broadcast-address 10.19.1.255;
        option domain-name-servers 10.19.2.2;
        default-lease-time 360;
        max-lease-time 7200;
    }

    " > /etc/dhcp/dhcpd.conf
    
    ```

# Soal 4
> Client yang melalui Switch3 mendapatkan range IP dari [prefix IP].3.10 - [prefix IP].3.30 dan [prefix IP].3.60 - [prefix IP].3.85

### Script

> Script dibawah ini terdapat pada **root node Westalis**, mengganti range IP Switch3 sesuai pada soal, yaitu prefix IP = 10.19, untuk menjalankannya bisa langsung dengan melakukan command `bash nomor4.sh`

- **Westalis**
    
    ```
    echo "
    subnet 10.19.3.0 netmask 255.255.255.0 {
    }
    subnet 10.19.1.0 netmask 255.255.255.0 {
        range 10.19.3.10 10.19.3.30;
        range 10.19.3.60 10.19.3.85;
        option routers 10.19.3.1;
        option broadcast-address 10.19.3.255;
        option domain-name-servers 10.19.2.2;
        default-lease-time 720;
        max-lease-time 7200;
    }" >> /etc/dhcp/dhcpd.conf
    
    ```

# Soal 5
> Client mendapatkan DNS dari WISE dan client dapat terhubung dengan internet melalui DNS tersebut

### Script

> Script dibawah ini terdapat pada **root node WISE**, untuk menjalankannya bisa langsung dengan melakukan command `bash nomor5.sh`

- **WISE**
    
    ```
    echo -e '
    options {
        directory \"/var/cache/bind\";

        forwarders {
            8.8.8.8;
            8.8.8.4;
        };

        // dnssec-validation auto;
    allow-query{ any; };
    auth-nxdomain no; # confirm to RFC1035
    listen-on-v6 { any; };
    }
    };" > /etc/bind/named.conf.options

    ```

Setelah selesai maka kita harus merestart bind9 dengan command `service bind9 restart` atau jalankan command `bash wise-5.sh`

# Soal 6
>  Lama waktu DHCP server meminjamkan alamat IP kepada Client yang melalui Switch1 selama 5 menit sedangkan pada client yang melalui Switch3 selama 10 menit. Dengan waktu maksimal yang dialokasikan untuk peminjaman alamat IP selama 115 menit.

### Script

> Script dibawah ini dapat dijalankannya dengan melakukan command `nano /etc/dhcp/dhcpd,conf` dengan mengganti `default-lease-time` pada switch1 selama 5 menit = 300s, dan pada switch2 selama 10 menit = 600s. Dan untuk `max-lease-time` diganti menjadi 115 menit = 6900s

- **Westalis**
    
    ```
    subnet 192.202.1.0 netmask 255.255.255.0 {
        range 192.202.1.50 192.202.1.88;
        range 192.202.1.120 192.202.1.155;
        option routers 192.202.1.1;
        option broadcast-address 192.202.1.255;
        option domain-name-servers 192.202.2.2;
        default-lease-time 300;
        max-lease-time 6900;
    }
    subnet 192.202.3.0 netmask 255.255.255.0 {
        range 192.202.3.10 192.202.3.30;
        range 192.202.3.60 192.202.3.85;
        option routers 192.202.3.1;
        option broadcast-address 192.202.3.255;
        option domain-name-servers 192.202.2.2;
        default-lease-time 600;
        max-lease-time 6900;
    }
    ```

Setelah selesai maka kita harus merestart dengan menjalankan command bash `westalis-3-6.sh`.

# Soal 7
> Loid dan Franky berencana menjadikan **Eden** sebagai server untuk pertukaran informasi dengan **alamat IP yang tetap** dengan IP [prefix IP].3.13

### Script

> Script dibawah ini terdapat pada **root node Westalis**, untuk menjalankannya bisa langsung dengan melakukan command `bash nomor7.sh`

- **Westalis**
    
    ```
    echo "
    host Eden{
        hardware ethernet 92:b2:9e:53:d4:b0;
        fixed-address 10.19.3.13;
    }" >> etc/dhcp/dhcpd.conf
    ```

> Script dibawah ini terdapat pada **root node Eden**, untuk menjalankannya bisa langsung dengan melakukan command `bash nomor7.sh`

- **Eden**

    ```
    echo "
    auto eth0
    iface eth0 inet dhcp
    hardware ethernet 92:b2:9e:53:d4:b0 " > etc/network/interfaces
    ```

