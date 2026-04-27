Michael Ludwikowski
===================

CSCI 496: Senior Portfolio

In partial fulfillment of the requirements for the degree of Bachelor of Science in Computer Science (class of 2026).

[View My GitHub Profile](https://github.com/MichaelLudwikowski)

[Back to Project Repository](../README.md)

---

Main Senior Project
------------------------------

### Stock Trading AI Analyst - Defense Documentation

- **Class:** Senior Project Construction CSCI 498, Senior Project Implementation/Defense CSCI 499
- **Status:** Completed and defended
- **Language(s):** Python, HTML/CSS, JavaScript
- **Tech Stack:** Flask, SQLite, Bokeh, Ollama (Llama 3.2)
- **Repository:** [MLud-CSU-Senior-Project](https://github.com/MichaelLudwikowski/MLud-CSU-Senior-Project)
- **Primary Document Source:** [docs/DefenseDocumentation.md](../docs/DefenseDocumentation.md)

The full defense documentation is included below as the main portfolio artifact.

---------------------------

# Stock Trading AI Analyst - Defense Documentation

Student: Michael Ludwikowski  
Advisor: Dr. Hayes  
Program: B.S. Computer Science  
Date: April 2026  

## Chapter 1: Statement of Purpose (with Problem Statement)

### Purpose
The purpose of this project is to create an educational stock trading platform that helps beginner traders learn stock market concepts, practice decision-making, and understand portfolio risk without using real money. The platform combines fake-money trading, market data, charts, and AI-generated analysis to create a guided learning environment.

### Problem Statement
Many new traders enter the stock market with little practical experience and lose money because they do not understand market behavior, risk management, or trading discipline. Existing tools are often either too advanced for beginners or too simple to provide realistic practice. This project addresses that gap by offering a safe system where users can learn by doing, analyze results, and improve before ever risking real capital.

### Project Objectives
1. Provide a realistic but safe stock trading experience using simulated funds.
2. Support learning through dashboards, charts, portfolio feedback, and guided pages.
3. Integrate AI-based recommendations to explain possible buy, sell, or hold decisions.
4. Store user activity so balances, trades, and portfolio changes can be reviewed.

## Chapter 2: Research and Background

### Domain Background
Stock trading education is difficult because users must learn both technical platform skills and market fundamentals at the same time. Core beginner challenges include:
- understanding volatility and trend behavior
- position sizing and risk control
- interpreting chart movement and recent price history
- avoiding emotional or impulsive decisions

### Technical Background
To support those learning goals, this project combines:
- market data retrieval with caching and fallback behavior
- simulated trade execution with transaction logging
- portfolio value and gain/loss calculations
- AI-assisted prediction output with confidence and risk messaging
- web interface workflows for dashboard, stock browsing, practice mode, and simulation mode

### Technical Expertise Developed

This project required building skills beyond normal class assignments. I had to dive into multiple technical areas to put them into one working system and troubleshoot them together:

- Flask web development:
   I learned how to build a multi-page web app with routes, sessions, and user workflows (login, trading actions, portfolio views, and practice/simulation pages).

- Database design:
   I implemented SQLite tables and operations for users, accounts, holdings, and transactions. This included schema planning, data retrieval, updates after trades, and keeping the stored state consistent with the UI.

- AI integration:
   I integrated a local Ollama model for recommendations and built fallback logic when the AI model is unavailable. This required prompt design, output parsing, error handling, and reliability testing.

- Full-stack integration and testing:
   I connected backend logic, data services, AI output, chart rendering, and frontend display into one workflow. I also built and used test scripts and test cases to validate edge conditions and core features.

This shows how course knowledge in programming, data structures, software engineering, and databases was expanded into a larger, production-style project workflow.


### Key Constraints Discovered
1. Free market-data APIs may have strict request limits and slower refresh times.
2. Some intraday or premium endpoints require paid tiers.
3. Cached data can quickly become stale if refresh logic is not handled carefully.
4. AI output quality depends on historical data quality and prompt design.

## Chapter 3: Project Language(s), Software, and Hardware

### Programming Languages
- Python: Primary implementation language for backend logic, AI integration, data handling, database access, and web routes.
- HTML/CSS/JavaScript: Frontend templates and user interaction.

### Frameworks and Libraries
- Flask: Web framework for routes, templates, and session-based UI flow.
- SQLite: Local database storage for users, accounts, holdings, and transactions.
- Pandas / NumPy: Data manipulation and numeric processing.
- Bokeh: Interactive charting support.
- Ollama (Llama model): AI-assisted stock analysis and recommendation generation.
- Alpha Vantage: HTTP communication for market API calls.
- Pytest: Test execution and validation.

### Development and Runtime Environment
- IDE: Visual Studio Code
- OS: Linux (primary development environment)
- Python Environment: Virtual environment (.venv)
- Source Control: Git/GitHub

### Hardware
- Primary development hardware: personal laptop/desktop class system
- No specialized GPU or cluster hardware required for the main version of the project

## Chapter 4: Project Requirements

### Requirements Development Progression (CSCI 497)

The project requirements were developed in stages instead of being written all at once. I started with a broad idea focused on helping beginner traders learn safely, then narrowed the scope based on advisor feedback and technical research.

As I started planning out the project, I was able to create more practical requirements tied to real system behaviors, such as account management, stock data access, and AI recommendations. As the project progressed, I adjusted the requirements to keep the project in scope with the timeline while prioritizing the most important functionalities.

This progression also helped separate completed features from future enhancements. Core workflows were kept as high priority for the final build, while advanced items such as deeper AI automation and broader account workflows were documented as partial or future work.

### Core Requirements Implemented

1. **Account and user management**
   - user registration and login
   - logout and password reset flow in the web interface
   - account reset back to the default starting balance

2. **Wallet and transaction controls** 
   - initialize new accounts with $1000 in fake money
   - prevent purchases when funds are not available
   - store holdings, balances, and transaction history in SQLite

3. **Stock data and analysis**
   - search stocks by symbol
   - retrieve quote and historical data with caching
   - display historical charts and stock detail information

4. **Trading operations**
   - buy and sell stock through the application
   - update holdings and portfolio value after trades
   - calculate total value and gain/loss information

5. **AI analyst support**
   - generate buy, sell, or hold recommendations
   - include confidence, risk level, and a short rationale

6. **Learning and practice features**
   - learning page for beginner information
   - historical simulation mode
   - practice mode with different difficulty settings

7. **Interface and display**
   - dashboard with balance, holdings, and recent activity
   - portfolio page and stock detail pages
   - interactive charts using Bokeh

8. **Testing and reliability**
   - test plan and written test cases
   - Python test scripts for API and AI integration work
   - transaction and balance validation in code

### Partially Implemented or Future Requirements
- Multiple account support exists in the data model, but the main workflow currently uses one main account.
- AI auto-investing and full AI training/performance tracking are only partially tested.
- Some advanced educational features such as quizzes and broader alert tools are still future work.

### Priority Notes
- Critical priorities include accurate wallet enforcement, core trading operations, and reliable stock information presentation.
- High priorities include dashboard clarity, portfolio analytics, AI-assisted guidance, and database-backed persistence.
- Medium priorities include expanded educational activities and advanced AI or trading options.

---

## Chapter 5: Project Implementation Description and Explanation

The final project was built mainly in Python. The main controller is in src/app.py, where the core parts of the system are connected together. These parts include the trading engine, market data provider, AI prediction engine, simulation mode, practice mode, and the database layer. This made the project easier to organize and test because each major feature is separated into its own module.

The project supports both a command-line version and a Flask web version. The web version is the main interface for the final project because it is easier to demonstrate and gives a clearer view of balances, holdings, charts, and stock details. In the web app, users can register, log in, reset their account, browse stocks, view their portfolio, and make trades. There are also pages for practice mode, simulation mode, and learning content.

Market data is handled through the market_data.py module. The program can request stock quotes and historical data, cache the data, and use fallback behavior if the API is limited or unavailable. This was important because free APIs do not always respond quickly and may have usage limits. The charting portion of the project uses Bokeh so that users can view interactive stock charts instead of only seeing raw numbers.

The AI portion of the project is handled through predictor.py. The system sends recent historical data to a local Ollama model and asks for a recommendation such as BUY, SELL, or HOLD. The result also includes a confidence value, risk level, and short explanation. If the model is not available, the system still works by using a fallback prediction method based on recent price trend data. This made the project more dependable during development and testing.

Another major part of the project is the practice and simulation support. Simulation mode lets the user move through historical market data over time. Practice mode creates a guided environment with synthetic companies and events so the user can practice without depending only on live data. These features support the educational purpose of the project and make it more than a basic buy/sell demo.

Source code repository: https://github.com/MichaelLudwikowski/MLud-CSU-Senior-Project

### Figures Used in This Documentation

Fig 1. Login page (web authentication entry point)

![Fig 1. Login page](../Project%20Explanation%20Pictures/Login%20Page.png)

Fig 2. Dashboard view after login (initial account overview)

![Fig 2. Dashboard view after login](../Project%20Explanation%20Pictures/Dashboard.png)

Fig 3. Stock search page (symbol search and popular stock list)

![Fig 3. Stock search page](../Project%20Explanation%20Pictures/Stock%20Search.png)

Fig 4. Stock detail page for AAPL (quick trade, AI recommendation, and interactive chart)

![Fig 4. AAPL stock detail page](../Project%20Explanation%20Pictures/AAPL%20Page.png)

Fig 5. Dashboard after placing a trade (cash, portfolio value, and transaction log update)

![Fig 5. Dashboard after AAPL trade](../Project%20Explanation%20Pictures/Dashboard%20after%20AAPL.png)

Fig 6. Practice mode setup page (difficulty and session length options)

![Fig 6. Practice mode setup](../Project%20Explanation%20Pictures/Practice%20mode%20page.png)

Fig 7. Practice mode active session (news events, progress, holdings, and gain/loss)

![Fig 7. Practice mode active session](../Project%20Explanation%20Pictures/Practice%20after%20some%20time.png)

Fig 8. Practice stock detail page (generated company, AI recommendation, and chart)

![Fig 8. Practice stock detail page](../Project%20Explanation%20Pictures/Fake%20Stock%20Practice.png)

---

## Chapter 6: Known Limitations and Risk Mitigation

One limitation of the project is that free market-data APIs have request limits. Because of that, the system uses caching and fallback behavior so that it can still show data even when the API cannot be called again right away. This reduces failures during demos and normal use.

Another limitation is that the AI features depend on a local Ollama setup. If Ollama is not running or the model is not installed, the full AI response will not be available. To reduce this problem, the project includes a fallback prediction method based on price trend analysis so that the application can still give a recommendation instead of failing completely.

Some planned features are not fully finished in the current version. Multiple account support exists in the data model but is not fully exposed in the user workflow. Margin trading logic also exists in code but is currently disabled. AI auto-investing and full AI training are only partially implemented. In this defense, those features should be presented as future improvements rather than as completed work.

The project is meant for education, not for real investing. Even when real market data is available, the system should not be treated as financial advice. This keeps the project focused on learning and practice instead of real-money trading.

---

## Chapter 7: Test Results Summary

### Tested Areas with Strongest Coverage

- Account creation and account data persistence
- Wallet enforcement and prevention of invalid trades
- Stock lookup and market data retrieval behavior
- AI recommendation generation with fallback handling

These results support the main goal of the project, which is to provide a safe educational trading platform with portfolio tracking and AI assistance.

### Requirements-to-Testing Traceability

| Requirement Area | Evidence in Test Cases | Coverage Status |
|---|---|---|
| Account Management | TC-001 to TC-006 | Implemented |
| Wallet and Transactions | TC-007 to TC-012 | Implemented |
| Stock Data and Analysis | TC-015, TC-019, TC-047 | Implemented |
| Trading Operations | TC-013, TC-014, TC-017, TC-018, TC-020 | Implemented |
| AI Recommendations | TC-021 to TC-027 | Implemented (fallback supported) |
| Practice and Simulation | TC-028 to TC-032, TC-048 | Partially Implemented (manual-heavy) |
| Interface and Display | TC-033 to TC-035, TC-047, TC-048 | Implemented (primarily manual evidence) |
| Testing and Reliability | TC-036 to TC-046 | Implemented |

### Test Execution Snapshot

- The test documentation currently includes 48 tabbed test cases (TC-001 through TC-048), covering account management, wallet controls, trading flows, AI features, educational features, interface behavior, and reliability scenarios.
- Core workflow testing was prioritized first, especially account creation/login, wallet enforcement, buy/sell behavior, stock lookup, and AI recommendation output.
- Majority of the test-case execution was manual with Python script-based checks being used, depending on the feature area and available automation support.
- The strongest evidence is for core trading, stock data access, and AI recommendation flows, which align directly with the primary educational goals of the project.
- Some advanced and future-facing features (such as deeper AI automation and expanded educational tooling) remain partially implemented and are documented as ongoing work rather than final completed scope.

### Supporting Test Artifacts

- GitHub-friendly test results summary: [docs/TestResultsSummary.md](TestResultsSummary.md)
- Spreadsheet-friendly execution export: [TestCases_Execution_Summary.csv](../TestCases_Execution_Summary.csv)
- Detailed execution worksheet: [TestCases_Execution_Skeleton.txt](../TestCases_Execution_Skeleton.txt)

---

## Chapter 8: Challenges Overcome

One of the first challenges that I faced was API reliability and rate limits. Since free market-data APIs can limit requests or respond slowly, I had to add caching and fallback behavior so the app would still work during demos and testing instead of failing when the API was unavailable.

Another challenge was AI dependency. The AI recommendation feature depends on a local Ollama model, so if the model server is not running or the model is not installed, predictions can fail. To handle this, I used fallback prediction logic so the system can still return a recommendation and keep the user workflow running.

A third challenge was balancing realism with eucational usability. I wanted the platform to feel like a real trading environment, but still be simple enough for beginners. This led to design decisions like fake-money accounts, clear dashboard metrics, practice mode with guided difficulty, and simulation mode for historical learning.

I also had to manage project scope over time. Some features were designed in the data model but not fully exposed in the current user workflow, such as full multi-account operation and deeper AI automation. Instead of forcing unfinished features into the final build, I prioritized making the core flows stable and presentable.

Overall, the main challenge was integration: combining data retrieval, AI analysis, trade execution, persistence, and frontend views into one consistent system. Solving those integration issues was one of the most important outcomes of the project.

---

## Point 9: Future Enhancements

Future work for this project includes finishing multi-account support, improving AI performance tracking, and expanding the educational side of the platform. More detailed alerts, better reporting, and additional learning activities would make the system more useful for beginner traders.

Another improvement would be better handling of real market data, especially around rate limits and refresh timing. The system could also be extended with stronger account security, more advanced portfolio analytics, and better administrative debugging tools.

Overall, the current version already demonstrates the main idea of the project, and future work would build on that foundation rather than restarting from scratch.
- multi-account workflow completion
- improved AI performance tracking and reporting
- expanded educational tools (alerts, quizzes, learning modules)
- security and analytics improvements

---

-------------------------

### Point 10: Supporting Senior Project Artifacts

- [Defense Slides (Marp)](../docs/DefenseSlides.md)
- [Presentation Deck (PPTX)](../docs/Michael%20Ludwikowski%20Final%20Project%20Presentation.pptx)
- [Test Results Summary](../docs/TestResultsSummary.md)
- [Execution Summary CSV](../TestCases_Execution_Summary.csv)
- [Execution Skeleton Worksheet](../TestCases_Execution_Skeleton.txt)

---

Programming Projects
--------------------

### [Name and ID Parser | CSCI 315](project1.md)

### [Website Balancer and Parser | CSCI 315](project2.md)

### [Wikipedia Parser | CSCI 301](project3.md)

### [Go-Fish Project | CSCI 325](project4.md)

---

Ethics Papers
-------------

### [Ethics Behind Copying Others Code](pdf/Michael%20Ludwikowski%20Survey%20of%20Survey%20Scripting%20Languages%20Ethics%20paper.pdf)

- **Class:** CSCI 301, Survey of Scripting Languages
- **Grade:** 100%

### [Software Testing](pdf/Michael%20Ludwikowski%20Ethics%20Paper%20Software%20Testing.pdf)

- **Class:** CSCI 315, Data Structure Analysis
- **Grade:** 100%

### [Coding Ethics in the Workplace](pdf/Michael%20Ludwikowski%20Ethics%20paper%20coding%20ethics%20in%20the%20workspace.pdf)

- **Class:** CSCI 325, Object-Oriented Programming
- **Grade:** 85%

---

Presentations
-------------

### [Canbus Presentation](pdf/Canbus%20assignment.mkv)

- **Class:** CSCI 332, Applied Networking
- **Grade:** 100%

### [Go-Fish Implementation Guide](pdf/uml%20diagram.pptx)

- **Class:** CSCI 325, Object-Oriented Programming
- **Grade:** 70%
