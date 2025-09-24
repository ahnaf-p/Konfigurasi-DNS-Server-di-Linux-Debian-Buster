# Konfigurasi-DNS-Server-di-Linux-Debian-Buster
24 September 2025  
  
# Pembahasan
  DNS (Domain Name System) bisa dibilang sebagai “buku telepon” internet. Dengan adanya DNS, kita tidak perlu repot mengingat alamat IP yang panjang untuk mengakses sebuah server, cukup dengan nama domain saja. Di Linux, khususnya Debian Buster (Debian 10), layanan DNS biasanya dijalankan menggunakan BIND9.  
  
# Konfigurasi
  Di sini saya mengunakan Debian 10 di Virtual Box. Untuk Networknya di adapter 1 mengunakan NAT, untuk mengakses internet dan mendownload repo yang dibutuhkan. Sebelum mulai kita bisa masuk ke root dan upgrade reponya dulu mengunakan  
  
    apt update
  1. Pertama kita bisa menginstall **bind9, bind9utils dan dnsutils** lalu gunakan **-y** untuk otomatis menjawab "yes" tanpa konfirmasi lagi.  

    apt install bind9 bind9utils dnsutils -y
  ![](IMAGES/)  
  2. Lalu nonaktifkan NAT agar Debian tidak mengambil dns dari Internet. Aktifkan jaringan Host-Only Adapter dengan memasang IP Static dan jangan lupa subnetnya. Di /etc/network/**interface**  
  ![](IMAGES/)  
  3. Jangan lupa untuk restart service networkingnya agar berubah, lalu cek dengan **ip a** untuk melihat apakah sudah sesuai.  
  ![](IMAGES/)  
  4. Selanjutnya kita bisa pergi ke **/etc/bind** dengan **cd /etc/bind**, kita bisa lihat disini ada beberapa file.  
  ![](IMAGES/)  
  5. Copy/duplikat file db.local dan db.127 menjadi file forward dan reverse untuk kita gunakan.  

    cp db.local db.penguin
    cp db.127 db.101
  6. 
