---
title: "The NewsScraper Package "
collection: open access(near future)
type: "R-based"
permalink: /open access/2024-spring-open access-2
venue: "Google News Crawling"
date: 2024-06-24
---

`NewsScraper` is an R package designed to scrape news articles for specified companies within a given date range and save the results to an Excel file.   This package is particularly useful for researchers and analysts who need to gather and analyze news data related to specific companies and topics.

**Features**

- Scrape news articles from Google News.
- Filter news articles based on specified date ranges.
- Search for news articles using customizable keywords with AND/OR logic.
- Save the scraped news data to an Excel file.

**Output**

The scrape_company_news function will generate an Excel file specified by output_file, containing the scraped news articles.  The output file will have the following columns:

- Company. Name: The name of the company.
- Ticker: The ticker symbol of the company.
- Title: The title of the news article.
- Link: The URL link to the news article.
- Publication. Date: The publication date of the news article.

**Main Function Format**

scrape_company_news(
  file_path = "x_x_x.xlsx",
  start_date = "YYYY-MM-DD", 
  end_date = "YYYY-MM-DD",
  keywords = '"keywords1" OR "keywords2" AND "keywords3",
  language = "en",
  country = "US",
  output_file = "All_news.xlsx"
)


**Clarification**
- After testing, this version of the R package has high network and bandwidth requirements, so I'm trying to further optimise the code structure to make it work more consistently.
- Considering that this R package relates to my working project, I can't have open access to this R package until I finish this project.


Information about this R package can be found [here](https://github.com/LINGYUAN1201/genDynamic).
