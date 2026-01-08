# 🎮 Switch NSP Forwarder Builder v1.0.0
### *(by **The Other Side**)*
A simple Windows tool that lets you create custom **NSP forwarders** for:

- Standard **Homebrew NROs**
- **RetroArch ROM forwarders** (boot a ROM directly into a core)

This tool requires **no coding**, **no command line**, and automatically builds proper forwarder NSPs compatible with Atmosphère.

---

# 📦 Included

```
Switch NSP Forwarder/
│
├── switch_forwarder_gui.exe    ← The main program
├── tools/
│   ├── hacbrewpack.exe
│   ├── prod.keys (NOT INCLUDED — user must add)
│   ├── template_forwarder/
│   │     ├── exefs/
│   │     └── control/
│   └── win-x64/
│
└── output/  (created automatically)
```

---

# ⚠️ IMPORTANT — User Must Provide Keys

For legal reasons, **prod.keys or keys.dat is NOT included**.

The user must place their own keys file here:

```
tools/prod.keys
```

OR:

```
tools/keys.dat
```

The tool will automatically detect either one.

---

# 🖥️ System Requirements

- Windows 10 or 11  
- Python **NOT required**  
- Atmosphère CFW  
- RetroArch on SD (if using ROM forwarders)

---

# 🚀 How to Use

## 1. Standard NRO Forwarders

Steps:

1. Open the program  
2. Select **Standard NRO Forwarder** tab  
3. Enter *Title*, *Publisher*, *Title ID*  
4. Set **NRO path on SD** (`sdmc:/switch/...`)  
5. Choose an icon  
6. Click **Build Standard Forwarder NSP**  
7. Install the generated `.nsp` in the output folder

---

## 2. RetroArch ROM Forwarders

Steps:

1. Select **RetroArch ROM Forwarder** tab  
2. Enter Title / Publisher / Title ID  
3. RetroArch NRO path:

```
sdmc:/switch/retroarch_switch.nro
```

4. Core path example:

```
/retroarch/cores/snes9x_libretro_libnx.nro
```

5. ROM path example:

```
/retroarch/downloads/snes/Super Mario World.smc
```

6. Choose icon  
7. Click **Build RetroArch Forwarder NSP**

---

# 🎨 Icon Features

- Drag & drop supported  
- Auto converts any image to **256×256 JPEG**  
- Supports: JPG, PNG, WEBP, BMP, GIF  
- Automatically removes alpha channel (no RGBA errors)

---

# 🌗 Light / Dark Theme

Use the buttons in the top-right corner to switch theme instantly.

---

# 📁 File Locations

Created automatically:

```
output/   → final NSPs  
work/     → temp build files  
```

Placed next to the EXE.

---

# 🔧 Troubleshooting

### **Keys file not found**
Place `prod.keys` or `keys.dat` inside:

```
tools/
```

### **template_forwarder not found**
Make sure this folder exists:

```
tools/template_forwarder/
```

### **Forwarder boots then returns to home**
- Check core path  
- Check ROM path  
- Check RetroArch NRO path  
- Confirm ROM is supported by selected core  

---

# © Credits

- Engine: hacBrewPack  
- Research: RetroArch community  
- GUI & Integration: *The Other Side*
- Omar Carlos for the idea *thanks bro*

---

Enjoy building your own forwarders!
