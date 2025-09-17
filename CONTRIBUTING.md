# 🤝 Contributing Guidelines

Thank you for considering contributing to this project!  
This scraper is used in live business environments, so contributions that improve stability, accuracy, and usability are especially valuable.

---

## 🧪 How You Can Help

### Testers
- Run the scraper on different ticket ranges and record:
  - Which ticket types succeed or fail (Trade-in, Refurbishment, Sales, etc.)
  - Performance metrics (tickets/hour)
  - Any crashes, freezes, or incorrect data
- Report results in [Issues](../../issues) with details (OS, Python version, Firefox version).

### Bug Reporters
- Open an [Issue](../../issues) with:
  - **Description** of the bug
  - **Steps to reproduce**
  - **Log output or screenshots**
  - **System details** (OS, Python, Firefox, scraper version)

### Developers
1. Fork the repository
2. Create a new branch:
   ```bash
   git checkout -b feature/my-improvement
   ```
3. Make changes with clear commit messages
4. Test your changes on multiple ticket types
5. Submit a Pull Request (PR) with:
   - A description of what you changed
   - Why the change improves the project
   - Any known limitations

---

## 📌 Areas That Need Work
- Improve parsing for:
  - Trade-in tickets
  - Refurbishment tickets
  - Sales tickets
- Smarter **403 Forbidden** handling:
  - Auto cooldowns
  - Resume batches after waiting
- Customer Info Scraper module (notes + history export)
- Hybrid **Requests + BeautifulSoup** mode for faster scraping
- Better **Excel export customization**
- Packaging for Windows/Mac/Linux (PyInstaller one-file builds)

---

## 🛡️ Code of Conduct
- Be respectful and constructive in Issues and PRs  
- Keep commits focused and descriptive  
- Test before submitting changes  
- Remember: This tool is mission-critical for some users’ businesses  

---

## ✅ Quick Contribution Workflow
1. Fork the repo  
2. Create a branch (`feature/my-change`)  
3. Make changes and commit with clear messages  
4. Push to your fork  
5. Open a Pull Request describing your changes  

---

Thank you for helping improve this project! 🚀
