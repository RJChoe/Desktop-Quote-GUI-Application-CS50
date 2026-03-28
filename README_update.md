# Quote Generator
#### CS50P Final Project — [Video Demo](<https://www.youtube.com/watch?v=qpzolxYkPAM>)

A Python command-line application that fetches and displays quotes matching a user-supplied keyword. Built with the ZenQuotes API, NLTK for natural language processing, and a JSON caching layer to minimize API calls.

---

## Features

- Interactive shell interface for keyword-based quote search
- Returns a different quote each run for the same keyword
- Validates input as a real English word using NLTK WordNet
- Caches API responses as JSON to reduce redundant network requests

---

## Tech Stack

| Layer | Tool |
|---|---|
| Language | Python 3.11.8 |
| NLP / Validation | NLTK 3.8.1 (WordNet, Punkt tokenizer) |
| Quote Source | ZenQuotes API |
| Testing | pytest 8.1.1 |
| HTTP | requests 2.31.0 |

---

## Installation

> **Prerequisites:** Python 3.11 and `pip` installed on your machine.

### 1. Clone the repository

```bash
git clone https://github.com/RJChoe/Desktop-Quote-GUI-Application-CS50
cd CS50-quote-shell
```

### 2. Create and activate a virtual environment

**Unix / macOS:**
```bash
python -m venv venv
source venv/bin/activate
```

**Windows:**
```bash
python -m venv venv
venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

> The Punkt tokenizer download is handled automatically on first run — no manual setup needed.

---

## Usage

```bash
python quote_shell.py
```

Enter any English keyword when prompted. The app returns a quote containing that word.

**Example:**

```
Enter a keyword: time

"Don't spend time beating on a wall, hoping to transform it into a door."
— Coco Chanel
```

Run it again with the same keyword for a different result:

```
Enter a keyword: time

"Mastery is not a function of genius or talent. It is a function of time and intense focus."
— Robert Greene
```

**Keywords with the most variety:** `man`, `love`, `past`

---

## Input Validation

User input is validated at two levels:

- **Syntax** — must be a text string of more than 2 characters
- **Semantic** — must be a recognized English word (validated via NLTK WordNet)

---

## Design Decisions

### Keyword Search vs. Fixed Categories
Allowing free-text keyword input gives users direct control over the search, making results more personal and specific. The trade-off is a larger validation burden and a narrower pool of matching quotes for uncommon words — a known limitation of the ZenQuotes API's rotating cache model.

### ZenQuotes API + JSON Caching
ZenQuotes returns a small, rotating JSON payload of quotes. Caching this response locally reduces redundant API calls and keeps the app fast, while the rotation ensures variety across sessions.

### NLTK for Word Validation
Rather than maintaining a static word list, NLTK WordNet provides a robust English lexicon for filtering out nonsense input. The Punkt tokenizer is also used to parse quotes for exact keyword matching, reducing false positives.

### Virtual Environment
All dependencies are pinned in `requirements.txt` for a reproducible environment and clean separation from other Python projects.

---

## Running Tests

```bash
pytest test_quote_shell.py
```

---

## Project Structure

```
CS50-quote-shell/
├── quote_shell.py          # Main application
├── test_quote_shell.py     # pytest test suite
├── requirements.txt        # Pinned dependencies
└── README.md
```

---

## Credits & Citations

**WordNet**
Princeton University. "About WordNet." WordNet. Princeton University. 2010.
[wordnet.princeton.edu](https://wordnet.princeton.edu/) — [License](https://wordnet.princeton.edu/license-and-commercial-use)

**NLTK**
Bird, Steven, Edward Loper and Ewan Klein (2009). *Natural Language Processing with Python.* O'Reilly Media Inc.

**ZenQuotes API**
Inspirational quotes provided by [ZenQuotes API](https://zenquotes.io/)

**Python**
Python Software Foundation. [python.org/downloads](https://www.python.org/downloads/)
