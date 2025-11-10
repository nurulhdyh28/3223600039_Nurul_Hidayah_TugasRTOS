Tugas RTOS 1

Repositori ini adalah penyerahan untuk Tugas 1 RTOS. Tujuan dari tugas ini adalah untuk mengimplementasikan dan menguji berbagai periferal I/O pada ESP32 menggunakan FreeRTOS.
Sesuai dengan instruksi tugas, proyek ini mencakup:
- Koneksi Periferal: 8 modul periferal berbeda (Button, Buzzer, Encoder, LED, OLED, Potentio       Servo, Stepper) telah dirangkai dan dihubungkan ke ESP32.
- Program I/O: Setiap periferal memiliki program demonya sendiri.
- Implementasi Multi-Core: Untuk setiap periferal, disediakan dua program identik. Satu program dikonfigurasi untuk berjalan di Core 0, dan program lainnya dikonfigurasi untuk berjalan di Core 1, sesuai dengan instruksi tugas.
- Dokumentasi: Setiap percobaan didokumentasikan dengan langkah percobaan, konfigurasi pin, serta bukti hasil berupa gambar dan video.

1. Oled
Langkah Percobaan
Tujuan: Menampilkan teks dengan efek "typewriter" pada layar OLED SSD1306 (I2C).

Konfigurasi Pin (I2C):
OLED_SDA: GPIO 14
OLED_SCL: GPIO 13

Logika Task (oledTask): Task membersihkan layar, lalu mencetak string teks karakter per karakter dengan jeda vTaskDelay 200ms antar karakter. Siklus berulang.

Video Percobaan: https://drive.google.com/drive/folders/1ONEEKmL2ppFtw3FKPm4DEMMZu2Flz05N?usp=drive_link

2. LED
Langkah Percobaan
Tujuan: Menyalakan tiga LED secara bergantian (sequential blink).

Konfigurasi Pin:
ledMerah: GPIO 13 (OUTPUT)
ledTosca: GPIO 12 (OUTPUT)
ledHijau: GPIO 11 (OUTPUT)

Logika Task (ledTask): Task menyalakan dan mematikan ledMerah, ledTosca, dan ledHijau secara berurutan dengan jeda 500ms untuk setiap aksi.

Video Percobaan: https://drive.google.com/drive/folders/1Nb5e-OA0thv_ShZqKWi_zeJE5a4dgDH1?usp=drive_link

3. Buzzer
Langkah Percobaan
Tujuan: Menghasilkan dua nada berbeda pada buzzer secara bergantian menggunakan vTaskDelay untuk pengaturan waktu.

Konfigurasi Pin:
buzzerPin: GPIO 14 (OUTPUT)

Logika Task (buzzerTask): Task berjalan dalam loop, membunyikan nada 1000 Hz (500ms), diam (300ms), lalu nada 1500 Hz (500ms), dan diam (800ms).

Video Percobaan: https://drive.google.com/drive/folders/1HNkKCBq_18Vt6EiJjao0gKt1EDfHkaJH?usp=drive_link

4. Push Button
Langkah Percobaan
Tujuan: Membaca input dari dua tombol (push button) untuk mengontrol dua LED secara independen menggunakan satu task.

Konfigurasi Pin:
button1Pin: GPIO 14 (INPUT_PULLUP)
button2Pin: GPIO 13 (INPUT_PULLUP)
led1Pin: GPIO 12 (OUTPUT)
led2Pin: GPIO 11 (OUTPUT)

Logika Task (buttonTask): Task berjalan dalam loop tak terbatas, membaca status button1Pin dan button2Pin. Tombol 1 mengontrol LED 1, dan Tombol 2 mengontrol LED 2.

Video Percobaan: (https://drive.google.com/drive/folders/1rQj-qFiVHNoIPgZ_PM2A-pFGdfZjNIVl?usp=drive_link)

5. Potentiometer
Langkah Percobaan
Tujuan: Membaca nilai analog dari potensiometer dan mencetaknya ke Serial Monitor.

Konfigurasi Pin:
potPin: GPIO 3 (INPUT)

Logika Task (potTask): Task membaca nilai ADC (0-4095) dari potPin setiap 500ms, mengonversinya ke tegangan (0-3.3V), dan mencetak kedua nilai ke Serial Monitor.

Video Percobaan: (https://drive.google.com/drive/folders/119C7AgNGNSk_RQqTXSsabPiloKuMZz4e?usp=drive_link)

6. Encoder
Langkah Percobaan
Tujuan: Membaca putaran (rotasi CW/CCW) dan penekanan tombol dari rotary encoder.

Konfigurasi Pin:
CLK: GPIO 6 (INPUT_PULLUP)
DT: GPIO 7 (INPUT_PULLUP)
SW: GPIO 8 (INPUT_PULLUP)

Logika Task (EncoderTask): Task memonitor pin CLK dan DT untuk mendeteksi arah putaran (menambah/mengurangi variabel count) dan memonitor pin SW untuk mendeteksi penekanan tombol. Hasil dicetak ke Serial Monitor.

Video Percobaan: https://drive.google.com/drive/folders/1JO3cDHdr_FkC3UFB6ch7ZRdvH8ZHtvy0?usp=drive_link

7. Motor Stepper
Langkah Percobaan
Tujuan: Menggerakkan motor stepper (dengan driver eksternal) satu putaran penuh Clockwise (CW) dan satu putaran Counter-Clockwise (CCW) secara bergantian.

Konfigurasi Pin:
STEP_PIN: GPIO 18 (OUTPUT)
DIR_PIN: GPIO 19 (OUTPUT)

Logika Task (StepperTask): Task mengatur DIR_PIN ke HIGH (CW), menghasilkan 200 pulsa STEP. Menunggu 1 detik. Mengatur DIR_PIN ke LOW (CCW), menghasilkan 200 pulsa STEP. Menunggu 1 detik, lalu mengulang.

Video Percobaan: (https://drive.google.com/drive/folders/1bVQev_WsVF4cDG2DXxmJlNL772ws7GWS?usp=drive_link) 

8. Motor Servo
Langkah Percobaan
Tujuan: Menggerakkan motor servo ke dua posisi (0 dan 90 derajat) secara berulang.

Konfigurasi Pin:
Servo Pin: GPIO 4

Logika Task (ServoTask): Task menggerakkan servo ke 0 derajat, menunggu 500ms, lalu menggerakkan ke 90 derajat, menunggu 500ms, dan mengulangi siklus.

Video Percobaan: https://drive.google.com/drive/folders/1pvaDUdqTDsf8-4HFAFEqrbnpU69Otp3K?usp=drive_link