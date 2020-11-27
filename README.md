**Kelompok A15 :**

Farrel Muhammad Taqi     05111840000071

Muhammad Iqbal Humam     05111840000103

**DHCP**

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
