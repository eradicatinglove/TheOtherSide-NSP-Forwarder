# Switch NSP Forwarder Builder

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
- Python **3.10+** (only if running the `.py` version)
- Required Python packages:
  ```bash
  pip install pillow pyside6
  ```

---

## Required Folder Structure

```
Switch-NSP-Forwarder/
 ├─ Switch-NSP-Forwarder.exe   (or .py)
 ├─ tools/
 │   ├─ hacbrewpack.exe
 │   ├─ prod.keys   OR  keys.dat   ← REQUIRED (user must provide)
 │   ├─ ImageMagick/            (recommended)
 │   │   └─ magick.exe
 │   └─ template_forwarder/
 │       ├─ control/
 │       ├─ exefs/
 │       ├─ romfs/
 │       └─ logo/
 ├─ work/        (auto-created)
 └─ output/      (auto-created)
```

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
   - **Startup Logo (PNG)** (optional)
   - **Startup Animation GIF** (optional)
5. Click **Build Forwarder NSP**
6. Your NSP will appear in the `output/` folder

---

## Icon (Home Menu Icon)

- Any image format accepted
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
- High-resolution artwork must be resized manually
- The tool does **NOT auto-resize** startup logos

✅ Best practice: design directly at **256×128**

---

## Startup Animation GIF (StartupMovie.gif)

### With ImageMagick (RECOMMENDED)
- Any GIF can be used
- Automatically converted to Switch-safe specs:
  - 256×80
  - No alpha
  - Safe frame timing
  - Loop enabled

### Without ImageMagick
- Only very simple GIFs may work
- Complex GIFs may fail or crash

---

## Common Problems & Fixes

### ❌ NSP crashes on boot
- Startup logo PNG is not 256×128
- PNG is too large or complex
- PNG contains transparency or metadata

### ❌ GIF works on website but not locally
- ImageMagick missing from `tools/`
- GIF has unusual frame timing

---

## Recommended Workflow

1. Create startup logo at **256×128 PNG**
2. Use any GIF you like (let ImageMagick convert it)
3. Test on real hardware
4. Ship your NSP

---

## Credits

- hacbrewpack
- Atmosphère
- ImageMagick
- Pillow / PySide6

---

## Disclaimer

This software is for **homebrew and educational use only**.
You are responsible for complying with local laws and Nintendo’s terms.
