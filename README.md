# PROJECT(6)-SISTEM OPERASI
# TUGAS 1 'Basic Recovery'
Langka[1]
Masuk ke dalam Direktori Desktop
```
cd Desktop
```
Masuk ke notpad dengan perintah CMD
```
notepad setup.bat
```
# SCRIPT PICTURES
[https://drive.google.com/file/d/1Fd0026XCT_VzST2Uk6CBhtNGBwZH7lLs/view?usp=drive_link]
# ISI SCRIPT
```
@echo off
title SETUP SIMULASI DATA RECOVERY
echo ===========================================
echo         MEMBUAT SIMULASI DRIVE D
echo ===========================================
echo.

:: Lokasi di Desktop
set base=C:\Users\ASUS\Desktop\SimulasiDrive_D

:: Membuat folder utama SimulasiDrive_D
echo Membuat folder utama SimulasiDrive_D...
mkdir "%base%" >nul 2>&1

echo Membuat struktur folder dan file...
echo.

for /l %%i in (1,1,10) do (

    echo Membuat Folder_%%i ...
    mkdir "%base%\Folder_%%i\SubFolder_A"
    mkdir "%base%\Folder_%%i\SubFolder_B"
    mkdir "%base%\Folder_%%i\SubFolder_C"

    :: ========== SUBFOLDER A ==========
    echo PDF dummy file > "%base%\Folder_%%i\SubFolder_A\dokumen_%%i_A.pdf"
    echo CSV dummy file > "%base%\Folder_%%i\SubFolder_A\data_%%i_A.csv"
    echo TXT dummy file > "%base%\Folder_%%i\SubFolder_A\catatan_%%i_A.txt"
    echo DOCX dummy file > "%base%\Folder_%%i\SubFolder_A\laporan_%%i_A.docx"
    echo BAT dummy file > "%base%\Folder_%%i\SubFolder_A\aplikasi_%%i_A.bat"

    :: ========== SUBFOLDER B ==========
    echo file B1 > "%base%\Folder_%%i\SubFolder_B\file_b1_%%i.txt"
    echo file B2 > "%base%\Folder_%%i\SubFolder_B\file_b2_%%i.csv"
    echo file B3 > "%base%\Folder_%%i\SubFolder_B\file_b3_%%i.docx"
    echo file B4 > "%base%\Folder_%%i\SubFolder_B\file_b4_%%i.py"
    echo file B5 > "%base%\Folder_%%i\SubFolder_B\file_b5_%%i.jpg"

    :: ========== SUBFOLDER C ==========
    echo file C1 > "%base%\Folder_%%i\SubFolder_C\file_c1_%%i.txt"
    echo file C2 > "%base%\Folder_%%i\SubFolder_C\file_c2_%%i.ini"
    echo file C3 > "%base%\Folder_%%i\SubFolder_C\file_c3_%%i.pdf"
    echo file C4 > "%base%\Folder_%%i\SubFolder_C\file_c4_%%i.xml"
    echo file C5 > "%base%\Folder_%%i\SubFolder_C\file_c5_%%i.csv"
    echo file C6 > "%base%\Folder_%%i\SubFolder_C\file_c6_%%i.py"

    :: ========== FILE LUAR SUBFOLDER ==========
    echo database dummy file > "%base%\Folder_%%i\database_%%i.db"
    echo config dummy file > "%base%\Folder_%%i\config_%%i.ini"
)

echo.
echo ===========================================
echo       SETUP SELESAI !! PROSES BERHASIL
echo ===========================================
pause
```
# HASIL OUTPUT SCRIPT[setup.bat]
[https://drive.google.com/file/d/1_M_2yRPlMYaIEKZnxOF1xd47Vh-1OivL/view?usp=sharing]

# TUGAS 2 'Modifikasi Script (Intermediate)'
Langkah[1]
Masuk ke dalam Direktori Desktop
```
cd Desktop
```
Masuk ke notpad dengan perintah CMD
```
notepad recovery.bat
```
# SCRIPT PICTURES
[https://drive.google.com/file/d/1ZK0sMbHnUb_CftgxbQBPbYJmptw7TSRv/view?usp=drive_link]
# ISI SCRIPT
```
@echo off
echo ===============================================
echo               PROCESS RECOVERY DATA
echo ===============================================
echo.

:: Lokasi sumber (folder simulasi drive D)
set sumber=C:\Users\ASUS\Desktop\SimulasiDrive_D

:: Lokasi tujuan (folder simulasi drive C)
set root=C:\Users\ASUS\Desktop\SimulasiDrive_C

:: Membuat folder utama SimulasiDrive_C jika belum ada
if not exist "%root%" mkdir "%root%"

:: Format tanggal dan waktu
set yr=%date:~10,4%
set mo=%date:~4,2%
set dy=%date:~7,2%
set hr=%time:~0,2%
set mn=%time:~3,2%

:: Hilangkan spasi pada jam
set hr=%hr: =0%

set tujuan=%root%\DataRecovery_%yr%%mo%%dy%_%hr%%mn%
mkdir "%tujuan%"

:: Lokasi file log
set logfile=%root%\recovery_log.txt

:: Buat folder tujuan recovery
mkdir "%tujuan%" >nul 2>&1

echo Menyalin file dari:
echo %sumber%
echo ke:
echo %tujuan%
echo.

echo Membuat file log...
echo RECOVERY LOG > "%logfile%"
echo Tanggal: %date%  Waktu: %time% >> "%logfile%"
echo Sumber: %sumber% >> "%logfile%"
echo Tujuan: %tujuan% >> "%logfile%"
echo ---------------------------------------- >> "%logfile%"

:: SALIN ISI FOLDER (PERBAIKAN UTAMA)
xcopy "%sumber%\*" "%tujuan%\" /E /H /C /I /Y >> "%logfile%"

echo ---------------------------------------- >> "%logfile%"
echo Recovery selesai >> "%logfile%"

echo.
echo ===============================================
echo            RECOVERY SELESAI !!!
echo ===============================================
echo Log File: %logfile%
echo.

pause
```
# HASIL OUTPUT SCRIPT[recovery.bat]
[https://drive.google.com/file/d/18CHiNfypRSNVDcy8zsLjuGXnlmaqA_l7/view?usp=sharing]

# TUGAS 3 'Skenario Advanced (Challenge)'
Langkah[1]
Masuk ke dalam Direktori Desktop
```
cd Desktop
```
Masuk ke notpad dengan perintah CMD
```
advanced.bat
```
# SCRIPT PICTURES
Foto 1
[https://drive.google.com/file/d/1gvDbfxlzi-utR9l-Zot5NHhOK2IeOLYm/view?usp=sharing]
Foto 2
[https://drive.google.com/file/d/1iT8AsxDFc7JkmwEa7L3pOnqJSJkJLnxA/view?usp=drive_link]
# ISI SCRIPT
```
@echo off
title ADVANCED DATA RECOVERY SYSTEM
color 0B

set BASE=%USERPROFILE%\Desktop
set SOURCE=%BASE%\SimulasiDrive_D
set DEST_BASE=%BASE%\SimulasiDrive_C

:MENU
cls
echo ==========================================================
echo                ADVANCED DATA RECOVERY SYSTEM
echo ==========================================================
echo Source Folder: %SOURCE%
echo Destination:   %DEST_BASE%
echo ==========================================================
echo  1. Selective Backup (Pilih Folder)
echo  2. Incremental Backup (Hanya file baru/berubah)
echo  3. Scheduled Backup (Backup tiap X menit)
echo  4. Email Notification (Notifikasi Gmail)
echo  5. Exit
echo ==========================================================
set /p opc=Masukkan pilihan (1-5): 

if %opc%==1 goto SELECTIVE
if %opc%==2 goto INCREMENTAL
if %opc%==3 goto SCHEDULE
if %opc%==4 goto EMAIL
if %opc%==5 exit
goto MENU


:SELECTIVE
cls
echo ---- SELECTIVE BACKUP ----
echo Folder tersedia:
dir "%SOURCE%" /b
echo.
set /p FOLDER=Ketik nama folder yang ingin di-backup: 

set DEST=%DEST_BASE%\Selective_%FOLDER%_%date:~-4%%date:~4,2%%date:~7,2%_%time:~0,2%%time:~3,2%
mkdir "%DEST%"

xcopy "%SOURCE%\%FOLDER%" "%DEST%" /E /H /C /I /Y

echo SELESAI! Backup selective tersimpan di:
echo %DEST%
pause
goto MENU


:INCREMENTAL
cls
echo ---- INCREMENTAL BACKUP ----
set DEST=%DEST_BASE%\IncrementalBackup
mkdir "%DEST%"

robocopy "%SOURCE%" "%DEST%" /E /XO /LOG:%DEST%\incremental_log.txt

echo SELESAI! Incremental backup berjalan.
pause
goto MENU


:SCHEDULE
cls
echo ---- SCHEDULED BACKUP ----
set /p interval=Backup berulang setiap berapa menit?: 
echo Jalankan CTRL + C untuk menghentikan proses.
timeout 3 > nul

:LOOP
set TS=%date:~-4%%date:~4,2%%date:~7,2%_%time:~0,2%%time:~3,2%
set DEST=%DEST_BASE%\Schedule_%TS%
mkdir "%DEST%"
xcopy "%SOURCE%" "%DEST%" /E /H /C /I /Y

echo ----- Backup dilakukan pada %TS% -----
timeout %interval% * 60 > nul
goto LOOP


:EMAIL
cls
echo ---- EMAIL NOTIFICATION ----
set /p email=Masukkan email Gmail tujuan: 
set /p pesan=Tulis pesan singkat notifikasi: 

C:\Program Files\PowerShell\7\pwsh.exe-Command "Send-MailMessage -To '%email%' -From '%email%' -Subject 'Backup Selesai' -Body '%pesan%' -SmtpServer 'smtp.gmail.com' -Port 587 -UseSsl -Credential (New-Object System.Management.Automation.PSCredential('%email%', (Read-Host 'Password email Gmail' -AsSecureString)))"

echo Email notifikasi dikirim sukses!
pause
goto MENU
```
# HASIL OUTPUT SCRIPT[recovery.bat]
# Foto 1
[https://drive.google.com/file/d/13GZvbvkEhqoQMCfo6xPw_0BM197YflRb/view?usp=sharing]
# Foto 2
[https://drive.google.com/file/d/1bcCu-8FNbHvxi3ErfEa89ssRYE37LZ5M/view?usp=sharing]
# Foto 3
[https://drive.google.com/file/d/13h6ZIXsrijazEaecyuZ-aRa2sGiyloBR/view?usp=sharing]
# Foto 4
[https://drive.google.com/file/d/1RYfUkEgWN8UmvDYJC_f5fULvMvv5SmQO/view?usp=drive_link]
# Foto 5
[https://drive.google.com/file/d/1EpeQ6xvUDlPFHy8iQ_1oAySrZBopmKSF/view?usp=drive_link]
