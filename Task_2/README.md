# **Assignment Report**  
**Title:** Pitch Deck Analysis using PaddleOCR and Gemini API  

---

## **1. Objective**  
The objective of this assignment is to extract text from a PDF pitch deck using **PaddleOCR**, preprocess the text, evaluate the content based on predefined section patterns, calculate a pitch score, and generate an analysis report using the **Gemini API** and **ReportLab**.  

---

## **2. Tools and Libraries Used**  
The following tools and libraries were used to implement the solution:  
- **PaddleOCR** – Used for extracting text from images within the PDF.  
- **PyMuPDF** – Used for reading and processing PDF files.  
- **OpenCV** – Used for image processing and conversion.  
- **NumPy** – Used for handling multi-dimensional image data.  
- **Re (Regular Expressions)** – Used for text preprocessing and pattern matching.  
- **Google Generative AI (Gemini API)** – Used for generating feedback on the pitch deck content.  
- **Markdown and BeautifulSoup** – Used for formatting the extracted text and feedback.  
- **ReportLab** – Used for generating the final PDF report.  

---

## **3. Methodology**  

### **3.1. Extracting Text using PaddleOCR**  
- The input PDF file is loaded using **PyMuPDF**.  
- Each page is processed and converted into an image using **OpenCV**.  
- The image is passed to the **PaddleOCR** model, which extracts text from the image.  
- The extracted text from all pages is combined into a single string.  

---

### **3.2. Preprocessing the Extracted Text**  
- The extracted text is cleaned by:  
  - Removing extra whitespace and line breaks.  
  - Removing special characters and punctuation marks (except for `,` and `.`).  
  - Converting the text to lowercase for uniform processing.  

---

### **3.3. Feature Engineering and Assigning Weights**  
A set of predefined section patterns is defined to identify the presence of key pitch deck components:  
| Section | Pattern Example |  
|---------|-----------------|  
| Problem | problem, pain point, challenge |  
| Solution | solution, approach, how it works |  
| Market | market, industry, competition |  
| Business Model | business model, revenue, monetization |  
| Financials | financials, funding, revenue, expenses |  
| Team | team, founder, experience |  

- Each section is assigned a binary value (`1` or `0`) based on the presence of these terms in the extracted text using regular expressions.  
- The presence of a term increases the section score, which contributes to the overall pitch score.  

---

### **3.4. Scoring Model**  
The pitch score is computed based on the presence of the key sections, with weights assigned as follows:  

| Section | Weight |  
|---------|--------|  
| Problem | 0.20 |  
| Solution | 0.20 |  
| Market | 0.15 |  
| Business Model | 0.15 |  
| Financials | 0.15 |  
| Team | 0.15 |  

- The total pitch score is calculated as:  
\[
\text{Pitch Score} = \sum_{i=1}^{6} (Section\_Presence_i \times Weight_i) \times 100
\]  
- A higher pitch score reflects a well-structured and complete pitch deck.  

---

### **3.5. Feedback Generation using Gemini API**  
- The extracted text is passed to the **Gemini API** with a prompt that asks for an evaluation of the pitch deck.  
- The API provides feedback on the following aspects:  
  - **Strengths** – Identifies well-defined sections and clear content.  
  - **Weaknesses** – Points out missing or unclear sections.  
  - **Suggestions** – Provides recommendations to improve the content and structure.  

---

### **3.6. Report Generation**  
- The generated feedback and pitch score are converted into a report using **Markdown** for formatting and **BeautifulSoup** for processing.  
- The report is structured as:  
  - **Pitch Score** – Numerical value based on section completion.  
  - **Strengths** – Summary of well-performing sections.  
  - **Weaknesses** – List of missing or underdeveloped sections.  
  - **Suggestions** – Recommendations for improving the pitch.  
- The final report is generated as a PDF using **ReportLab**.  


