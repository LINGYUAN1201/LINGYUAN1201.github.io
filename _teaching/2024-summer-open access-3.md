---
title: "News Scraper Tool (`train.exe`) User Guide"
collection: open access
type: "Python-based"
permalink: /open access/22024-summer-open access-3
venue: "Get news"
date: 2024-08-19
---

## 1. Introduction

This project introduces a Python-based news scraper tool that leverages PyQt5 for the graphical user interface (GUI) and utilizes Selenium and BeautifulSoup for scraping financial news from websites such as Yahoo Finance. The tool allows users to scrape news for individual or multiple stock tickers and export the results in CSV, JSON, or TXT formats. Packaged into a standalone Windows executable file (`.exe`), the tool can be run without requiring a Python environment.

## 2. Features

- **Single Ticker Scraping:** Enables users to input a single stock ticker and retrieve related financial news.
- **Batch Ticker Scraping:** Users can load multiple tickers from files (Excel, CSV, or TXT) and perform batch scraping.
- **Multithreading Support:** For batch scraping, users can select the number of threads (1–8) to improve scraping speed and performance.
- **Real-Time Progress Bar:** A progress bar provides real-time updates, reflecting the ongoing scraping process.
- **Scraping Result Display:** The scraped news is displayed in JSON format within the GUI.
- **Export Data:** Users can export scraping results in CSV, JSON, or TXT formats.
- **Periodic Pausing Mechanism:** In batch mode, the tool pauses for 1-2 minutes after scraping 100 tickers to prevent server overload and avoid blocking.

## 3. System Requirements

- **Operating System:** Windows (packaged as an `.exe` file).
- **Recommended Hardware:** Multicore CPU and at least 8GB of RAM for optimal performance, particularly when using multithreading in batch mode.
- **Internet Connection:** A stable connection is required since Selenium is used to fetch live data from the web.

## 4. Prerequisites for Running

- No installation is necessary. Download the `train.exe` file and place it in an accessible directory, such as the Desktop or Documents folder.
- Ensure that ChromeDriver is installed and matches the version of the Chrome browser installed on your system (applicable only when using the source code version).

## 5. Running the Program

To start the program:

1. Double-click the `train.exe` file.
2. The graphical user interface (GUI) will launch, offering multiple options for scraping news data.

## 6. Usage Guide

### Single Ticker Mode

1. Select the "Single Ticker" mode.
2. Enter a stock ticker (e.g., AAPL or TSLA) in the input field.
3. Set the number of refreshes (default: 3).
4. Click the "Start Scraping" button to initiate the scraping process.
5. The results will be displayed in JSON format within the program window.

### Batch Ticker Mode

1. Select the "Batch Ticker" mode.
2. Click the "Browse" button to upload a file containing multiple tickers (supported formats: Excel, CSV, TXT).
3. Set the number of refreshes (default: 3).
4. Select the number of threads (1–8) to accelerate the batch scraping process.
5. Click the "Start Scraping" button to scrape news for all tickers listed in the file.
6. The progress bar will update in real-time, and the results will be displayed in JSON format within the program window.

## 7. Exporting Scraping Results

1. Once the scraping is complete, click the "Save Results" button.
2. Choose the desired export file format (CSV, JSON, or TXT).
3. Select the save location, and the results will be exported in the chosen format.

## 8. Interrupting or Canceling Tasks

- **Interrupt Task:** To temporarily pause the ongoing scraping task, click the "Interrupt Task" button. The task will resume upon command.
- **Cancel Task:** To stop the scraping task entirely, click the "Cancel Task" button. This will immediately halt all scraping operations.

## 9. Troubleshooting and Notes

### a. File Input Format

- **Supported formats:** Excel (.xlsx), CSV (.csv), and TXT (.txt).
- The file should contain a column labeled "ticker" (in Excel/CSV) or individual tickers listed on separate lines (in TXT).

### b. Network Requirements

- A stable internet connection is essential for proper functionality. An unstable connection may result in scraping failures for some tickers, with error messages provided in such cases.

### c. ChromeDriver Compatibility

- Ensure that your ChromeDriver version matches your installed Chrome browser version. If mismatched, download the correct ChromeDriver version from the [official ChromeDriver website](https://sites.google.com/chromium.org/driver/).

### d. Multithreading Considerations

- When using batch mode, selecting a higher number of threads can significantly improve scraping speed, but it will also increase system resource consumption.
- For most systems, choosing between 4–8 threads will offer an optimal balance between speed and resource usage.

### e. Data Export

- The tool supports exporting scraping results in CSV, JSON, and TXT formats. Ensure that the correct save path and file format are selected during export.

---

With these instructions, users can effectively operate the `train.exe` news scraper tool and customize their scraping experience based on individual or batch ticker preferences. Proper system configuration and file formatting will ensure smooth operation and high-performance results.


**You can download it here**
