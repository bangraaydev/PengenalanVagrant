# PengenalanVagrant

**Apa dan Untuk apa?**
-------------
Sebagai seorang software developer, di tengah banyaknya persaingan sekaligus permintaan yang tinggi akan perangkat lunak, mengharuskan kita untuk bekerja lebih pintar dan efisien. Salah satunya adalah dengan memanfaatkan berbagai macam tools yang bisa mempermudah saat pengembangan ataupun testing perangkat lunak. Khususnya kalau anda seorang web developer pastinya sering mengalami hal-hal berikut:

 1. Transfer project antar workstation, misalkan anda sehari-hari melakukan development di PC kantor/rumah terus besoknya tiba-tiba ada meeting dengan klien untuk menunjukkan progress projek dimana kita akan bawa laptop untuk presentasi. Pastinya kita harus copy dulu file projek kita, terus set semuanya (install web server di laptop, install DB server, Lampp dll) dan berharap semuanya akan lancar berjalan seperti biasanya

 2. Team development menggunakan berbagai OS (Sistem Operasi) berbeda, Ini juga sering terjadi. Misal kita mengembangkan aplikasi web berbasis Django/Python di Ubuntu, sedangkan team front-end kita bekerja di Mac OS atau Windows. Bagaimana caranya supaya project kita jalan dengan baik di OS mereka, sedangkan tidak semua designer/front-end developer mengerti bagaimana menghidupkan server, DB dan segala macam keperluannya?
 
 3. Di PC saya jalan, kenapa di PC kamu error ya? ini juga erat dengan 2 point saya diatas. Masalah ini sering terjadi karena sering perbedaan sistem operasi, versi, perogram-program pendukung lainnya yang tidak sama dengan yang kita pakai.

Oke, kita akui masalah-masalah tersebut diatas masih menghantui kita sampai sekarang, tapi adakah solusinya? yang membuat kehidupan kita sebagai software engineer lebih menyenangkan? Pastinya, salah satu yang bisa kita pakai untuk meminimalisir masalah diatas adalah dengan menggunakan Mesin Virtual (VM).

