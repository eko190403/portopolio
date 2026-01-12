# 🚀 Flutter Setup Guide - Windows

Panduan lengkap install Flutter di Windows untuk development Android/Web/Desktop.

---

## 📋 STEP 1: Download & Install Prerequisites

### 1.1 Download Flutter SDK
1. Buka: https://docs.flutter.dev/get-started/install/windows
2. Download Flutter SDK (zip file ~1GB)
3. Extract ke: `C:\src\flutter` (jangan di Program Files)

### 1.2 Install Git
1. Download: https://git-scm.com/download/win
2. Install dengan default settings
3. Restart terminal setelah install

### 1.3 Install VS Code (Recommended - Lebih Ringan)
1. Download: https://code.visualstudio.com/
2. Install dengan default settings
3. Jauh lebih ringan dari Android Studio (~200MB vs 3GB)

**Note:** Kita TIDAK perlu Android Studio IDE. Cukup Android SDK tools saja (step berikutnya).

---

## ⚙️ STEP 2: Setup Flutter Path

### Windows 10/11:
1. Tekan `Windows + R`
2. Ketik: `sysdm.cpl` → Enter
3. Klik tab **Advanced** → **Environment Variables**
4. Di **User variables**, pilih **Path** → **Edit**
5. Klik **New** → Tambahkan: `C:\src\flutter\bin`
6. Klik **OK** semua dialog
7. **Restart terminal/PowerShell**

### Verifikasi:
```powershell
flutter --version
```

---

## 🔧 STEP 3: Setup Android SDK (Tanpa Android Studio)

### 3.1 Download Android Command Line Tools
1. Buka: https://developer.android.com/studio#command-line-tools-only
2. Scroll ke "Command line tools only"
3. Download untuk Windows
4. Extract ke: `C:\Android\cmdline-tools\latest`

### 3.2 Setup Android SDK via Flutter
Jalankan command ini, Flutter akan otomatis setup Android SDK:

```powershell
flutter doctor --android-licenses
```

Ketik `y` untuk menerima semua licenses.

### 3.3 Install Android Build Tools (Manual)
Jika masih ada error, install manual:

```powershell
# Set ANDROID_HOME
$env:ANDROID_HOME = "C:\Users\$env:USERNAME\AppData\Local\Android\Sdk"

# Install platform tools
flutter doctor
```

**Alternatif: Install via Android Studio (Lebih Mudah)**
Jika cara di atas ribet, bisa install Android Studio sekali untuk setup SDK, lalu uninstall IDE-nya. SDK tetap tersimpan.

---

## 💻 STEP 4: Setup VS Code

### 4.1 Install Extensions
1. Buka VS Code
2. Go to Extensions (Ctrl+Shift+X)
3. Install:
   - **Flutter** (by Dart Code)
   - **Dart** (by Dart Code)

### 4.2 Verifikasi Flutter di VS Code
1. **Ctrl+Shift+P** → ketik: **Flutter: Run Flutter Doctor**
2. Lihat output di terminal

---

## 📱 STEP 5: Setup Emulator atau Test di Chrome

### Option 1: Test di Chrome (Paling Mudah)
Tidak perlu emulator, langsung test di browser:
```powershell
flutter run -d chrome
```

### Option 2: Test di HP Android Fisik
1. Enable **Developer Options** di HP
2. Enable **USB Debugging**
3. Colok HP ke PC via USB
4. Jalankan:
```powershell
flutter devices
flutter run
```

### Option 3: Install Android Emulator (Optional)
Jika butuh emulator tanpa Android Studio:
1. Install **Android Studio** (temporary)
2. Setup emulator via AVD Manager
3. Uninstall Android Studio IDE (emulator tetap jalan)

---

## ✅ STEP 6: Flutter Doctor

Jalankan command ini untuk cek setup:

```powershell
flutter doctor
```

**Output yang diharapkan:**
```
[✓] Flutter (Channel stable, 3.x.x)
[✓] Android toolchain - develop for Android devices
[✓] Chrome - develop for the web
[!] Android Studio (not installed) ← INI NORMAL
[✓] VS Code (version 1.x)
[✓] Connected device (2 available)
```

**Note:** Android Studio (not installed) itu AMAN, karena kita pakai VS Code.

### Fix Issues:
Jika ada [✗] atau [!]:

**Android Licenses:**
```powershell
flutter doctor --android-licenses
```
Ketik `y` untuk semua.

---

## 💻 STEP 7: Create First Flutter App (Tanpa Android Studio)

### Via Command Line:
```powershell
# Navigate ke folder project
cd C:\xampp\htdocs

# Create Flutter project
flutter create my_first_app

# Masuk ke folder project
cd my_first_app

# Run app (pilih device: Chrome atau Android Emulator)
flutter run
```

### Via VS Code:
1. **Ctrl+Shift+P** → ketik: **Flutter: New Project**
2. Pilih **Application**
3. Pilih folder location
4. Beri nama project
5. Tekan **F5** untuk run

---

## 🧪 STEP 8: Test Build (Tanpa Emulator)

### Test Web (Paling Mudah):
```powershell
flutter run -d chrome
```

### Test Android (Pakai HP Fisik):
```powershell
flutter devices  # Cek HP terdeteksi
flutter run      # Auto pilih device
```

### Test Windows Desktop:
```powershell
flutter run -d windows
```

**Rekomendasi:** Test di Chrome dulu, paling cepat dan mudah!

---

## 🛠️ Common Issues & Solutions

### Issue: "cmdline-tools component is missing"
**Fix:**
```powershell
flutter doctor --android-licenses
```

### Issue: "Unable to find bundled Java version"
**Fix:**
1. Download JDK 11: https://www.oracle.com/java/technologies/javase/jdk11-archive-downloads.html
2. Install
3. Set JAVA_HOME di Environment Variables

### Issue: "Flutter command not found"
**Fix:**
- Pastikan Path sudah benar
- Restart terminal/PowerShell
- Restart Windows jika perlu

### Issue: Emulator lambat
**Fix:**
1. Enable Virtualization (VT-x/AMD-V) di BIOS
2. Install Intel HAXM: https://github.com/intel/haxm

---

## 📚 Quick Reference

### Flutter Commands:
```powershell
flutter create <app_name>      # Create new project
flutter run                    # Run app
flutter build apk              # Build Android APK
flutter build appbundle        # Build Android App Bundle
flutter build web              # Build for web
flutter clean                  # Clean build files
flutter pub get                # Get dependencies
flutter upgrade                # Update Flutter SDK
flutter doctor -v              # Detailed health check
```

### Hot Reload:
- Press `r` di terminal saat app running
- Atau save file di VS Code (auto hot reload)

---

## ✨ Next Steps

1. ✅ Verifikasi `flutter doctor` semua hijau
2. ✅ Buat project pertama
3. ✅ Run di emulator/chrome
4. ✅ Mulai coding!

### Learning Resources:
- Official Docs: https://docs.flutter.dev
- Flutter Cookbook: https://docs.flutter.dev/cookbook
- Flutter Codelabs: https://docs.flutter.dev/codelabs
- Widget Catalog: https://docs.flutter.dev/development/ui/widgets

---

## 🎓 Project Ideas untuk Belajar:

1. **Todo List App** - CRUD basics
2. **Weather App** - API integration
3. **Calculator** - UI & logic
4. **News Reader** - ListView & networking
5. **Chat App** - Firebase integration

---

**Status**: Siap development setelah semua step selesai! 🚀
