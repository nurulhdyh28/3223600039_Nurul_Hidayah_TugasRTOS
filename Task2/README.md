ESP32-S3 FreeRTOS Task2

Menunjukkan kemampuan multitasking pada ESP32-S3 menggunakan FreeRTOS. Program ini menjalankan beberapa tugas secara bersamaan untuk mengelola berbagai periferal input dan output.
Fitur Utama Program ini menggunakan FreeRTOS untuk memisahkan setiap periferal ke dalam task-nya sendiri. Program juga memanfaatkan kedua inti prosesor (Core 0 dan Core 1) untuk alokasi tugas yang berbeda.

Periferal yang Digunakan 
- OLED Display (SSD1306, I2C) 
- Potentiometer 
- Servo Motor  
- LED (Yellow, Red, White) 
- Push Button 
- Rotary Encoder  
- Stepper Motor 
- Buzzer

Struktur Task Proyek ini dibagi menjadi beberapa tugas independen: 
- taskOLED (Core 0): Mengupdate layar OLED dengan data sensor. 
- taskLEDs (Core 0): Menjalankan pola kedip bergantian pada tiga LED. 
- taskButtons (Core 0): Membaca input dari dua push button dan mencetak ke Serial. 
- taskPotentiometer (Core 1): Membaca nilai analog potensiometer. 
- taskEncoder (Core 1): Membaca putaran dan tombol rotary encoder. 
- taskServo (Core 0): Menggerakkan servo bolak-balik (0-90 derajat). 
- taskStepper (Core 1): Menggerakkan stepper motor maju dan mundur. 
- taskBuzzer (Core 0): Memainkan nada "Beep" secara berkala.

Alokasi Pin 
- OLED SDA: Pin 8 
- OLED SCL: Pin 9 
- Potentiometer: Pin 1 
- Servo: Pin 18 
- LED 1 (Yellow): Pin 14 
- LED 2 (Red): Pin 13 
- LED 3 (White): Pin 21 
- Button 1: Pin 15 
- Button 2: Pin 16 
- Encoder CLK: Pin 10 
- Encoder DT: Pin 11 
- Encoder SW: Pin 12 
- Stepper (Manual) Step: Pin 18 
- Stepper (Manual) Dir: Pin 19 
- Stepper (AccelLib) Ena: Pin 20 
- Stepper (AccelLib) Step: Pin 38 
- Stepper (AccelLib) Dir: Pin 39 
- Buzzer: Pin 17

Library yang Dibutuhkan 
- Wire.h 
- Adafruit_GFX.h 
- Adafruit_SSD1306.h 
- ESP32Servo.h 
- AccelStepper.h