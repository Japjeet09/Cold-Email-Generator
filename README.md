# Cold-Email-Generator

This project generates cold emails based on job descriptions scraped from a given website's careers page. The system uses LangChain's `llama-3.1` model via the `groq_api_key` for natural language generation, and integrates with a vector database (ChromaDB) to query portfolio links that match the job's required skills. It automates the process of writing professional cold emails tailored to potential clients based on their job postings.

## Features

- **Web Scraping**: Extract job postings from a provided URL.
- **Job Extraction**: Process job descriptions and extract relevant details like role, experience, skills, and job description in JSON format.
- **Cold Email Generation**: Automatically generate a personalized cold email for each job posting, with relevant portfolio links based on the required skills.
- **Portfolio Matching**: Match job skills with corresponding portfolio projects to showcase relevant work.
- **Streamlit Frontend**: User-friendly interface using Streamlit for easy interaction.

## Tech Stack

- **Language Model**: Llama-3.1 (via `groq_api_key`)
- **Framework**: LangChain
- **Frontend**: Streamlit
- **Database**: ChromaDB for vector-based portfolio querying
- **Web Scraping**: WebBaseLoader from LangChain

## Installation

1. **Clone the repository**:

    ```bash
    git clone https://github.com/Japjeet09/Cold-Email-Generator.git
    cd Cold-Email-Generator
    ```

2. **Set up a virtual environment** (optional but recommended):

    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3. **Install the required dependencies**:

    ```bash
    pip install -r requirements.txt
    ```

4. **Set up environment variables**:
   - Create a `.env` file and add your `GROQ_API_KEY`:

    ```bash
    GROQ_API_KEY=your_groq_api_key_here
    ```

5. **Prepare the portfolio CSV**:
   - The portfolio CSV file (`my_portfolio.csv`) should be in `app/resource/` directory, and contain tech stack and portfolio links like so:

    ```csv
    Techstack,Links
    "React, Node.js, MongoDB",https://example.com/react-portfolio
    ```

## Usage

1. **Run the Streamlit app**:

    ```bash
    streamlit run .\app\main.py
    ```

2. **Interacting with the app**:
   - Enter the URL of a job page (e.g., a careers page from a company website).
   - The app will scrape the content and clean the text.
   - It will extract job postings and generate personalized cold emails using LangChain's Llama-3.1 model.
   - The system will query your portfolio for relevant projects based on the skills required in the job posting.
   - The generated email will be displayed on the screen.

## Code Overview

- **chains.py**: Contains the logic for extracting job descriptions and generating emails using the Llama model and LangChain prompts.
- **main.py**: Sets up the Streamlit frontend to take input from the user and handle the workflow.
- **portfolio.py**: Manages portfolio data, storing it in a ChromaDB collection and querying relevant links based on job skills.
- **utils.py**: Includes utility functions such as `clean_text()` to process and clean the scraped text.
