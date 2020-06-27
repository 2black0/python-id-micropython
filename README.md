# python-id-micropython

Micropython.org menyediakan live micropython secara online yang diberi nama unicorn, bisa diakses di: https://micropython.org/unicorn/

## Instalasi MicroPython ke ESP32

### Perangkat yang dibutuhkan:
 - python (saya merekomendasikan conda)
 - esptool
 - jupyter
 - ESP32
 - led RGB
 - sensor DHT11

### Instalasi Python
sumber: https://docs.conda.io/projects/conda/en/latest/user-guide/install/download.html

saya menggunakan versi minimalis yaitu Miniconda

<img src="pic/miniconda.png" width="275" align="left"/>

### Instalasi esptool
saya merekomendasikan membuat environment baru dan sekalian menginstall pip pada environment tersebut, untuk conda bisa ketik perintah berikut
> `> conda create --name micropython`
>
> `> conda install -c anaconda pip`

install jupyter dengan perintah:
> `> conda install -c anaconda jupyter`

install esptool dengan perintah:
> `> pip install esptool`

cek hasil instalasi dengan ketik dan akan muncul versi yang digunakan
> `> esptool`

<img src="pic/esptool.png" width="750" align="left"/>

### Flash Firmware MicroPython ke ESP32

download firmware: http://micropython.org/download/esp32/

<img src="pic/micropython-firmware.png" width="350" align="left"/>

download bisa dilakukan secara manual dengan klik link atau menggunakan wget dengan perintah:

> `> wget http://micropython.org/resources/firmware/esp32-idf3-20191220-v1.12.bin`

hubungkan ESP32 dengan laptop / komputer via kabel USB dan cek COM yang terdeteksi via device manager

<img src="pic/serial-com.png" width="650" align="left"/>

hapus firmware sebelum kita mengupgrade firmware yang lebih baru dengan mengetik:

> `> esptool.py --chip esp32 erase_flash`

kemudian flash firmware yang telah kita download dengan cara ketik (perhatikan COM yang digunakan):
> `> esptool.py --chip esp32 --port COM9 write_flash -z 0x1000 esp32-idf3-20191220-v1.12.bin`

## REPL (Read-Eval-Print Loop)

download putty: https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html

jalankan dan isi COM yang digunakan serta baudrate 115200 dan klik open untuk membuka koneksi

<img src="pic/putty-1.png" width="450" align="left"/>

## Jupyter notebook MicroPython Kernel

install kernel pada jupyter notebook dengan mengetik:
> `> git clone https://github.com/goatchurchprime/jupyter_micropython_kernel.git`
>
> `> pip install -e jupyter_micropython_kernel`
>
> `> python -m jupyter_micropython_kernel.install`

buka jupyter notebook dengan perintah:
> `> jupyter notebook`

<img src="pic/jupyter-notebook.png" width="650" align="left"/>