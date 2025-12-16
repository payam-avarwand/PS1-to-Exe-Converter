# PS1 to Exe Converter

**PS1 to Exe Converter** is a modern, user-friendly graphical utility that converts PowerShell scripts (`.ps1`) into standalone Windows executable (`.exe`) files with full metadata support. The tool features a sleek dark-themed interface and uses `ps2exe` combined with `rcedit` to ensure all EXE properties are properly set.

---

## ✨ Features

### 🎨 Modern Interface
- **Dark-themed GUI** - Professional, easy-on-the-eyes interface
- **Single-window design** - All options visible at once, no multiple dialogs
- **Real-time progress tracking** - Visual progress bar with status updates
- **Intuitive controls** - Browse buttons for file selection, clear labels for all fields

### 📋 Complete Metadata Support
- **Product Name** - Set via Internal Name field
- **Product Version** - Automatically uses first 2 version parts (e.g., "1.0" from "1.0.0.0")
- **File Version** - Full 4-part version number (e.g., "1.0.0.0")
- **File Description** - Custom description for your executable
- **Company Name** - Your company or organization name
- **Copyright** - Automatically formatted (e.g., "© Your Company")
- **Custom Icon** - Use your own `.ico` file

### ⚙️ Advanced Options
- **Admin Permission Control** - Choose whether the EXE requires administrator privileges
  - Not Required (default) - Runs as normal user
  - Required - Requests UAC elevation
- **Automatic metadata injection** - Uses `rcedit` to set all EXE properties that `ps2exe` doesn't support
- **Output naming** - Automatically generates filename: `[InternalName] [ProductVersion] - portable.exe`

### 🛡️ Built-in Safeguards
- **PowerShell Core detection** - Prevents running under incompatible PowerShell versions
- **Input validation** - Ensures all required fields are filled correctly
- **File existence checks** - Verifies files exist before processing
- **Error handling** - Clear error messages if something goes wrong

---

## 🪟 How to Use

