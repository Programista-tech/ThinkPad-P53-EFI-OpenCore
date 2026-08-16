# ThinkPad P53 Hackintosh (OpenCore)

Otwarta konfiguracja OpenCore dla laptopa **Lenovo ThinkPad P53**. 

> 🆕 **Najnowsza aktualizacja:** Dodano pełne wsparcie dla **macOS Tahoe** z działającą akceleracją graficzną!

---

## 💻 Specyfikacja sprzętowa / Hardware Status

| Komponent | Model / Opis | Stan | Uwagi |
| :--- | :--- | :---: | :--- |
| **CPU** | **Intel Core i7-9850H** | 🟢 Działa | Zoptymalizowane zarządzanie energią |
| **Dysk SSD** | **Western Digital PC SN740** | 🟢 Działa | System macOS zainstalowany i uruchomiony na tym dysku |
| **iGPU** | Intel UHD Graphics 630 | 🟢 Działa | **Pełna akceleracja graficzna (Metal)** |
| **dGPU** | Dedykowana karta NVIDIA | 🔴 Niewspierana | Wyłączona za pomocą SSDT (zgodnie z ograniczeniami macOS) |
| **Porty USB** | USB 3.1 / Type-C | 🟢 Działa | Pełne zmapowanie portów (USBMap / UTBMap) |
| **Wi-Fi & Bluetooth** | Karta fabryczna / kompatybilna | 🟢 Działa | Wsparcie przez odpowiednie kexty |
| **Trackpad & Klawiatura** | Synaptics / PS2 | 🟢 Działa | Działają gesty oraz klawisze funkcyjne |
| **Dźwięk (Audio)** | **Synaptics Audio** | 🔴 Nie działa | Brak dźwięku z głośników (do dopracowania layout-id / AppleALC) |
| **Mikrofon** | Wbudowany mikrofon | 🔴 Nie działa | Mikrofon nie jest obecnie wykrywany |
| **Sleep / Wake** | Uśpienie | 🟡 Częściowo | Wymaga dalszych testów pod macOS Tahoe |

---

## ⚠️ WAŻNE: Przed użyciem (SMBIOS)

Ze względów bezpieczeństwa oraz ochrony konta Apple ID, z pliku `config.plist` zostały usunięte unikalne numery seryjne komputera!

**Przed uruchomieniem systemu musisz wygenerować własny SMBIOS:**

1. Pobierz narzędzie [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS).
2. Otwórz `config.plist` w edytorze (np. *ProperTree*).
3. Wygeneruj nowe dane dla odpowiedniego modelu (np. `MacBookPro16,1`).
4. Uzupełnij poniższe pola w `PlatformInfo -> Generic`:
   * `SystemSerialNumber`
   * `MLB`
   * `SystemUUID`
   * `ROM`
5. Zapisz plik `config.plist`.

---

## 🚀 Instalacja / Update

1. Sformatuj pendrive do systemu plików **FAT32** z partycją **GUID Partition Map (GPT)**.
2. Skopiuj folder `EFI` na partycję EFI dysku instalacyjnego / systemowego.
3. Upewnij się, że ustawienia BIOS w ThinkPadzie są odpowiednio skonfigurowane:
   * **Disable:** Secure Boot, VT-d (lub `DisableIoMapper` w OpenCore), Fast Boot.
   * **AHCI Mode** dla kontrolera SATA/NVMe.
   * **Graphics Device:** Hybrid Graphics / UMA (w zależności od konfiguracji).

---

## 🛠️ Known Issues / Do zrobienia (To-Do)

- [ ] Naprawa kextów audio (**AppleALC**) pod kątem obsługi wyjścia audio Synaptics i wbudowanego mikrofonu w macOS Tahoe.
- [ ] Dalsze dopracowywanie zarządzania energią na procesorze i7-9850H.

---

## 📜 Credits

- [Acidanthera](https://github.com/acidanthera) za OpenCore oraz kexty (`Lilu`, `WhateverGreen`, `VirtualSMC`, `AppleALC`).
- Społeczność Hackintosh za wsparcie i dokumentację.
