# Reddit Post Summarizer with n8n

Automate your Reddit content consumption with AI-powered summaries! This project extracts top posts from target subreddits, processes them through Google Gemini for intelligent summarization, and stores the results in Google Sheets for easy access and review.

![Reddit Post Summarizer Cover](./images/Reddit%20Post%20Summarizer.png)

---

## Table of Contents

- [Overview](#overview)
- [How It Works](#how-it-works)
  - [Workflow Steps](#workflow-steps)
- [Benefits](#benefits)
- [Requirements](#requirements)
- [Setup Instructions](#setup-instructions)
  - [1. Clone or Import Workflow](#1-clone-or-import-workflow)
  - [2. Connect Reddit API](#2-connect-reddit-api)
  - [3. Connect Google Gemini](#3-connect-google-gemini)
  - [4. Connect Google Sheets](#4-connect-google-sheets)
  - [5. Customize Subreddit Targets](#5-customize-subreddit-targets)
  - [6. Schedule the Trigger](#6-schedule-the-trigger)
  - [7. Test the Workflow](#7-test-the-workflow)
- [Customization](#customization)
  - [Subreddit Configuration](#subreddit-configuration)
  - [AI Summary Customization](#ai-summary-customization)
  - [Google Sheets Structure](#google-sheets-structure)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## Overview

**Reddit Post Summarizer** is an n8n workflow designed for content creators, researchers, and Reddit enthusiasts. It:

- Automatically fetches top posts from specified subreddits on a daily basis
- Processes post content through Google Gemini AI for intelligent summarization
- Converts Reddit posts into concise, informative summaries
- Stores structured summaries in Google Sheets for easy access and organization
- Runs on a scheduled basis to keep you updated with the latest Reddit insights

---

## How It Works

![Subreddit Top Post Summarizer Workflow](./images/Subreddit%20Top%20Post%20Summarizer.png)

### Workflow Steps

1. **Scheduled Trigger**
   - Initiates the workflow nightly at 6:00 PM (configurable timing)

2. **Get Many Posts (Reddit)**
   - Retrieves top posts from the target subreddit (default: r/n8n)
   - Fetches up to 5 posts with "top" category filter

3. **Split Out**
   - Separates post content and titles for individual processing
   - Ensures each post is handled independently

4. **Generate Summary (LLM Chain)**
   - Sends post title and content to Google Gemini AI
   - Uses structured prompts for consistent summary generation
   - Processes content through LangChain integration

5. **Structured Output Parser**
   - Ensures AI responses follow the required JSON format
   - Validates output structure for reliable data processing

6. **Google Gemini Chat Model**
   - Provides the AI language model for content summarization
   - Handles the actual text processing and summary generation

7. **Append or Update Row in Sheet**
   - Saves summaries to Google Sheets with metadata
   - Includes title, content, summary, and timestamp
   - Prevents duplicates by matching on post titles

---

## Benefits

- **Saves time** reading full Reddit posts while maintaining understanding
- **Delivers concise daily insights** from your favorite subreddits
- **Centralizes summaries** for easy access and reference
- **Enhances content understanding** with intelligent AI assistance
- **Automates Reddit content consumption** for busy professionals
- **Maintains historical record** of summarized posts

---

## Requirements

- [n8n](https://n8n.io/) installation or cloud account
- Reddit account with API access (OAuth2 credentials)
- Google account with access to Gemini AI API
- Google Sheets account for storing summaries
- Target subreddits you want to monitor and summarize

---

## Setup Instructions

### 1. Clone or Import Workflow

- Download or import the attached `Subreddit Top Post Summarizer.json` workflow in your n8n instance
- Use the Visual editor or Desktop version for easy setup

### 2. Connect Reddit API

- Add your Reddit OAuth2 credentials in n8n
- Configure the Reddit node with your preferred subreddit targets
- Ensure proper API permissions for reading subreddit posts

### 3. Connect Google Gemini

- Add your Google/Gemini AI credentials in n8n
- Configure the AI node with your preferred model settings
- Set appropriate rate limits and API quotas

### 4. Connect Google Sheets

- Add your Google Sheets credentials to the workflow
- Configure the sheet ID and worksheet name for storing summaries
- Ensure proper permissions for creating and updating records

### 5. Customize Subreddit Targets

- Edit the subreddit parameter in the Reddit node
- Change from "n8n" to your preferred subreddit(s)
- Adjust the post limit and category filters as needed

### 6. Schedule the Trigger

- Configure the schedule node for your preferred run frequency
- Default is nightly at 6:00 PM, but you can adjust this
- Consider your timezone and when you want to receive summaries

### 7. Test the Workflow

- Run the workflow manually to verify all connections
- Check Google Sheets for properly formatted summary records
- Monitor AI processing and content quality

---

## Customization

### Subreddit Configuration

Configure your target subreddits by editing the Reddit node:

```javascript
// Example subreddit configuration
const subreddit = "programming"; // Change to your preferred subreddit
const postLimit = 10; // Increase for more posts
const category = "top"; // Options: hot, new, top, rising
```

### AI Summary Customization

Customize the Gemini AI prompt for different summary styles:

**Concise Summary**: "Provide a 2-3 sentence summary of the key points in this Reddit post."

**Detailed Analysis**: "Summarize this Reddit post in 4-5 sentences, highlighting main arguments and community insights."

**Technical Focus**: "Extract the key technical insights and practical applications from this Reddit post."

### Google Sheets Structure

Your Google Sheets should include these columns for optimal organization:

- **Title**: Reddit post headline
- **Content**: Original post content
- **Summary**: AI-generated summary
- **Date**: Processing timestamp

The workflow automatically creates this structure and prevents duplicate entries by matching on post titles.

---

## Troubleshooting

- **Reddit API errors**: Verify OAuth2 credentials and API permissions
- **Gemini AI failures**: Check API quotas and authentication
- **Google Sheets connection issues**: Verify credentials and sheet permissions
- **Content processing errors**: Review AI prompt formatting and output parsing
- **Workflow scheduling problems**: Check n8n instance status and cron expressions

---

## Contributing

Contributions and suggestions are welcome!  
Fork the repo, submit issues, or create pull requests for workflow improvements.

---

## License

This project is licensed under the MIT License.

---

## Contact

- **Email:** nebeyoumusie@gmail.com
- **LinkedIn:** [LinkedIn](https://www.linkedin.com/in/nebeyou-musie)
- **X(Twitter):** [X](https://x.com/NebeyouMusie)
- **Upwork:** [Upwork](https://www.upwork.com/freelancers/~017ff01729e3cd26e0?mp_source=share)
- **My Agency:** [Fuzion Tech Website](https://fuzion-tech.com/) or [Fuzion Tech on Upwork](https://www.upwork.com/agencies/1948388369189366041/)

---

**Skills & Technologies:**  
`n8n`, `Reddit API`, `Google Gemini`, `AI Automation`, `Content Summarization`

---

**Enjoy automated Reddit insights and AI-powered content summaries!**

---

> _For any issues, please contact the project maintainer or open an issue on your workflow repository.
