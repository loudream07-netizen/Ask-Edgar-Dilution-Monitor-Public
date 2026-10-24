# Ask Edgar Dilution Monitor

A desktop research overlay that lets you enter any ticker manually and displays dilution risk data from [Ask Edgar](https://askedgar.io).

Enter a ticker symbol and click **Analyze** (or press Enter) to fetch:

- **Dilution risk ratings** – Overall risk, offering ability, dilution level, frequency, cash need, warrants
- **Float & outstanding shares** – With market cap, sector, and country
- **Recent news & SEC filings** – 8-K, 6-K, and news headlines with clickable links
- **Grok AI summary** – Latest AI-generated analysis
- **Offering ability breakdown** – Shelf capacity, ATM capacity, pending S-1/F-1 registrations
- **In-play dilution** – Active warrants and convertibles near current price, color-coded by risk
- **JMT415 analyst notes** – Recent analyst commentary
- **Management commentary** – From Ask Edgar's dilution analysis

## What It Looks Like

The app runs as a dark-themed, always-on-top overlay panel. Tickers are entered directly in the app; no trading platform needs to be installed or running.

- Risk badges are color-coded: **red** (high), **orange** (medium), **green** (low)
- News items have colored stripes: **cyan** (news), **orange** (8-K/6-K), **purple** (grok)
- Warrants/convertibles highlight **green** if strike/conversion price is at or below current price (in the money), **orange** otherwise
- Pending S-1/F-1 registrations are bolded in red as a warning
- Everything is clickable – badges link to Ask Edgar, news links to source documents

## Compatibility

| Requirement | Details |
|---|---|
| **OS** | Windows |
| **Python** | 3.10+ |
| **Ticker input** | Manual entry in the app |
| **API Access** | [Ask Edgar](https://askedgar.io) API key |

The app no longer detects DAS Trader Pro or thinkorswim windows. You can use it independently and enter ticker symbols yourself.

## Quick Start (No coding experience needed)

> **New to coding?** You can skip all the steps below — just install [Claude Code](https://claude.ai/download), [Cursor](https://cursor.com/), or [Windsurf](https://windsurf.com/) in your code editor, open the project folder, and tell it *"set up and run this app."* It will read this README and handle everything for you.

### 1. Install Python

Download Python from [python.org/downloads](https://www.python.org/downloads/) and install it.

**IMPORTANT:** During installation, check the box that says **"Add Python to PATH"** — this is required.

### 2. Download this app

Click the green **"Code"** button at the top of this page, then click **"Download ZIP"**.

Extract the ZIP file to a folder on your computer (e.g. your Desktop).

### 3. Run the setup

Open the extracted folder and **double-click `setup.bat`**. This will:
- Install the required Python packages
- Create a `.env` file for your API key

### 4. Add your API key

Open the `.env` file (in the same folder) with Notepad and replace `your_api_key_here` with your actual API key:

```
ASKEDGAR_API_KEY=paste_your_key_here
```

**Don't have a key?** Request a free trial at [askedgar.io](https://share-na2.hsforms.com/1mRWaNy8PRFuCZr5YJvjdQQqjkci). One key works for all endpoints.

### 5. Launch the app

**Double-click `run.bat`** to start the overlay.

Enter a ticker in the **TICKER** field, then click **Analyze** or press Enter. The research panels load for that symbol.

To stop the app, just close the overlay window (click the X) or close the command prompt window that opened with it.

---

<details>
<summary><b>Alternative: Setup via command line</b></summary>

```bash
git clone https://github.com/jasontange/Ask-Edgar-Dilution-Monitor-Public.git
cd Ask-Edgar-Dilution-Monitor-Public
pip install -r requirements.txt
cp .env.example .env
# Edit .env with your API key
python das_monitor.py
```

</details>

## Troubleshooting

If you prefer to set things up manually, watch out for these common issues:

- **Python not installed** — If you type `python --version` in your terminal and get an error, you need to install it from [python.org](https://www.python.org/downloads/). Make sure to check **"Add Python to PATH"** during installation.
- **Git not installed** (command line setup only) — You need [Git](https://git-scm.com/) to clone the repo. Downloading the ZIP is not the same thing. If you used the ZIP/`setup.bat` approach above, you don't need Git.
- **Missing dependencies** — After cloning or extracting, run `pip install -r requirements.txt` in the project folder. Even if some packages are already installed on your machine, run it anyway to be safe.
- **`.env` formatting** — Your `.env` file should have your API key with no spaces and no quotes around the value: `ASKEDGAR_API_KEY=ask-live-yourkey`
- **Still stuck?** Don't guess — connect an AI assistant (Claude Code, Cursor, Windsurf) to the project folder and ask it to help. This README has everything it needs to guide you.

## How to Customize (Vibe Coding)

This is a single Python file — no frameworks, no build tools. You can customize it with an AI coding assistant like **Claude Code**, **Cursor**, or **GitHub Copilot** in VS Code.

### Setting up your editor

1. Install [VS Code](https://code.visualstudio.com/) or [Cursor](https://cursor.com/)
2. Open the extracted folder: **File > Open Folder** and select the app folder
3. You should see `das_monitor.py` in the file list on the left — that's the entire app

### Example: Change the window size

Try asking your AI assistant:

> "Make the overlay window wider — change it from 480px to 600px"

It will find this line in `das_monitor.py` and update it:

```python
# Before
self.root.geometry("480x620+50+50")

# After
self.root.geometry("600x620+50+50")
```

To test your change, run the app from the terminal in VS Code (`` Ctrl+` `` to open it):

```bash
python das_monitor.py
```

Or just double-click `run.bat` again.

### Other things you can customize

| What | Where to look | Example prompt for your AI assistant |
|---|---|---|
| **Window size/position** | `geometry("480x620+50+50")` | "Make the overlay 600px wide" |
| **Colors** | Color constants at the top | "Change the background to navy blue" |
| **News count** | `fetch_news_and_grok` | "Show 5 news headlines instead of 2" |

## Tech Stack

- **Python 3.10+** with tkinter (built-in GUI)
- **requests** for API calls
- **python-dotenv** for loading `.env` files

No frameworks, no build tools, no npm. Just one Python file.

## License

MIT – do whatever you want with it.
