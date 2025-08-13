# RepairQ Ticket Scraper (Tkinter GUI)

This tool automates logging into a RepairQ POS system, navigating through ticket pages, and exporting ticket data into an Excel file (`.xlsx`).  
It uses a Tkinter-based graphical interface, making it easy to use without editing the code.

---

## 🚀 Quick Start (2 Minutes)
1. **Install requirements**:
   ```bash
   pip install selenium openpyxl
   ```
2. **Download Firefox** (if not installed)  
   and **geckodriver** from [here](https://github.com/mozilla/geckodriver/releases).  
   Place `geckodriver.exe` in the same folder as the script.
3. **Run the program**:
   ```bash
   python repairq_gui.py
   ```
4. **Fill in** your:
   - Base URL (e.g., `https://yourshop.repairq.io`)
   - Username & Password
   - Ticket range
   - Paths to Firefox and geckodriver (if needed)
5. **Click “Test Login”** → If successful, **Run Scraper**.  
6. Your Excel file will be saved where you specified.

---

## Features
- ✅ **GUI interface** — No coding knowledge needed  
- ✅ **Login test** button to confirm credentials before scraping  
- ✅ Adjustable **Base URL** for different RepairQ instances  
- ✅ Custom start and end **Ticket IDs**  
- ✅ Export all ticket details to Excel  
- ✅ Optional **headless mode** (no browser window)  
- ✅ Works with your local Firefox install or a custom path

---

## Requirements
- **Python 3.8+**
- **pip**
- **Firefox** browser installed (or portable version)
- **geckodriver** for your OS: [Download here](https://github.com/mozilla/geckodriver/releases)
- Python packages:
  ```bash
  pip install selenium openpyxl
  ```

---

## Setup
1. Download `repairq_gui.py` to a folder.
2. Download **geckodriver** and place it in the same folder as the script (or specify its path in the GUI).
3. (Optional) Download **portable Firefox** if not installed.

---

## Running the Program
From a terminal or command prompt:
```bash
python repairq_gui.py
```

---

## Using the GUI
### Step 1 — Fill out the form:
- **Base URL** — e.g., `https://nextgentech.repairq.io`
- **Username** / **Password** — RepairQ login credentials
- **Start Ticket ID** / **End Ticket ID** — Ticket range to scrape
- **Firefox EXE (optional)** — Leave blank to use system Firefox
- **geckodriver Path** — Path to `geckodriver.exe`
- **Output Excel File** — Path where results will be saved

---

### Step 2 — Optional settings:
- **Run Headless** — Check to run without showing Firefox.

---

### Step 3 — Test Login:
Click **Test Login** to verify:
- The Base URL is reachable
- Credentials are correct  
A popup will confirm success or failure.

---

### Step 4 — Run the scraper:
Click **Run Scraper**:
- Logs in to RepairQ
- Visits each ticket in the specified range
- Extracts:
  - Ticket ID & status
  - Customer ID, name, phone
  - Ticket items (with price, quantity, discount)
  - Device info (name, serial, passcode)
  - Diagnostics
  - Notes (merged into one cell)
  - Created & last updated dates
  - Location
  - Amount paid
- Saves results to Excel

---

### Step 5 — Review the output:
When complete, you’ll see:
```
✅ Done. Saved to: your_output_path.xlsx
```
Open the file in Excel, LibreOffice, or Google Sheets.

---

## Troubleshooting
- **Test Login fails** — Check URL, credentials, Firefox/geckodriver paths.
- **Tickets skipped** — They may not exist or be inaccessible to your account.
- For large ranges, run with headless **off** to watch progress.

---

## License
This project is for **internal use only** within your organization.  
No warranty or guarantee is provided.
