SISTEM CARIAN SLIP PENCAPAIAN MURID V2
SMK DATO' MOHD SAID NILAI
===================================

KANDUNGAN
1. index.html - fail utama untuk dimuat naik ke GitHub Pages
2. Code.gs    - kod Google Apps Script (salin ke Apps Script)

FUNGSI
- 1 nombor KP boleh mempunyai banyak slip (UPSA, UASA, PBD, dan sebagainya)
- Carian semua PDF dengan padanan nombor KP yang TEPAT
- Label jenis pentaksiran dan tahun ditentukan daripada NAMA FAIL
- Senarai mengikut tahun terkini, lihat PDF dan muat turun
- Folder Drive asal kekal private (tiada keperluan "Anyone with link" pada PDF)

FORMAT NAMA FAIL PDF DALAM FOLDER GOOGLE DRIVE
  120101011234_UASA_2026.pdf
  120101011234_UPSA_2026.pdf
  120101011234_PBD_AKHIR_2026.pdf
  120101011234_PBD_PERTENGAHAN_2026.pdf
  120101011234.pdf
  120101-01-1234_UASA_2026.pdf

Folder ID sudah dimasukkan dalam Code.gs:
  1DPoMHkY6lEhkorUnlckf8vKzxU-AblZx

LANGKAH A - APPS SCRIPT
1. Log masuk akaun Google yang mempunyai akses kepada folder slip.
2. Buka https://script.google.com/ > New project.
3. Padam kandungan Code.gs sedia ada dan tampal SELURUH kod daripada fail Code.gs ini.
4. Save > pilih fungsi ujiSambungan > Run > berikan kebenaran.
5. Deploy > New deployment > Web app.
   Execute as: Me
   Who has access: Anyone (HANYA jika dibenarkan oleh polisi sekolah).
6. Deploy; salin URL yang berakhir dengan /exec.
   Untuk perubahan kod kemudian: Deploy > Manage deployments > Edit > New version.

LANGKAH B - GITHUB PAGES
1. Buka index.html dalam text editor.
2. Cari baris:
   const SCRIPT_URL = 'PASTE_URL_APPS_SCRIPT_DI_SINI';
3. Ganti teks PASTE_URL_APPS_SCRIPT_DI_SINI dengan URL /exec Apps Script.
4. GitHub > New repository > Upload index.html ke root folder.
5. Settings > Pages > Deploy from a branch > main > /(root) > Save.
6. Akses URL GitHub Pages setelah tapak diterbitkan.

CARA UJI
- Sediakan dua PDF contoh dalam folder dengan nombor KP DUMMY (bukan KP sebenar):
  990101019999_UPSA_2026.pdf
  990101019999_UASA_2026.pdf
- Cari 990101019999. Sepatutnya keluar kedua-dua slip.
- Klik Lihat PDF / Muat Turun setiap slip.
- Pastikan nombor KP yang tiada tidak memaparkan slip.

PERHATIAN TEKNIKAL
- Fail PDF mesti berada secara terus dalam folder tersebut (bukan subfolder).
- PDF maksimum 8 MB bagi setiap fail, boleh ubah MAX_PDF_MB dalam Code.gs.
- Muat turun PDF dilakukan melalui Apps Script, bukannya pautan perkongsian awam Google Drive.
- Aplikasi mengambil PDF mengikut beberapa bahagian (chunks) untuk lebih stabil.
- Fail kecil lebih laju. Elakkan slip PDF terlalu besar.
- Jangan masukkan API key atau rahsia dalam index.html (fail GitHub bersifat public).

AMARAN PERLINDUNGAN DATA
Nombor kad pengenalan BUKAN kata laluan. Sesiapa yang mengetahui KP boleh mendapatkan
slip jika aplikasi dibuka untuk umum. Kelulusan pentadbir sekolah dan pematuhan
polisi perlindungan data diperlukan sebelum digunakan dengan data murid sebenar.
Untuk keselamatan yang lebih baik, tambah PIN unik ibu bapa / murid atau login.
