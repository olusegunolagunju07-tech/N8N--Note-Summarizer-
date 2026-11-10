# Notes Summarizer + Quiz Generator (n8n)

An automation that turns lecture notes into a 5-minute revision summary and a 10-question practice quiz, delivered straight to your inbox.

## The problem
Students spend hours condensing long notes before exams. This workflow does the first pass automatically: upload a PDF, get a summary and a quiz by email.

## How it works
1. A student uploads a PDF and their email address through a web form.
2. n8n extracts the text from the PDF.
3. Google Gemini writes a short revision summary.
4. Gemini generates 10 practice questions with answers (conceptual and calculation).
5. A Code node combines both, a Markdown node converts them to HTML, and Gmail sends the result.

![Workflow overview](Overview%20of%20the%20workflow.png)

## Node by node

**1. Form trigger**
![Notes form](Notes%20form.png)

**2. Extract text from the PDF**
![Extract from File](Extract%20file%20node%20.png)

**3. Summary chain**
![Summary node](Summary%20node%20.png)

**4. Quiz chain**
![Quiz node](Quiz%20Generation%20node%20.png)

**5. Combine summary and quiz (JavaScript)**
![Code node](Code%20node%20.png)

**6. Convert Markdown to HTML**
![Convert to HTML](Convert%20to%20HTML%20node%20.png)

**7. Send the email**
![Email node](Email%20node%20.png)

## Tools
n8n · Google Gemini · Gmail · JavaScript (Code node)

## Run it yourself
1. In n8n, choose **Import from file** and select `notes-summarizer-quiz-workflow.json`.
2. Open the Gmail node and both Gemini nodes, and select your own credentials.
3. Open the form trigger's test URL, upload a PDF, and check your inbox.

## What I learned
- How n8n passes data between nodes as JSON items.
- Writing prompts that keep AI output clean (for example, plain-text math instead of LaTeX).
- Converting Markdown to HTML so emails look professional.

## Limitations
- Works best with text-based PDFs of roughly 50 pages or fewer.
- Scanned or photographed notes need a vision-capable model.

## Next steps
- Split long PDFs into chunks and summarize each one.
- Put the answers in a separate answer key section.
