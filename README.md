# Reddit to Video Automation (n8n Workflow)

## Overview
This repository contains an n8n workflow designed to assist content creators in repurposing their own Reddit text posts into multimedia formats for accessibility and personal archiving. 

The tool orchestrates a connection between the Reddit Data API and external media synthesis APIs to convert text-heavy discussions into audio-visual summaries.

## Purpose
The primary goal of this automation is **utility and accessibility**:
* **Accessibility:** Converting text-based content into audio/video formats for users who prefer listening over reading.
* **Archiving:** Creating local backups of specific threads in a media format.
* **Content Repurposing:** assisting creators in transforming their *own* text posts into video formats for other platforms.

## Workflow Logic
This tool is built on **n8n** (a workflow automation platform) to handle long-running asynchronous tasks that are not possible on real-time platforms like Devvit.

1.  **Trigger:** The workflow is triggered manually or by a specific saved post event.
2.  **Fetch Data:** Uses the Reddit API to retrieve the text body of a specific post/comment.
3.  **Sanitization:** Cleans the text (removes markdown, URLs) to prepare it for synthesis.
4.  **Media Generation:** Sends the sanitized text to a Text-to-Speech (TTS) and Video Generation API.
5.  **Output:** Saves the resulting media file to local storage or a cloud drive for the user's review.

## Compliance with Reddit API Terms
This project adheres strictly to the **Reddit Responsible Builder Policy**:

* **Rate Limiting:** The workflow is configured with strict throttles (maximum 60 requests/minute) to respect Reddit's API rate limits and prevent server load.
* **Data Retention:** No Reddit user data is permanently stored in a database. Data is processed in-memory solely for the purpose of media generation and then discarded.
* **Privacy:** The tool does not scrape private data, attempt to de-anonymize users, or analyze sensitive user characteristics.
* **Attribution:** The generated output is intended to maintain context and attribution to the original Reddit thread.

## Why n8n?
This tool is built off-platform (outside of Devvit) because video rendering is a long-running process (10-60+ seconds) involving heavy binary payloads (video files), which exceeds the execution time and memory limits of Reddit's native Developer Platform.

## Setup
1.  Import the `workflow.json` file into your n8n instance.
2.  Configure your Reddit API Credentials (Client ID and Secret).
3.  Configure your Media Generation API credentials.
4.  Activate the workflow.

---
**Disclaimer:** This tool is an independent open-source project and is not affiliated with, authorized, maintained, sponsored, or endorsed by Reddit Inc.
