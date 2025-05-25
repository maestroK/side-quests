# Quantum Machine Learning Paper Scraper

## Overview
A Jupyter notebook (`nature_scraper.ipynb`) to scrape recent **Quantum Machine Learning (QML)** articles from [Nature](https://www.nature.com) (last 7 days), filter by title and arXiv abstract, and download PDFs from [arXiv](https://arxiv.org). Saves metadata (title, date, URL, PDF link) to `recent_qml_nature_links.txt`.

## Features
- **QML Filter**: Targets papers with "quantum" and terms like "machine learning", "qml", "neural network", or "deep learning" in title and arXiv abstract.
- **arXiv Integration**: Queries arXiv API for PDFs using title and abstract.
- **Output**: Saves metadata to `recent_qml_nature_links.txt` and PDFs to `downloads/`.
- **Rate Limiting**: 2-second delays to avoid server bans.

## Requirements
- Python 3.8+
- Libraries: `requests`, `beautifulsoup4`, `jupyter`
```bash
pip install requests beautifulsoup4 jupyter
```

## Usage
1. Clone the repository:
```bash
git clone https://github.com/maestroK/side-quests.git
cd side-quests/nature_scraper
```
2. Run the notebook:
```bash
jupyter notebook nature_scraper.ipynb
```
Execute all cells in Jupyter.

3. Check outputs:
   - Metadata: `recent_qml_nature_links.txt`
   - PDFs: `downloads/`

## Automation with Cron
Convert the notebook to a Python script for cron jobs:
```bash
jupyter nbconvert --to script nature_scraper.ipynb
```
Automate weekly runs (e.g., Sunday at midnight):
```bash
crontab -e
```
Add (replace with your paths):
```bash
0 0 * * 0 /usr/bin/python3 /path/to/side-quests/nature_scraper/nature_scraper.py
```
Verify Python path with `which python3`.

## Notes
- **Platform**: Tested on macOS (M1 MacBook Pro).
- **Limitations**: arXiv search may miss papers due to title/abstract mismatches. Consider fuzzy matching for improvement.
- **Maintenance**: Update CSS selectors (`.c-card`, `.app-article-list-row__item`) if Nature’s page changes.

## License
MIT License. See [LICENSE](LICENSE).

## Contributing
Pull requests welcome. Open an issue for major changes.