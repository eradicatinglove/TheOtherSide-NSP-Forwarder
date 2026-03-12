
![Capture](https://github.com/user-attachments/assets/0563d8ac-492c-4a97-8f09-0b692ae7be61)


![Capture](https://github.com/user-attachments/assets/9ddfd69b-a4ec-4fc7-a6e5-1b23f5f9b02d)


# The Other Side NSP Forwarder v5.0.0

This tool builds Nintendo Switch **NSP forwarders** for:
- Standard Homebrew `.nro` applications
- RetroArch cores + ROM forwarders

It supports **custom icons**, **startup logos**, and **startup animations**

---

## ⚠️ IMPORTANT LEGAL NOTICE

This tool **does NOT include Nintendo encryption keys**.

You **MUST provide your own keys** to use this software.

Sharing, redistributing, or downloading keys is **NOT supported** and may be illegal in your region.

---

## Requirements

- Windows 10 / 11
- Python 3.10+ *(only if running `.py` instead of `.exe`)*

---

## Required Folder Structure

```
Switch-NSP-Forwarder/
 ├─ Switch-NSP-Forwarder.exe   (or .py)
 ├─ tools/
 │   ├─ hacbrewpack.exe
 │   ├─ prod.keys   OR  keys.dat   ← REQUIRED (user must provide)
 │   ├─ app.ico
 │   └─ template_forwarder/
 │       ├─ control/
 │       ├─ exefs/
 │       ├─ romfs/
 │       └─ logo/
 ├─ work/        (auto-created)
 └─ output/      (auto-created)
```

> **Note:** ImageMagick is no longer required. All GIF conversion is now handled automatically inside the program.

---

### 🔑 Keys File (REQUIRED)

You **must** provide **one** of the following inside the `tools/` folder:

- `prod.keys` **(preferred)**
- `keys.dat`

The program will:
1. Look for `tools/prod.keys`
2. If not found, fall back to `tools/keys.dat`

If neither file exists, the build **will fail**.

---

## How to Use

1. Launch `Switch-NSP-Forwarder.exe`
2. Choose a tab:
   - **Standard NRO Forwarder**
   - **RetroArch ROM Forwarder**
3. Fill in:
   - Title
   - Publisher
   - Title ID (or click **Random**)
4. Choose your assets:
   - **Icon** (required)
   - **Startup Logo PNG** (optional)
   - **Startup Animation GIF** (optional)
5. Click **Build Forwarder NSP**
6. Your NSP will appear in the `output/` folder

---

## Icon (Home Menu Icon)

- Any image format accepted (PNG, JPG, BMP, etc.)
- Automatically converted to:
  - **256×256**
  - **JPEG**
  - RGB color
- Drag & drop supported

---

## Startup Logo (NintendoLogo.png)

⚠️ **VERY STRICT REQUIREMENTS**

You must provide a **ready-to-use PNG**.

### REQUIRED:
- **Format:** PNG
- **Resolution:** **256×128**
- **Color:** RGB
- **Transparency:** Not recommended

### NOTES:
- Large images will crash the NSP
- High-resolution artwork must be resized manually before loading
- The tool does **NOT auto-resize** startup logos

✅ Best practice: design directly at **256×128**

---

## Startup Animation GIF (StartupMovie.gif)

You can add a custom animation that plays on the splash screen when your NSP launches.

The program handles **ALL conversion automatically** — no ImageMagick, no manual resizing needed.

### How to create your GIF:
1. Go to [ezgif.com](https://ezgif.com) → **Video to GIF**
2. Upload your video
3. Click **Convert to GIF** and download it
4. ⚠️ **Do NOT resize the GIF on ezgif** — let the program handle it

Your GIF can be **any size, any aspect ratio, from any source**.

### Two animation modes:

| Button | Description |
|--------|-------------|
| **Startup GIF - Crop to Fill** | Fills the entire 256x80 area, edges may be slightly cropped. Best for square or centered animations. |
| **Startup GIF - Fit Whole Image** | Shows the complete image, black bars fill remaining space. Nothing gets cropped. |

### What the program fixes automatically:
- ✅ Size — resized to 256×80
- ✅ Duration — trimmed to fit Switch boot window
- ✅ Frame timing — normalized for Switch compatibility
- ✅ Colors — reduced to Switch-safe palette
- ✅ Transparency — composited onto black background
- ✅ Embedded watermarks/comments — stripped

---

## RetroArch ROM Forwarder

Fill in the same fields as Standard, plus:

- **RetroArch Core path on SD** — path to the `.nro` core file
  ```
  /retroarch/cores/snes9x_libretro_libnx.nro
  ```
- **ROM on SD** — path to your ROM file
  ```
  /retroarch/downloads/snes/MyGame.sfc
  ```

### Supported ROM types:
`.sfc` `.smc` `.gba` `.zip` `.nes` `.md` `.cue/.bin` `.z64` `.v64` and more

### Supported ROM folders:
`/roms/` `/retroarch/downloads/` `/games/` `/media/` `/anything/`

---

## Common Problems & Fixes

### ❌ NSP crashes on boot
- Startup logo PNG is not exactly 256×128
- PNG is too large or complex
- PNG contains transparency or metadata

### ❌ Startup animation not showing on Switch
- Make sure you converted your video to GIF on ezgif first
- Do **not** resize the GIF on ezgif — load it straight into the program
- Try **Fit Whole Image** if **Crop to Fill** doesn't work

### ❌ Build fails — keys not found
- Make sure `prod.keys` or `keys.dat` is inside the `tools/` folder
- Keys must match your Switch firmware version

### ❌ Build fails — hacbrewpack not found
- Make sure `hacbrewpack.exe` is inside the `tools/` folder

---

## Building EXE (Developer)

Install dependencies:
```
pip install pillow pyside6
```

Build single EXE:
```
pyinstaller --clean --onefile --windowed ^
  --name Switch-NSP-Forwarder ^
  --icon tools/app.ico ^
  switch_forwarder_gui.py
```

Output will be in the `dist/` folder.

---

## Credits

- hacbrewpack
- Atmosphère
- Pillow / PySide6

---

## Disclaimer

This software is for **homebrew and educational use only**.
You are responsible for complying with local laws and Nintendo's terms of service.




