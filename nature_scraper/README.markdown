# Quantum Machine Learning Paper Scraper

## Overview
This Python script scrapes recent **Quantum Machine Learning (QML)** articles from [Nature](https://www.nature.com) published within the last 7 days. It filters for QML-specific papers, downloads their PDF versions from [arXiv](https://arxiv.org) if available, and saves metadata (title, date, URL, PDF link) to a text file.

## Features
- **QML Filter**: Targets papers with "quantum" and terms like "machine learning", "qml", "neural network", or "deep learning" in the title.
- **arXiv Integration**: Queries arXiv's API to find and download PDF versions.
- **Output**: Saves article metadata to `recent_qml_nature_links.txt` and PDFs to a `downloads` folder.
- **Rate Limiting**: Includes 2-second delays to respect server limits.

## Requirements
- Python 3.8+
- Libraries: `requests`, `beautifulsoup4`
```bash
pip install requests beautifulsoup4
```

## Usage
1. Clone the repository:
```bash
git clone [your-repo-url]
cd [repo-name]
```
2. Run the script:
```bash
python scrape_qml_nature.py
```
3. Check outputs:
   - Metadata: `recent_qml_nature_links.txt`
   - PDFs: `downloads/` folder

## Automation with Cron
Automate weekly runs using a cron job (e.g., every Sunday at midnight):
```bash
crontab -e
```
Add:
```bash
0 0 * * 0 /path/to/python3 /path/to/scrape_qml_nature.py
```

## Notes
- **Platform**: Tested on macOS (M1 MacBook Pro).
- **Limitations**: arXiv search may miss papers if titles differ slightly. Consider adding fuzzy matching for robustness.
- **Maintenance**: Nature’s page structure may change; update CSS selectors (`.c-card`, `.app-article-list-row__item`) if needed.

## License
MIT License. See [LICENSE](LICENSE) for details.

## Contributing
Pull requests welcome! For major changes, open an issue first.