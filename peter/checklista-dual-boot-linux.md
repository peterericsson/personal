# Checklista: Dual boot Linux Mint XFCE på MacBook Pro (Intel, T2)

Checklista för **MacBookPro16,2** (13" Intel MacBook Pro, 2020) med macOS Sequoia. Målet är dual boot: **macOS + Linux Mint 22.3 XFCE (T2-ISO)** på samma disk.

**Valt:** Linux Mint **22.3 XFCE**, T2-bygge från [t2linux/T2-Mint](https://github.com/t2linux/T2-Mint/releases/latest) — inte ISO:n på linuxmint.com.

### Läget just nu (2026-08-29)

| Steg | Status |
|---|---|
| Distro | valt: Mint 22.3 XFCE T2 |
| FileVault | **av** (`FileVault is Off.`) |
| ISO | `~/Downloads/linuxmint-22.3-xfce-7.0.9-t2-noble.iso` (3,0 GB). SHA256 **OK:** `d26a5b2fb72af22f52eb5647301805ee0235db01efeea01247d943bbc6d3561c` |
| Installer-USB | **beställd** Kjell 36162 Dual Drive Go 64 GB, 379 kr — upphämtning **2026-08-30 från kl 10** |
| Time Machine | **skippas** (ett USB räcker: ISO-stickan) |
| Firmware (`firmware.sh`) | **klart i macOS** (Method 1, EFI). Linux-kommandona körs **efter** install |
| Partitionering | **klart:** `Linux` 400 GB ExFAT = `disk0s4`, macOS APFS 600 GB |

**Ett USB:** SanDisk Ultra Dual Drive Luxe 64 GB till ISO:n. Time Machine skippas medvetet. Om partitioneringen i installern går fel kan macOS-data försvinna — därför **Something else**, radera bara Linux-partitionen.

Medan du väntar på stickan: **firmware i macOS är klart.** Kvar: köp USB, skriv ISO, Secure Boot, ev. partitionera i Diskverktyg.

**Läs detta först.** Den här Macen har Apples **T2-säkerhetschip**. Vanliga ISO:er från ubuntu.com / fedora.org fungerar dåligt: tangentbord, styrplatta och Wi‑Fi saknas ofta redan i installern. Använd därför en **T2-anpassad ISO** från [t2linux](https://t2linux.org/).

Behåll macOS. T2-Linux-projektet rekommenderar dual boot, bland annat för firmwareuppdateringar och en enkel väg tillbaka.

Kanoniska guider (följ dem parallellt med den här listan):

- [t2linux.org](https://t2linux.org/)
- [Förinstallation](https://wiki.t2linux.org/guides/preinstall/)
- [Ubuntu/Mint-installation](https://wiki.t2linux.org/distributions/ubuntu/installation/)
- [Wi‑Fi och Bluetooth](https://wiki.t2linux.org/guides/wifi-bluetooth/)
- [Hårdvarustatus](https://wiki.t2linux.org/state/)

---

## 0. Din Mac (utgångsläge)

| | |
|---|---|
| Modell | MacBook Pro 13" 2020, `MacBookPro16,2` |
| CPU / RAM | Intel Core i7 (Ice Lake, 4 kärnor) / 32 GB |
| GPU | Intel Iris Plus (inbyggd) — bra Linux-stöd |
| Disk | intern 1 TB SSD, ca **779 GB ledigt** |
| macOS | Sequoia 15.7.4 |
| Portar | bara USB‑C / Thunderbolt 3 (ingen USB‑A) |
| Extra | T2-chip, Touch Bar, Activation Lock på (Find My) |
| **Linux (valt)** | **Linux Mint 22.3 XFCE, T2-ISO** (`linuxmint-22.3-xfce-…-t2-noble`) |

**Utrymme:** ca 150 GB används av macOS. Du har gott om plats. Ett rimligt första val är **200–400 GB till Linux** och resten till macOS.

**Ta inte med serienummer i delade anteckningar.** Find My / Activation Lock behöver inte stängas av för dual boot.

---

## 1. Distro (valt)

**Linux Mint 22.3 XFCE (T2-ISO)** — beslutat.

Bygger på Ubuntu 24.04, T2-kärna ingår, XFCE håller skrivbordet lätt. Cursor, VS Code, Docker och Chrome är tunga appar; **32 GB RAM räcker**.

- T2-kärna: tangentbord, styrplatta, Touch Bar, ljud
- Ubuntu 24.04-bas → officiella `.deb` för Cursor, VS Code/Codium, Docker, Bitwarden
- Mint: Timeshift, mjukvarubutik, LTS-bas till 2029

**Ladda inte ner från linuxmint.com.** Hämta T2-bygget:

- [t2linux/T2-Mint releases](https://github.com/t2linux/T2-Mint/releases/latest)
- Aktuell bygge vid skrivande: `v7.0.9-1` (maj 2026)
- Fil att sikta på: **`linuxmint-22.3-xfce-…-t2-noble`**

### Verktyg på den här distron

| Behov | Vad som funkar bäst | Kommentar |
|---|---|---|
| **Webbläsare** | Firefox (förinstallerad) + **Chrome eller Brave** | Figma och WhatsApp Web mår bäst i Chromium. Installera Chrome/Brave som `.deb` eller Flatpak. |
| **Docker** | **Docker Engine + Compose**, inte Docker Desktop | Desktop finns för Linux men är tyngre och mer krångel. Engine är standard på Linux och räcker till VS Code/Cursor. |
| **VS Code / Codium** | Officiell `.deb` från Microsoft, eller VSCodium | Samma Ubuntu-repo som vanligt. |
| **Cursor** | Officiell Linux-`.deb` från [cursor.com/download](https://cursor.com/download) | Intel x64. Fungerar på Mint/Ubuntu. AppImage finns som backup. |
| **Mail** | **Thunderbird** | Bästa IMAP-klienten (Gmail, iCloud, Fastmail, Proton med Bridge). Lättare: Geary. Webbmail i Chrome funkar också. |
| **Figma** | **figma.com i Chrome** | Inget officiellt Linux-skrivbord. Webben är rätt väg. |
| **Bitwarden** | Webben + **browser extension** + ev. officiell Linux-app | Extension i Chrome/Firefox är det du använder varje dag. |
| **WhatsApp** | **web.whatsapp.com** som PWA i Chrome | Ingen officiell Linux-app. PWA ger eget fönster och notifieringar. Undvik slumpmässiga “WhatsApp för Linux”-appar. |
| **Övriga mess** | Telegram, Signal, Discord, Slack har Linux-appar | **iMessage finns inte.** Det stannar i macOS (därför dual boot är bra). Messenger/Instagram: webben eller en PWA. |

Samla flera chattar i ett fönster: [Ferdium](https://ferdium.org/) (WhatsApp + Messenger + Slack + …). Annars en PWA per tjänst.

**Docker Desktop vs Engine:** Docker Desktop på Linux kräver extra runtime och tar mer RAM. På den här maskinen: installera Engine, lägg till din användare i gruppen `docker`, använd Cursor/VS Code Docker-extension. Vill du ha GUI: Portainer i en container, eller Docker Desktop senare.

**Använd inte** ISO från linuxmint.com, ubuntu.com eller andra vanilla-byggen — då saknas tangentbord/styrplatta i installern. Cinnamon-smaken på samma T2-Mint-repo är tyngre och inte det som är valt här.

---

## 2. USB-sticka: ja, det finns modeller med båda utgångarna

Din Mac har bara USB‑C. Äldre PC:ar har USB‑A. **Ja — det finns stickor med USB‑C i ena änden och USB‑A i den andra.** Då slipper du adapter.

ISO:n är några GB. **32 GB räcker, 64 GB är det lugna valet** (plats över till firmware, extra ISO, backup av `firmware.tar`).

### Köp detta (bästa match)

**SanDisk Ultra Dual Drive Go 64 GB** (Kjell)  
[Art. 36162](https://www.kjell.com/se/produkter/dator/lagring/usb-minne-for-mobil/sandisk-ultra-dual-drive-go-usb-minne-med-usb-c-64-gb-p36162)

- USB‑C **och** USB‑A
- USB 3.1, ca 150 MB/s — räcker för ISO:n
- **Luxe** (metall) finns inte hos Kjell; **Go** är samma funktion

32 GB ([art. 36161](https://www.kjell.com/se/produkter/dator/lagring/usb-minne-for-mobil/sandisk-ultra-dual-drive-go-usb-minne-med-usb-c-32-gb-p36161)) räcker också. Inte Ultra Slider (bara USB‑C).

### Om du vill ha en “allmän” snabb dual-sticka senare

**SanDisk Extreme PRO Dual Drive** (USB‑A + USB‑C, upp till 1000 MB/s) finns hos t.ex. Proshop/Dustin, men **börjar på 256 GB och ~1 200 kr**. Överkill för den här uppgiften.

Andra dual-modeller: Kingston Dual Portable SSD, Lexar D50E, Amazon Basics Dual USB‑C/A. Samma princip: **båda kontakterna, minst 32 GB, USB 3.**

### Praktiska krav

- [ ] Minst 16 GB, helst **32 eller 64 GB**
- [ ] USB‑C (obligatoriskt på den här Macen)
- [ ] USB‑A extra (så den funkar på äldre maskiner) — dual-sticka
- [ ] Inte den enda kopian av viktiga filer: allt på stickan **raderas** när ISO:n skrivs

**Adapter som backup:** USB‑C-hona till USB‑A-hane (eller dongel) om du redan har en vanlig USB‑A-sticka. Dual-sticka är enklare.

---

## 3. Innan du rör disken

- [x] FileVault är **av** (kollat 2026-08-29: `FileVault is Off.`)
- [x] Time Machine **skippas** — bara ett USB (ISO-stickan). Accepterad risk: fel partitionering i installern kan radera macOS-data. Motåtgärd: **Something else**, rör bara Linux-partitionen.
- [ ] Recovery till hands (Command-R). Behåll macOS.
- [ ] Koppla in strömadapter vid partitionering och ISO-skrivning.
- [ ] Stäng tunga appar. iOS Simulator-imagen på ~24 GB (disk2/disk3) är inte den interna disken.

---

## 4. Firmware för Wi‑Fi / Bluetooth (gör i macOS)

T2-Macen har Broadcom **BCM4364** (Trinidad). Drivrutinen finns i T2-kärnan, men **firmware måste tas från macOS**.

Gör det **innan** Linux-installationen, medan du fortfarande är inloggad i macOS. Enklast (ingen extra mjukvara): kopiera firmware till EFI-partitionen.

Wikins “Click here” är lätt att missa. Direktlänk:

**[https://wiki.t2linux.org/tools/firmware.sh](https://wiki.t2linux.org/tools/firmware.sh)**

(Safari kan visa skriptet som text. Spara då som `firmware.sh` i Hämtade filer, eller använd curl nedan.)

```bash
curl -fsSL -o ~/Downloads/firmware.sh https://wiki.t2linux.org/tools/firmware.sh
chmod +x ~/Downloads/firmware.sh
bash ~/Downloads/firmware.sh
```

- [x] `firmware.sh` i `~/Downloads`
- [x] **Method 1** körd i macOS (2026-08-29): EFI monterad, firmware + skript kopierade, EFI avmonterad

Kör **inte** Linux-kommandona nu. De hör hemma efter Mint är installerat, om Wi‑Fi saknas:

```bash
sudo mkdir -p /tmp/apple-wifi-efi
sudo mount /dev/nvme0n1p1 /tmp/apple-wifi-efi
bash /tmp/apple-wifi-efi/firmware.sh
sudo umount /tmp/apple-wifi-efi
```

T2-Mint kan också: `get-apple-firmware get_from_macos`

Method 1 i macOS är redan gjord. EFI (`disk0s1`) ska lämnas orörd vid partitionering.

---

## 5. Partitionera i Diskverktyg

**Kritiskt:** välj **Add Partition**, inte **Add Volume**. Volume = extra APFS-volym inuti macOS. Partition = egen skiva som Linux kan formatera.

- [ ] Öppna **Diskverktyg**
- [ ] Visa alla enheter (Visa → Visa alla enheter) och välj den **fysiska** disken (`APPLE SSD…` / 1 TB), inte bara “Macintosh HD”
- [ ] **Partitionera** (pajdiagrammet uppe till höger)
- [ ] **+** → när frågan kommer: **Add Partition** (inte Volume)
- [ ] Namn: `Linux`
- [ ] Format: **ExFAT** (inte APFS — APFS förväxlas lätt med macOS i Linux-installern). Partitionen raderas och formateras om till ext4 under installationen.
- [ ] Storlek: t.ex. **300 GB** (välj en gång; att växa/krympa efteråt är jobbigt)
- [ ] Verkställ och vänta tills det är klart
- [x] Partition **Linux**, 400 GB, ExFAT — `disk0s4` (`Microsoft Basic Data`). macOS-containern är 600.3 GB (`disk0s2`). EFI `disk0s1` orörd. Kollat 2026-08-29 med `diskutil list`.

Lämna EFI-partitionen (`disk0s1`, ~315 MB) orörd.

---

## 6. Ladda ner T2-ISO och skriv USB

ISO:erna ligger ofta **uppdelade** (`.iso.00`, `.iso.01`, …). Använd det officiella skriptet eller t2linux Installer, inte bara en slumpmässig `.iso.00`.

### Nedladdning

- [x] ISO hämtad: `~/Downloads/linuxmint-22.3-xfce-7.0.9-t2-noble.iso` (3,0 GB, 2026-08-29)
- [x] SHA256 verifierad mot [sha256-xfce](https://github.com/t2linux/T2-Mint/releases/download/v7.0.9-1/sha256-xfce): `d26a5b2fb72af22f52eb5647301805ee0235db01efeea01247d943bbc6d3561c`
- [ ] Skriv ISO:n till USB **när stickan är köpt** (raderar stickan)

### Skriv till USB med `dd` (raderar stickan)

Inget GUI. Stickan i, sedan:

```bash
diskutil list
```

USB = **external, physical** (t.ex. `disk4`, ~64 GB). **Inte** `disk0` (intern 1 TB) och inte `disk1`.

```bash
sudo diskutil unmountDisk /dev/diskN
sudo dd if=~/Downloads/linuxmint-22.3-xfce-7.0.9-t2-noble.iso of=/dev/rdiskN bs=1m
```

Byt `diskN`. `rdisk` är snabbare. `control-T` visar förlopp. Klart när prompten kommer tillbaka (~3 GB, några minuter).

```bash
diskutil eject /dev/diskN
```

- [ ] Stickan är bootbar, USB‑C-änden mot Macen

---

## 7. Stäng av Secure Boot (Recovery)

Apples Secure Boot släpper bara in macOS/Windows. Linux kräver **No Security**.

- [ ] Stäng av Macen
- [ ] Starta och håll **Command (⌘) + R** tills Recovery kommer
- [ ] Logga in
- [ ] Menyrad: **Verktyg → Startsäkerhetsverktyg** (Startup Security Utility)
- [ ] Lösenord igen
- [ ] **Secure Boot:** No Security
- [ ] **Allow Boot Media:** Allow booting from external or removable media
- [ ] Valfritt: slå på **firmware-lösenord** så att annat än standard-OS kräver lösen — kompenserar lite för sänkt Secure Boot
- [ ] Starta om

Efter att Linux ligger på intern SSD kan du i samma verktyg **förbjuda USB-start igen**, så bara intern disk bootar utan extra steg.

---

## 8. Starta Linux-USB och installera

- [ ] USB i en USB‑C-port, gärna närmast ström om du är osäker
- [ ] Starta om och håll **Option (⌥)** tills startväljaren syns
- [ ] Välj den **orange EFI Boot**. Finns två: prova den **längst till höger** först
- [ ] Om du får *“A software update is required to use this startup disk”*: Secure Boot är fortfarande på, eller fel EFI-post — gå tillbaka till steg 7 / prova andra EFI Boot
- [ ] I GRUB: **Start Linux Mint** / **Install Linux Mint**

### Partitionering i installern — det här steget kan radera macOS

- [ ] Välj **Something else** / manuell partitionering
- [ ] **Aldrig** Automatic / Erase disk / Install alongside om du är det minsta osäker — automatik på T2-Mac har raderat macOS
- [ ] Hitta ExFAT-partitionen du skapade (storleken du valde, t.ex. ~300 GB). **Radera bara den** och skapa:

  | Partition | Filssystem | Monteringspunkt |
  |---|---|---|
  | Befintlig EFI (`nvme0n1p1`) | EFI, **formatera inte** | `/boot/efi` |
  | Din Linux-partition | ext4 (eller btrfs) | `/` |

- [ ] Swap är valfritt (32 GB RAM räcker; hibernate vill ha swap ≈ RAM)
- [ ] Bootloader: befintlig EFI, inte en ny disk
- [ ] Installera, starta om, ta ur USB

---

## 9. Första starten och Wi‑Fi

- [ ] Håll **Option (⌥)** vid start → orange **EFI Boot** = Linux. Apple-ikonen = macOS. Det är det vanliga sättet att växla.
- [ ] Om svart skärm efter GRUB (känt hos T2-Ubuntu/Mint + Mac Startup Manager): installera [rEFInd](https://wiki.t2linux.org/distributions/ubuntu/installation/) från macOS och starta Linux-kärnan därifrån
- [ ] Wi‑Fi saknas:

  ```bash
  get-apple-firmware get_from_macos
  ```

  eller hämta firmware från EFI (Method 1):

  ```bash
  sudo mkdir -p /tmp/apple-wifi-efi
  sudo mount /dev/nvme0n1p1 /tmp/apple-wifi-efi
  bash /tmp/apple-wifi-efi/firmware.sh
  sudo umount /tmp/apple-wifi-efi
  ```

- [ ] Starta om efter firmware
- [ ] Touch Bar: `sudo apt update && sudo apt install tiny-dfr` och starta om

---

## 10. Efterarbete och appar

- [ ] `sudo apt update && sudo apt upgrade` — behåll T2-kärnan (`linux-t2`), installera inte `broadcom-wl`
- [ ] Ljud / fläkt: se [postinstall](https://wiki.t2linux.org/guides/postinstall/) och t2linux FAQ om något saknas
- [ ] I Recovery: stäng av start från USB igen om du vill
- [ ] FileVault kan slås på igen **bara för macOS**
- [ ] Standardstart: Systeminställningar → Allmänt → Startskiva, eller håll Option varje gång

### Appar att sätta upp (Mint XFCE)

Webbläsare och “webben räcker”:

- [ ] Chrome eller Brave (Figma + WhatsApp PWA). Firefox räcker för vanlig surf.
- [ ] Figma: öppna i Chrome, ev. “Installera app” / PWA
- [ ] Bitwarden: extension i webbläsaren (+ ev. [desktop-app](https://bitwarden.com/download/))
- [ ] WhatsApp: [web.whatsapp.com](https://web.whatsapp.com) → i Chrome: **Installera** / “Skapa genväg” så du får ett eget fönster. Telefonen måste vara i närheten första gången.

Utveckling:

- [ ] Cursor: `.deb` från [cursor.com/download](https://cursor.com/download), sedan `sudo apt install ./cursor_*.deb`
- [ ] VS Code eller Codium: officiell `.deb`
- [ ] Docker Engine (lättare än Desktop):

  ```bash
  # officiella Docker-repon för Ubuntu/Mint (noble)
  sudo apt install ca-certificates curl
  sudo install -m 0755 -d /etc/apt/keyrings
  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
  echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu noble stable" | sudo tee /etc/apt/sources.list.d/docker.list
  sudo apt update
  sudo apt install docker-ce docker-ce-cli containerd.io docker-compose-plugin
  sudo usermod -aG docker "$USER"
  ```

  Logga ut och in. Testa med `docker run hello-world`. Skippa Docker Desktop tills du saknar just den GUI:n.

Mail och chatt:

- [ ] Thunderbird (`sudo apt install thunderbird`) — IMAP för Gmail/iCloud/Fastmail. Proton: Proton Mail Bridge + Thunderbird.
- [ ] Telegram: `sudo apt install telegram-desktop` eller Flatpak
- [ ] Signal / Discord / Slack: Flatpak eller officiell `.deb`
- [ ] iMessage, FaceTime, Apple Mail-synk som på macOS: **nej** — använd macOS-sidan av dual boot

Valfritt: [Ferdium](https://ferdium.org/) om du vill ha WhatsApp + Messenger + flera chattar i ett fönster.

---

## 11. Vad som brukar fungera på den här Macen

Enligt [t2linux state](https://wiki.t2linux.org/state/), med T2-kärna och firmware:

| Fungerar | Begränsat / nej |
|---|---|
| Tangentbord, styrplatta, USB‑C | **Touch ID** — nej |
| Skärm, Intel-GPU, skalning | Secure Boot måste vara av |
| Wi‑Fi / BT efter firmware | Touch Bar: F-tangenter/media utan `tiny-dfr` |
| Ljud (ibland extra config) | Vissa strömsparlägen / hibernate |
| Kamera (t2bce, nyare kärnor) | macOS-firmwareuppdateringar kräver macOS |
| Intern NVMe | |

Linux på T2 är användbart, inte identiskt med macOS. Räkna med lite efterarbete.

---

## 12. Mini-inköpslista

| Sak | Kommentar |
|---|---|
| SanDisk Ultra Dual Drive **Go** 64 GB | Kjell [36162](https://www.kjell.com/se/produkter/dator/lagring/usb-minne-for-mobil/sandisk-ultra-dual-drive-go-usb-minne-med-usb-c-64-gb-p36162). USB‑C + USB‑A. Inte Slider. |
| (Valfritt) USB‑C Ethernet eller telefon-tethering | Om Wi‑Fi strular under install |
| (Valfritt) USB‑C-hubb med USB‑A | Bara om du skippar dual-sticka |

---

## 13. Ordning att kryssa av

1. [x] FileVault av. Time Machine **skippas**
2. [x] USB beställd: Kjell **36162** Dual Drive Go 64 GB, 379 kr — hämta **imorgon (sön 30 aug) från kl 10**
3. [x] Distro: **Linux Mint 22.3 XFCE T2** (valt)
4. [x] ISO i `~/Downloads`, SHA256 OK
5. [x] `firmware.sh` Method 1 i macOS — firmware ligger på EFI
6. [x] Partitionera: **Add Partition**, ExFAT **400 GB** (`disk0s4`)
7. [ ] Skriv ISO till USB när stickan är hemma
8. [ ] Recovery: No Security + tillåt USB-start
9. [ ] Option → EFI Boot → installer → **Something else** (radera bara Linux-partitionen)
10. [ ] ext4 på Linux-partitionen, EFI orörd som `/boot/efi`
11. [ ] I Linux, om Wi‑Fi saknas: `mount` EFI + `firmware.sh` (kommandona skriptet skrev ut)
12. [ ] `tiny-dfr`, uppdateringar, stäng USB-start om du vill
13. [ ] Chrome/Brave, Cursor `.deb`, Docker Engine, Thunderbird, WhatsApp PWA

---

*Uppdaterad 2026-08-29. USB Kjell 36162 upphämtning 30 aug kl 10. Därefter: `diskutil list` → `dd` → Secure Boot.*