Kalau anda pernah memakai VirtualBox, VMWare maka anda pernah mengunakan mesin virtual. Namun Mesin Virtual tidaklah cukup, kita perlu tool khusus lagi yang lebih powerful yaitu [Vagrant](http://www.vagrantup.com/).

**Apa itu Vagrant?**
-------------
Vagrant adalah sebuah program yang memanfaatkan teknologi Mesin Virtual yang memungkinkan kita untuk membuat lingkungan development software secara portable, mudah di duplikasi, konsisten, sehingga proses pengembangan lebih fleksibel.
**Keuntungannya**
-------------

Dengan berbasis mesin virtual, itu artinya point ke-2 dari masalah kita diatas sudah teratasi. Karena proyek kita dijalankan dalam lingkungan virtual yang sama persis/identik dengan lingkungan saat kita melakukkan development, ini artinya apapun sistem operasi teman/anggota team kita, selama mereka memiliki VM dan Vagrant terinstall, maka proyek bisa jalan dengan baik.

Bahkan bagi designer yang tidak mengetahui cara menghidupkan server misalnya, hanya dengan satu buah command, maka mesin virtual akan hidup dan projek kita langsung aktif di dalamnya. Karena sifatnya yang portable, ini artinya lingkungan virtual proyek yang kita kerjakan dengan mudah di transfer atau di copy ke PC/laptop lain dengan catatan sudah terinstal VM dan Vagrant juga disana. Dan ketika dijalankan maka hasilnya akan sama.
**Cara kerjanya**
-------------

Dibalik semua keuntungan yang bisa kita peroleh menggunakkan Vagrant, pada dasarnya prinsip kerjanya cukup sederhana. Ini dimulai dengan pemilihan Sistem Operasi, OS apa yang akan kita pasang di VM tersebut, misalkan kita pakai Ubuntu server.

Ini juga menyangkut konsistensi, misalkan aplikasi web kita nantinya akan di hosting pada Ubuntu server, maka sekalian kita developnya di Ubuntu server juga. Vagrant bekerja memanfaatkan Mesin Virtual (misalnya VirtualBox atau VMWare), melalui vagrant kita bisa mengaktifkan VM tersebut, dan setelah mesin tersebut aktif kita bisa perintahkan Vagrant untuk menginstall semua program-program pendukung untuk menjalankan projek dengan sempurna, dan menyimpan semua konfigurasi VM melalui Vagrant.

Ketika akan di duplikasi dan didistribusikan ke anggota team, apapun OS yang mereka gunakan untuk bekerja, maka ketika diaktifkan dengan Vagrant maka VM akan menjalankan Ubuntu server juga, dengan segala konfigurasi yang sama seperti kita set sebelumnya. Untuk lebih jauh mengenal Vagrant, artikel ini akan saya bagi menjadi beberapa seri.

Jadi sampai jumpa di seri berikutnya dimana kita akan mulai dengan instalasi.




**Instalasi**
-------------

Instalasi Vagrant cukup mudah dan hampir sama dengan instalasi aplikasi lainnya. Karena Vagrant perlu vitual machine untuk berjalan maka pastikan anda juga sudah menginstall Virtual Box sebelumnya.

Untuk instalasi, silahkan mengacu ke halaman [download Vagrant](https://www.vagrantup.com/downloads) dan pilih sesuai sistem operasi yang anda gunakan. Saya pengguna Ubuntu 64bit maka saya pilih versi Linux (Deb) 64 bit.

Setelah instalasi selesai coba jalankan command `vagrant -v` untuk mengetahui apakah Vagrant sudah terinstal dan versinya. Kalau di laptop saya hasilnya seperti ini:

    eka@lenovo:~$ vagrant -v

Seperti terlihat, versi saya masih versi 1.6.2 diinstall setahun yang lalu sepertinya, dan saat ini versi terbaru adalah versi 2.

Untuk di Windows, instalasi secara otomatis menambahkan vagrant ke system path, apabila ketika menjalankan command `vagrant -v` ternyata vagrant tidak ditemukan, silahkan logout dan login kembali dari Windows dan coba kembali.

**Uninstall**
-------------
Untuk meng-uninstall Vagrant dari komputer anda juga sama seperti menguninstall program lainnya, berikut cara uninstall Vagrant yang saya kutip dari dokumentasinya:

Di Windows, uninstall melalui **Add/Remove program** di Control Panel.

Di Mac OS X, hapus direktori `/Applications/Vagrant`	 dan file `/usr/bin/vagrant` dan juga jalankan perintah `sudo pkgutil –forget com.vagrant.vagrant` ini akan membuat Mac OS X melupakan bahwa Vagrant pernah terinstall, sehingga menghindari konflik pada instalasi berikutnya.

Di Linux, tinggal hapus direktori `/opt/vagran` dan juga file `/usr/bin/vagrant`.

Sekian untuk proses Instalasi dan Uninstall, di seri berikutnya kita akan berkenalan dengan Vagrant Box.

**Tentang Vagrant Boxes**
-------------
Setelah sebelumnya kita menginstall Vagrant, kali ini kita akan memahami sedikit tentang apa itu Vagrant Boxes.

Box atau Kotak merupakan sebuah mesin virtual dimana sistem operasi dan semua yang konfigurasi yang telah kita lakukkan akan tersimpan di dalam sebuah Box.

Dengan demikian, menggunakan Vagrant pada dasarnya kita menghidupkan mesin virtual, itulah alasannya kita kenapa kita memerlukkan VirtualBox atau VMWare untuk menjalankan vagrant. Vagrant sendiri hanyalah tool pembantu untuk mengaktifkan mesin virtual dengan berbagai kelebihan tentunya.

Anda bisa saja tidak menggunakan Vagrant, cukup menghidupkan VirtualBox dan install Ubuntu di dalamnya, untuk mengkoneksikan dengan jaringan internet harus mengkonfigurasi terlebih dahulu, mensetup SSH secara manual dan lainnya harus dilakukkan manual.

Dengan Vagrant, semua itu sudah diatur, hanya dengan satu perintah, server anda sudah aktif dan menjalankan semua aplikasi didalamnya secara otomatis.

Saya tidak sarankan anda membuat Box sendiri, memang bisa tetapi lebih baik kita menggunakan Box yang sudah ada untuk kemudahan pemakaian.

Cara paling gampang adalah dengan mendownload melalui repository Vagrant box yang tersedia secara online. Melalui https://atlas.hashicorp.com/boxes/search.
atau [disini](http://www.vagrantbox.es/)

Mendownload yang saya maksudkan bukan dengan download via browser, tetapi dengan perintah melalui Vagrant. Berikut formatnya untuk menambahkan Box baru:

    $ vagrant box add USER/BOX

Bagian `USER/BOX` anda ganti dengan USER (User yang membuat box tersebut) dan BOX (Nama box).

Misalnya saya jalankan command `vagrant add ubuntu/trusty64` atau `vagrant box add hashicorp/precise64`.

Dari kedua command tersebut `ubuntu` dan `hashicorp` adalah user pembuat box tersebut sedangkan `trusty64` dan `precise64` adalah boxnya sendiri dimana Ubuntu Trusty 64 bit dan Ubuntu Precise 64 bit.

**Perhatian**
-------------
Seperti yang kita tahu bahwa ukuran instalasi untuk Ubuntu ataupun distro linux lainnya cukup besar, ini artinya proses download akan berlangsung cukup lama tergantung koneksi internet anda. Jadi pastikan anda memiliki koneksi internet yang bagus sebelum memutuskan untuk menginstall Box baru.

**Kesimpulan**
-------------
Vagrant hanyalah sebuah software/program untuk membantu memudahkan anda menggunakan Virtual Machine. Jadi jangan bingung antara Vagrant dan Box, Vagrant bukan Virtual Machine, Vagrant juga bukan sebuah Box tetapi vagrant berada di tengah-tengah mereka berdua menyediakan tools untuk developer mempermudah bekerja dengan keduanya.

Selanjutnya kita akan coba Install Box pertama kita.

**Project, UP dan SSH**
-------------
Setelah sebelumnya kita belajar sedikit mengenai teorinya, sekarang kita akan coba praktekkkan langsung.

Sebagai contoh, pertama buat sebuah direktori dan kita beri nama vagrant-test dan misalkan lokasinya menjadi `/home/eka/vagrant-test`.

Masuk ke direktory tersebut dan jalankan perintah vagrant init dan hasilnya seperti di bawah ini:

    $ vagrant init

	A `Vagrantfile` has been placed in this directory. You are now ready to `vagrant up` your first virtual environment! Please read the comments in the 
	`Vagrantfile` as well as documentation on

Perintah di atas akan membuatkan kita sebuah file bernama Vagrantfile dan kalau dibuka sebagian isinya seperti ini:


    # -*- mode: ruby -*-
    # vi: set ft=ruby :

	 # Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
	
	VAGRANTFILE_API_VERSION = "2"
	
	Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
	
	  # All Vagrant configuration is done here. The most common configuration
	
	  # options are documented and commented below. For a complete reference,
	
	  # please see the online documentation at vagrantup.com.
	
	  # Every Vagrant virtual environment requires a box to build off of.
	
	  config.vm.box = "base"  ...
	
	  ...


Untuk saat ini jangan dibingungkan dahulu mengenai arti isi file tersebut, Vagrantfile merupakan konfigurasi bagaimana kita akan menjalankan Box nantinya, seperti Box mana yang akan dipakai, dan ketika dijalankan perintah apa yang dieksekusi dan lain sebagainya.

Setelah kita mempunyai Vagrantfile, sekarang saatnya kita menginstall Box yang akan dipakai. Seperti artikel sebelumnya kita sudah tahu bagaimana cara menginstall Box yaitu `vagrant box add hashicorp/precise64`.

    $ vagrant box add hashicorp/precise64

	== box: Loading metadata for box 'hashicorp/precise64'
	
	    box: URL: https://vagrantcloud.com/hashicorp/precise64
	
	== box: Adding box 'hashicorp/precise64' (v1.0.0) for provider: virtualbox
	
	...
	
	...

Setelah download selesai, maka kita perlu memberitahu Vagrant bahwa kita akan menggunakan `Box hashicorp/precise64` yang baru saja kita download, maka buka file `Vagrantfile` dan ganti pada bagian `config.vm.box = “base”` menjadi `config.vm.box = “hashicorp/precise64”`.

**Jalankan Mesin Virtual**
-------------
Ok, box sudah terinstall, Vagrantfile sudah di update. Kita akan jalankan box hashicorp/precise64 dengan perintah vagrant up masih di direktori yang sma yaitu`vagrant-test`.

    $ vagrant up

	Bringing machine 'default' up with 'virtualbox' provider...
	
	== default: Importing base box 'hashicorp/precise64'...
	
	== default: Matching MAC address for NAT networking...
	
	== default: Checking if box 'hashicorp/precise64' is up to date...
	
	== default: Setting the name of the VM: vagrant-test_default_1444449714334_40363
	
	== default: Clearing any previously set network interfaces...
	
	== default: Preparing network interfaces based on configuration...
	
	    default: Adapter 1: nat
	
	== default: Forwarding ports...
	
	    default: 22 = &gt; 2222 (adapter 1)
	
	== default: Booting VM...
	
	== default: Waiting for machine to boot. This may take a few minutes...
	
	    default: SSH address: 127.0.0.1:2222
	
	    default: SSH username: vagrant
	
	    default: SSH auth method: private key
	
	    default: Warning: Connection timeout. Retrying...
	
	== default: Machine booted and ready!
	
	== default: Checking for guest additions in VM...
	
	    default: The guest additions on this VM do not match the installed version of
	
	    default: VirtualBox! In most cases this is fine, but in rare cases it can
	
	    default: prevent things such as shared folders from working properly. If you see
	
	    default: shared folder errors, please make sure the guest additions within the
	
	    default: virtual machine match the version of VirtualBox you have installed on
	
	    default: your host and reload your VM.
	
	    default: 
	
	    default: Guest Additions Version: 4.2.0
	
	    default: VirtualBox Version: 4.3
	
	== default: Mounting shared folders...
	
	    default: /vagrant =&gt; /home/eka/vagrant-test


Seperti yang terlihat diatas, box saya sudah berjalan dan Vagrant melakukkan beberapa pengaturan standar yaitu mengatur SSH dan Shared folder. Shared folder disini artinya folder tempat anda mengaktifkan Vagrant saat ini secara otomatis bisa diakses melalui box ketika login via SSH.

Perhatikan baris ini: `default: /vagrant =&gt; /home/eka/vagrant-test` artinya ketika anda login via ssh ke dalam Box, anda tinggal pindah direktori ke /vagrant (`cd /vagrant`) dan anda akan melihat semua isi direktori lokal anda.


**Login dengan SSH**
-------------
Sekarang Box Ubuntu anda sudah aktif dan kita bisa login kedalamnya via SSH, cukup dengan perintah vagrant ssh.

    $ vagrant ssh

	Welcome to Ubuntu 14.04 LTS (GNU/Linux 3.2.0-23-generic-pae i686)
	
	Welcome to your Vagrant-built virtual machine.
	
	Last login: Fri Sep 14 06:22:31 2012 from 10.0.2.2
	
	vagrant@precise64:~$

Seperti anda lihat seketika kita sudah berada di dalam Box ubuntu. Keren bukan?

Nah untuk menguji apakah benar file di laptop saya bisa saya akses dari dalam Box, tinggal pindah ke direktori `/vagrant`.

    vagrant@precise32:~$ cd /vagrant

	vagrant@precise32:/vagrant$ ls
	
	Vagrantfile

Anda lihat file `Vagrantfile` yang telah buat sebelumnya. Jadi di dalam box ini kita bisa melakukkan apa saja seperti menginstall web server, mengupdate software, melakukkan konfigurasi, dan yang lainnya.

Berikutnya kita akan belajar bagaimana cara menghentikan Box, dan mengaktifkannya lagi tanpa harus kehilangan semua konfigurasi yang sudah anda lakukkan di dalam Box.

**Suspend, Halt dan Destroy**
-------------

Nah setelah sebelumnya kita berhasil menjalankan Box ubuntu, mengetahui bagaimana cara login dan mengakses file lokal di direktori `/vagrant`.

Misalkan kita sudah setup box nya sesuai keperluan, sudah dipasangi webserver, software sudah diupdate, konfigurasi sudah ok. Tentunya kita ingin nantinya atau besoknya ketika menjalankan `vagrant up` lagi, semua konfigurasi dan software yang kita install masih utuh dan tidak hilang.

Di Vagrant ada 3 mode kita menghentikan/shut down Box yang lagi berjalan yaitu:

 1. vagrant suspend, ini sama seperti kita mensuspend komputer dimana semua yang kita lakukkan saat itu akan disimpan apa adanya, software yang sedang berjalan akan disimpan state nya, konfigurasi tidak akan hilang dan prosesnya cepat. Namun dengan mensuspend box maka akan memakan sedikit lebih banyak disk space
 
 2. vagrant halt, ini akan men-shut down box anda namun smua file, software dan konfigurasi yang sudah ada akan masih di tempatnya. Jadi ketika lain kali menjalankan vagrant up lagi, semua masih seperti sediakala. Ini sama seperti anda mematikan/shut-down komputer
 
 3. vagrant destroy, ini akan menghapus box anda, jadi semua yang sudah terinstall dan terkonfigurasi otomatis akan hilang. Ketika anda menjalankan vagrant up kembali maka semua proses akan diulang dari awal. Ini yang paling hemat disk space karena box telah dihapus.


Ini pastinya sesuai keperluan, misalnya setelah membuat tutorial ini saya akan menjalankan `vagrant destroy` karena sudah tidak diperlukan lagi.

Apabila anda mengerjakan sebuah project dengan Vagrant dan sudah melakukkan berbagai konfigurasi di dalam Box, saya menyarankan anda menggunakan `vagrant suspend` atau `vagrant halt`.

    $ vagrant halt

	== default: Attempting graceful shutdown of VM...

> Catatan: perintah-perintah diatas bukan dijalankan dari dalam box, anda harus keluar terlebih dahulu dengan perintah `exit` dari ssh, setelah itu baru menjalankan perintah diatas.

Selanjutnya kita akan mencoba menggunakan fitur Provision, dimana dengan provision otomatis, kita bisa membuat sebuah shell script menginstruksikan hal-hal apa saja yang perlu dilakukkan saat pertama kali menjalankan vagrant up.

Ini sangat praktis ketika kita perlu menyusun program-program apa saja yang perlu diinstall saat box dibuat, membuat direktori di tempat tertentu, membuat file konfigurasi atau bahkan otomatis menjalankan program tertentu ketika box sudah aktif tanpa perlu kita melakukkannya secara manual setiap kali membuat box.


**Provisioning dan Networking**
-------------
**Provisioning**
-------------

**Provisioning** bisa kita artikan sebagai sebuah proses untuk mengkonfigurasi/nenginstall/mengupdate sebuah sistem operasi (dalam hal ini Box linux kita) dengan program-program yang diperlukan saat pertama kali box tersebut diaktifkan.

Misal kita sedang mengerjakan proyek berbasis PHP sehingga perlu PHP5, Apache webserver, MySql Database di dalam Box, normalnya kita login via SSH ke box dan menginstallnya satu-persatu. Tentunya sangat tidak effisien kalau harus melakukkannya berulang kali setiap kali anda menjalankan `vagrant up`

Disinilah provisioning otomatis akan sangat membantu, bagaimana caranya? cara yang paling sederhana adalah anda cukup membuat sebuah file shell di direktori yang sama dengan file Vagrantfile, misal kita beri nama `provision.sh`
dan didalamnya kita isi dengan perintah untuk menginstall Apache, MySQL dan PHP5.

    #!/usr/bin/env bash

	apt-get update
	
	 # install apache2
	
	apt-get install -y apache2
	
	 # Kita ganti root direktori apache dari /var/www ke /vagrant (lokasi file kita)
	
	if ! [ -L /var/www ]; then
	
	  rm -rf /var/www
	
	  ln -fs /vagrant /var/www
	
	fi
	
	 # install mysql
	
	apt-get install mysql-server php5-mysql
	
	 # install PHP5
	
	apt-get install php5 libapache2-mod-php5 php5-mcrypt

File diatas hanya contoh sederhana, hanya untuk menunjukkan apa yang bisa kita lakukkan melalui fitur provisioning.

Setelah file tersebut kita buat, selanjutnya kita edit Vagrantfile supaya mengeksekusi file provision.sh saat menjalankan
menjadi seperti ini.

    # -*- mode: ruby -*-

	 # vi: set ft=ruby :
	
	 # Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
	
	VAGRANTFILE_API_VERSION = "2"
	
	Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
	
	  # All Vagrant configuration is done here. The most common configuration
	
	  # options are documented and commented below. For a complete reference,
	
	  # please see the online documentation at vagrantup.com.
	
	  # Every Vagrant virtual environment requires a box to build off of.
	
	  config.vm.box = "hashicorp/precise32"
	
	  config.vm.provision :shell, path: "provision.sh"
	
	...

Kita tambahkan baris baru: `config.vm.provision :shell, path: "provision.sh"`

Selanjutnya untuk menjalankan file provisioner kita, tinggal tambahkan parameter `-provision`
ketika menjalankan `vagrant up` , maka otomatis setelah box aktif script akan dieksekusi dan semua perintah di dalamnya akan dijalankan.

> Catatan: Ketika pertama kali anda menjalankan `vagrant up`, maka vagrant akan otomatis menjalankan script provisioner, setelah itu provisioner tidak akan dijalankan kecuali anda menggunakan parameter –provision.

Saat anda login via SSH, anda akan mendapati Box sudah terinstall Apache, Mysql dan PHP5. Praktis bukan?

Untuk lebih lengkap mengenai metode-metode provisioning yang lebih advance, silahkan merujuk ke [dokumentasinya](https://docs.vagrantup.com/v2/provisioning/index.html).

Sekarang Apache sudah terinstall, bagaimana caranya untuk mengakses dari broser lokal kita?. Untuk bisa mengakses port 80 (webserver) dari box, kita perlu mengkonfigurasi sedikit di Networkingnya.

**Networking**
-------------

Kita perlu memberitahu Vagrant bahwa kita ingin mengakses port 80 di dalam box supaya bisa kita akses di port 8080 misalnya di komputer local. Vagrant melakukkannya dengan port forwarding.

Caranya edit kembali Vagrantfile dan tambahkan baris berikut: `config.vm.network :forwarder_port, guest: 80, host :8080`

Sekarang jalankan perintah `vagrant reload` (apabila box sudah aktif) atau `vagrant up`

(box belum aktif). Maka ketika anda mengakses http://localhost:8080, sebenarnya ada mengakses web server Apache di box kita.

Untuk lebih detail mengenai networking di Vagrant silahkan baca-baca di sini https://docs.vagrantup.com/v2/networking/index.html.

Jadi demikianlah sedikit tutorial yang saya buat untuk memperkenalkan Vagrant, mudah-mudahan bisa membuat hidup anda sebagai developer lebih mudah.

Vagrant adalah topik yang sangat luas, jadi tidak mungkin saya bahas semuanya disini. Mudah-mudahan seri Pengenalan Vagrant ini bisa membantu anda mulai menggunakan Vagrant. Selamat mencoba, dan jangan lupa bagi pengalaman anda setelah menggunakan Vagrant.
