**Kelompok A15 :**

Farrel Muhammad Taqi     05111840000071

Muhammad Iqbal Humam     05111840000103

**DHCP**

**PROXY**

8. Pertama, akses ke proxy hanya bisa dilakukan oleh Anri sendiri sebagai user TA. (7) User autentikasi milik Anri memiliki format: User : userta_yyy Password : inipassw0rdta_yyy

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
