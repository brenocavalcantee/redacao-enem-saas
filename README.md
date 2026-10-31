# Redator AI — Intelligent ENEM Essay Correction Platform

> **About this repository:** : This public repository contains the MVP and proof of concept. The production version is maintained privately to protect intellectual property.

## Overview

**Redator AI** is a SaaS platform that uses artificial intelligence to evaluate ENEM essays, provide personalized feedback, and track student progress.

It combines handwritten text recognition, evaluation based on the five official ENEM competencies, and performance analytics to make exam preparation more accessible and effective.

## The Problem

ENEM 2025 recorded **4.8 million registrations**, with approximately **3.5 million participants on the first day**, when the essay is administered. However, students face several preparation challenges:

- **Expensive and time-consuming corrections:** Limit frequent practice and continuous learning.
- **Lack of progress tracking:** Without organized history, students struggle to identify weaknesses and measure improvement.
- **Increasing competition:** Courses such as Medicine, Computer Science, Artificial Intelligence, and Law demand competitive scores. Essay performance can be a significant differentiator in admissions.

Essay writing also offers a concrete opportunity to improve admission scores: in 2025, only approximately **5.4% of essays scoring above zero achieved 900 points or more**, and only 10 participants received a perfect score of 1,000.

## The Solution

Redator AI provides an integrated environment for essay practice, correction, and performance tracking:

- **Automated correction:** Students upload photos of handwritten essays and receive feedback quickly.
- **Competency-based evaluation:** Scores from 0 to 200 for each of the five competencies, accompanied by comments and improvement suggestions.
- **History and charts:** Records of previous essays and visualizations of score progression over time.
- **Targeted learning:** Identification of strengths and weaknesses to guide study efforts.

## Application Screenshots

<p align="center">
  <img src="https://github.com/user-attachments/assets/751fd9f0-1a40-4cc8-8166-699ded9a3763" alt="Home Dashboard">
</p>
<p align="center">
  <img src="https://github.com/user-attachments/assets/e97275a4-a419-491f-aead-09944877f1bc" alt="Essay Evaluation Result">
</p>
<p align="center">
  <img src="https://github.com/user-attachments/assets/6b40011f-0ccf-40da-acbf-d1604b1e029a" alt="Login Screen">
</p>

## System Overview

![System Diagram](https://github.com/brenimcode/enem-redacao-ai/blob/main/fluxo2.png)

The processing pipeline consists of:

1. **Image Upload:** Students upload an essay image through the React frontend.
2. **Preprocessing and OCR:** The FastAPI backend preprocesses the image and extracts text using Tesseract OCR.
3. **Text Evaluation:** The extracted text is analyzed by a LangChain pipeline using Gemini and the official ENEM criteria.
4. **Feedback Generation:** The model returns structured feedback, including competency scores, comments, and improvement suggestions.
5. **Results and History:** The frontend displays the correction and allows students to review their performance over time.

This architecture combines image processing and language-model analysis to deliver structured, accessible essay feedback.

## Technologies Used

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white&style=for-the-badge)
![LangChain](https://img.shields.io/badge/LangChain-%23000000.svg?style=for-the-badge&logo=langchain&logoColor=white)
![Gemini](https://img.shields.io/badge/Google_Gemini-8E75B2?style=for-the-badge&logo=google-gemini&logoColor=white)
![Tesseract OCR](https://img.shields.io/badge/Tesseract_OCR-4B8BBE?style=for-the-badge)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?logo=fastapi&logoColor=white&style=for-the-badge)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white&style=for-the-badge)
![ReactJS](https://img.shields.io/badge/React-20232A?logo=react&logoColor=61DAFB&style=for-the-badge)

## Core Features

### 1. User Authentication
- User registration and login.
- Bearer-token authentication using JWT.
- Password hashing with bcrypt.
- PostgreSQL-backed user data.
- Request and data validation with Pydantic.

### 2. Essay Submission
- Upload essays in JPG or PNG format.
- File type and size validation (maximum 5 MB).
- Image validation using Pillow.

### 3. Optical Character Recognition (OCR)
- Text extraction from handwritten essay images using Tesseract OCR.
- Portuguese language support.
- Image preprocessing with OpenCV, including grayscale conversion and thresholding.

### 4. AI-Powered Essay Evaluation
- Essay analysis using Gemini through LangChain.
- Evaluation based on the five official ENEM competencies.
- Structured JSON output containing:
  - Individual competency scores.
  - Total score.
  - General feedback and improvement suggestions.

### 5. Performance Tracking
- Access to previous essay corrections.
- Historical competency and total scores.
- Charts to visualize progress over time and identify areas for improvement.

### 6. Request Rate Limiting

To prevent abuse, the system limits requests per user using SlowAPI:
- 5 requests per minute.
- 100 requests per hour.
- 500 requests per day.

### 7. Correction Results Interface
- Clear presentation of individual competency scores.
- Automatically calculated total score.
- General comments and actionable feedback.
