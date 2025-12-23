# Ultimate Hands-Free Multi-Disc Ripper

A robust Bash script designed for automated, unattended disc archiving. It detects media types, clones discs to ISO format using `ddrescue` for maximum data recovery, and intelligently handles large Blu-ray files by splitting them and generating SHA256 checksums.

---

## 🚀 Features

* **Fully Automated:** Continuously monitors your optical drive; just insert a disc and walk away.
* **Intelligent Media Detection:** Automatically adjusts block sizes based on whether a DVD or Blu-ray is detected.
* **Data Recovery Powered:** Uses `ddrescue` to perform multiple passes, ensuring the best possible rip even from slightly damaged media.
* **Smart Splitting:** Automatically splits large Blu-ray images (>25GB) into 4GB chunks for better compatibility with FAT32 systems or cloud storage limits.
* **Integrity Verification:** Generates individual SHA256 checksums for every file or split part produced.
* **Auto-Mount:** Automatically mounts the resulting ISO to your desktop for immediate inspection (for non-split files).
* **Master Logging:** Maintains a `disc_rip_master_log.csv` on your desktop containing timestamps, file sizes, parts count, and checksums.
* **Safety Checks:** Verifies available disk space before starting and prevents filename collisions.

---

## 🛠 Prerequisites

The script runs on Linux (tested on Ubuntu/Debian-based systems). It will attempt to install `gddrescue` automatically if missing.

* **Linux OS**
* **sudo privileges** (for mounting and `ddrescue` operations)
* **Optical Drive** (mapped to `/dev/cdrom`)
* **Required Utilities:** `ddrescue`, `sha256sum`, `blkid`, `eject`.

---

## 📦 Installation & Usage

1. **Clone or Download** the script to your machine.
2. **Make it executable**:
```bash
chmod +x "Ultimate Hands-Free Multi-Disc Ripper with Full SHA256 for Split Blu-rays.sh"

```


3. **Run the script**:
```bash
./"Ultimate Hands-Free Multi-Disc Ripper with Full SHA256 for Split Blu-rays.sh"

```


4. **Insert a disc.** The script will detect it, rip it to your Desktop, log the data, and eject the tray when finished.

---

## 📊 Output Structure

* **ISOs:** Saved directly to your `~/Desktop`.
* **Split Parts:** If a Blu-ray is >25GB, it creates `filename_partaa`, `filename_partab`, etc.
* **Logs:** * Individual `ddrescue` logs for every disc.
* A global `disc_rip_master_log.csv` summarizing all sessions.



---

## ⚙️ Configuration

You can easily modify the following variables at the top of the script:

* `DVD_DEVICE`: The path to your optical drive (default: `/dev/cdrom`).
* `DESKTOP`: The output directory (default: `$HOME/Desktop`).

---

## ⚠️ Important Notes

* **Encrypted Media:** This script is a bit-for-bit copier. It does not natively decrypt CSS (DVD) or AACS (Blu-ray) protection. For commercial movies, ensure you have the necessary decryption libraries (like `libdvdcss`) installed or use this for personal backups and data discs.
* **Storage:** Ensure your destination has enough space; Blu-rays can require up to 50GB (or 100GB for XL layers).

