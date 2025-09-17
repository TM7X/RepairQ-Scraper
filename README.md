# 📘 How to Use the RepairQ Parallel Scraper

This guide explains how to install Python and Firefox, set up the environment, and run the scraper.

---

## 1. Install Python
1. Go to [python.org/downloads](https://www.python.org/downloads/).
2. Download **Python 3.11 or newer** for your operating system.
3. During installation, check ✅ **“Add Python to PATH.”**
4. Verify the installation in a terminal/command prompt:
   ```bash
   python --version
   ```
   You should see something like:
   ```
   Python 3.11.7
   ```

---

## 2. Install Firefox
1. Download Firefox from [mozilla.org/firefox](https://www.mozilla.org/firefox/).
2. Install it with default settings.
   - On **Windows**, it usually installs here:
     ```
     C:\Program Files\Mozilla Firefox\firefox.exe
     ```
   - On **macOS**, Firefox is placed in Applications.
   - On **Linux**, install via your package manager (or Snap/Flatpak).

---

## 3. Download the Scraper Files
Place the following two files in the same folder (for example, `C:\Users\YourName\Documents\RepairQScraper`):
- `setupV2.py`
- `repairq_scraperV2.py`

---

## 4. Run the Setup Script
The setup script will:
- Create a local Python virtual environment (`.venv`)
- Install dependencies (`selenium`, `openpyxl`)
- Download and configure **geckodriver**
- Detect Firefox
- Create handy launcher scripts

### On Windows
Open and Run SetupV2.py

### On macOS/Linux
Open a terminal, navigate to the folder, then run:
```bash
python3 setupv2.py
```

This generates:
- `.venv/` (virtual environment folder)
- `geckodriver.exe` (or `geckodriver` on Mac/Linux)
- `run_scraper.bat` (Windows launcher)
- `run_scraper.sh` (Mac/Linux launcher)

---

## 5. Run the Scraper
### On Windows
Run the scraper by double-clicking:
```
repairq_scraperV2.py
```

---

## 6. Configure and Use
- When running, a GUI window will open.
- Change the Base Url to yours.
- Enter Login Credentials (User/Password)
- Enter Starting Ticket Number
- Enter Ending Ticket Number (I recommend working in batches like 1000-2000 tickets at time in case of errors)
- Workers is Default 3 (Increasing the number will increase number of browser windows working but wont increase speed as RepairQ has a rate limit)
- Make sure the script is pointed to your Firefox installation, Geckodriver Location, and where you want the output Excel Sheet located)
- Run Headless allows running the background so you can still use the computer without windows opening and closing.
- Select the data you want scraper (Ticket type, ticket items, etc)
- Click Test Login and make sure you get a message saying "Login Successful"
- If Successful click "Run Scraper"
- The scraper will iterate through tickets and export results to an Excel file (`.xlsx`) in the selected folder.

---

## 7. Troubleshooting
- **Firefox not found**: ensure it’s installed in the default location.  
  If not, edit location on Gui Firefox.exe `browse` and set:
  ```python
  opts.binary_location = r"C:\Path\To\Your\Firefox.exe"
  ```
- **Geckodriver missing**: rerun the setup script (`setupV2.py`).
- **Excel file not created**: check script output and confirm ticket range was set properly.

---

## ✅ Quick Summary
1. Install **Python** and **Firefox**.  
2. Place both scripts (`setup_old_selenium.py` + `repairq_selenium_old.py`) in the same folder.  
3. Run:
   ```bash
   python setup_old_selenium.py
   ```
4. Use:
   - Windows: `run_scraper.bat`
   - macOS/Linux: `./run_scraper.sh`
  
   - ---

---

## ⚠️ Known Errors and Bugs

This scraper is still under development, and some ticket types or scenarios may not be parsed correctly. Please review this list before running large batches.

### Ticket Types
- **Trade-in Tickets**  
  Fields may not map correctly and some values may be missing or placed in the wrong columns.

- **Refurbishment Tickets**  
  Certain device details and notes may fail to scrape as expected.

- **Sales Tickets**  
  Occasionally these do not populate item or pricing data consistently.

---

### HTTP Errors
- **403 Forbidden Errors**  
  - The RepairQ site enforces rate limiting and anti-DDoS measures.  
  - When scraping too quickly or running multiple workers, you may see:
    ```
    selenium.common.exceptions.WebDriverException: Message: 403 Forbidden
    ```
  - If this happens:  
    1. **Stop the current batch**  
    2. Wait **10 minutes** before resuming scraping.  
    3. Reduce workers or increase the delay between requests if errors persist.

---

### Workarounds
- If specific tickets are missing data, check them manually in the RepairQ dashboard.  
- For long runs, schedule scraping in smaller batches to reduce the risk of hitting 403 errors.  
- Keep backups of your Excel output between runs to avoid re-scraping the same ticket ranges.

---

## 🔮 Future Fixes Planned

The following improvements are planned for upcoming versions:

- **Better Handling of Ticket Types**  
  Improve parsing logic for **Trade-in**, **Refurbishment**, and **Sales** tickets so data maps correctly into the Excel output.

- **Smarter 403 Handling**  
  Instead of aborting on repeated 403 errors, the scraper will automatically pause the current batch, wait out the cooldown period, and resume where it left off.

- **Customer Info Scraper (Under Development)**  
  A new module is being built to extract **detailed customer information** alongside tickets.  
  - This will include pulling **customer notes**.  
  - Still in early development and not yet available in the current release.

---

## 🗺️ Roadmap

Here’s a high-level look at the direction of this project:

### v3 (Next Release)
- Integrate **smarter error handling** for 403 rate-limit responses (auto pause + resume).
- Improve parsing for **Trade-in** and **Refurbishment** tickets.
- Introduce a **hybrid mode**: log in once with Selenium, then fetch ticket pages with **Requests + BeautifulSoup** for faster, lighter scraping.
- Improve **Excel output customization** (choose and reorder columns).

### v4
- **Full Customer Info Scraper** release:
  - Export detailed customer records, including **notes, history, and linked tickets**.
  - Merge customer and ticket data into a single Excel workbook.

### Long-Term
- Move toward a **plugin-based system**, where users can enable/disable modules (Ticket Scraper, Customer Scraper, Inventory Exporter, etc.).
- Optional **database export** (SQLite or MySQL) in addition to Excel.
- Add **cross-platform packaging** (one-click installer with bundled dependencies).

---

## 🤝 Contributing

We welcome contributions to improve this scraper. Whether you’re a **tester, bug reporter, or developer**, here’s how you can help:

### 🧪 Testers
- Run the scraper on different ranges of tickets and report:
  - Which ticket types (Trade-in, Refurbishment, Sales, etc.) are missing data
  - Any unexpected behavior or crashes
  - Performance results (tickets/hour, error rates)

### 🐞 Bug Reports
- Open an [Issue](../../issues) on GitHub with:
  - A clear description of the bug
  - Steps to reproduce the issue
  - Relevant log output or error messages
  - Your environment details (OS, Python version, Firefox version)

### 👨‍💻 Developers
- Fork the repo and create a feature branch:
  ```bash
  git checkout -b feature/my-improvement
  ```
- Make your changes with clear commit messages
- Ensure code is formatted (PEP8) and tested
- Submit a Pull Request (PR) describing:
  - What you changed
  - Why the change is useful
  - Any known limitations

### 📌 Areas Needing Help
- **Improved parsing** for Trade-in, Refurbishment, and Sales tickets
- **403 error handling** with smarter retry and cooldown logic
- **Customer Info Scraper module** (notes + history export)
- **Requests + BeautifulSoup hybrid mode** for faster scraping
- **Cross-platform packaging** (PyInstaller, single-exe builds)

---

## 🛡️ Code of Conduct
Please be respectful and constructive in discussions, Issues, and PRs.  
This project is used in real business workflows, so reliability and clarity are top priorities.


