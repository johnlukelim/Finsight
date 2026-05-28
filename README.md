# Finsight - Equity Research, Simplified 
Team: John Luke Lim Kang & Jermaine  Khor | Orbital 2026 | Apollo 11 | Team 7666
Proposed level of acheievement: Apollo 11

# Motivation behind the project
Investors and students in Singapore face a fragmanted research experience. To screen stocks by fundamental metrics, view price history and assess financial health, a student analyst has to jump between multiple platforms. Most of which are either paywalled, US-centric or poorly suited to SGX-listed equities. This process has too many hoops, which unecessarily complicates investing.

Professional tools like Bloomberg termainals and FactSet are inaccessible to most undergraduates. Free alternatives like Yahoo Finance lack the clean, focused interface that a student analyst actually needs. This fragmentation is a real barrier to making informed decisions during investment

FinSight is built to close that gap, and our goal is a simple unified platform that brings together stock screening, fundamental data, price history, and a quantitative financial health indicator. This allows for users, specifically student analysts to develop rigorous, data-driven approches to equity research without needing access to professional or pay-walled tools. 

# Aim
FinSight is a web application for students to research stocks listed on the Singapore Exchange (SGX) and US markets. Users can search for stocks, view clean price charts, and use a colour-coded Financial Health Score to assess whether a company is financially stable. Logged-in users can also maintain a personal watchlist to track stocks they are interested in.

# Features

- Stock Screener | Users can filter SGX and US-listed stocks by exchange, sector, P/E ratio and market capitalisation. Data is fetched live via the yfinance API. This is the primary entry point for users who want to discover stocks matching specific criteria.
- Stock Detail Page | Each stock has a dedicated page showing its current price, price to earnings ratio, earnings per share (EPS), market cap, dividend yield, and 52-week high and low. Every metric has an explanation, making the platform accessible to beginners. Data will be fetched in real time via yfinance (Yahoo! Finance API)
  
- Personal Watchlist | Authenticated users can save stocks to a personal watchlist, add annotations and remove stocks. Watchlist data is a stored in a database.

- Finacial Health Score | A colour-coded risk indicatior (Low, Medium and High) calculated from three financial ratios: debt-to-equity, current ratio and interest coverage ratio. The score is then computed.

# Extension Features 

- Interactive Price Charts | Hostorical closing prices rendered using Chart.js over 1M, 3M and 1Y windows, where users are given the option to toggle between them.

- Stock search | A search bar that suggests stock tickers and company names, using live data

- Watchlist CSV Export | Logged-in users can download their watchlist as a CSV file for use in Excel and other tools.

  
