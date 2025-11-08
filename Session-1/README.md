# Session 1 - Solidity Fundamental Learning

Folder ini berisi materi pembelajaran dasar Solidity yang terstruktur dari level pemula hingga menengah. Semua kontrak menggunakan Solidity versi ^0.8.30 dengan lisensi MIT.

## 📁 Struktur Folder

### Root Files

#### 1. **LearnFunctionModifiers.sol**
Kontrak untuk mempelajari function modifiers dalam Solidity:
- **View functions**: Membaca state tanpa mengubahnya (gratis, tidak perlu gas)
  - `getCounter()`, `getOwner()`, `getBalance()`
- **Pure functions**: Tidak membaca dan tidak mengubah state (gratis)
  - `add()`, `multiply()`, `calculateDouble()`
- **Payable functions**: Fungsi yang dapat menerima ETH
  - `deposit()`, `buyItem()`
- **Regular functions**: Fungsi yang mengubah state (perlu gas)
  - `incrementCounter()`, `setCounter()`

#### 2. **LiskGarden.sol** 
Proyek akhir yang mengimplementasikan game plant management lengkap dengan fitur:
- **Enum & Struct**: GrowthStage (SEED, SPROUT, GROWING, BLOOMING) dan Plant struct
- **State Management**: Mapping plants, userPlants, dan counter
- **Game Mechanics**:
  - Plant seed dengan biaya 0.001 ETH
  - Water system dengan deplesi otomatis
  - Stage progression berdasarkan waktu
  - Harvest dengan reward 0.003 ETH
- **Events**: PlantSeeded, PlantWatered, PlantHarvested, StageAdvanced, PlantDied
- **Constants**: PLANT_PRICE, REWARD_PANEN, STAGE_DURATION, WATER_DEPLETION_TIME

---

## 📚 Solidity-101: Tipe Data Dasar

### **LearnAddress.sol**
Pengenalan tipe data `address` untuk menyimpan alamat wallet Ethereum:
- Variabel `owner` dan `gardener` bertipe address
- Penggunaan `msg.sender` untuk mendapatkan alamat pemanggil
- Fungsi `setGardener()` untuk mengubah address

### **LearnBoolean.sol**
Belajar tipe data `bool` untuk nilai true/false:
- Variabel `isAlive` dan `isBlooming`
- Fungsi untuk mengubah status boolean

### **LearnNumber.sol**
Penggunaan tipe data `uint256` untuk angka:
- Variabel `plantId` dan `waterLevel`
- Operasi aritmatika sederhana (penambahan)
- Fungsi `addWater()` untuk increment nilai

### **LearnString.sol**
Mempelajari tipe data `string`:
- Variabel `plantName`
- Fungsi untuk mengubah string
- Penggunaan `memory` keyword

### **SimplePlant.sol**
Template latihan untuk mengombinasikan semua tipe data dasar (berisi TODO untuk dikerjakan).

---

## 📚 Solidity-102: Struktur Data Kompleks

### **LearnEnum.sol**
Pengenalan `enum` untuk mendefinisikan tipe data dengan nilai terbatas:
- Enum `GrowthStage` dengan 4 nilai: SEED (0), SPROUT (1), GROWING (2), BLOOMING (3)
- Fungsi `grow()` untuk mengubah stage secara berurutan
- Penggunaan conditional statements dengan enum

### **LearnStruct.sol**
Belajar `struct` untuk mengelompokkan data terkait:
- Struct `Plant` dengan 5 field: id, owner, stage, waterLevel, isAlive
- Kombinasi enum dan struct
- Fungsi untuk memanipulasi data struct

---

## 📚 Solidity-103: Collections

### **LearnArray.sol**
Mempelajari `array` untuk menyimpan daftar data:
- Dynamic array `allPlantIds`
- Fungsi `push()` untuk menambah elemen
- Fungsi `length` untuk mendapatkan jumlah elemen
- Return array dari fungsi

### **LearnMapping.sol**
Pengenalan `mapping` untuk key-value storage:
- Mapping plantId => waterLevel
- Mapping plantId => owner address
- Tidak bisa iterate mapping (berbeda dengan array)

### **MultiplePlants.sol**
Kombinasi mapping, struct, dan counter untuk manajemen multiple objects:
- Mapping untuk menyimpan Plant struct
- Counter untuk auto-increment ID
- Fungsi CRUD (Create, Read) untuk tanaman

---

## 📚 Solidity-104: Advanced Concepts

### **LearnEvents.sol**
Belajar `event` untuk logging dan tracking:
- Event `PlantAdded` dan `PlantWatered`
- Penggunaan `indexed` parameter untuk filtering
- `emit` keyword untuk trigger event

### **LearnModifier.sol**
Mempelajari custom `modifier` untuk reusable logic:
- Modifier `onlyOwner`: Batasi akses hanya untuk owner
- Modifier `onlyPlantOwner`: Validasi kepemilikan tanaman
- Symbol `_` untuk menandai posisi eksekusi fungsi

### **LearnRequire.sol**
Penggunaan `require()` untuk validasi:
- Cek ownership sebelum eksekusi
- Error message custom
- Revert transaksi jika kondisi tidak terpenuhi

---

## 📚 Solidity-105: Ethereum Transactions

### **LearnPayable.sol**
Fungsi `payable` untuk menerima ETH:
- Fungsi `buyPlant()` dengan biaya minimum
- `msg.value` untuk mendapatkan jumlah ETH yang dikirim
- `address(this).balance` untuk cek saldo contract

### **LearnSendETH.sol**
Mengirim ETH dari contract:
- Fungsi `deposit()` untuk terima ETH
- `.call{value: amount}("")` untuk kirim ETH (recommended method)
- Pengecekan `success` untuk validasi transfer

---

## 📚 Solidity-106: Best Practices & Advanced Topics

### **LearnErrorHandling.sol**
Tiga metode error handling:
- **require()**: Validasi input dan kondisi (paling umum)
- **revert()**: Manual error dengan kondisi custom
- **assert()**: Internal error checking untuk bug detection

### **LearnFunctionModifiers.sol**
Penjelasan lengkap tentang function modifiers (sama dengan root file).

### **LearnScopes.sol**
Memahami scope variabel:
- **State variables**: Disimpan permanent di blockchain storage
- **Global variables**: Built-in Solidity (`msg.sender`, `block.timestamp`, dll)
- **Local variables**: Temporary dalam fungsi

### **LearnVisibility.sol**
Visibility specifiers untuk kontrol akses:
- **public**: Bisa dipanggil dari mana saja (otomatis ada getter untuk state var)
- **external**: Hanya dari luar contract
- **internal**: Contract ini dan turunannya
- **private**: Hanya contract ini