### Quick Start
1. **Download** the latest `PS1 to Exe Converter.exe` from the [Releases](https://github.com/payam-avarwand/PS1-to-Exe-Converter/releases) section
2. **Double-click** the `.exe` file to launch the application
3. **Fill in the form fields:**

   | Field | Description | Required |
   |-------|-------------|----------|
   | **PowerShell Script** | Your `.ps1` file to convert | ✅ Yes |
   | **Icon File** | Custom `.ico` file for the executable | ✅ Yes |
   | **Output Directory** | Where to save the generated `.exe` | ✅ Yes |
   | **Internal Name** | Product name (used in EXE properties) | ✅ Yes |
   | **Version** | Full version number (format: 0.0.0.0) | ✅ Yes |
   | **File Description** | Description shown in EXE details | ⚪ Optional |
   | **Company Name** | Your company/organization name | ✅ Yes |
   | **Admin Permission** | Whether EXE requires admin rights | ✅ Yes (default: Not Required) |

4. **Click "Convert to EXE"** - The tool will:
   - Install/import `ps2exe` module if needed
   - Download `rcedit` tool (first time only, ~1MB)
   - Compile your script with `ps2exe`
   - Inject extended metadata with `rcedit`
   - Show success message with all set properties

5. **Done!** Your executable will be saved with the filename: `[InternalName] [ProductVersion] - portable.exe`

### Example
If you enter:
- Internal Name: `MyScript`
- Version: `1.2.3.4`
- Company: `Acme Corp`

The output will be: `MyScript 1.2 - portable.exe`

With EXE properties:
- Product Name: `MyScript`
- Product Version: `1.2`
- File Version: `1.2.3.4`
- Company: `Acme Corp`
- Copyright: `© Acme Corp`

---

## 🔧 Technical Details

### How It Works
1. **ps2exe Module** - Creates the base executable with core properties (version, copyright, icon, admin flag)
2. **rcedit Tool** - Post-processes the EXE to add extended metadata (product name, product version, file description, company name)

### System Requirements
- **Windows** operating system
- **Windows PowerShell** (not PowerShell Core)
- **Internet connection** (first run only, to download `ps2exe` module and `rcedit` tool)

### Output Files
- Generated executables are **portable** - can run without installing PowerShell scripts
- Executables wrap the `.ps1` script with a launcher
- No full PowerShell runtime is embedded

---

## 💡 Notes

### Metadata Handling
- The tool automatically handles the limitation that `ps2exe` doesn't support all metadata parameters
- `rcedit` is downloaded once to `%TEMP%` folder and reused for future conversions
- All EXE properties are properly set without manual post-processing

### Version Numbering
- **File Version**: Uses all 4 parts you enter (e.g., `1.2.3.4`)
- **Product Version**: Automatically uses first 2 parts (e.g., `1.2`)
- This follows Windows versioning best practices

### Admin Permissions
- Selecting "Not Required" creates a standard executable
- Selecting "Required" embeds a UAC manifest that requests elevation
- You can change this setting after creation using manifest tools

---

## 🎯 Troubleshooting

### "This script must run in Windows PowerShell"
- Make sure you're using **Windows PowerShell**, not PowerShell Core (v6+)
- Right-click the `.ps1` file → Run with PowerShell (not pwsh)

### "Failed to download rcedit"
- Check your internet connection
- Verify that `https://github.com` is accessible
- The tool will still work with basic metadata if rcedit download fails

### Missing Metadata in Generated EXE
- Make sure you filled in all required fields
- Check the success message - it shows which metadata was set
- If rcedit fails, you can manually edit with Resource Hacker

---

## 📄 License

This software is provided **free of charge** for both personal and commercial use.  
Please read the full [End User License Agreement (EULA)](#end-user-license-agreement-eula) below.

---

## END USER LICENSE AGREEMENT (EULA)

This software, titled **"PS1 to Exe Converter"**, is developed and provided by **Payam Avarwand**, and is distributed free of charge for both personal and commercial use.

By installing, copying, or using this software, you agree to the following terms:

### 1. LICENSE GRANT
You are hereby granted a non-exclusive, non-transferable license to install and use this software on your personal or business devices.

### 2. RESTRICTIONS
- You may not reverse engineer, decompile, disassemble, or alter any part of this software
- You may not redistribute, sublicense, rent, lease, or sell the software or any of its components
- You may not represent this software as your own or claim any ownership of it
- You may not use this software for unlawful, malicious, or harmful purposes

### 3. OWNERSHIP
All rights, title, and intellectual property associated with this software remain exclusively with **Payam Avarwand**.

### 4. DISCLAIMER OF WARRANTY
This software is provided "AS IS", without warranties of any kind, express or implied, including but not limited to warranties of merchantability or fitness for a particular purpose.

Under no circumstances shall the author be held liable for any damages or losses resulting from the use or inability to use this software.

### 5. TERMINATION
This license shall terminate automatically if you fail to comply with any of the terms in this agreement. Upon termination, you must cease all use of the software and destroy all copies.

---

## 📸 Screenshots

*The tool features a modern dark-themed interface with all conversion options in a single window, making the process quick and intuitive.*

---

## 🔄 Version History

### v1.0.2.57 (Current)
- ✨ Complete GUI redesign with dark theme
- ✨ Single-window interface with all options
- ✨ Added Internal Name field (Product Name)
- ✨ Added File Description field
- ✨ Added Company Name field
- ✨ Added Admin Permission selector
- ✨ Progress bar with real-time status updates
- ✨ Automatic metadata injection via rcedit
- ✨ Product Version (2-part) vs File Version (4-part)
- ✨ Success/failure popup notifications
- ✨ Exit button for easy closing
- 🔧 Improved error handling and validation

---

## 🙋‍♂️ Contact & Support

For feedback, suggestions, bug reports, or questions:

📧 **Email:** [payam_avar@yahoo.com](mailto:payam_avar@yahoo.com)  
👤 **Developer:** Payam Avarwand

---

## ⭐ Show Your Support

If you find this tool useful, please:
- ⭐ **Star this repository** on GitHub
- 🐛 **Report bugs** via Issues
- 💡 **Suggest features** you'd like to see
- 📢 **Share** with others who might benefit

---

© 2025 **Payam Avarwand**. All rights reserved.