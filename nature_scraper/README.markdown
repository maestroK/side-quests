Quantum Machine Learning Paper Scraper
Overview
A Jupyter notebook (nature_scraper.ipynb) to scrape recent Quantum Machine Learning (QML) articles from Nature (last 7 days), filter by title and arXiv abstract, and download PDFs from arXiv. Saves metadata (title, date, URL, PDF link) to recent_qml_nature_links.txt.
Features

QML Filter: Targets papers with "quantum" and terms like "machine learning", "qml", "neural network", or "deep learning" in title and arXiv abstract.
arXiv Integration: Queries arXiv API for PDFs using title and abstract.
Output: Saves metadata to recent_qml_nature_links.txt and PDFs to downloads/.
Rate Limiting: 2-second delays to avoid server bans.

Requirements

Python 3.8+
Libraries: requests, beautifulsoup4, jupyter

pip install requests beautifulsoup4 jupyter

Usage

Clone the repository:

git clone https://github.com/maestroK/side-quests.git
cd side-quests/nature_scraper


Run the notebook:

jupyter notebook nature_scraper.ipynb

Execute all cells in Jupyter.

Check outputs:
Metadata: recent_qml_nature_links.txt
PDFs: downloads/



Automation with Cron
Convert the notebook to a Python script for cron jobs:
jupyter nbconvert --to script nature_scraper.ipynb

Automate weekly runs (e.g., Sunday at midnight):
crontab -e

Add (replace with your paths):
0 0 * * 0 /usr/bin/python3 /path/to/side-quests/nature_scraper/nature_scraper.py

Verify Python path with which python3.
Notes

Platform: Tested on macOS (M1 MacBook Pro).
Limitations: arXiv search may miss papers due to title/abstract mismatches. Consider fuzzy matching for improvement.
Maintenance: Update CSS selectors (.c-card, .app-article-list-row__item) if Nature’s page changes.

License
MIT License. See LICENSE.
Contributing
Pull requests welcome. Open an issue for major changes.
