# ELEVATE_LABS_PYTHON-TASK3-
Web Scraper for News Headlines
Objective
Scrape top news headlines from a public website and save them into a text file.
Tools Used
Python, requests, BeautifulSoup (bs4), Text File Output
Key Concepts
HTTP Requests, Web Scraping, HTML Parsing, File Handling
Features
- Fetch HTML from website
- Parse / tags for headlines
- Save headlines to .txt file
- Error handling
- Easy to customize
How to Run
1. Install dependencies:
pip install requests
pip install beautifulsoup4
2. Run script:
python news_scraper.py
Usage
Automate collection of latest headlines for analysis, study, or personal use.
Folder Structure
project/
■■■ news_scraper.py
■■■ headlines.txt
■■■ README.md
Code
import requests
from bs4 import BeautifulSoup
def scrape_headlines(url, output_file):
try:
response = requests.get(url)
response.raise_for_status()
html_content = response.text
soup = BeautifulSoup(html_content, "html.parser")
headlines = [h2.get_text(strip=True) for h2 in soup.find_all("h2")]
if not headlines:
headlines = [h3.get_text(strip=True) for h3 in soup.find_all("h3")]
with open(output_file, "w", encoding="utf-8") as file:
for line in headlines:
file.write(line + "\n")
print(f"Headlines saved to {output_file}")
except Exception as e:
print("Error:", e)
news_url = "https://www.bbc.com/news"
output_file = "headlines.txt"
scrape_headlines(news_url, output_file)
Sample Output
India announces new tech policy
Global markets fall amid recession fears
AI becomes part of daily life...
Author
Tasmiya Shaik
Email: tasmiyashaik37@gmail.com
Database Used: Text file storage (headlines.txt)
