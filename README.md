# Advotics Dashboard Web Interview

## Deployment Link
```
https://advotics-dashboard-johanesimarmata.netlify.app
```
## Frameworks/Tools/Libraries
 - VueJs
 - Vuetify with Core JS
 - Vue Router
 - JSCharting Vue
##  Notes

 - Homepage bukan merupakan dashboard namun berisi tombol untuk mengakses dashboard
 - Dashboard juga dapat diakses melalui Navigation Drawer
 - Untuk filter period:
	1. Minimum time range 1 day: contohnya hari ke-i dan hari ke-(i+1)
	2. Maximum time range 6 months: Saya menghitungnya berdasarkan selisih bulannya contohnya 1 Januari ke 1 Juli. Saya tidak menghitungnya berdasarkan 6 * 30 (asumsi 1 bulan = 30) = 180 hari.
 - Untuk chart, itu static sehingga tidak ada perubahan ketika value dari select diganti
 - Untuk product dari selling SKU dan competitor SKU, mereka memiliki sebuah class selected untuk membedakan mana product yang sedang aktif (atau di click terakhir) dengan default bahwa product yang sedang aktif adalah product teratas
## How to Run
Saya asumsikan sudah memiliki nodejs di dalam laptop atau pc masing-masing.
 - Clone git repository ini
 - Buka hasil clone dengan text editor
 - Run npm install untuk menginstall dependencies
 - Run npm run serve untuk menjalankan secara local
