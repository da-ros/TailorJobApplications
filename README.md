
# CrewAI Job Application Tailoring

This project uses a multi-agent system built with CrewAI to tailor resumes to different job postings. The goal is to automate the process of customizing resumes to match job requirements and generate relevant interview preparation materials.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [Agents](#agents)
- [Tasks](#tasks)
- [Running the Crew](#running-the-crew)
- [Outputs](#outputs)
- [License](#license)

## Installation

Ensure you have the necessary libraries installed. If you're running this project on your own machine, you can install the required libraries with:

```bash
pip install crewai==0.28.8 crewai_tools==0.1.6 langchain_community==0.0.29
```

## Usage

1. Clone the repository and navigate to the project directory.
2. Ensure you have your API keys set up for OpenAI and SerperDev.
3. Run the script to start the multi-agent system and generate the tailored resume and interview materials.

## Agents

The project consists of four main agents, each with a specific role:

### 1. Tech Job Researcher
- **Goal:** Analyze job postings to extract key skills, experiences, and qualifications.
- **Tools:** ScrapeWebsiteTool, SerperDevTool

### 2. Personal Profiler for Engineers
- **Goal:** Compile a detailed personal and professional profile from provided URLs and personal write-ups.
- **Tools:** ScrapeWebsiteTool, SerperDevTool, FileReadTool, MDXSearchTool

### 3. Resume Strategist for Engineers
- **Goal:** Tailor the resume to highlight the most relevant skills and experiences based on job requirements.
- **Tools:** ScrapeWebsiteTool, SerperDevTool, FileReadTool, MDXSearchTool

### 4. Engineering Interview Preparer
- **Goal:** Create potential interview questions and talking points based on the tailored resume and job requirements.
- **Tools:** ScrapeWebsiteTool, SerperDevTool, FileReadTool, MDXSearchTool

## Tasks

### 1. Extract Job Requirements
- **Description:** Analyze the job posting URL to extract key skills, experiences, and qualifications.
- **Expected Output:** A structured list of job requirements.

### 2. Compile Comprehensive Profile
- **Description:** Compile a detailed profile using the provided GitHub URL and personal write-up.
- **Expected Output:** A comprehensive profile document.

### 3. Align Resume with Job Requirements
- **Description:** Tailor the resume to highlight the most relevant areas based on job requirements.
- **Expected Output:** An updated resume.

### 4. Develop Interview Materials
- **Description:** Create a set of potential interview questions and talking points.
- **Expected Output:** A document containing key questions and talking points.

## Running the Crew

Set the inputs for the execution of the crew:

```python
job_application_inputs = {
    'job_posting_url': 'https://jobs.lever.co/AIFund/6c82e23e-d954-4dd8-a734-c0c2c5ee00f1?lever-origin=applied&lever-source%5B%5D=AI+Fund',
    'github_url': 'https://github.com/joaomdmoura',
    'personal_writeup': """Noah is an accomplished Software
    Engineering Leader with 18 years of experience, specializing in
    managing remote and in-office teams, and expert in multiple
    programming languages and frameworks. He holds an MBA and a strong
    background in AI and data science. Noah has successfully led
    major tech initiatives and startups, proving his ability to drive
    innovation and growth in the tech industry. Ideal for leadership
    roles that require a strategic and innovative approach."""
}
```

Execute the crew:

```python
result = job_application_crew.kickoff(inputs=job_application_inputs)
```

## Outputs

The system generates two main output files:

- `tailored_resume.md`: The tailored resume highlighting the candidate's qualifications and experiences relevant to the job.
- `interview_materials.md`: A document containing key questions and talking points for interview preparation.

## License

This project is licensed under the MIT License.
