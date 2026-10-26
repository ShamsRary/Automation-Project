# Automation Engineeing: Practicum Proposal

## Student Information
- **Name:** Shams Rary 
- **Instructor:**  Alex Washburn
- **Date:**  10/26/2026

---

## 1. Project Title
Automated Flashcard Pipeline and Vocabulary learning for computer science terms

---

## 2. Overview / Abstract
> Write a brief (1–2 paragraph) summary of the task you plan to automate.  
> Include the purpose of the task and why automation is beneficial.
This will scrap quizlet data or a similar themed website and then pump it into a mysql database. I will then count each of the words/answers and then explained them in context to the other words in the quizlet using ML or some algorithim. Finally an automated email will periodicall sends structured vocabulary for me to learn. I might also put the words into a crossword puzzel for fun. These quizlet should be computer science or tech based.
---

## 3. Task Description
### 3.1 Manual Process Description
> Describe the task as it is currently performed manually.
What are the steps?
A person  searches for study sets on Quizlet, copies terms and definitions one by one into a spreadsheet and then researches context and then  manually sends emails to peers so they can study.
Who performs them?
The student/person? Whoever wants to study
How frequently is the task performed?
Everyday or everyweek for habitual learning.

### 3.2 Problem Statement
> What inefficiencies, challenges, or limitations exist in the current process?
This is highly repetitive, time-consuming, and prone to formatting errors. Also you spend less time studying and more time making the study material.

### 3.3 Automation Goal
> Clearly define what successful automation looks like.
What will be improved? (speed, accuracy, scalability, etc.)
I want a email thats will help me learn terms, and its final output can be done in a fun way like a crossword or just regular words for learning. I also want a idea of how big or niche this term is or if people call it another word.

---

## 4. Inputs to the Task
> Describe all inputs required for the task.


### 4.1 Input Sources
Target study set URLs or search queries (e.g., Quizlet search endpoints or direct set links).
User subscription preferences and email addresses stored in the database.

### 4.2 Input Formats
HTML markup from web pages, JSON payloads, and plain text strings.

### 4.3 Input Frequency
In theory periodic/every day or week in the morning time

---

## 5. Outputs and End States
> Describe the expected results of the automated process.


### 5.1 Outputs
- (e.g., reports, database updates, notifications, API calls)
MySQL table
HTML-formatted email 

### 5.2 Output Formats
- SQL database rows and HTML email/pdf?

### 5.3 End State Conditions
> What conditions indicate the task has completed successfully?
- Web scraper successfully extracts all terms
- Raw data is successfully parsed, validated, and inserted into MySQL staging tables
- ML pipeline or algorithim generates context-aware definitions and updates database records
- Email dispatch service successfully sends the vocabulary

---

## 6. Data Transformations
> Describe how data is processed and transformed throughout the task.

### 6.1 Transformation Steps
- **Input Cleaning:** Strip HTML tags and trim whitespace
- **Parsing:** Isolate key terms
- **Filtering:** Duplicate records, validate definition
- **Context:** Feed terms and raw definitions into a language model or some other algorithim
- **Formatting:** Map enriched fields into relational SQL schema formats and render HTML templates for email digests.

### 6.2 Transformation Examples
> Provide at least one concrete example:
Data
HTML Tag 1 who is the best teacher
HTML Tag 2 the best teacher is Alex

Step 1 extract answer
HTML Tag2 Alex!!!

Step 2 parse out the answer
Alex

Step 3 put into database
sql insert data

step 4
ML who is Alex and why is he the best

step 5
email why alex is the best teacher

## 7. Proposed Automation Approach
> Explain how you plan to automate the task.


### 7.1 Techniques
- (e.g., web scraping, API interaction, scripting, scheduling, event-driven automation, RPA)
- Web scraping and parsing
- REST API interaction
- Relational database modeling
- LLM
- Scheduled script execution

### 7.2 Tools and Technologies
- Programming languages: Python
- Libraries/frameworks:BeautifulSoup4
- External services/APIs:SMTP email provider
- Operating system tools:Task Scheduler or docker

### 7.3 System Architecture (Optional)
> Describe how components interact (you may include a diagram if desired).
[Web Target / Quizlet URL]
        │
        ▼
[Python Scraper & Cleaner]
        │
        ▼
[MySQL Staging DB]
        │
        ▼
[ML Processing Engine (Context Generation)]
        │
        ▼
[MySQL Master DB (Enriched Records)]
        │
        ▼
[SMTP Email Dispatcher]
        │
        ▼
[User Inbox]

## 8. Pseudocode for Automated Task
> Provide high-level pseudocode that outlines the logic of your automation.
> This can look like any programming language that you are comfortable with.

```
    FUNCTION scrape_quizlet(url):
        response = HTTP_GET(url)
        IF response.status_code == 200 THEN
            soup = PARSE_HTML(response.text)
            terms = EXTRACT_ELEMENTS(soup, class="term-definition-pairs")
            RETURN terms
        ELSE
            LOG error "Failed to fetch URL"
            RETURN empty list
        END IF
    END FUNCTION

    FUNCTION enrich_with_ml(term_list):
        enriched_data = []
        FOR item IN term_list:
            prompt = BUILD_PROMPT(item.term, item.definition)
            contextual_result = LLM_INFERENCE(prompt)
            enriched_item = MERGE(item, contextual_result)
            APPEND enriched_item TO enriched_data
        END FOR
        RETURN enriched_data
    END FUNCTION

    ##then email logic
```

> Expand and customize this pseudocode to reflect your specific task.

# 9. Testing and Validation Plan

- **Test cases:**
  1. Scrape a valid public Quizlet
  2. Test scraper against invalid URLs
  3. Confirm email formatting
- **Expected vs. actual results:** Ensure scraped term counts match database record counts
- **Error handling strategies:** parse dont validate

---

## 10. References (Optional)

---

## Instructor Feedback (To be completed by instructor)
- Approval Status:
- Comments:
- Suggested Improvements:
