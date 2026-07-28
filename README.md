# ThinkPad P53 - macOS OpenCore EFI

Krótka, przejrzysta konfiguracja OpenCore EFI dla laptopa **Lenovo ThinkPad P53** przygotowana pod system macOS.

---

## 💻 Specyfikacja sprzętowa

| Podzespół | Model | Status w macOS |
| :--- | :--- | :--- |
| **Procesor** | Intel Core i7-9850H (6C/12T) | ✅ Działa |
| **Grafika zintegrowana** | Intel UHD Graphics 630 | ✅ Działa (Metal / Akceleracja) |
| **Grafika dedykowana** | NVIDIA Quadro T2000 | ❌ Wyłączona (Brak wsparcia w macOS) |
| **Pamięć RAM** | 16 GB DDR4 | ✅ Działa |
| **Karta sieciowa (LAN)** | Intel Ethernet Connection I219-LM | ❌ Wyłączona (Planowana poprawka) |
| **Karta Wi-Fi / BT** | Intel Wi-Fi 6 AX200 | ❌ Wyłączona (Kernel panic) |

---

## ⚡ Aktualny status / Uwagi

- **Instalator:** ✅ W pełni bootowalny i sprawny.
- **Obsługa dysków NVMe:** ⚠️ **Tymczasowo wyłączona** ze względu na specyficzny/niekompatybilny dysk NVMe używany w konfiguracji testowej.
- **Wi-Fi, Bluetooth & Ethernet:** ⚠️ **Wyłączone.** Sieć bezprzewodowa oraz Bluetooth wywoływały *kernel panic*. Kexty odpowiedzialne za obsługę karty Wi-Fi, Bluetooth oraz karty sieciowej Ethernet zostaną dodane/poprawione w następnej aktualizacji EFI.

---

## 🛠 Konfiguracja OpenCore

1. Wygeneruj własne numery seryjne (**SMBIOS**: `MacBookPro16,1` lub `MacBookPro16,4`) za pomocą **GenSMBIOS**.
2. Wklej wygenerowane `Serial`, `Board Serial`, `SmUUID` oraz `MLB` do `config.plist` w sekcji `PlatformInfo`.
3. Dostosuj kexty/sterowniki dysku NVMe oraz sieciowe do swojego sprzętu przed przystąpieniem do instalacji.
