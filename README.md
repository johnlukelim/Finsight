# Finsight - Equity Research, Simplified 
Team: John Luke Lim Kang & Jermaine  Khor | Orbital 2026 | Apollo 11 | Team 7666
Proposed level of achievement: Apollo 11

# Motivation behind the project
Investors and students in Singapore face a fragmented research experience. To screen stocks by fundamental metrics, view price history and assess financial health, a student analyst has to jump between multiple platforms. Most of which are either paywalled, US-centric or poorly suited to SGX-listed equities. This process has too many hoops, which unnecessarily complicates investing.

Professional tools like Bloomberg terminals and FactSet are inaccessible to most undergraduates. Free alternatives like Yahoo Finance lack the clean, focused interface that a student analyst actually needs. This fragmentation is a real barrier to making informed decisions during investment.

FinSight is built to close that gap, and our goal is a simple unified platform that brings together stock screening, fundamental data, price history, and a quantitative financial health indicator. This allows users, specifically student analysts, to develop rigorous, data-driven approaches to equity research without needing access to professional or pay-walled tools. 

# Aim
FinSight is a web application for students to research stocks listed on the Singapore Exchange (SGX) and US markets. Users can search for stocks, view clean price charts, and use a colour-coded Financial Health Score to assess whether a company is financially stable. Logged-in users can also maintain a personal watchlist to track stocks they are interested in.

# Features

- Stock Screener | As a beginner retail investor, I want to filter SGX and US-listed stocks by exchange, sector and market capitalisation so that I can identify companies that match my investment criteria without switching between multiple platforms. Data is fetched live via the yfinance API. This is the primary entry point for users who want to discover stocks matching specific criteria.
  
- Stock Detail Page | Each stock has a dedicated page showing its current price, price to earnings ratio, earnings per share (EPS), market cap, dividend yield, and 52-week high and low. Every metric has an explanation, making the platform accessible to beginners. Data will be fetched in real time via yfinance (Yahoo! Finance API)
  
- Personal Watchlist | Authenticated users can save stocks to a personal watchlist, add annotations and remove stocks. Watchlist data is stored in a database.

- Financial Health Score | A colour-coded risk indicator (Low, Medium and High) calculated from three financial ratios: debt-to-equity, current ratio and interest coverage ratio. The ratios are combined into a colour-coded Financial Health Score that helps users quickly identify potentially risky companies.

# Extension Features 

- Interactive Price Charts | Historical closing prices rendered using Chart.js over 1M, 3M and 1Y windows, where users are given the option to toggle between them.

- Stock search | A search bar that suggests stock tickers and company names, using live data

- Watchlist CSV Export | Logged-in users can download their watchlist as a CSV file for use in Excel and other tools.

# User Stories (potential use cases)
- As a beginner retail investor, I want to filter SGX and US-listed stocks by exchange, sector and market capitalisation so that I can narrow down my options without switching between multiple platforms.
  
- As a student analyst, I want to avoid financially distressed companies. I want to view a colour-coded financial health score for easy decision-making and to save time so that I can quickly assess risk before doing deeper research.

- As a user tracking multiple stocks who wants to stay organised, I want to create a personal account and save stocks to a watchlist so that I can efficiently check through my stock list.

- As a student learning about price movements, I want to view interactive historical price charts over different timeframes so that I can understand how a stock has performed over time.

# System Design

Finsight follows a standard three-tier web application architecture. The presentation layer consists of Jinja2 HTML templates rendered by Flask, with Chart.js handling interactive price charts on the client side. The application layer is built entirely in Python for simplicity using Flask, which handles all routing, logic and calculations.

The data layer consists of a SQLite database for storing user accounts and watchlists, and the yfinance API for fetching live and historical market data.

When a user visits a stock page, the browser first sends a GET request to the stock route. Flask matches the URL and calls the route function. The function fetches live data from yfinance using the ticker symbol. Relevant fields are extracted from the response dictionary using .get(). The Financial Health Score is computed from the ratio data. The score will then be displayed to the user. Flask passes all values to the stock template via render_template. Jinja2 then fills the placeholders and returns the finished HTML to the browser. 

The current database schema for Milestone 1 contains one table:

User table: id (int, primary key), username (txt, unique, and not null), password_hash (text, not null)

The database will have a Watchlist table added with the following columns: id (int, primary key), user_id (int, foreign key referencing user), ticker (txt, not null), note (txt).

# Tech Stack

Python 3 is the primary language for all backend logic, data processing and calculations, Flask is used as the web framework due to its lightweight nature, as FinSight does not require the full feature set of something like Django, and Flask's simplicity made it appropriate for myself and Jermaine as we are learning web development from scratch. Jinja 2 is Flask's built-in templating engine and allows Python variables to be rendered directly in HTML without needing a separate frontend framework. SQLite via Flask-SQLAlchemy provides the relational database layer. SQLite requires no separate database server, which makes local development and deployment straightforward. yfinance is an open source Python library that fetches live and historical data from Yahoo Finance, providing coverage of both SGX-listed and US-listed equities. Flask-Login handles user session management, login, logout and route protection. Chart.js is a JavaScript library for rendering interactive price charts entirely in the browser. Render is the cloud platform used for deployment, chosen for its free tier which is sufficient for Orbital evaluation, though we are open for changes whenever necessary.

# Software Engineering Practices

All development is managed on GitHub using a feature-branch workflow. The main branch contains only stable reviewed code. Features are developed on dedicated branches named descriptively and merged into a dev branch via pull request before being pushed to the main branch. This ensures that dysfunctional code and bugs never reach the stable branch and gives both Jermaine and I a chance to review each other's work before merging. 

Every feature and bug is tracked as a GitHub Issue with appropriate labels including feature, bug, documentation, backend, frontend, database and testing. Each issue is assigned to a team member and attached to the relevant Orbital milestone. Commit messages follow a consistent format describing what changed and why.

Backend logic is kept separate from frontend rendering. Route functions in app.py handle request logic and pass clean data to templates. Financial scoring logic will be extracted into a separate module. Database models are defined in models.py separately from application logic. Variables, functions and routes are named descriptively and inline comments are added, particularly in the financial health scoring calculation.

# Development Plan

Milestone 1 (by 1 June): Flask backend integrated with yfinance fetching and displaying live data for a single stock ticker. Basic stock detail page rendering real-time price and fundamental data. Working SQLite database storing user accounts. User registration and login with password hashing. GitHub repository with branching, issues and version control established.

Milestone 2 (by 29 June): Stock screener with filtering by at least three metrics including exchange, sector and market capitalisation. Full user authentication including sign up, login and logout. Personal watchlist allowing logged-in users to save and remove stocks. Financial Health Score module calculating a risk rating from three financial ratios. System testing documented in README.

Milestone 3 (by 27 July): Interactive price charts using Chart.js over 1M, 3M and 1Y windows. Stock search with autocomplete. CSV export of watchlist. Fully responsive UI with tooltips explaining every financial term. User testing with external testers with results documented in README.

Project Log
Full project log tracking tasks, dates and hours for each team member is maintained at: 
Hours logged to date:
John Luke Lim Kang: X hours
Jermaine Khor: X hours
