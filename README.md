# AI-Powered Resume Formatter

## Overview

This project is a web application that allows users to upload their resume in PDF format, select a template, and then generate a formatted resume in PDF. The application leverages the power of AI, specifically the Google Gemini Pro model, for data extraction from the uploaded resume.

## Features

*   **PDF Resume Upload:** Users can upload their existing resumes in PDF format.
*   **AI-Powered Data Extraction:** Utilizes the Google Gemini Pro model to intelligently extract key information from the resume, such as name, contact details, work experience, education, skills, etc.
*   **Template Selection:** Offers a variety of pre-designed resume templates to choose from.
*   **Automated Formatting:** Automatically populates the selected template with the extracted data, creating a well-formatted resume.
*   **PDF Generation:** Generates the final resume as a PDF file, ready for download.
*   **Database Storage:** Resume data, including the extracted text and selected template, is stored in a MongoDB database for record-keeping.
*   **Template preview** Selecting the desired Template from the available ones.
*   **User data peristence** Setting localstorage to keep the selected option in the case of new submission

## Technologies Used

*   **Frontend:**
    *   HTML
    *   CSS
    *   JavaScript
    *   html2pdf.js: For client-side HTML to PDF conversion
*   **Backend:**
    *   Node.js
    *   Express: Web framework for handling API requests
    *   Multer: Middleware for handling file uploads
    *   pdf-parse: Library to extract text content from PDF files
    *   @google-generative-ai: Google's Generative AI SDK for interacting with Gemini Pro
    *   Dotenv: Loads environment variables from a `.env` file
    *   Mongoose: MongoDB ODM for interacting with the database
*   **Database:**
    *   MongoDB

## Setup and Installation

1.  **Clone the repository:**

    ```bash
    git clone [repository_url]
    cd [repository_name]
    ```

2.  **Install dependencies:**

    ```bash
    npm install
    ```

3.  **Configure environment variables:**

    *   Create a `.env` file in the root directory.
    *   Add the following environment variables, replacing the placeholders with your actual values:

        ```
        GEMINI_API_KEY=[Your Google Gemini Pro API Key]
        MONGO_URI=[Your MongoDB Connection String]
        ```

4.  **Start the server:**

    ```bash
    npm start
    ```

5.  **Open the application in your browser:**

    Visit `http://localhost:3000` in your web browser.

## Usage

1.  **Upload your resume:** Click the "Choose File" button and select your resume PDF file.
2.  **Select a template:** Click on a template image to select it.
3.  **Generate PDF:** Click the "Generate PDF" button. The formatted resume will be downloaded as a PDF file.

## API Endpoints

*   `POST /upload`: Handles the resume PDF upload and data extraction.  Requires a `resume` file in the `multipart/form-data` and `template` as a form value.
    *   Returns:
        *   `success: true` and `extractedData` (JSON object with extracted resume information) on success.
        *   `success: false` and an error message on failure.
*   `POST /generateHtml`: Generates the HTML for the selected template with the extracted data. Requires `template` (template ID) and `data` (extracted data JSON) in the request body.
    *   Returns:
        *   `success: true` and `generatedHTML` (HTML content) on success.
        *   `success: false` and an error message on failure.
*   `GET /resumes`: Fetches all resume data from the database.
    *   Returns:
        *   `success: true` and `data` (array of resume objects) on success.
        *   `success: false` and an error message on failure.

## Project Structure
