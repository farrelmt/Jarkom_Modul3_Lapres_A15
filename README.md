**Kelompok A15 :**

Farrel Muhammad Taqi     05111840000071

Muhammad Iqbal Humam     05111840000103

**DHCP**

1. Membuat topologi jaringan sesuai soal

    a. Atur topologi jaringan pada putty sesuai soal seperti dibawah
    
    ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/1.1.PNG)
    
    b. Jalankan topologinya, jika bisa maka topologi telah berhasil

2. Mengatur topologi uml sesuai soal 

    a. Install DHCP Relay di SURABAYA dengan command apt-get install isc-dhcp-relay
    
    b. Pada /etc/sysctl.conf tambahkan   net.ipv4.ip_forward=1 dan net.ipv4.conf.all.accept_source_route = 1
    
    ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/2.1.PNG)
    
    c. Pada isc-dhcp-relay tambahkan interfaces seperti dibawah
    
    ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/2.2.PNG)
    
    d.	Install DHPC Server di TUBAN dengan command apt-get install isc-dhcp-server
    
    e.	Pada dhcpd.conf tambahkan subnet dibawah untuk server
    
    f.	Install Squid di MOJOKERTO sebagai Proxy 

    g.	Untuk semua client buat seperti dibawah
    
    ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/2.3.PNG)

3. Untuk mengatur client subnet 1 hanya bisa mendapatkan IP 192.168.0.10 sampai 192.168.0.100 dan 192.168.0.110 sampai 192.168.0.200 dapat diatur di dhcpd.conf dengan mengatur range seperti gambar dibawah 

    ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/3.1.PNG)
    
4. Untuk mengatur client subnet 3 hanya bisa mendapatkan range IP 192.168.1.50 sampai 192.168.170 dapat diatur di dhcpd.conf dengan mengatur range seperti gambar dibawah 

    ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/4.1.PNG)

5. Agar client mendapatkan DNS Malang dan DNS 202.46.129,2 dari DHCP maka perlu ditambahkan option domain-name-servers di dhcpd.conf seperti gambar dibawah

    ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/5.1.PNG)
    
6. Agar client pada subnet 1 hanya dapat meminjam alamat IP selama 5 menit dan client pada subnet 3 selama 10 menit maka pada dhcpd.conf pada masing-masing subnetnya dapat diatur default-lease-timenya seperti gambar dibawah 

    ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/5.1.PNG)


**PROXY**

7. Pertama, akses ke proxy hanya bisa dilakukan oleh Anri sendiri sebagai user TA. (7) User autentikasi milik Anri memiliki format: User : userta_yyy Password : inipassw0rdta_yyy

    a. Instal squid terlebih dahulu di mojokerto
    
    ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/7.1.png)
    
    b. Setting Proxy pada Setting Windows / pada setting browser (firefox)
    
    ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/7.2.png)
    
    c. Buat user login
    
    ```apt-get install apache2-utils```

    ```htpasswd -c /etc/squid/passwd userta_a15```

    ```Passwordnya : inipassw0rdta_a15```
    
    d. Edit konfigurasi config
    
    ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/7.3.png)
    
    e. Service squid restart
    
    f. Cek di firefox
    
    ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/7.4.png)
    
8. Anri sudah menjadwal pengerjaan TA-nya (8) setiap hari Selasa-Rabu pukul 13.00-18.00. Bu Meguri membatasi penggunaan internet Anri hanya pada jadwal yang telah ditentukan itu saja. Maka diluar jam tersebut, Anri tidak dapat mengakses jaringan internet dengan proxy tersebut.

    a. Buat file nano /etc/squid/acl.conf
    
    b. Dan tambahkan acl AVAILABLE_WORKING time TW 13:00-18:00
    
    ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/8.1.png)
    
    c. Ubah konfigurasi di squid.conf
    
    ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/8.2.png)
    
    d. Hasil
    
     ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/8.3.png)
     
9. Jadwal bimbingan dengan Bu Meguri adalah (9) setiap hari Selasa-Kamis pukul 21.00 - 09.00 keesokan harinya (sampai Jumat jam 09.00)

    a. Tambahkan ini pada acl.conf

    ```acl BIMBINGAN_NIGHT_TIME time TWH 21:00-23:59```

    ```acl BIMBINGAN_MORNING_TIME time WHF 00:00-09:00```
    
    ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/9.1.png)
    
    b. Ubah settingan pada squid.conf
    
    ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/9.2.png)
    
    c. hasil
    
    ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/9.3.png)
    
10.Agar Anri bisa fokus mengerjakan TA, (10) setiap dia mengakses google.com, maka akan di redirect menuju monta.if.its.ac.id agar Anri selalu ingat untuk mengerjakan TA🙂.

   a. pada squid.conf, tambahkan script yang di-block berikut :
    
   ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/10.1.png)
    
   b. pada acl.conf, tambahkan script yang di-block berikut :
    
   ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/10.2.png)

11. Untuk menandakan bahwa Proxy Server ini adalah Proxy yang dibuat oleh Anri, (11) Bu Meguri meminta Anri untuk mengubah error page default squid menjadi seperti berikut:
Note : File error page bisa diunduh dengan cara wget 10.151.36.202/ERR_ACCESS_DENIED
   Tidak perlu di extract, cukup cp -r
   
   a. Lakukan wget untuk download file yang telah disediakan oleh soal pada folder squid3
   
   b. buat directory baru di folder squid3 dengan nama terserah dengan script ```mkdir```, kami memberi nama pages
   
   c. lakukan ```Cp -r``` file yang di-downlaod tadi ke pages
   
   e. Pada squid.conf tambahkan script berikut :
   
   ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/11.1.png)
   
   f. hasil :
   
   ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/11.2.png)

   
12.Karena Bu Meguri dan Anri adalah tipe orang pelupa, maka untuk memudahkan mereka, Anri memiliki ide ketika menggunakan proxy cukup dengan mengetikkan domain janganlupa-ta.yyy.pw dan memasukkan port 8080.

   a. instal bind di UML malang
    
   ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/12.1.png)
    
   b. tambahkan konfigurasi situs janganlupa-ta.a15.pw di named.conf.local di malang
    
   ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/12.2.png)
    
   c. ubah konfigurasi web janganlupa-ta.a15.pw sesuai gambar berikut
    
   ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/12.3.png)
    
   d. ubah settingan proxy pada windows atau pada firefox dengan mengganti IP mojokerto dengan ```janganlupa-ta.a15.pw```
    
   ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/12.4.png)
    
   e. hasil 
    
   ![fotooooo](https://github.com/farrelmt/Jarkom_Modul3_Lapres_A15/blob/main/screenshot/12.5.png)
